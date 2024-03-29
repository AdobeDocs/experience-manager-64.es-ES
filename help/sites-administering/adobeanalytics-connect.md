---
title: Conectarse a Adobe Analytics y crear marcos
seo-title: Connecting to Adobe Analytics and Creating Frameworks
description: Obtenga información sobre cómo conectar AEM al SiteCatalyst y crear marcos.
seo-description: Learn about connecting AEM to SiteCatalyst and creating frameworks.
uuid: 04325409-435c-4394-9ab7-c9022e19e085
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 88dbfd34-1f8d-47a2-893d-20faf1a80f95
exl-id: 654387e3-d837-4bde-a9e4-962862ad69e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1570'
ht-degree: 10%

---

# Conectarse a Adobe Analytics y crear marcos{#connecting-to-adobe-analytics-and-creating-frameworks}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para rastrear datos web de sus páginas AEM en Adobe Analytics, cree una configuración de Adobe Analytics Cloud Services y un marco de trabajo de Adobe Analytics:

* **Configuración de Adobe Analytics:** La información sobre su cuenta de Adobe Analytics. La configuración de Adobe Analytics permite AEM conectarse a Adobe Analytics. Cree una configuración de Adobe Analytics para cada cuenta que utilice.
* **Adobe Analytics Framework:** Conjunto de asignaciones entre las propiedades de los grupos de informes de Adobe Analytics y las variables de CQ. Utilice un marco para configurar el modo en que los datos del sitio web rellenan los informes de Adobe Analytics. Los módulos están asociados a una configuración de Adobe Analytics. Puede crear varios marcos de trabajo para cada configuración.

Cuando se asocia una página web con un marco, el marco realiza un seguimiento de dicha página y de los descendientes de dicha página. Las vistas de página se pueden recuperar de Adobe Analytics y mostrar en la consola Sitios .

## Requisitos previos {#prerequisites}

### Cuenta de Adobe Analytics {#adobe-analytics-account}

Para realizar un seguimiento de AEM datos en Adobe Analytics, debe tener una cuenta de Adobe Marketing Cloud Adobe Analytics válida.

La cuenta de Adobe Analytics debe:

* Tiene **Administrador** privilegios
* Se asignará a la variable **Acceso a servicio web** grupo de usuarios.

>[!CAUTION]
>
>Proporcionar **Administrador** privilegios (dentro de Adobe Analytics) no es suficiente para permitir que un usuario se conecte de AEM a Adobe Analytics. La cuenta también debe tener **Acceso a servicio web** privilegios.

![chlimage_1-316](assets/chlimage_1-316.png)

Antes de continuar, asegúrese de que sus credenciales le permiten iniciar sesión en Adobe Analytics mediante uno de los métodos siguientes:

* [Inicio de sesión en Adobe Experience Cloud](https://login.experiencecloud.adobe.com/exc-content/login.html)

* [Inicio de sesión en Adobe Analytics](https://sc.omniture.com/login/)

### Configuración de AEM para usar sus centros de datos de Adobe Analytics {#configuring-aem-to-use-your-adobe-analytics-data-centers}

Adobe Analytics [centros de datos](https://developer.omniture.com/en_US/content_page/concepts-terminology/c-how-is-data-stored) recopilar, procesar y almacenar datos asociados a su grupo de informes de Adobe Analytics. Debe configurar AEM para utilizar el centro de datos que aloja su grupo de informes de Adobe Analytics. En la tabla siguiente se enumeran los centros de datos disponibles y su URL.

| Centro de datos | URL |
|---|---|
| San José | https://api.omniture.com/admin/1.4/rest/ |
| Dallas | https://api2.omniture.com/admin/1.4/rest/ |
| Londres | https://api3.omniture.com/admin/1.4/rest/ |
| Singapur | https://api4.omniture.com/admin/1.4/rest/ |
| Oregón | https://api5.omniture.com/admin/1.4/rest/ |

AEM utiliza el centro de datos de San José (https://api.omniture.com/admin/1.4/rest/) de forma predeterminada.

Utilice la variable [Consola web para configurar el paquete OSGi](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) **Adobe AEM cliente HTTP de Analytics**. Agregue la variable **URL del centro de datos** para el centro de datos que aloja un grupo de informes para el que sus páginas AEM recopilan datos.

![aa-07](assets/aa-07.png)

1. Abra la consola web en el explorador web. ([http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr))
1. Introduzca sus credenciales para acceder a la consola.

   >[!NOTE]
   >
   >Póngase en contacto con el administrador del sitio para averiguar si tiene acceso a esta consola.

1. Seleccione el elemento de configuración denominado **Adobe AEM cliente HTTP de Analytics**.
1. Para añadir la dirección URL de un centro de datos, pulse el botón + situado junto al **Direcciones URL del centro de datos** y escriba la dirección URL en el cuadro.

1. Para eliminar una dirección URL de la lista, haga clic en el botón - situado junto a la dirección URL.
1. Haga clic en Guardar.

## Configuración de la conexión a Adobe Analytics {#configuring-the-connection-to-adobe-analytics}

>[!CAUTION]
>
>Debido a los cambios de seguridad de la API de Adobe Analytics, ya no es posible utilizar la versión de Activity Map incluida en AEM.
>
>La variable [Complemento Activity Map proporcionado por Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=es) debe usarse ahora.

## Configuración del Activity Map {#configuring-for-the-activity-map}

>[!CAUTION]
>
>Debido a los cambios de seguridad de la API de Adobe Analytics, ya no es posible utilizar la versión de Activity Map incluida en AEM.
>
>La variable [Complemento Activity Map proporcionado por Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=es) debe usarse ahora.

## Creación de un marco de Adobe Analytics {#creating-a-adobe-analytics-framework}

Para el ID de grupo de informes (RSID) que utilice, puede controlar qué instancias de servidor (autor, publicación o ambas) contribuyen a los datos del grupo de informes:

* **Todo**: La información del autor y de la instancia de publicación rellena el grupo de informes.
* **Autor**: Solo la información de la instancia de autor rellena el grupo de informes.
* **Publicación**: Solo la información de la instancia de publicación rellena el grupo de informes.

>[!NOTE]
>
>La selección del tipo de instancia de servidor no restringe las llamadas a Adobe Analytics, solo controla qué llamadas incluyen el RSID.
>
>Por ejemplo, un marco de trabajo está configurado para usar el *diweretail* grupo de informes y autor es la instancia de servidor seleccionada. Cuando las páginas se publican junto con la infraestructura, las llamadas se realizan a Adobe Analytics, aunque estas llamadas no contienen el RSID. Solo las llamadas de la instancia de autor incluyen el RSID.

1. Uso **Navegación**, seleccione **Herramientas**, **Cloud Services**, luego **Cloud Services heredados**.
2. Desplácese hasta **Adobe Analytics** y haga clic en **[+]** junto a **Configuraciones disponibles**.
3. Haga clic en el **[+]** vínculo junto a la configuración de Adobe Analytics.

4. En el **Crear marco** diálogo:

   * Especifique un **Título**.
   * Si lo desea, puede especificar la variable **Nombre**, para el nodo que almacena los detalles del marco en el repositorio.
   * Select **Adobe Analytics Framework**

   Y haga clic en **Crear**.

   El marco de trabajo se abrirá para editarlo.

5. En el **Grupos de informes** sección del pod lateral (lado derecho del panel principal), haga clic en **Agregar elemento**. A continuación, utilice la lista desplegable para seleccionar la ID del grupo de informes (por ejemplo, `geometrixxauth`) con la que interactuará el marco.

   >[!NOTE]
   >
   >El buscador de contenido de la izquierda se rellena con variables de Adobe Analytics (variables de SiteCatalyst) al seleccionar una ID de grupo de informes.

6. A continuación, utilice el **Ejecutar modo** desplegable (junto al ID del grupo de informes) para seleccionar las instancias de servidor a las que desea enviar información al grupo de informes.

   ![aa-framework-01](assets/aa-framework-01.png)

7. Para que el marco esté disponible en la instancia de publicación del sitio, en la variable **Página** ficha de la barra de tareas, haga clic en **Activar marco.**

### Configuración del servidor para Adobe Analytics {#configuring-server-settings-for-adobe-analytics}

El sistema marco permite cambiar la configuración del servidor en cada marco de Adobe Analytics.

>[!CAUTION]
>
>Estos ajustes determinan dónde se envían los datos y cómo, por lo tanto, es imprescindible que *no manipule esta configuración* y deje que su representante de Adobe Analytics lo configure en su lugar.

Comience abriendo el panel. Presione la flecha hacia abajo junto a **Servidores**:

![server_001](assets/server_001.png)

* **Servidor de seguimiento**

   * contiene la dirección URL utilizada para enviar llamadas de Adobe Analytics

      * cname: el valor predeterminado es *Nombre de la empresa * de la cuenta de Adobe Analytics
      * d1 - corresponde al centro de datos al que se enviará la información (puede ser d1, d2 o d3)
      * sc.omtrdc.net - nombre de dominio

* **Servidor de seguimiento seguro**

   * Tiene los mismos segmentos que el servidor de seguimiento
   * Se utiliza para enviar datos desde páginas seguras (https://)

* **Espacio de nombres del visitante**

   * El área de nombres determina la primera parte de la dirección URL de seguimiento.
   * Por ejemplo, cambiar el área de nombres a **CNAME** hará que las llamadas realizadas a Adobe Analytics parezcan como **CNAME.d1.omtrdc.net** en lugar del valor predeterminado.

## Asociación de una página a un marco de Adobe Analytics {#associating-a-page-with-a-adobe-analytics-framework}

Cuando una página está asociada con un marco de Adobe Analytics, la página envía datos a Adobe Analytics cuando se carga la página. Las variables que rellena la página se asignan y recuperan de las variables de Adobe Analytics en la infraestructura. Por ejemplo, las vistas de página se recuperan de Adobe Analytics.

Los descendientes de la página heredan la asociación con la estructura. Por ejemplo, cuando se asocia la página raíz del sitio con un marco, todas las páginas del sitio se asocian con el marco.

1. En el **Sitios** , seleccione la página que desea configurar con seguimiento.
1. Abra el **[Propiedades de página](/help/sites-authoring/editing-page-properties.md)**, ya sea directamente desde la consola o desde el editor de páginas.
1. Abra el **Cloud Services** pestaña .

1. Utilice la variable **Agregar configuración** lista desplegable para seleccionar **Adobe Analytics** de las opciones disponibles. Si la herencia está colocada, debe deshabilitarla antes de que el selector esté disponible.

1. El selector desplegable de **Adobe Analytics** se añadirán a las opciones disponibles. Utilice esto para seleccionar la configuración del marco necesaria.

1. Select **Guardar y cerrar**.
1. **[Publicación](/help/sites-authoring/publishing-pages.md)** la página para activar la página y cualquier configuración o archivo conectado.
1. El paso final es visitar la página en la instancia de publicación y buscar una palabra clave (por ejemplo, eggfactory) utilizando la variable **Buscar** componente.
1. A continuación, puede comprobar las llamadas realizadas a Adobe Analytics con una herramienta adecuada; por ejemplo, [Adobe Experience Cloud Debugger](https://experienceleague.adobe.com/docs/debugger/using/experience-cloud-debugger.html).
1. Utilizando el ejemplo proporcionado, la llamada debe contener el valor introducido (es decir, eggcentral) en eVar7 y la lista de eventos debe contener event3.

### Vistas de la página {#page-views}

Cuando una página está asociada a un marco de Adobe Analytics, el número de vistas de página se puede mostrar en la vista Lista de la consola Sitios .

Consulte [Visualización de datos de análisis de página](/help/sites-authoring/pa-using.md) para obtener más información.

### Configuración del intervalo de importación {#configuring-the-import-interval}

Configure la instancia adecuada del **Adobe AEM configuración de sondeo administrado** servicio:

* **Intervalo de encuesta**:

   Intervalo, en segundos, en el que el servicio recupera los datos de vista de página de Adobe Analytics.

   El intervalo predeterminado es 43200000 ms (12 horas).

* **Enable**:

   Habilite o deshabilite el servicio. De forma predeterminada, el servicio está habilitado.

Para configurar este servicio OSGi, puede usar la variable [Consola web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) o [nodo osgiConfig en el repositorio](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) (el PID de servicio es `com.day.cq.polling.importer.impl.ManagedPollConfigImpl`).

## Edición de configuraciones y/o marcos de Adobe Analytics {#editing-adobe-analytics-configurations-and-or-frameworks}

Al igual que cuando se crea una configuración o un marco de Adobe Analytics, vaya a (heredado) **Cloud Services** en el Navegador. Select **Mostrar configuraciones** y, a continuación, haga clic en el vínculo a la configuración específica que desea actualizar.

Al editar una configuración de Adobe Analytics, también debe presionar el botón **Editar** en la propia página de configuración para abrir **Editar componente** diálogo.

## Eliminación de marcos de Adobe Analytics {#deleting-adobe-analytics-frameworks}

Para eliminar un marco de Adobe Analytics, primero [ábrala para editarla](#editing-adobe-analytics-configurations-and-or-frameworks).

A continuación, seleccione **Eliminar marco** de la variable **Página** de la barra de tareas.
