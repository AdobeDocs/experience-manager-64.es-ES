---
title: Sincronización de usuarios
seo-title: User Synchronization
description: Obtenga información sobre la sincronización de usuarios en AEM.
seo-description: Learn about user synchronization in AEM.
uuid: 0c7c35a3-9fed-4d48-8bd5-7f4382bf5fa3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 707b150b-7759-437f-9150-9f4784856754
exl-id: 537b86f5-ad38-4419-8dde-40ec08091b7e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2529'
ht-degree: 4%

---

# Sincronización de usuarios{#user-synchronization}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

Cuando la implementación es un [publicar granja](/help/sites-deploying/recommended-deploys.md#tarmk-farm), los miembros deben poder iniciar sesión y ver sus datos en cualquier nodo de publicación.

Los usuarios y grupos de usuarios (datos de usuario) creados en el entorno de publicación no son necesarios en el entorno de creación.

La mayoría de los datos de usuario creados en el entorno de creación están pensados para permanecer en el entorno de creación y no se copian en las instancias de publicación.

El registro y las modificaciones realizadas en una instancia de publicación deben sincronizarse con otras instancias de publicación para que tengan acceso a los mismos datos de usuario.

A partir de AEM 6.1, cuando la sincronización de usuarios está habilitada, los datos de usuario se sincronizan automáticamente en las instancias de publicación de la granja y no se crean en el autor.

## Distribución de Sling {#sling-distribution}

Los datos de usuario, junto con sus [ACL](/help/sites-administering/security.md), se almacenan en la variable [Oak Core](/help/sites-deploying/platform.md), la capa debajo de Oak JCR y se accede a ella mediante la variable [API de Oak](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/oak/api/package-tree.html). Con actualizaciones poco frecuentes, es razonable que los datos de usuario se sincronicen con otras instancias de publicación mediante [Distribución de contenido de Sling](https://github.com/apache/sling/blob/trunk/contrib/extensions/distribution/README.md) (Distribución de Sling).

Los beneficios de la sincronización de usuarios mediante la distribución Sling, en comparación con la replicación tradicional, son:

* *usuarios*, *perfiles de usuario* y *grupos de usuarios* creadas en la publicación no se crean en el autor

* La distribución de Sling establece propiedades en eventos jcr, lo que permite actuar dentro de los oyentes de eventos del lado de publicación sin preocuparse por los bucles de replicación infinitos
* La distribución de Sling solo envía datos de usuario a instancias de publicación que no sean de origen, eliminando así el tráfico innecesario
* [ACL](/help/sites-administering/security.md) configurado en el nodo de usuario se incluyen en la sincronización

>[!NOTE]
>
>Si se requieren sesiones, se recomienda utilizar una solución SSO o utilizar una sesión adhesiva y hacer que los clientes inicien sesión si se cambian a otro publicador.

>[!CAUTION]
>
>Sincronización del ***administradores** *grupo no es compatible, incluso cuando la sincronización de usuarios está habilitada. En su lugar, se registrará un error al &quot;importar la comparación de diferencias&quot; en el registro de errores.
>
>Por lo tanto, cuando la implementación es un conjunto de servidores de publicación, si se agrega o elimina un usuario del ***administradores** *grupo, la modificación debe realizarse manualmente en cada instancia de publicación.

## Habilitar sincronización de usuarios {#enable-user-sync}

>[!NOTE]
>
>De forma predeterminada, la sincronización de usuarios es `disabled`.
>
>Habilitar la sincronización de usuarios implica modificar *existente* Configuraciones de OSGi.
>
>No se deben agregar nuevas configuraciones como resultado de habilitar la sincronización de usuarios.

La sincronización de usuarios depende del entorno de creación para administrar las distribuciones de datos de usuario, aunque los datos de usuario no se creen en el autor. Gran parte de la configuración, pero no toda, se realiza en el entorno de creación y cada paso identifica claramente si se va a realizar en el autor o la publicación.

A continuación se indican los pasos necesarios para habilitar la sincronización de usuarios, seguidos de una [Resolución de problemas](#troubleshooting) sección:

### Requisitos previos {#prerequisites}

1. Si los usuarios y grupos de usuarios ya se han creado en un publicador, se recomienda [sincronizar manualmente](#manually-syncing-users-and-user-groups) los datos de usuario se envían a todos los editores antes de configurar y habilitar la sincronización de usuarios.

   Una vez habilitada la sincronización de usuarios, solo se sincronizan los usuarios y grupos recién creados.

1. Asegúrese de que se ha instalado el código más reciente:

* [AEM actualizaciones de la plataforma](https://helpx.adobe.com/es/experience-manager/kb/aem62-available-hotfixes.html)
* [Actualizaciones de AEM Communities](/help/communities/deploy-communities.md#latest-releases)

### 1. Agente de distribución Apache Sling: fábrica de agentes de sincronización {#apache-sling-distribution-agent-sync-agents-factory}

**Habilitar sincronización de usuarios**

* **en author**

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizar `Apache Sling Distribution Agent - Sync Agents Factory`

      * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

         Verificar `name`: **`socialpubsync`**

      * seleccione `Enabled` casilla de verificación
      * select `Save`



![chlimage_1-387](assets/chlimage_1-387.png)

### 2. Crear usuario autorizado {#createauthuser}

**Configuración de permisos**
Este usuario autorizado se utilizará en el paso 3 para configurar la distribución de Sling en el autor.

* **en cada instancia de publicación**

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola de seguridad](/help/sites-administering/security.md)

      * por ejemplo, [http://localhost:4503/useradmin](http://localhost:4503/useradmin)
   * crear un nuevo usuario

      * por ejemplo, `usersync-admin`
   * agregue este usuario al **`administrators`** grupo de usuarios
   * [agregar ACL para este usuario a /home](#addacls)

      * `Allow jcr:all` con restricción `rep:glob=*/activities/*`



>[!CAUTION]
>
>Se debe crear un nuevo usuario.
>
>* El usuario predeterminado asignado es **`admin`**.
>* No use `*communities-user-admin *user*.*`
>


#### Cómo añadir ACL {#addacls}

* CRXDE Lite de acceso

   * por ejemplo, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* select `/home` node
* en el panel derecho, seleccione `Access Control` ficha
* seleccione `+` para agregar una entrada ACL

   * **Principal**: *buscar usuarios creados para sincronización de usuarios*
   * **Tipo**: `Allow`
   * **Privilegios**: `jcr:all`
   * **Restricciones** rep:glob: `*/activities/*`
   * select **OK**

* select **Guardar todo**

![chlimage_1-388](assets/chlimage_1-388.png)

Consulte también

* [Gestión de derechos de acceso](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Sección Resolución de problemas [Modificar excepción de operación durante el procesamiento de respuestas](#modify-operation-exception-during-response-processing).

### 3. Distribución de Adobe Granite: proveedor secreto de transporte de contraseña cifrada {#adobegraniteencpasswrd}

**Configuración de permisos**

Una vez que sea un usuario autorizado, un miembro de **`administrators`**grupo de usuarios, se ha creado en todas las instancias de publicación, que el usuario autorizado debe identificarse como autor con permiso para sincronizar datos de usuario de autor a publicación.

* **en author**

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizar `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`
   * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

      Verificar `property name` : **`socialpubsync-publishUser`**

   * establezca el nombre de usuario y la contraseña en la variable [usuario autorizado](#createauthuser) creado al publicar en el paso 2

      * por ejemplo, `usersync-admin`


![chlimage_1-389](assets/chlimage_1-389.png)

### 4. Agente de distribución Apache Sling: fábrica de agentes de cola {#apache-sling-distribution-agent-queue-agents-factory}

**Habilitar sincronización de usuarios**

* **al publicar** :

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localizar `Apache Sling Distribution Agent - Queue Agents Factory`

      * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

         Verificar `Name` : `socialpubsync-reverse`

      * seleccione `Enabled` casilla de verificación
      * select `Save`
   * **repetir** para cada instancia de publicación



![chlimage_1-390](assets/chlimage_1-390.png)

### 5. Distribución de Adobe Granite - Fábrica de Observadores de Diff {#diffobserver}

**Habilitar la sincronización de grupos**

* **en cada instancia de publicación** :

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localizar `Adobe Granite Distribution - Diff Observer Factory`

      * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

         Verificar `agent name` : `socialpubsync-reverse`

      * seleccione `Enabled` casilla de verificación
      * select `Save`


![chlimage_1-391](assets/chlimage_1-391.png)

### 6. Déclencheur de distribución de Apache Sling: fábrica de Déclencheur programados {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Opcional) modificar el intervalo de sondeo**

De forma predeterminada, el autor sondeará los cambios cada 30 segundos. Para modificar este intervalo :

* **en author**

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizar `Apache Sling Distribution Trigger - Scheduled Triggers Factory`

      * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

         * Verificar `Name` : `socialpubsync-scheduled-trigger`
      * configure la variable `Interval in Seconds` al intervalo deseado
      * select `Save`



![chlimage_1-392](assets/chlimage_1-392.png)

## Configurar para varias instancias de publicación {#configure-for-multiple-publish-instances}

La configuración predeterminada es para una única instancia de publicación. Como el motivo para habilitar la sincronización de usuarios es sincronizar varias instancias de publicación, como para un conjunto de servidores de publicación, las instancias de publicación adicionales deberán agregarse a la fábrica de agentes de sincronización.

### 7. Agente de distribución Apache Sling: fábrica de agentes de sincronización {#apache-sling-distribution-agent-sync-agents-factory-1}

**Añadir instancias de publicación :**

* **en author**

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
   * localizar `Apache Sling Distribution Agent - Sync Agents Factory`

      * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

         Verificar `Name` : `socialpubsync`


![chlimage_1-393](assets/chlimage_1-393.png)

* **Puntos finales del exportador**
Debe haber un punto final de exportador para cada publicador. Por ejemplo, si hay 2 editores, localhost:4503 y 4504, debe haber 2 entradas:

   * http://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse
   * http://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse

* **Puntos finales del importador**
Debe haber un extremo del importador para cada publicador. Por ejemplo, si hay 2 editores, localhost:4503 y 4504, debe haber 2 entradas:

   * http://localhost:4503/libs/sling/distribution/services/importers/socialpubsync
   * http://localhost:4504/libs/sling/distribution/services/importers/socialpubsync

* select `Save`

### 8. Listener de sincronización de usuarios de AEM Communities {#aem-communities-user-sync-listener}

**(Opcional) Sincronizar nodos JCR adicionales**

Si hay datos personalizados que se desea sincronizar en varias instancias de publicación, entonces:

* **en cada instancia de publicación**:

   * iniciar sesión con privilegios de administrador
   * acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

      * por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)
   * localizar `AEM Communities User Sync Listener`
   * seleccione la configuración existente para abrirla y editarla (icono de lápiz)

      Verificar `Name`: `socialpubsync-scheduled-trigger`


![chlimage_1-394](assets/chlimage_1-394.png)

* **Tipos de nodo**

   Esta es la lista de tipos de nodos que se sincronizarán. Cualquier tipo de nodo que no sea sling:Folder debe aparecer aquí (sling:folder se gestiona de forma independiente).

   Lista predeterminada de tipos de nodos para sincronizar:

   * rep:Usuario
   * nt:unstructured
   * nt:resource

* **Propiedades ignorables**

   Esta es la lista de propiedades que se ignorarán si se detecta algún cambio. Los cambios realizados en estas propiedades pueden sincronizarse como un efecto secundario de otros cambios (ya que la sincronización siempre se realiza en el nivel de nodo), pero los cambios realizados en estas propiedades no provocarán por sí mismos la sincronización de déclencheur.

   Propiedad predeterminada para ignorar:

   * cq:lastModified

* **Nodos ignorables**

   Subrutas que se ignorarán por completo durante la sincronización. Nada debajo de estas subrutas se sincronizará en cualquier momento.

   Nodos predeterminados para ignorar:

   * .tokens
   * system

* **Carpetas distribuidas**

   La mayoría de las carpetas sling:Folders se ignoran porque la sincronización no es necesaria. Las pocas excepciones se enumeran aquí.

   Carpetas predeterminadas para sincronizar

   * segmentos/puntuación
   * social/relaciones
   * actividades

### 9. ID de Sling único {#unique-sling-id}

>[!CAUTION]
>
>Si el ID de Sling coincide entre dos o más instancias de publicación, la sincronización de grupos de usuarios fallará.

Si el ID de Sling es el mismo para varias instancias de publicación en un conjunto de servidores de publicación, los grupos de usuarios no se sincronizarán.

Para validar que todos los valores de ID de Sling difieren, en cada instancia de publicación :

1. buscar `http://<host>:<port>/system/console/status-slingsettings`
1. compruebe el valor de **Sling ID**

![chlimage_1-395](assets/chlimage_1-395.png)

Si el ID de Sling de una instancia de publicación coincide con el ID de Sling de cualquier otra instancia de publicación, entonces:

1. detener una de las instancias de publicación que tenga un ID de Sling coincidente
1. en el directorio crx-quickstart/launchpad/felix

   * buscar y eliminar el archivo denominado *sling.id.file*

      * por ejemplo, en un sistema Linux:

         `rm -i $(find . -type f -name sling.id.file)`

      * por ejemplo, en un sistema Windows:

         `use windows explorer and search for *sling.id.file*`

1. iniciar la instancia de publicación

   * al inicio, se le asignará un nuevo ID de Sling

1. valide que la variable **Sling ID** ahora es único

Repita estos pasos hasta que todas las instancias de publicación tengan un ID de Sling único.

## Fábrica de generador de paquetes de almacenamiento {#vault-package-builder-factory}

Para que las actualizaciones se sincronicen correctamente, es necesario modificar el creador de paquetes bóveda para la sincronización de usuarios :

* en cada instancia de publicación AEM
* acceda al [Consola web](/help/sites-deploying/configuring-osgi.md)

   * por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* localice el `Apache Sling Distribution Packaging - Vault Package Builder Factor`

   * `Builder name: socialpubsync-vlt`

* seleccione el icono de edición
* añadir dos `Package Filters` :

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* administración de directivas :

   * para sobrescribir los nodos rep:policy existentes con otros nuevos, agregue un tercer filtro de paquetes :

      * `/home/users|+.*/rep:policy`
   * para evitar que las políticas se distribuyan, establezca

      * `Acl Handling :` `IGNORE`


![chlimage_1-396](assets/chlimage_1-396.png)

## Qué sucede cuando... {#what-happens-when}

### El usuario se registra automáticamente o edita el perfil al publicar {#user-self-registers-or-edits-profile-on-publish}

Por diseño, los usuarios y perfiles creados en el entorno de publicación (registro propio) no aparecen en el entorno de creación.

Cuando la topología es un [publicar granja](/help/sites-deploying/recommended-deploys.md#tarmk-farm) y la sincronización de usuarios se ha configurado correctamente, el *usuario *y *perfil de usuario* se sincroniza en la granja de publicación mediante la distribución Sling.

### Los usuarios o grupos de usuarios se crean mediante la Consola de seguridad {#users-or-user-groups-are-created-using-security-console}

Por diseño, los datos de usuario creados en el entorno de publicación no aparecen en el entorno de creación y viceversa.

Cuando la variable [Administración de usuarios y seguridad](/help/sites-administering/security.md) se utiliza para agregar nuevos usuarios en el entorno de publicación, la sincronización de usuarios sincroniza a los nuevos usuarios y su pertenencia a grupos con otras instancias de publicación, si es necesario. La sincronización de usuarios también sincronizará los grupos de usuarios creados mediante la consola de seguridad.

## Solución de problemas {#troubleshooting}

### Cómo desconectar la sincronización de usuarios {#how-to-take-user-sync-offline}

Para desactivar la sincronización de usuarios, para [quitar un publicador](#how-to-remove-a-publisher) o [sincronizar manualmente datos](#manually-syncing-users-and-user-groups), la cola de distribución debe estar vacía y en silencio.

Para comprobar el estado de la cola de distribución:

* sobre autor:

   * using [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)

      * buscar entradas en `/var/sling/distribution/packages`

         * nodos de carpeta con el patrón `distrpackage_*`
   * using [Administrador de paquetes](/help/sites-administering/package-manager.md)

      * buscar paquetes pendientes (aún no instalados)

         * con el patrón `socialpubsync-vlt*`
         * creado por `communities-user-admin`


Cuando la cola de distribución esté vacía, desactive la sincronización de usuarios :

* en author

   * *desmarque *el `Enabled` casilla de verificación [Agente de distribución Apache Sling: fábrica de agentes de sincronización](#apache-sling-distribution-agent-sync-agents-factory)

Una vez completadas las tareas, para volver a habilitar la sincronización de usuarios :

* en author

   * compruebe el `Enabled` casilla de verificación [Agente de distribución Apache Sling: fábrica de agentes de sincronización](#apache-sling-distribution-agent-sync-agents-factory)

### Diagnóstico de sincronización de usuario {#user-sync-diagnostics}

Diagnóstico de sincronización de usuarios es una herramienta que comprueba la configuración e intenta identificar cualquier problema.

En el autor, simplemente navegue desde la consola principal a través de **Herramientas, Operaciones, Diagnóstico, Diagnóstico de sincronización de usuarios.**

Al entrar simplemente en la consola Diagnóstico de sincronización de usuarios se mostrarán los resultados.

Esto es lo que se muestra cuando la sincronización de usuarios no se ha habilitado :

![chlimage_1-397](assets/chlimage_1-397.png)

#### Cómo ejecutar diagnósticos para editores {#how-to-run-diagnostics-for-publishers}

Cuando el diagnóstico se ejecuta desde el entorno de creación, los resultados de aprobación/error incluirán un [INFORMACIÓN] muestra la lista de instancias de publicación configuradas para su confirmación.

En la lista se incluye una dirección URL para cada instancia de publicación que ejecutará los diagnósticos para esa instancia. El parámetro de URL `syncUser` se anexa a la URL de diagnóstico con su valor establecido en la variable *usuario de sincronización autorizado* creado en [Paso 2](/help/sites-administering/sync.md#createauthuser).

**Nota** : antes de iniciar la dirección URL, la variable *usuario de sincronización autorizado* ya debe haber iniciado sesión en esa instancia de publicación.

![chlimage_1-398](assets/chlimage_1-398.png)

### Configuración añadida incorrectamente {#improperconfig}

Cuando la sincronización de usuarios no funciona, el problema más común es que se han realizado configuraciones adicionales *added*. En su lugar, se debería haber configurado *la configuración predeterminada existente *editado*.

A continuación se muestran las vistas de cómo aparecen las configuraciones predeterminadas editadas en la consola web. Si aparece más de una instancia, se debe eliminar la configuración añadida.

#### (autor) Un agente de distribución Apache Sling: fábrica de agentes de sincronización {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![chlimage_1-399](assets/chlimage_1-399.png)

#### (autor) Distribución de un Adobe Granite: proveedor secreto de transporte cifrado de contraseña {#author-one-adobe-granite-distribution-encrypted-password-transport-secret-provider}

![chlimage_1-400](assets/chlimage_1-400.png)

#### (publicación) Un agente de distribución Apache Sling: fábrica de agentes de cola {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![chlimage_1-401](assets/chlimage_1-401.png)

#### (publicación) Distribución de un Adobe Granite - Fábrica de Observadores de Diff {#publish-one-adobe-granite-distribution-diff-observer-factory}

![chlimage_1-402](assets/chlimage_1-402.png)

#### (autor) Un Déclencheur de distribución de Apache Sling: fábrica de Déclencheur programados {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![chlimage_1-403](assets/chlimage_1-403.png)

### Modificar excepción de operación durante el procesamiento de respuestas {#modify-operation-exception-during-response-processing}

Si lo siguiente está visible en el registro :

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

A continuación, compruebe que la sección [2. Crear usuario autorizado](#createauthuser) se siguió correctamente.

En esta sección se describe la creación de un usuario autorizado, que existe en todas las instancias de publicación, y la identificación de estos en la configuración OSGi de &quot;Proveedor secreto&quot; del autor. De forma predeterminada, el usuario es `admin`.

El usuario autorizado debe hacerse miembro de la función **`administrators`** los permisos y grupos de usuarios de ese grupo no deben modificarse.

El usuario autorizado debe tener explícitamente los siguientes privilegios y restricciones en todas las instancias de publicación :

| **path** | **jcr:all** | **rep:glob** |
|---|---|---|
| /home | X | &amp;ast;/activities/&amp;ast; |
| /home/users | X | &amp;ast;/activities/&amp;ast; |
| /home/groups | X | &amp;ast;/activities/&amp;ast; |

Como miembro de `administrators` , el usuario autorizado debe tener los siguientes privilegios en todas las instancias de publicación :

| **path** | **jcr:all** | **jcr:read** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Error en la sincronización del grupo de usuarios {#user-group-sync-failed}

Si el ID de Sling coincide entre dos o más instancias de publicación, la sincronización de grupos de usuarios fallará.

Consulte la sección [9. ID único de Sling](#unique-sling-id)

### Sincronización manual de usuarios y grupos de usuarios {#manually-syncing-users-and-user-groups}

* en el editor en el que existen usuarios y grupos de usuarios :

   * [si está activado, desactive la sincronización de usuarios](#how-to-take-user-sync-offline)
   * [crear un paquete](/help/sites-administering/package-manager.md#creating-a-new-package) de `/home`

      * al editar el paquete

         * Ficha Filtros : Añadir filtro : Ruta raíz: `/home`
         * Pestaña Avanzado : Manejo de CA : `Overwrite`
   * [exportar el paquete](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)


* en otras instancias de publicación :

   * [importar el paquete](/help/sites-administering/package-manager.md#installing-packages)

Para configurar o habilitar la sincronización de usuarios, vaya al paso 1: [Agente de distribución Apache Sling: fábrica de agentes de sincronización](#apache-sling-distribution-agent-sync-agents-factory)

### Cuando un publicador deja de estar disponible {#when-a-publisher-becomes-unavailable}

Cuando una instancia de publicación deja de estar disponible, no se debe eliminar si vuelve a estar en línea en el futuro. Los cambios se pondrán en cola para el editor y una vez que vuelva a estar en línea, se procesarán.

Si la instancia de publicación nunca volverá a estar en línea, si está sin conexión de forma permanente, debe eliminarse, ya que la acumulación de colas dará como resultado un uso notable del espacio en disco en el entorno de creación.

Cuando un editor está inactivo, el registro de autor tendrá excepciones similares a :

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Cómo quitar un publicador {#how-to-remove-a-publisher}

Para quitar un publicador de la [Agente de distribución Apache Sling: fábrica de agentes de sincronización](#apache-sling-distribution-agent-sync-agents-factory), la cola de distribución debe estar vacía y en silencio.

* en author :

   * [Desconectar sincronización de usuarios](#how-to-take-user-sync-offline)
   * seguir [paso 7](#apache-sling-distribution-agent-sync-agents-factory) para eliminar el publicador de ambas listas de servidores :

      * `Exporter Endpoints`
      * `Importer Endpoints`
   * volver a habilitar la sincronización de usuarios

      * compruebe el `Enabled` casilla de verificación [Agente de distribución Apache Sling: fábrica de agentes de sincronización](#apache-sling-distribution-agent-sync-agents-factory)
