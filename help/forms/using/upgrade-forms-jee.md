---
title: Actualizar a AEM 6.4 Forms
seo-title: Actualizar a AEM 6.4 Forms
description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
seo-description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: ffa45c8fa98e1ebadd656ea58e4657b669ddd830
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 0%

---


# Actualizar a AEM 6.4 Forms en JEE {#upgrade-to-aem-forms-jee}

Utilice una de las siguientes rutas de actualización, según corresponda para su entorno.

## AEM 6.2 Forms en JEE o AEM 6.3 Forms en JEE > AEM 6.4 Forms en JEE {#aem-forms-jee-62-63-to-64}

Realice el siguiente procedimiento para actualizar el Forms existente AEM 6.2 en JEE o el Forms AEM 6.3 en JEE a AEM 6.4 Forms en JEE:

1. Descargue el instalador de Forms AEM 6.4 en JEE desde el [sitio web de licencias de Adobe (LWS)](https://licensing.adobe.com/). Se requiere un contrato de mantenimiento y soporte válido para descargar el instalador.
1. Consulte [Planificación y lista de comprobación de la actualización](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) para obtener más información sobre las comprobaciones que se deben realizar para garantizar una actualización correcta.
1. Consulte [Preparación para la actualización a AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) para conocer y realizar las tareas que aseguran que la actualización se ejecute correctamente con un tiempo de inactividad mínimo en el servidor.
1. Según el entorno y el servidor de aplicaciones existentes, elija uno de los siguientes documentos y siga las instrucciones.

   * [Actualice de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms para JBoss](assets/upgrade-jboss.pdf)
   * [Actualice de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic.pdf)
   * [Actualice de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms para WebSphere](assets/upgrade-websphere.pdf)
   * [Actualice de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms para JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms en JEE > AEM 6.3 Forms en JEE {#aem-forms-jee-60-to-63}

No está disponible la actualización directa de LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms, AEM 6.1 Forms a AEM 6.4 Forms. Puede realizar una actualización intermedia a una o más versiones de LiveCycle o AEM Forms y, a continuación, actualizar desde AEM 6.4 Forms. Para ver la lista de las versiones intermedias y las instrucciones de actualización correspondientes, consulte [Elija una ruta de actualización](upgrade.md).

## LiveCycle ES4 SP1 > AEM 6.4 Forms en JEE {#livecycle-es4sp1-forms-jee}

La actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms en JEE es una actualización fuera de lugar, ya que implica la migración de recursos y datos de versiones anteriores a instancias nuevas (nuevas versiones) de servidores de aplicaciones, sistemas operativos y bases de datos compatibles.

A continuación se ofrece una descripción general del procedimiento para actualizar un servidor LiveCycle ES4 SP1 a Forms AEM 6.4. Para obtener instrucciones detalladas, consulte los documentos enumerados al final del procedimiento.

1. Antes de actualizar:

   1. Descargue el instalador de Forms AEM 6.4 en JEE desde el [sitio web de licencias de Adobe (LWS)](https://licensing.adobe.com/). Se requiere un contrato de mantenimiento y soporte válido para descargar el instalador.
   1. Decida el tipo de repositorio de contenido (repositorio de CRX) que va a utilizar. Solo unas pocas funciones de AEM Forms en JEE utilizan la persistencia del repositorio de contenido para almacenar contenido y recursos. Instale y configure el Repositorio de contenido solo si planea utilizar este AEM Forms en las capacidades de JEE:

      * En LiveCycle ES4 SP1, las funciones de gestión de correspondencia, Forms Portal, HTML Workspace y Sistema de informes de procesos utilizan el repositorio de contenido. Si no utilizó estas funciones en LiveCycle ES4 y planea no utilizarlas en AEM Forms, no es necesario el Repositorio de contenido.
      * En AEM Forms, Forms adaptable, Gestión de correspondencia, Forms HTML5 (conocido como Forms móvil en LiveCycle ES4 SP1), Forms Portal, HTML Workspace, Sistema de informes de procesos,  de flujos de trabajo centrados de Forms en OSGi, las funciones utilizan el repositorio de contenido. Si planea utilizar AEM Forms para estas funciones, se requiere el Repositorio de contenido.
      * No necesita el repositorio de contenido para la seguridad de AEM Forms Documento.

      Además, el tipo de repositorio de LiveCycle y AEM Forms son diferentes. Para obtener información relacionada y tipos de repositorio disponibles, consulte [Elección de un tipo de persistencia para una instalación de AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Cree una copia de seguridad del contenido y los datos de LiveCycle ES4 SP1:

      Cree una copia de seguridad de la base de datos LiveCycle ES4 SP1, el Almacenamiento de datos globales (GDS) y el repositorio crx (no es necesario para la seguridad de documento). Si está actualizando a la persistencia MongoMK o RDBMK, exporte los recursos de gestión de correspondencia de LiveCycle ES4 SP1 en un archivo .cmp y los formularios como un paquete AEM.

   1. Asegúrese de que la plataforma existente (es decir, servidor de aplicaciones, base de datos, sistema operativo, Adobe Acrobat, aplicaciones de terceros y hardware) sea compatible con AEM 6.4 Forms en JEE. Para obtener información sobre el hardware y el software admitidos, consulte el documento [Combinaciones de plataformas admitidas](/help/forms/using/aem-forms-jee-supported-platforms.md).

      Si crea una nueva instancia de la base de datos, importe los datos de los que se ha hecho una copia de seguridad en el paso 3 a la base de datos. Para obtener información sobre cómo importar datos a una base de datos, consulte la documentación del proveedor de la base de datos correspondiente.

      >[!NOTE]
      >
      >Si utiliza el formato de persistencia RDBMK, utilice una sola base de datos para la persistencia del repositorio y los servicios de documento que se ejecutan en AEM Forms en JEE.


1. Realice la actualización:

   1. Instale AEM 6.4 Forms en JEE en un nuevo servidor ejecutando el programa de instalación. El instalador coloca todos los archivos necesarios en el equipo, dentro de una estructura de directorio de instalación.
   1. Una vez finalizada la instalación, ejecute el **Administrador de configuración** para configurar varios módulos de AEM Forms y configurar las configuraciones adecuadas. Junto con la configuración, permite especificar la ruta del Almacenamiento de datos global (GDS) y el repositorio crx.

      >[!NOTE]
      >
      >En la pantalla de selección de Tareas de actualización, seleccione la opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]**. La opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]** permite al administrador de configuración actualizar desde LiveCycle ES4 SP1 a AEM 6.4 Forms.

   1. (No es necesario para el módulo de seguridad de AEM Forms documento) Importe contenido al repositorio de contenido (CRX-Repository) en AEM servidor Forms 6.4.

      >[!NOTE]
      >
      >* Después de actualizar el repositorio crx y de migrar el contenido, cambie la contraseña de la cuenta de administrador. Para obtener instrucciones detalladas, consulte [Cambio de la contraseña de un usuario existente](/help/sites-administering/granite-user-group-admin.md).


1. Realice las tareas posteriores a la implementación para comprobar las credenciales de inicio de sesión, configurar los servicios de documento, la administración de correspondencia, la seguridad de documento y mucho más según el caso de uso.
1. Compruebe que el servidor se haya actualizado correctamente:

   Realice algunas operaciones rutinarias en el servidor AEM Forms actualizado para asegurarse de que el servidor se actualiza correctamente. Puede rellenar y enviar algunos formularios migrados o proteger documentos para garantizar una actualización correcta.

   >[!NOTE]
   >
   >En AEM 6.4 Forms, la estructura del repositorio crx ha cambiado. Después de actualizar a formularios AEM 6.4, utilice las rutas cambiadas para la personalización que vuelva a crear. Para obtener la lista completa de las rutas cambiadas, consulte [Reestructuración del repositorio de Forms en AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Según el entorno y el servidor de aplicaciones existentes, elija uno de los siguientes documentos y siga las instrucciones detalladas:**

* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms para WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Realice la actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms con JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms en JEE {#livecycle-es3-forms-jee}

La actualización de LiveCycle ES3 a AEM 6.4 Forms en JEE es una actualización fuera de lugar, ya que implica la migración de recursos y datos de versiones anteriores a instancias nuevas (nuevas versiones) de servidores de aplicaciones, sistemas operativos y bases de datos compatibles.

A continuación se ofrece una descripción general del procedimiento para actualizar un servidor LiveCycle ES3 existente a AEM 6.4 Forms. Para obtener instrucciones detalladas, consulte los documentos enumerados al final del procedimiento.

1. Antes de actualizar:

   1. Descargue el instalador de Forms AEM 6.4 en JEE desde el [sitio web de licencias de Adobe (LWS)](https://licensing.adobe.com/). Se requiere un contrato de mantenimiento y soporte válido para descargar el instalador.
   1. Decida el tipo de repositorio de contenido (repositorio de CRX) que va a utilizar. Solo unas pocas funciones de AEM Forms en JEE utilizan la persistencia del repositorio de contenido para almacenar contenido y recursos. Instale y configure el Repositorio de contenido solo si planea utilizar este AEM Forms en las capacidades de JEE:

      * En AEM Forms, los flujos de trabajo adaptables Forms, Correspondence Management, HTML5 Forms, Forms Portal, HTML Workspace, Process Sistema de informes y Forms en las funciones OSGi utilizan el repositorio de contenido. Si planea utilizar AEM Forms para estas funciones, se requiere el Repositorio de contenido.
      * No necesita el repositorio de contenido para la seguridad de AEM Forms Documento.

      Además, el tipo de repositorio de LiveCycle y AEM Forms son diferentes. Para obtener información relacionada y tipos de repositorio disponibles, consulte [Elección de un tipo de persistencia para una instalación de AEM Forms](/help/forms/using/choosing-persistence-type-for-aem-forms.md).

   1. Cree una copia de seguridad de la base de datos ES3 de LiveCycle, el Almacenamiento de datos globales (GDS) y el Repositorio de contenido (no necesario para la seguridad de documento). Si está actualizando a la persistencia MongoMK o RDBMK, exporte los recursos de gestión de correspondencia de LiveCycle ES3 como archivo.
   1. Asegúrese de que la plataforma existente (es decir, servidor de aplicaciones, base de datos, sistema operativo, Adobe Acrobat, aplicaciones de terceros y hardware) sea compatible con AEM 6.4 Forms en JEE. Para obtener información sobre el hardware y el software admitidos, consulte el documento [Combinaciones de plataformas admitidas](/help/forms/using/aem-forms-jee-supported-platforms.md).

      Si crea una nueva instancia de la base de datos, importe los datos de los que se ha hecho una copia de seguridad en el paso 3 a la base de datos. Para obtener información sobre cómo importar datos a una base de datos, consulte la documentación del proveedor de la base de datos correspondiente.

      >[!NOTE]
      >
      >Si utiliza el formato de persistencia RDBMK, utilice una sola base de datos para la persistencia del repositorio y para los servicios de documento que se ejecutan en AEM Forms en JEE.


1. Realice la actualización:

   1. Instale AEM 6.4 Forms en JEE en un nuevo servidor ejecutando el programa de instalación. El instalador coloca todos los archivos necesarios en el equipo, dentro de una estructura de directorio de instalación.
   1. Una vez finalizada la instalación, ejecute el **Administrador de configuración** para configurar varios módulos de AEM Forms y configurar las configuraciones adecuadas. Junto con la configuración, permite especificar la ruta del Almacenamiento de datos global (GDS) y el repositorio crx.

      >[!NOTE]
      >
      >En la pantalla de selección de Tareas de actualización, seleccione la opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]**. La opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]** permite al administrador de configuración actualizar desde LiveCycle ES3 a AEM 6.4 Forms.

   1. (No es necesario para el módulo de seguridad de AEM Forms documento) Actualice e importe el repositorio de CRX en AEM servidor Forms 6.4.

      >[!NOTE]
      >
      >Después de actualizar el repositorio crx y de migrar el contenido, cambie la contraseña de la cuenta de administrador. Para obtener instrucciones detalladas, consulte [Cambio de la contraseña de un usuario existente](/help/sites-administering/granite-user-group-admin.md).
1. Realice las tareas posteriores a la implementación para comprobar las credenciales de inicio de sesión, configurar los servicios de documento, la administración de correspondencia, la seguridad de documento y mucho más según el caso de uso.
1. Compruebe que el servidor se haya actualizado correctamente:

   Realice algunas operaciones rutinarias en el servidor AEM Forms actualizado para asegurarse de que el servidor se actualiza correctamente. Puede rellenar y enviar algunos formularios migrados o proteger documentos para garantizar una actualización correcta.

   >[!NOTE]
   >
   >En AEM 6.4 Forms, la estructura del repositorio crx ha cambiado. Después de actualizar a formularios AEM 6.4, utilice las rutas cambiadas para la personalización que vuelva a crear. Para obtener la lista completa de las rutas cambiadas, consulte [Reestructuración del repositorio de Forms en AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Según el entorno y el servidor de aplicaciones existentes, elija uno de los siguientes documentos y siga las instrucciones detalladas:**

* [Actualización de LiveCycle ES3 a AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Actualización de LiveCycle ES3 a AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Actualización de LiveCycle ES3 a AEM 6.4 Forms para WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Actualice de LiveCycle ES3 a AEM 6.4 Forms con JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
