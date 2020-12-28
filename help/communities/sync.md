---
title: Sincronización de usuarios de comunidades
seo-title: Sincronización de usuarios de comunidades
description: Funcionamiento de la sincronización de usuarios
seo-description: Funcionamiento de la sincronización de usuarios
uuid: 5b9bb7b6-9238-41f6-81da-84b9a303b9e2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 32b56b48-75cb-4cc9-a077-10e335f01a35
translation-type: tm+mt
source-git-commit: 5ddbcb2addff2d6e3a3e9d7e100a6d9ba89fdd60
workflow-type: tm+mt
source-wordcount: '2507'
ht-degree: 0%

---


# Sincronización de usuarios de comunidades {#communities-user-synchronization}

## Introducción {#introduction}

En AEM Communities, desde el entorno de publicación (según los permisos configurados), *los visitantes del sitio* pueden convertirse en *miembros*, crear *grupos de usuarios* y editar su *perfil de miembros*.

*Los* datos de usuario son un término utilizado para referirse a  *usuarios*,  *perfiles de* usuario y grupos *de* usuarios.

** La pertenencia es un término utilizado para referirse a  ** los usuarios registrados en el entorno de publicación, en lugar de a los usuarios registrados en el entorno de creación.

Para obtener más información acerca de los datos de usuario, visite [Administración de usuarios y grupos de usuarios](users.md).

## Sincronización de usuarios en una granja de publicaciones {#synchronizing-users-across-a-publish-farm}

Por diseño, los datos de usuario creados en el entorno de publicación no aparecen en el entorno de creación.

La mayoría de los datos de usuario creados en el entorno del autor están pensados para permanecer en el entorno del autor y no se sincronizan ni replican para publicar instancias.

Cuando la [topología](topologies.md) es un [conjunto de servidores de publicación](../../help/sites-deploying/recommended-deploys.md#tarmk-farm), el registro y las modificaciones realizadas en una instancia de publicación deben sincronizarse con otras instancias de publicación. Los miembros deben poder iniciar sesión y ver sus datos en cualquier nodo de publicación.

Cuando la sincronización de usuarios está habilitada, los datos de usuario se sincronizan automáticamente en todas las instancias de publicación del conjunto de servidores.

### Instrucciones de configuración de sincronización de usuarios {#user-sync-setup-instructions}

Para obtener instrucciones detalladas paso a paso sobre cómo habilitar la sincronización en un conjunto de servidores de publicación, consulte

* [Sincronización de usuarios](../../help/sites-administering/sync.md)

## Sincronización del usuario en segundo plano {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **Paquete** VLT: es un archivo zip de todos los cambios realizados en un editor, que deben distribuirse entre los editores. Los cambios realizados en un editor generan eventos que el detector de eventos de cambios selecciona. Esto crea un paquete vlt que contiene todos los cambios.

* **Paquete** de distribución: contiene información de distribución para Sling. Es información sobre dónde debe distribuirse el contenido y cuándo se distribuyó por última vez.

## Qué sucede cuando... {#what-happens-when}

### Publicar sitio desde la consola Sitios de comunidades {#publish-site-from-communities-sites-console}

Cuando se publica un sitio de comunidad desde la consola [Sitios de comunidades](sites-console.md), el efecto es [replicar](../../help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) las páginas asociadas y Sling distribuir los grupos de usuarios de la comunidad creados dinámicamente, incluida su pertenencia.

### El usuario se crea o edita el Perfil al publicar {#user-is-created-or-edits-profile-on-publish}

Por diseño, los usuarios y perfiles creados en el entorno de publicación (por ejemplo, mediante registro propio, inicio de sesión social o autenticación LDAP) no aparecen en el entorno de creación.

Cuando la topología es un [conjunto de servidores de publicación](topologies.md) y la sincronización de usuarios se ha configurado correctamente, el *usuario* y el *perfil de usuario* se sincronizan en el conjunto de servidores de publicación mediante la distribución Sling.

### Se crea un nuevo grupo de comunidad en Publicar {#new-community-group-is-created-on-publish}

Aunque se inicia desde una instancia de publicación, la creación de grupos de comunidad, que da como resultado nuevas páginas de sitio y un nuevo grupo de usuarios, se produce realmente en la instancia de autor.

Como parte del proceso, las nuevas páginas del sitio se replican en todas las instancias de publicación. El grupo de usuarios de la comunidad creado dinámicamente y su pertenencia son Sling distribuidos en todas las instancias de publicación.

### Los usuarios o grupos de usuarios se crean con la Consola de seguridad {#users-or-user-groups-are-created-using-security-console}

Por diseño, los datos de usuario creados en el entorno de publicación no aparecen en el entorno de creación y viceversa.

Cuando se utiliza la consola [Administración de usuarios y seguridad](../../help/sites-administering/security.md) para agregar nuevos usuarios en el entorno de publicación, la sincronización de usuarios sincronizará los nuevos usuarios y su pertenencia a grupos con otras instancias de publicación, si es necesario. La sincronización de usuarios también sincronizará los grupos de usuarios creados mediante la consola de seguridad.

### El usuario publica contenido en la publicación {#user-posts-content-on-publish}

Para el contenido generado por el usuario (UGC), se accede a los datos introducidos en una instancia de publicación a través del [SRP](srp-config.md) configurado.

## Prácticas recomendadas {#bestpractices}

De forma predeterminada, la sincronización de usuarios está **deshabilitada**. Habilitar la sincronización de usuarios implica modificar las configuraciones de OSGi *existentes*. No se deben agregar nuevas configuraciones como resultado de habilitar la sincronización de usuarios.

La sincronización de usuarios depende del entorno de creación para administrar las distribuciones de datos de usuario, aunque los datos de usuario no se hayan creado en el autor.

**Requisitos previos**

1. Si ya se han creado usuarios y grupos de usuarios en un publicador, se recomienda [sincronizar manualmente](../../help/sites-administering/sync.md#manually-syncing-users-and-user-groups) los datos de usuario con todos los editores antes de configurar y habilitar la sincronización de usuarios.

   Una vez habilitada la sincronización de usuarios, solo se sincronizan los usuarios y grupos recién creados.

1. Asegúrese de que se ha instalado el código más reciente:

   * [Actualizaciones de la plataforma AEM](https://helpx.adobe.com/es/experience-manager/kb/aem62-available-hotfixes.html)
   * [Actualizaciones de AEM Communities](deploy-communities.md#latestfeaturepack)

Las siguientes configuraciones son necesarias para habilitar la sincronización de usuarios en AEM Communities. Asegúrese de que estas configuraciones sean correctas para evitar que la distribución de contenido de sling falle.

### Agente de distribución Apache Sling: fábrica de agentes de sincronización {#apache-sling-distribution-agent-sync-agents-factory}

Esta configuración recoge el contenido que se va a sincronizar en los editores. La configuración está en la instancia de Autor. El autor debe realizar un seguimiento de todos los editores que están allí y dónde sincronizar toda la información.

Los valores predeterminados de la configuración son para una sola instancia de publicación. Dado que la sincronización de usuarios resulta útil para sincronizar varias instancias de publicación, como en un conjunto de publicaciones, es necesario agregar más instancias de publicación a la configuración.

**¿Cómo se sincroniza el contenido?**

La instancia de autor indica el punto final del exportador de los editores. Cada vez que se crea o actualiza un usuario en editores específicos (n), el autor obtiene el contenido de los extremos de sus exportadores y [lo envía a otros editores (n-1, que es distinto de los editores desde los que se obtiene el contenido).](sync.md#main-pars-image-1413756164)

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para configurar los agentes de sincronización de Apache Sling

En AEM instancia de autor:

1. Inicie sesión con privilegios de administrador.
1. Acceda a la [Consola Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Localice **[!UICONTROL Agente de distribución Apache Sling - Fábrica de agentes de sincronización]**.

   * Seleccione la configuración existente para abrirla y editarla (icono de lápiz).
   * Verificar nombre: **`socialpubsync`.**
   * Seleccione la casilla **[!UICONTROL Habilitado]**.
   * Seleccione **[!UICONTROL Usar varias colas]**.
   * Especifique **[!UICONTROL Extremos del exportador]** y **[!UICONTROL Extremos del importador]** (puede agregar más extremos del exportador y del importador).

      Estos extremos definen de dónde desea obtener el contenido y desde dónde desea insertar el contenido. El autor obtiene el contenido del extremo del exportador especificado y lo envía a los editores (excepto al editor del que obtuvo el contenido).
   ![sync-agent-facto](assets/sync-agent-fact.png)

### Distribución de granito de Adobe: Proveedor secreto de transporte de contraseña cifrada {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Permite al autor identificar al usuario autorizado, ya que tiene permiso para sincronizar datos de usuario del autor para realizar la publicación.

El [usuario autorizado creado](../../help/sites-administering/sync.md#createauthuser) en todas las instancias de publicación ayuda a los editores a conectarse con el autor y configurar la distribución de Sling en el autor. Este usuario autorizado tiene todas las [ACL](../../help/sites-administering/sync.md#howtoaddacl) necesarias.

Siempre que se vayan a instalar o recuperar datos de los editores, el autor se conecta con los editores mediante las credenciales (nombre de usuario y contraseña) establecidas en esta configuración.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para conectar a un autor con editores mediante un usuario autorizado

En AEM instancia de autor:

1. Inicie sesión con privilegios de administrador.
1. Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md).

   Por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Localice **[!UICONTROL Adobe Granite Distribution - Encrypted Password Transport Secret Provider]**.
1. Seleccione la configuración existente para abrirla y editarla (icono de lápiz).

   Verificar la propiedad `name:` **`socialpubsync`\- `publishUser` .**
1. Establezca el nombre de usuario y la contraseña para el [usuario autorizado](../../help/sites-administering/sync.md#createauthorizeduser).

   Por ejemplo, **`usersync`\-admin**

   ![granite-paswrd-trans](assets/granite-paswrd-trans.png)

### Agente de distribución Apache Sling: fábrica de agentes de cola {#apache-sling-distribution-agent-queue-agents-factory}

Esta configuración se utiliza para configurar los datos que desea sincronizar entre los editores. Cuando se crean o actualizan datos en rutas especificadas en **[!UICONTROL Raíces permitidas]**, se activa &quot;var/community/distribution/diff&quot; y el replicador creado obtiene los datos de un publicador y los instala en otros editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para configurar los datos (rutas de nodos) para sincronizar

En AEM instancia de publicación:

1. Inicie sesión con privilegios de administrador.
1. Acceda a la [Consola Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localice **[!UICONTROL Agente de distribución Apache Sling - Factoría de agentes de cola]**.
1. Seleccione la configuración existente para abrirla y editarla (icono de lápiz).

   Verificar nombre: `socialpubsync` \-inverso.
1. Seleccione la casilla **[!UICONTROL Habilitado]** y guarde.
1. Especifique las rutas de nodo que se replicarán en **[!UICONTROL raíces permitidas]**.
1. Repita el procedimiento para cada instancia `publish`.

   ![queue-agent-facto](assets/queue-agents-fact.png)

### Distribución de granito de Adobe - Fábrica de observación de diferencias {#adobe-granite-distribution-diff-observer-factory}

Esta configuración sincroniza la pertenencia a grupos entre editores.\
Si al cambiar la pertenencia a un grupo en un publicador no se actualiza su pertenencia a otros editores, asegúrese de que **ref:members** se agrega a **nombres de propiedades miradas**.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantizar la sincronización de miembros

En cada instancia de publicación AEM:

1. Inicie sesión con privilegios de administrador.
1. Acceda a la [Consola Web](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/configuring-osgi.html).

   Por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Localice **[!UICONTROL Distribución de granito de Adobe - Fábrica de observación de diferencias]**.
1. Seleccione la configuración existente para abrirla y editarla (icono de lápiz).

   Verifique **[!UICONTROL nombre del agente]**: `socialpubsync` \-reverso&amp;ast;&amp;ast;..
1. Seleccione la casilla **[!UICONTROL Habilitado]**.
1. Especifique **rep`:members`** como `description` para propertyName en **[!UICONTROL nombres de propiedades miradas]** y Guardar.

   ![diff-obs](assets/diff-obs.png)

### Activador de distribución de Apache Sling - Fábrica de activadores programados {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Esta configuración le permite configurar el intervalo de sondeo (después de lo cual el autor hace ping a los editores y extrae los cambios) para sincronizar los cambios entre los editores.

El autor sondea a los editores cada 30 segundos (valor predeterminado). Si hay algún paquete presente en la carpeta */var/sling/distribution/packages/ socialpubsync - vlt /shared*, entonces recuperará esos paquetes e los instalará en otros editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para modificar el intervalo de sondeo

En AEM instancia de autor:

1. Inicie sesión con privilegios de administrador.
1. Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md), por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Localizar **[!UICONTROL Activador de distribución de Apache Sling: Fábrica de activadores programados]**

   * Seleccione la configuración existente para abrirla y editarla (icono de lápiz)
   * Verificar `Name:` **`socialpubsync`\-programador**
   * Establezca el intervalo en segundos en el intervalo deseado y guárdelo.

   ![schedule-desencadenador](assets/scheduled-trigger.png)

### Escucha de sincronización de usuarios de AEM Communities {#aem-communities-user-sync-listener}

Para problemas en la distribución de Sling en los que hay una discrepancia en las suscripciones y, a continuación, compruebe si se han establecido las siguientes propiedades en las configuraciones **[!UICONTROL Listener de sincronización de usuarios de AEM Communities]**:

* NodeTypes
* IgnorableProperties
* Nodos ignorables
* DistributedFolders

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para sincronizar suscripciones, seguimientos y notificaciones

En cada instancia de publicación AEM:

1. Inicie sesión con privilegios de administrador.
1. Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md). Por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Busque **[!UICONTROL Listener de sincronización de usuarios de AEM Communities]**.
1. Seleccione la configuración existente para abrirla y editarla (icono de lápiz).

   Verificar nombre: **`socialpubsync`\-programador-programado**
1. Configure lo siguiente **`NodeTypes`**:

   rep:Usuario

   `nt` :sin estructurar

   `nt` :medio

   rep:ACL

   sling:Folder

   sling:OrderedFolder

   Los tipos de nodo especificados en esta propiedad se sincronizarán y la información de notificaciones (blogs y configuraciones seguidos) se sincronizarán entre diferentes editores.
1. Añada todas las carpetas para sincronizar en **[!UICONTROL DistributedFolders]**. Por ejemplo,

   segmentos/puntuación

   social/relaciones

   actividades

1. Establezca **`ignorablenodes`** en:

   .tokens

   sistema

   rep `:cache` (dado que usamos sesiones adhesivas, no necesitamos sincronizar este nodo con diferentes editores)

   ![user-sync-listner](assets/user-sync-listner.png)

### Id. único de Sling {#unique-sling-id}

AEM instancia de creación utiliza el ID de Sling para identificar de dónde provienen los datos y a qué editores debe (o no necesita) devolver el paquete.

Asegúrese de que todos los editores de un conjunto de servidores de publicación tengan un ID de Sling único. Si el ID de Sling es el mismo para varias instancias de publicación en un conjunto de servidores de publicación, se producirá un error en la sincronización del usuario. Como el autor no sabrá de dónde recuperar el paquete y desde dónde instalarlo.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para garantizar un ID de Sling único de los editores en el conjunto de servidores de publicación

En cada instancia de publicación:

1. Vaya a [https://_host:port_/system/console/status-slingsettings](http://localhost:4503/system/console/status-slingsettings).
1. Compruebe el valor de **[!UICONTROL Sling ID]**.

   ![slingid](assets/slingid.png)

   Si el ID de Sling de una instancia de publicación coincide con el ID de Sling de cualquier otra instancia de publicación, entonces:

1. Detenga una de las instancias de publicación que tenga un ID de Sling coincidente.
1. En el directorio `crx-quickstart/launchpad/felix`, busque y elimine el archivo denominado _sling.id.file.

   *por ejemplo, en un sistema Linux:*

   `rm -i $(find . -type f -name sling.id.file)`

   *por ejemplo, en un sistema Windows:*

   `use windows explorer and search for _sling.id.file_`

1. Inicio de la instancia de publicación. Al iniciar se le asignará un nuevo ID de Sling.
1. Valide que el **[!UICONTROL ID de Sling]** sea ahora único.

Repita estos pasos hasta que todas las instancias de publicación tengan un ID de Sling único.

### Fábrica del generador de paquetes de almacenamiento {#vault-package-builder-factory}

Para que las actualizaciones se sincronizen correctamente, es necesario modificar el creador de paquetes de bóveda para la sincronización del usuario.\
En `/home/users`, se crea un nodo `/rep:cache`. Es una memoria caché que se utiliza para encontrar que si consulta en el nombre principal de un nodo, esta memoria caché se puede utilizar directamente.

La sincronización de usuarios se puede detener si `rep:cache `nodos se sincronizan entre editores.

<!--This section used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Para asegurarse de que las actualizaciones se sincronizan correctamente entre editores

En cada instancia de publicación AEM:

1. Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md), por ejemplo, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr).
1. Busque el **[!UICONTROL Apache Sling Distribution Packaging - Vault Package Builder Factory Builder nombre]**: socialpubsync-vlt.
1. Seleccione el icono de edición.
1. Añada dos Filtros de paquete:

   * `/home/users|-.\*/.tokens`
   * `/home/users|**+**.\*/rep:cache`
1. Gestión de políticas
   * Para sobrescribir los nodos existentes de rep `:policy` con otros nuevos, agregue un tercer filtro de paquete:

      `/home/users|**+**.\*/rep:policy`
   * Para evitar que las directivas se distribuyan, establezca

      Administración de llamada: IGNORE

![vault-package-builder-Factory](assets/vault-package-builder-factory.png)

## Solucionar problemas de distribución de Sling en AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Si la distribución de Sling falla, pruebe los siguientes pasos de depuración:

1. **Compruebe si hay configuraciones [ agregadas ](../../help/sites-administering/sync.md#improperconfig)incorrectamente.** Asegúrese de que no se agreguen ni editen varias configuraciones; en su lugar, se deben editar las configuraciones predeterminadas existentes.
1. **Compruebe las configuraciones**. Asegúrese de que todas las [configuraciones](sync.md#bestpractices) estén correctamente configuradas en la instancia de AEM Author, como se indica en las [optimizaciones](sync.md#main-pars-header-863110628).
1. **Compruebe los permisos** de usuario autorizados. Si los paquetes no están instalados correctamente, compruebe que el [usuario autorizado](../../help/sites-administering/sync.md#createauthuser) creado en la primera instancia de Publish tiene las ACL correctas.

   Para validar esto, en lugar de [usuario autorizado creado](../../help/sites-administering/sync.md#createauthuser) cambie la configuración de [Adobe Granite Distribution - Encrypted Password Transport Secret Provider](../../help/sites-administering/sync.md#adobegraniteencpasswrd) en la instancia de Autor para utilizar las credenciales de usuario administrador. Ahora intente instalar los paquetes de nuevo. Si la sincronización de usuario funciona correctamente con las credenciales de administrador, significa que el usuario de publicación creado no tenía las ACL adecuadas.

1. **Compruebe la configuración** de la fábrica de observación de Diff. Si solo no se sincronizan nodos específicos en la granja de servidores de publicación (por ejemplo, los miembros del grupo no se sincronizan), asegúrese de que la configuración de [Adobe Granite Distribution - Diff Observer Factory](../../help/sites-administering/sync.md#diffobserver) esté habilitada y **rep:members** se definan en **nombres de propiedades miradas**.
1. **Compruebe la configuración del oyente de sincronización de usuarios de AEM Communities.** Si los usuarios creados están sincronizados pero las suscripciones y los siguientes no funcionan, asegúrese de que la configuración del escucha de sincronización de usuarios de AEM Communities tenga:

   * Tipos de nodos: establecidos en **rep:User, nt:unestructure**, **nt:resource**, **rep:ACL**, **sling:Folder** y **sling:OrderedFolder**
   * Nodos ignorables establecidos en **.tokens**, **sistema** y **rep:cache**
   * Carpetas distribuidas: configure las carpetas que desee distribuir

1. **Compruebe los registros generados durante la creación del usuario en la instancia** de publicación. Si las configuraciones anteriores están correctamente configuradas pero la sincronización de usuarios no funciona, compruebe los registros generados al crear el usuario.

   Compruebe si el orden de los registros es el mismo, como se indica a continuación:

   ```shell
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ2: ADD paths=[/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK], user=communities-user-admin
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ3: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy], user=communities-user-admin
   15.05.2016 18:33:01.757 *INFO* [sling-oak-observation-7431] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_ebb27ad9-a861-4405-9342-d64c916654e2:0.0.1
   15.05.2016 18:33:01.820 *INFO* [sling-oak-observation-7422] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_58811273-5861-48fe-95d2-4aff367b99c3:0.0.1
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK/profile]
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ4: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK/profile], user=communities-user-admin
   15.05.2016 18:33:02.273 *INFO* [sling-oak-observation-7430] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337182039_f34f4fa6-10b9-42eb-8740-4da9d4d38f99:0.0.1
   ```

   Para depurar:

   1. Deshabilitar la sincronización de usuarios:
   1. En AEM instancia de autor, inicie sesión con privilegios de administrador.

      1. Acceda a la [Consola Web](../../help/sites-deploying/configuring-osgi.md). Por ejemplo, [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
      1. Localice la configuración **[!UICONTROL Agente de distribución Apache Sling: fábrica de agentes de sincronización]**.

      1. Anule la selección de la casilla **[!UICONTROL Habilitado]**.
      Al desactivar la sincronización de usuarios en la instancia de autor, los extremos (exportador e importador) se desactivan y la instancia de autor es estática. Los paquetes **[!UICONTROL vlt]** no son arrastrados ni recuperados por el autor.

      Ahora, si se crea un usuario en una instancia de publicación, el paquete **[!UICONTROL vlt]** se crea en el nodo */var/sling/distribution/packages/ socialpubsync - vlt /data*. Y si el autor envía estos paquetes a otro servicio. Puede descargar y extraer estos datos para comprobar qué propiedades se insertan en otros servicios.

   1. Vaya a un editor y cree un usuario en el editor. Como resultado, se crean eventos.
   1. Compruebe el [orden de registros](sync.md#troubleshoot-sling-distribution-in-aem-communities), creado al crearse el usuario.
   1. Compruebe si se crea un paquete **[!UICONTROL vlt]** en `/var/sling/distribution/packages/socialpubsync-vlt/data`.
   1. Ahora, habilite la sincronización de usuarios en AEM instancia de autor.
   1. En el editor, cambie los extremos del exportador o del importador en **[!UICONTROL Agente de distribución Apache Sling - Fábrica de agentes de sincronización]**.

      Podemos descargar y extraer datos del paquete para comprobar qué propiedades se insertan en otros editores y qué datos se pierden.


