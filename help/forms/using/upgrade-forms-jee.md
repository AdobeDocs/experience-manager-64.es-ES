---
title: Actualización a AEM 6.4 Forms
seo-title: Actualización a AEM 6.4 Forms
description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
seo-description: 'Puede realizar una actualización directa de AEM 6.1 Forms, AEM 6.2 Forms y LiveCycle ES4 SP1 a AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: d2657bc364b7a814fac9228afdec60f96faaf175

---


# Actualización a AEM 6.4 Forms en JEE {#upgrade-to-aem-forms-jee}

Utilice una de las siguientes rutas de actualización, según corresponda para su entorno.

## AEM 6.2 Forms en JEE o AEM 6.3 Forms en JEE > AEM 6.4 Forms en JEE {#aem-forms-jee-62-63-to-64}

Realice el siguiente procedimiento para actualizar los formularios existentes de AEM 6.2 en JEE o AEM 6.3 Forms en JEE a AEM 6.4 Forms en JEE:

1. Descargue el instalador de AEM 6.4 Forms en JEE del sitio web de licencias de [Adobe (LWS)](https://licensing.adobe.com/). Se requiere un contrato de mantenimiento y soporte válido para descargar el instalador.
1. Consulte [Actualización de la lista de comprobación y planificación](https://www.adobe.com/go/learn_aemfroms_upgrade_checklist_63) para conocer las comprobaciones que se deben realizar para garantizar una actualización correcta.
1. Consulte [Preparación de la actualización a AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_63) para conocer y realizar las tareas que garantizan la correcta ejecución de la actualización con un tiempo de inactividad mínimo en el servidor.
1. Según el entorno y el servidor de aplicaciones existentes, elija uno de los siguientes documentos y siga las instrucciones.

   * [Actualización de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms for JBoss](assets/upgrade-jboss.pdf)
   * [Actualización de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms for WebLogic](assets/upgrade-weblogic.pdf)
   * [Actualización de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere.pdf)
   * [Actualización de AEM 6.2 o AEM 6.3 Forms a AEM 6.4 Forms for JBoss Turnkey](assets/upgrade-turnkey.pdf)

## AEM 6.0 Forms en JEE > AEM 6.3 Forms en JEE {#aem-forms-jee-60-to-63}

No está disponible la actualización directa de LiveCycle ES2, LiveCycle ES3, AEM 6.0 Forms y AEM 6.1 Forms a AEM 6.4 Forms. Puede realizar una actualización intermedia a una o varias versiones de LiveCycle o AEM Forms y, a continuación, actualizar desde AEM 6.4 Forms. Para obtener la lista de versiones intermedias e instrucciones de actualización correspondientes, consulte [Elegir una ruta](/help/forms/using/upgrade.md#main-pars-header)de actualización.

## LiveCycle ES4 SP1 > AEM 6.4 Forms en JEE {#livecycle-es4sp1-forms-jee}

Actualizar LiveCycle ES4 SP1 a AEM 6.4 Forms en JEE es una actualización fuera de lugar, ya que implica migrar recursos y datos de versiones anteriores a instancias nuevas (nuevas versiones) de servidores de aplicaciones, sistemas operativos y bases de datos compatibles.

A continuación se ofrece una descripción general del procedimiento para actualizar un servidor LiveCycle ES4 SP1 existente a AEM 6.4 Forms. Para obtener instrucciones detalladas, véanse los documentos enumerados al final del procedimiento.

1. Antes de actualizar:

   1. Descargue el instalador de AEM 6.4 Forms en JEE del sitio web de licencias de [Adobe (LWS)](https://licensing.adobe.com/). Se requiere un contrato de mantenimiento y soporte válido para descargar el instalador.
   1. Decida el tipo de repositorio de contenido (repositorio de CRX) que va a utilizar. Solo unas pocas funciones de AEM Forms en JEE utilizan la persistencia del repositorio de contenido para almacenar contenido y recursos. Instale y configure el repositorio de contenido solo si tiene pensado utilizar estos formularios de AEM en las funciones de JEE:

      * En LiveCycle ES4 SP1, las capacidades de Gestión de correspondencia, Portal de formularios, Espacio de trabajo HTML e Informes de procesos utilizan el repositorio de contenido. Si no ha utilizado estas funciones en LiveCycle ES4 y tiene pensado no utilizarlas en AEM Forms, no es necesario el repositorio de contenido.
      * En AEM Forms, formularios adaptables, administración de correspondencia, formularios HTML5 (conocidos como formularios móviles en LiveCycle ES4 SP1), Forms Portal, HTML Workspace, informes de procesos, flujos de trabajo centrados en formularios en OSGi, las capacidades utilizan el repositorio de contenido. Si planea utilizar AEM Forms para estas funciones, se requiere el repositorio de contenido.
      * No necesita el repositorio de contenido para AEM Forms Document Security.
      Además, el tipo de repositorio de LiveCycle y AEM Forms son diferentes. Para obtener información relacionada y tipos de repositorio disponibles, consulte [Selección de un tipo de persistencia para una instalación](/help/forms/using/choosing-persistence-type-for-aem-forms.md)de AEM Forms.

   1. Cree una copia de seguridad del contenido y los datos de LiveCycle ES4 SP1:

      Cree una copia de seguridad de la base de datos de LiveCycle ES4 SP1, el almacenamiento global de datos (GDS) y el repositorio crx (no es necesario para la seguridad de documentos). Si está actualizando a la persistencia MongoMK o RDBMK, exporte los recursos de administración de correspondencia de LiveCycle ES4 SP1 en un archivo .cmp y los formularios como un paquete de AEM.

   1. Asegúrese de que la plataforma existente (es decir, servidor de aplicaciones, base de datos, sistema operativo, Adobe Acrobat, aplicaciones de terceros y hardware) sea compatible con AEM 6.4 Forms en JEE. Para obtener información sobre hardware y software compatibles, consulte el documento Combinaciones [de plataformas](/help/forms/using/aem-forms-jee-supported-platforms.md) admitidas.

      Si crea una nueva instancia de la base de datos, importe los datos de los que se ha hecho una copia de seguridad en el paso 3 a la base de datos. Para obtener información sobre cómo importar datos a una base de datos, consulte la documentación del proveedor de la base de datos correspondiente.

      >[!NOTE]
      >
      >Si utiliza el formato de persistencia RDBMK, utilice una única base de datos para la persistencia del repositorio y para servicios de documentos que se ejecuten en AEM Forms en JEE.


1. Realice la actualización:

   1. Instale AEM 6.4 Forms en JEE en un nuevo servidor ejecutando el programa de instalación. El instalador coloca todos los archivos necesarios en el equipo, dentro de una estructura de directorio de instalación.
   1. Una vez finalizada la instalación, ejecute **Configuration Manager** para configurar varios módulos de AEM Forms y definir las configuraciones adecuadas. Junto con la configuración, permite especificar la ruta del Almacenamiento de datos global (GDS) y el repositorio crx.

      >[!NOTE]
      >
      > En la pantalla de selección de tareas de actualización, seleccione la opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]** . La opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]** permite al administrador de configuración actualizar de LiveCycle ES4 SP1 a AEM 6.4 Forms.

   1. (No es necesario para el módulo de seguridad de documentos de AEM Forms) Importe contenido en el repositorio de contenido (CRX-Repository) al servidor de AEM 6.4 Forms.

      >[!NOTE]
      >
      >*  Después de actualizar el repositorio crx y de migrar el contenido, cambie la contraseña de la cuenta de administrador. Para obtener instrucciones detalladas, consulte [Cambio de la contraseña de un usuario](/help/sites-administering/granite-user-group-admin.md)existente.


1. Realice las tareas posteriores a la implementación para verificar las credenciales de inicio de sesión, configurar servicios de documentos, administración de correspondencia, seguridad de documentos y mucho más según el caso de uso.
1. Compruebe que el servidor se haya actualizado correctamente:

   Realice algunas operaciones rutinarias en el servidor de AEM Forms actualizado para asegurarse de que el servidor se actualiza correctamente. Puede rellenar y enviar algunos formularios migrados o proteger documentos para garantizar una actualización correcta.

   >[!NOTE]
   >
   >En AEM 6.4 Forms, la estructura del repositorio crx ha cambiado. Después de actualizar a formularios AEM 6.4, utilice las rutas cambiadas para la personalización que vuelva a crear. Para obtener la lista completa de las rutas modificadas, consulte Reestructuración de [repositorios de formularios en AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Según el entorno y el servidor de aplicaciones existentes, elija uno de los siguientes documentos y siga las instrucciones detalladas:**

* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle.pdf)
* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic-livecycle.pdf)
* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle.pdf)
* [Actualización de LiveCycle ES4 SP1 a AEM 6.4 Forms mediante JBoss Turnkey](assets/upgrade-turnkey-livecycle.pdf)

<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

## LiveCycle ES3 > AEM 6.4 Forms en JEE {#livecycle-es3-forms-jee}

Actualizar LiveCycle ES3 a AEM 6.4 Forms en JEE es una actualización fuera de lugar, ya que implica migrar recursos y datos de versiones anteriores a instancias nuevas (nuevas versiones) de servidores de aplicaciones, sistemas operativos y bases de datos compatibles.

A continuación se ofrece una descripción general del procedimiento para actualizar un servidor LiveCycle ES3 existente a AEM 6.4 Forms. Para obtener instrucciones detalladas, véanse los documentos enumerados al final del procedimiento.

1. Antes de actualizar:

   1. Descargue el instalador de AEM 6.4 Forms en JEE del sitio web de licencias de [Adobe (LWS)](https://licensing.adobe.com/). Se requiere un contrato de mantenimiento y soporte válido para descargar el instalador.
   1. Decida el tipo de repositorio de contenido (repositorio de CRX) que va a utilizar. Solo unas pocas funciones de AEM Forms en JEE utilizan la persistencia del repositorio de contenido para almacenar contenido y recursos. Instale y configure el repositorio de contenido solo si tiene pensado utilizar estos formularios de AEM en las funciones de JEE:

      * En AEM Forms, los formularios adaptables, la gestión de correspondencia, los formularios HTML5, Forms Portal, HTML Workspace, los informes de procesos y los flujos de trabajo centrados en formularios en las funciones OSGi utilizan el repositorio de contenido. Si planea utilizar AEM Forms para estas funciones, se requiere el repositorio de contenido.
      * No necesita el repositorio de contenido para AEM Forms Document Security.
      Además, el tipo de repositorio de LiveCycle y AEM Forms son diferentes. Para obtener información relacionada y tipos de repositorio disponibles, consulte [Selección de un tipo de persistencia para una instalación](/help/forms/using/choosing-persistence-type-for-aem-forms.md)de AEM Forms.

   1. Cree una copia de seguridad de la base de datos LiveCycle ES3, Global Data Storage (GDS) y Content Repository (no es necesaria para la seguridad de documentos). Si está actualizando a la persistencia MongoMK o RDBMK, exporte los recursos de administración de correspondencia de LiveCycle ES3 como archivo.
   1. Asegúrese de que la plataforma existente (es decir, servidor de aplicaciones, base de datos, sistema operativo, Adobe Acrobat, aplicaciones de terceros y hardware) sea compatible con AEM 6.4 Forms en JEE. Para obtener información sobre hardware y software compatibles, consulte el documento Combinaciones [de plataformas](/help/forms/using/aem-forms-jee-supported-platforms.md) admitidas.

      Si crea una nueva instancia de la base de datos, importe los datos de los que se ha hecho una copia de seguridad en el paso 3 a la base de datos. Para obtener información sobre cómo importar datos a una base de datos, consulte la documentación del proveedor de la base de datos correspondiente.

      >[!NOTE] Si utiliza el formato de persistencia RDBMK, utilice una sola base de datos para la persistencia del repositorio y para servicios de documentos que se ejecuten en AEM Forms en JEE.


1. Realice la actualización:

   1. Instale AEM 6.4 Forms en JEE en un nuevo servidor ejecutando el programa de instalación. El instalador coloca todos los archivos necesarios en el equipo, dentro de una estructura de directorio de instalación.
   1. Una vez finalizada la instalación, ejecute **Configuration Manager** para configurar varios módulos de AEM Forms y definir las configuraciones adecuadas. Junto con la configuración, permite especificar la ruta del Almacenamiento de datos global (GDS) y el repositorio crx.

      >[!NOTE] En la pantalla de selección de tareas de actualización, seleccione la opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]** . La opción **[!UICONTROL Actualizar desde Adobe Experience Manager Forms 6.2.0]** permite al administrador de configuración actualizar de LiveCycle ES3 a AEM 6.4 Forms.

   1. (No es necesario para el módulo de seguridad de documentos de AEM Forms) Actualice e importe el repositorio de CRX al servidor de AEM 6.4 Forms.

      >[!NOTE] Después de actualizar el repositorio crx y de migrar el contenido, cambie la contraseña de la cuenta de administrador. Para obtener instrucciones detalladas, consulte [Cambio de la contraseña de un usuario](/help/sites-administering/granite-user-group-admin.md)existente.
1. Realice las tareas posteriores a la implementación para verificar las credenciales de inicio de sesión, configurar servicios de documentos, administración de correspondencia, seguridad de documentos y mucho más según el caso de uso.
1. Compruebe que el servidor se haya actualizado correctamente:

   Realice algunas operaciones rutinarias en el servidor de AEM Forms actualizado para asegurarse de que el servidor se actualiza correctamente. Puede rellenar y enviar algunos formularios migrados o proteger documentos para garantizar una actualización correcta.

   >[!NOTE] En AEM 6.4 Forms, la estructura del repositorio crx ha cambiado. Después de actualizar a formularios AEM 6.4, utilice las rutas cambiadas para la personalización que vuelva a crear. Para obtener la lista completa de las rutas modificadas, consulte Reestructuración de [repositorios de formularios en AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

**Según el entorno y el servidor de aplicaciones existentes, elija uno de los siguientes documentos y siga las instrucciones detalladas:**

* [Actualización de LiveCycle ES3 a AEM 6.4 Forms para JBoss](assets/upgrade-jboss-livecycle-es3.pdf)
* [Actualización de LiveCycle ES3 a AEM 6.4 Forms para WebLogic](assets/upgrade-weblogic-livecycle-es3.pdf)
* [Actualización de LiveCycle ES3 a AEM 6.4 Forms for WebSphere](assets/upgrade-websphere-livecycle-es3.pdf)
* [Actualización de LiveCycle ES3 a AEM 6.4 Forms mediante JBoss Turnkey](assets/upgrade-turnkey-livecycle-es3.pdf)
