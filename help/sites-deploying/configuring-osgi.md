---
title: Configuración de OSGi
seo-title: Configuración de OSGi
description: OSGi es un elemento fundamental de la pila tecnológica de Adobe Experience Manager (AEM). Se utiliza para controlar los paquetes compuestos de AEM y su configuración. Este artículo detalla cómo puede administrar los ajustes de configuración de estos paquetes.
seo-description: OSGi es un elemento fundamental de la pila tecnológica de Adobe Experience Manager (AEM). Se utiliza para controlar los paquetes compuestos de AEM y su configuración. Este artículo detalla cómo puede administrar los ajustes de configuración de estos paquetes.
uuid: b39059a5-dd61-486a-869a-0d7a732c3a47
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: d701e4ba-417f-4b57-b103-27fd25290736
feature: Configuring
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 0%

---


# Configuración de OSGi{#configuring-osgi}

[](https://www.osgi.org/) OSGies un elemento fundamental de la pila de tecnología de Adobe Experience Manager (AEM). Se utiliza para controlar los paquetes compuestos de AEM y su configuración.

OSGi &quot;*proporciona los primitivos estandarizados que permiten construir aplicaciones a partir de componentes pequeños, reutilizables y colaborativos. Estos componentes se pueden componer en una aplicación e implementar*&quot;.

Esto permite una administración sencilla de los paquetes, ya que se pueden detener, instalar e iniciar individualmente. Las interdependencias se gestionan automáticamente. Cada componente OSGi (consulte la [Especificación OSGi](https://www.osgi.org/Specifications/HomePage)) está contenido en uno de los distintos paquetes.

Puede administrar los ajustes de configuración de estos paquetes mediante:

* uso de la [consola web de Adobe CQ](#osgi-configuration-with-the-web-console)
* uso de [archivos de configuración](#osgi-configuration-with-configuration-files)
* configuración de [nodos de contenido ( `sling:OsgiConfig`) en el repositorio](#osgi-configuration-in-the-repository)

Cualquiera de los métodos puede utilizarse aunque haya diferencias sutiles, principalmente en relación con los [modos de ejecución](/help/sites-deploying/configure-runmodes.md):

* [Consola web de Adobe CQ](#osgi-configuration-with-the-web-console)

   * La Consola Web es la interfaz estándar para la configuración OSGi. Proporciona una interfaz de usuario para editar las distintas propiedades, donde se pueden seleccionar valores posibles de listas predefinidas.

      Como tal, es el método más fácil de usar.

   * Las configuraciones realizadas con la consola web se aplican inmediatamente y son aplicables a la instancia actual, independientemente del modo de ejecución actual o de los cambios posteriores en el modo de ejecución.

* [archivos de configuración](#osgi-configuration-with-configuration-files)

   * Contiene la configuración definida en la consola web.
   * Se puede incluir en paquetes de contenido para su uso en otras instancias.

* [content-nodes (sling:osgiConfig) en el repositorio](#osgi-configuration-in-the-repository)

   * Esto requiere una configuración manual mediante CRXDE Lite.
   * Debido a las convenciones de nomenclatura de los nodos `sling:OsgiConfig`, puede enlazar la configuración a un [modo de ejecución](/help/sites-deploying/configure-runmodes.md) específico. Incluso puede guardar configuraciones para más de un modo de ejecución en el mismo repositorio.
   * Las configuraciones adecuadas se aplican inmediatamente (depende del modo de ejecución).

Cualquiera que sea el método que utilice, todos estos métodos de configuración:

* Asegúrese de que al copiar o replicar el contenido del repositorio se recrean configuraciones idénticas.
* Permiten comprobar las configuraciones en FileVault o Subversion; para seguridad o para actualizaciones adicionales.
* Se puede guardar en paquetes para utilizarlos al configurar otras instancias.
* Permite realizar implementaciones de configuración mediante secuencias de comandos para asignar los detalles de configuración.

>[!NOTE]
>
>Los detalles de ciertas configuraciones importantes se enumeran en [Configuración de OSGi.](/help/sites-deploying/osgi-configuration-settings.md)

## Configuración de OSGi con la Consola Web {#osgi-configuration-with-the-web-console}

La [consola web](/help/sites-deploying/web-console.md) de AEM proporciona una interfaz estandarizada para configurar los paquetes. La pestaña **Configuration** se utiliza para configurar los paquetes OSGi y, por lo tanto, es el mecanismo subyacente para configurar AEM parámetros del sistema.

Los cambios realizados se aplican inmediatamente a la configuración OSGi relevante, no es necesario reiniciar.

>[!NOTE]
>
>Los cambios realizados en la consola web se guardan en el repositorio como [archivos de configuración](#osgi-configuration-with-configuration-files). Se pueden incluir en paquetes de contenido para su reutilización en instalaciones posteriores.

>[!NOTE]
>
>En la consola web, cualquier descripción que mencione la configuración predeterminada está relacionada con los valores predeterminados de Sling.
>
>Adobe Experience Manager tiene sus propios valores predeterminados, por lo que los valores predeterminados establecidos pueden diferir de los documentados en la consola.

Para actualizar una configuración con la consola web:

1. Acceda a la pestaña **Configuration** de la consola web mediante:

   * Apertura de la consola web desde el vínculo del menú **Herramienta -> Operaciones**. Después de iniciar sesión en la consola, puede utilizar el menú desplegable de:

      **los paquetes >**

   * La dirección URL directa; por ejemplo:

      `http://localhost:4502/system/console/configMgr`
   Se mostrará una lista.

1. Seleccione el paquete que desea configurar mediante:

   * hacer clic en el icono **Edit** para ese paquete
   * haciendo clic en el **Name** del paquete

1. Se abrirá un cuadro de diálogo: Aquí puede editar según sea necesario; por ejemplo, configure **Log Level** en `INFO`:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Las actualizaciones se guardan en el repositorio como [archivos de configuración](#osgi-configuration-with-configuration-files). Para ubicarlos posteriormente (por ejemplo, para incluir en un paquete de contenido para utilizarlo en otra instancia), debe tomar nota de la identidad persistente ( `PID`).

1. Haga clic en **Guardar**.

   Los cambios se aplican inmediatamente a la configuración OSGi relevante del sistema en ejecución, no es necesario reiniciar.

   >[!NOTE]
   >
   >Ahora puede localizar los [archivos de configuración relacionados](#osgi-configuration-with-configuration-files); por ejemplo, para incluir en un paquete de contenido para utilizarlo en otra instancia.

## Configuración de OSGi con archivos de configuración {#osgi-configuration-with-configuration-files}

Los cambios de configuración realizados con la consola web se mantienen en el repositorio como archivos de configuración ( `.config`) en:

`/apps`

Se pueden incluir en paquetes de contenido y reutilizar en otras instancias.

>[!NOTE]
>
>El formato de los archivos de configuración es muy específico; consulte la [documentación de Sling Apache](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format) para obtener más información.
>
>Por este motivo, se recomienda crear y mantener el archivo de configuración realizando cambios reales en la consola web.

La consola web no muestra ninguna indicación de dónde se han guardado los cambios en el repositorio, pero se pueden localizar fácilmente:

1. Cree el archivo de configuración [realizando un cambio inicial en la consola web](#osgi-configuration-with-the-web-console).
1. Abra el CRXDE Lite .
1. En el menú **Herramientas** seleccione **Consulta ...** .
1. Envíe una consulta de **Type** `SQL` para buscar el PID de la configuración que ha actualizado.

   Por ejemplo, **Apache Felix OSGi Management Console** tiene la identidad persistente (PID) de:

   `org.apache.felix.webconsole.internal.servlet.OsgiManager`

   Por lo tanto, la consulta SQL podría ser:

   ```shell
   select * from nt:base where jcr:path like '/apps/%' and contains(*, 'org.apache.felix.webconsole.internal.servlet.OsgiManager')
   ```

1. Se mostrará el nodo del archivo de configuración.

   Para el ejemplo anterior:

   `/apps/system/config/org.apache.felix.webconsole.internal.servlet.OsgiManager.config`

   >[!CAUTION]
   >
   >Puede abrir este archivo para ver los cambios, pero para evitar errores de escritura, se recomienda realizar cambios reales con la consola.

1. Ahora puede crear un paquete de contenido que contenga este nodo y utilizarlo como sea necesario en las demás instancias.

## Configuración de OSGi en el repositorio {#osgi-configuration-in-the-repository}

Además de utilizar la consola web, también puede definir los detalles de configuración en el repositorio. Esto le permite configurar fácilmente los distintos modos de ejecución.

Estas configuraciones se realizan creando `sling:OsgiConfig` nodos en el repositorio para que el sistema haga referencia a ellos. Estos nodos reflejan las configuraciones de OSGi y forman una interfaz de usuario para ellas. Para actualizar los datos de configuración, actualice las propiedades del nodo.

Si modifica los datos de configuración en el repositorio, los cambios se aplican inmediatamente a la configuración OSGi relevante como si los cambios se hubieran realizado utilizando la consola web, con las comprobaciones de validación y coherencia adecuadas. Esto también se aplica a la acción de copiar una configuración de `/libs/` a `/apps/`.

Como el mismo parámetro de configuración puede estar ubicado en varios lugares, el sistema:

* busca todos los nodos de tipo `sling:OsgiConfig`
* filtros según el nombre del servicio
* filtros según el modo de ejecución

>[!NOTE]
>
>Lea también [cómo definir una confinación basada en repositorios para una instancia específica solamente](https://helpx.adobe.com/experience-manager/kb/RunModeDependentConfigAndInstall.html).

### Añadir una nueva configuración al repositorio {#adding-a-new-configuration-to-the-repository}

#### Qué debe saber {#what-you-need-to-know}

Para agregar una nueva configuración al repositorio, debe saber lo siguiente:

1. **Identidad persistente** (PID) del servicio.

   Haga referencia al campo **Configurations** en la consola web. El nombre se muestra entre corchetes después del nombre del paquete (o en **Configuration Information** hacia la parte inferior de la página).

   Por ejemplo, cree un nodo `com.day.cq.wcm.core.impl.VersionManagerImpl.` para configurar **AEM Administrador de versiones de WCM**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Indica si se requiere un [modo de ejecución](/help/sites-deploying/configure-runmodes.md) específico. Cree la carpeta:

   * `config` - para todos los modos de ejecución
   * `config.author` - para el entorno de creación
   * `config.publish` - para el entorno de publicación
   * `config.<run-mode>` - según proceda

1. Si es necesario **Configuration** o **Factory Configuration**.
1. Los parámetros individuales que se van a configurar; incluyendo cualquier definición de parámetro existente que deba recrearse.

   Haga referencia al campo de parámetro individual en la consola web. El nombre se muestra entre corchetes para cada parámetro.

   Por ejemplo, crear una propiedad
   `versionmanager.createVersionOnActivation` para configurar  **Crear versión al activar**.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. ¿Ya existe una configuración en `/libs`? Para enumerar todas las configuraciones en la instancia, utilice la herramienta **Query** en el CRXDE Lite para enviar la siguiente consulta SQL:

   `select * from sling:OsgiConfig`

   Si es así, esta configuración se puede copiar en ` /apps/<yourProject>/` y luego personalizarse en la nueva ubicación.

#### Creación de la configuración en el repositorio {#creating-the-configuration-in-the-repository}

Para añadir la nueva configuración al repositorio:

1. Utilice el CRXDE Lite para desplazarse a:

   ` /apps/<yourProject>`

1. Si no existe, cree la carpeta `config` ( `sling:Folder`):

   * `config` - aplicable a todos los modos de ejecución
   * `config.<run-mode>` : específico para un modo de ejecución determinado

1. En esta carpeta, cree un nodo:

   * Tipo: `sling:OsgiConfig`
   * Nombre: la identidad persistente (PID);

      por ejemplo, para AEM WCM Version Manager use `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Al realizar una configuración de fábrica, añada `-<identifier>` al nombre.
   >
   >Como en: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Donde `<identifier>` se reemplaza por texto libre que debe introducir para identificar la instancia (no puede omitir esta información); por ejemplo:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Para cada parámetro que desee configurar, cree una propiedad en este nodo:

   * Nombre: el nombre del parámetro como se muestra en la consola web; el nombre se muestra entre corchetes al final de la descripción del campo. Por ejemplo, para `Create Version on Activation` use `versionmanager.createVersionOnActivation`
   * Tipo: según proceda.
   * Valor: según sea necesario.

   Solo es necesario crear propiedades para los parámetros que desea configurar, mientras que otros seguirán tomando los valores predeterminados establecidos por AEM.

1. Guarde todos los cambios.

   Los cambios se aplican en cuanto se actualiza el nodo reiniciando el servicio (como sucede con los cambios realizados en la consola web).

>[!CAUTION]
>
>No debe cambiar nada en la ruta `/libs`.

>[!CAUTION]
>
>La ruta completa de una configuración debe ser correcta para que se lea al inicio.

## Detalles de configuración {#configuration-details}

### Orden de resolución al inicio {#resolution-order-at-startup}

Se utiliza el siguiente orden de prioridad:

1. Los nodos del repositorio en `/apps/*/config...`.con el tipo `sling:OsgiConfig` o archivos de propiedad.

1. Nodos de repositorio con tipo `sling:OsgiConfig` en `/libs/*/config...`. (definiciones predeterminadas).

1. Cualquier archivo `.config` de `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. en el sistema de archivos local.

Esto significa que una configuración genérica en `/libs` puede enmascararse con una configuración específica de proyecto en `/apps`.

### Orden de resolución en tiempo de ejecución {#resolution-order-at-runtime}

Los cambios de configuración realizados mientras el sistema ejecuta el déclencheur de una recarga con la configuración modificada.

A continuación, se aplica el siguiente orden de prioridad:

1. La modificación de una configuración en la consola web tendrá efecto inmediato, ya que tiene prioridad en el tiempo de ejecución.
1. Modificar una configuración en `/apps` tendrá efecto inmediato.
1. Modificar una configuración en `/libs` tendrá efecto inmediato, a menos que esté oculta por una configuración en `/apps`.

### Resolución de varios modos de ejecución {#resolution-of-multiple-run-modes}

Para configuraciones específicas del modo de ejecución, se pueden combinar varios modos de ejecución. Por ejemplo, puede crear carpetas de configuración en el siguiente estilo:

`/apps/*/config.<runmode1>.<runmode2>/`

Las configuraciones en dichas carpetas se aplicarán si todos los modos de ejecución coinciden con un modo de ejecución definido al inicio.

Por ejemplo, si se inició una instancia con los modos de ejecución `author,dev,emea`, se aplicarán los nodos de configuración de `/apps/*/config.emea`, `/apps/*/config.author.dev/` y `/apps/*/config.author.emea.dev/`, mientras que los nodos de configuración de `/apps/*/config.author.asean/` y `/config/author.dev.emea.noldap/` no se aplicarán.

Si se aplican varias configuraciones para el mismo PID, se aplica la configuración con el mayor número de modos de ejecución coincidentes.

Por ejemplo, si se inició una instancia con los modos de ejecución `author,dev,emea` y `/apps/*/config.author/` y `/apps/*/config.emea.author/` definen una configuración para\
`com.day.cq.wcm.core.impl.VersionManagerImpl`, se  `/apps/*/config.emea.author/` aplicará la configuración de .

La granularidad de esta regla se encuentra en el nivel de PID.\
No se pueden definir algunas propiedades para el mismo PID en `/apps/*/config.author/` y otras más específicas en `/apps/*/config.emea.author/` para el mismo PID.\
La configuración con el mayor número de modos de ejecución coincidentes será efectiva para todo el PID.

### Configuraciones estándar {#standard-configurations}

La siguiente lista muestra una pequeña selección de las configuraciones disponibles (en una instalación estándar) en el repositorio:

* Autor: AEM filtro WCM:

   `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Publicar: AEM filtro WCM:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Publicar: AEM Estadísticas de página de WCM:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Dado que estas configuraciones residen en `/libs` no deben editarse directamente, sino copiarse en el área de la aplicación ( `/apps`) antes de la personalización.

Para enumerar todos los nodos de configuración en la instancia, utilice la funcionalidad **Query** en el CRXDE Lite para enviar la siguiente consulta SQL:

`select * from sling:OsgiConfig`

### Persistencia de configuración {#configuration-persistence}

* Si cambia una configuración a través de la consola web, (normalmente) se escribe en el repositorio en:

   `/apps/{somewhere}`

   * De forma predeterminada, `{somewhere}` es `system/config`, por lo que la configuración se escribe en

      `/apps/system/config`

   * Sin embargo, si está editando una configuración que inicialmente proviene de otras partes del repositorio: por ejemplo:

      /libs/foo/config/someconfig

      A continuación, la configuración actualizada se escribe en la ubicación original; por ejemplo:

      `/apps/foo/config/someconfig`

* La configuración que cambia `admin` se guarda en archivos `*.config` en:

   ```
      /crx-quickstart/launchpad/config
   ```

   * Este es el área de datos privada del administrador de configuración de OSGi y contiene todos los detalles de configuración especificados por `admin`, independientemente de cómo ingresaron al sistema.
   * Se trata de un detalle de implementación y nunca debe editar este directorio directamente.
   * Sin embargo, es útil conocer la ubicación de estos archivos de configuración para que se puedan realizar copias de seguridad o instalación múltiple:

      * Consola de administración Apache Felix OSGi

         `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * Repositorio de cliente CRX Sling

         `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>Debe ***nunca*** editar las carpetas o archivos en:
>
>`/crx-quickstart/launchpad/config`

