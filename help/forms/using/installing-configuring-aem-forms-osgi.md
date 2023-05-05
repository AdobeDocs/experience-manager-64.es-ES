---
title: Instalar y configurar las capacidades de captura de datos
seo-title: Install and configure data capture capabilities
description: Instale y configure formularios adaptables, formularios PDF y formularios HTML5. Configure Adobe Analytics y Adobe Target para formularios adaptables con el fin de analizar el uso de los formularios y dirigirse a los usuarios en función de su perfil.
seo-description: Install and configure adaptive forms, PDF Forms, and HTML5 Forms. Configure Adobe Analytics and Adobe Target for adaptive forms to analyze usage of forms and target users based on their profile.
uuid: ce253b5a-eeb2-47d2-a6c9-e6f59384159a
contentOwner: khsingh
topic-tags: installing
discoiquuid: 1bb8360c-5543-484e-9712-590822211298
role: Admin
exl-id: 45b0fb99-9f7f-47e6-a4de-4db321867f8f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 91%

---

# Instalar y configurar las capacidades de captura de datos {#install-and-configure-data-capture-capabilities}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Instale y configure formularios adaptables, formularios PDF y formularios HTML5. Configure Adobe Analytics y Adobe Target para formularios adaptables con el fin de analizar el uso de los formularios y dirigirse a los usuarios en función de su perfil.

## Introducción {#introduction}

AEM Forms proporciona un conjunto de formularios para obtener datos del usuario final: formularios adaptables, formularios HTML5 y formularios PDF. También proporciona herramientas para ver una lista de todos los formularios disponibles en una página web, analizar el uso de los formularios y dirigirse a los usuarios en función de su perfil. Estas capacidades están incluidas en el paquete de complementos de AEM Forms. El paquete de complementos se implementa en una instancia de autor o de publicación de AEM.

**Formularios adaptables:** estos formularios cambian de aspecto en función del tamaño de pantalla del dispositivo, y son atractivos e interactivos. Forms adaptable también se puede integrar con Adobe Analytics, Acrobat Sign y Adobe Target. Esto le permite ofrecer formularios personalizados y experiencias orientadas a procesos a los usuarios en función de su demografía y otras características. También puede integrar formularios adaptables con Acrobat Sign.

Los **formularios PDF** son adecuados para realizar impresiones Pixel Perfect y capturar información digital en un documento PDF. Puede utilizar Adobe Acrobat o Acrobat Reader en el avatar digital para rellenar este tipo de formularios. Puede alojar estos formularios en su sitio web o utilizar el portal de formularios para mostrarlos en forma de lista en un sitio de AEM. También puede enviar por correo electrónico estos formularios a otros usuarios como archivos adjuntos. Estos formularios son los más adecuados para entornos de escritorio.

Los **formularios HTML5** son una versión de los formularios PDF compatible con el explorador. Los formularios HTML5 son adecuados para aquellos entornos que no admiten complementos de PDF. Este tipo de formularios permite procesar formularios basados en XFA tanto en dispositivos móviles como en exploradores de equipos de escritorio no compatibles con PDF basados en XFA. Los formularios HTML5 son los más adecuados para entornos de escritorio y tabletas.

AEM Forms es una potente plataforma de clase empresarial, y Data Capture (formularios adaptables, formularios PDF y formularios HTML5) es solo una de sus capacidades. Para obtener la lista completa de capacidades, consulte [Introducción a AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Topología de implementación {#deployment-topology}

El paquete de complementos de AEM Forms es una aplicación implementada en AEM. Lo único que necesita es disponer al menos de una instancia de autor de AEM y otra de publicación para ejecutar las capacidades de AEM Forms Data Capture. Le sugerimos que utilice la siguiente topología para ejecutar las capacidades de AEM Forms Data Capture. Para obtener información detallada sobre la topología, consulte [Arquitectura y topologías de implementación para AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![topología-recomendada](assets/recommended-topology.png)

## Requisitos del sistema {#system-requirements}

Antes de empezar a instalar y configurar la capacidad de captura de datos en AEM Forms, asegúrese de que:

* Se ha implementado la infraestructura de hardware y software. Para obtener una lista detallada del hardware y el software compatibles, consulte [Requisitos técnicos](/help/sites-deploying/technical-requirements.md).

* La ruta de instalación de la instancia de AEM no contiene espacios en blanco.
* Se está ejecutando una instancia de AEM. En la terminología de AEM, una &quot;instancia&quot; es una copia de AEM que se ejecuta en un servidor en el modo Autor o Publicación. Necesita al menos dos [instancias de AEM (una de autor y otra de publicación)](/help/sites-deploying/deploy.md) para ejecutar las capacidades de AEM Forms Data Capture:

   * **Autor**: la instancia de AEM utilizada para crear, cargar y editar contenido y administrar el sitio web. Una vez que el contenido está listo para su publicación, se replica en la instancia de publicación.
   * **Publicación**: la instancia de AEM que sirve el contenido publicado al público a través de Internet o de una red interna.

* Se cumplen los requisitos de memoria. El paquete de complementos de AEM Forms requiere:

   * 15 GB de espacio temporal para instalaciones basadas en Microsoft Windows.
   * 6 GB de espacio temporal para instalaciones basadas en UNIX.

* Se ha establecido la replicación y la replicación inversa para las instancias de autor y publicación. Para obtener más información, consulte [Replicación](/help/sites-deploying/replication.md).
* Requisitos adicionales para sistemas basados en UNIX: si está utilizando un sistema operativo basado en UNIX, instale los siguientes paquetes desde los medios de instalación del sistema operativo correspondiente.

<table> 
 <tbody> 
  <tr> 
   <td>expat</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr> 
  <tr> 
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr> 
  <tr> 
   <td>glibc</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr> 
  <tr> 
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr> 
 </tbody> 
</table>

## Instalación del paquete de complementos de AEM Forms {#install-aem-forms-add-on-package}

El paquete de complementos de AEM Forms es una aplicación implementada en AEM. El paquete contiene AEM Forms Data Capture y otras capacidades. Siga estos pasos para instalar el paquete de complementos:

1. Abra [Distribución de software](https://experience.adobe.com/downloads). Necesitará un Adobe ID para iniciar sesión en la distribución de software.
1. Pulse **[!UICONTROL Adobe Experience Manager]**, disponible en el menú del encabezado.
1. En la sección **[!UICONTROL Filtros]**:
   1. Seleccione **[!UICONTROL Forms]** en la lista desplegable **[!UICONTROL Solución]**.
   2. Seleccione la versión y el tipo del paquete. También puede usar la opción **[!UICONTROL Buscar descargas]** para filtrar los resultados.
1. Pulse el nombre del paquete aplicable a su sistema operativo, seleccione **[!UICONTROL Aceptar términos de EULA]** y pulse **[!UICONTROL Descargar]**.
1. Abra el [Administrador de paquetes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=es) y haga clic en **[!UICONTROL Cargar paquete]** para cargar el paquete.
1. Seleccione el paquete y haga clic en **[!UICONTROL Instalar]**.

   También puede descargar el paquete a través del vínculo directo que aparece en el artículo [Versiones de AEM Forms](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html).

1. Una vez instalado el paquete, se le pedirá que reinicie la instancia de AEM. **No reinicie el servidor inmediatamente.** Antes de detener el servidor de AEM Forms, espere a que los mensajes ServiceEvent REGISTERED y ServiceEvent UNREGISTERED dejen de aparecer en el archivo [AEM-Installation-Directory]/crx-quickstart/logs/error.log y el registro sea estable.
1. Repita los pasos del 1 al 7 en todas las instancias de autor y publicación.

## Configuraciones posteriores a la instalación {#post-installation-configurations}

AEM Forms incluye algunas configuraciones obligatorias y otras opcionales. Entre las configuraciones obligatorias se incluyen la configuración de las bibliotecas BouncyCastle y el agente de serialización. Las configuraciones opcionales incluyen la configuración de Dispatcher, el portal de Forms, Acrobat Sign, Adobe Analytics y Adobe Target.

### Configuraciones posteriores a la instalación obligatorias {#mandatory-post-installation-configurations}

#### Configuración de las bibliotecas RSA y BouncyCastle  {#configure-rsa-and-bouncycastle-libraries}

Realice los siguientes pasos en todas las instancias de autor y publicación para iniciar y delegar las bibliotecas:

1. Detenga la instancia de AEM subyacente.
1. Abra el [directorio de instalación de AEM]\crx-quickstart\conf\sling.properties para editarlo.

   Si usa el [directorio de instalación de AEM]\crx-quickstart\bin\start.bat para iniciar AEM, edite el archivo sling.properties ubicado en [AEM_root]\crx-quickstart\.

1. Agregue las siguientes propiedades al archivo sling.properties:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Solo AIX) Agregue las siguientes propiedades al archivo sling.properties :

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Guarde y cierre el archivo e inicie la instancia de AEM.
1. Repita los pasos del 1 al 4 en todas las instancias de autor y publicación.

#### Configuración del agente de serialización {#configure-the-serialization-agent}

Siga estos pasos en todas las instancias de autor y publicación para incluir el paquete en la lista de permitidos:

1. Abra el Administrador de configuración de AEM en una ventana del explorador. La URL predeterminada es `https://[server]:[port]/system/console/configMgr`.
1. Busque y abra **[!UICONTROL Deserialización de la configuración de Firewall]**.
1. Agregue el paquete **[!UICONTROL sun.util.calendar]** en el campo **[!UICONTROL Lista de permitidos]**. Haga clic en **[!UICONTROL Guardar]**.
1. Repita los pasos del 1 al 3 en todas las instancias de autor y publicación.

### Configuraciones posteriores a la instalación opcionales {#optional-post-installation-configurations}

#### Configurar Dispatcher {#configure-dispatcher}

Dispatcher es una herramienta de almacenamiento en caché y equilibrio de carga de AEM. AEM Dispatcher también contribuye a proteger el servidor de AEM de ataques. Puede reforzar la seguridad de su instancia de AEM mediante Dispatcher y un servidor web de clase empresarial. Si usa [Dispatcher](https://helpx.adobe.com/es/experience-manager/dispatcher/using/dispatcher-configuration.html), realice las siguientes configuraciones en AEM Forms:

1. Configure el acceso en AEM Forms:

   Abra el archivo dispatcher.any para editarlo. Vaya a la sección de filtros y agregue el siguiente filtro:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Guarde y cierre el archivo. Para obtener información detallada sobre los filtros, consulte la [documentación de Dispatcher](https://helpx.adobe.com/es/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configure el servicio del Filtro de referente:

   Inicie sesión en el Administrador de configuración de Apache Felix como administrador. La URL predeterminada del Administrador de configuración es `https://[server]:[port_number]/system/console/configMgr`. En el menú **[!UICONTROL Configuraciones]**, seleccione la opción **[!UICONTROL Filtro de referente de Apache Sling]**. En el campo Permitir hosts, introduzca el nombre de host de Dispatcher para permitirlo como referente y haga clic en **[!UICONTROL Guardar]**. El formato de la entrada es `https://[server]:[port]`.

#### Configurar la caché {#configure-cache}

Una caché es un mecanismo para acortar los tiempos de acceso los datos, reducir la latencia y mejorar las velocidades de entrada y salida (E/S). La caché de los formularios adaptables almacena únicamente el contenido HTML y la estructura JSON de un formulario adaptable sin guardar los datos rellenados previamente. Esto contribuye a reducir el tiempo necesario para representar un formulario adaptable.

* Cuando utilice la caché de los formularios adaptables, utilice [AEM Dispatcher](https://helpx.adobe.com/es/experience-manager/dispatcher/using/dispatcher-configuration.html) para almacenar en caché las bibliotecas de cliente (CSS y JavaScript) de un formulario adaptable.
* A la hora de desarrollar componentes personalizados, mantenga deshabilitada la caché de los formularios adaptables en el servidor utilizado para el desarrollo.

Realice los siguientes pasos para configurar la caché de los formularios adaptables:

1. Vaya al Administrador de configuración de la consola web de AEM en `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en **[!UICONTROL Configuración del canal web de comunicaciones interactivas y formularios adaptables]** para editar sus valores de configuración. En el cuadro de diálogo Editar valores de configuración, especifique el número máximo de formularios o documentos que una instancia del servidor de AEM Forms puede almacenar en caché en el campo **[!UICONTROL Número de formularios adaptables]**. El valor predeterminado es 100. Haga clic en **[!UICONTROL Guardar]**.

   >[!NOTE]
   >
   >Para deshabilitar la caché, establezca el valor del campo Número de formularios adaptables en **0**. La caché se restablece y todos los formularios y documentos se eliminan de ella cuando se desactiva o cambia su configuración.

#### Configuración de la comunicación SSL para el modelo de datos de formulario {#configure-ssl-communcation-for-form-data-model}

Puede activar la comunicación SSL para el modelo de datos de formulario. Para habilitar la comunicación SSL para el modelo de datos de formulario, antes de iniciar una instancia de AEM Forms, agregue los certificados al almacén de confianza de Java de todas las instancias. Puede ejecutar el siguiente comando para añadir los certificados:

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Configuración de Acrobat Sign {#configure-adobe-sign}

Acrobat Sign permite los flujos de trabajo de firma electrónica para formularios adaptables. Las firmas electrónicas mejoran los flujos de trabajo para procesar documentos para el área legal, ventas, nóminas, administración de recursos humanos y muchas más.

En un escenario típico de Acrobat Sign y formularios adaptables, un usuario rellena un formulario adaptable para solicitar un servicio. Por ejemplo, una solicitud de tarjeta de crédito y un formulario de solicitud para una prestación. Cuando un usuario rellena, envía y firma el formulario de solicitud, este se envía al proveedor de servicios para que realice más acciones. El proveedor de servicios revisa la aplicación y utiliza Acrobat Sign para marcar la aplicación aprobada. Para habilitar flujos de trabajo de firma electrónica similares, puede integrar Acrobat Sign con AEM Forms.

Para usar Acrobat Sign con AEM Forms, [Integración de Acrobat Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Configuración de Adobe Analytics {#configure-adobe-analytics}

AEM Forms se integra con Adobe Analytics para permitirle capturar y realizar un seguimiento de las métricas de rendimiento de los formularios y los documentos que ha publicado. El objetivo detrás del análisis de estas métricas es tomar decisiones informadas basadas en los datos sobre los cambios necesarios para que los formularios o documentos sean más utilizables.

Para usar Adobe Analytics con AEM Forms, consulte [Configuración de análisis e informes](/help/forms/using/configure-analytics-forms-documents.md).

#### Integración con Adobe Target {#integrate-adobe-target}

Es probable que los clientes abandonen un formulario si la experiencia que ofrece no es atractiva. A pesar de que para ellos resulta frustrante, también puede aumentar el volumen y el coste de la asistencia en su organización. Identificar y ofrecer una experiencia del cliente correcta que aumente la tasa de conversión es fundamental, además de un desafío. AEM Forms es la solución a este problema.

AEM Forms se integra con Adobe Target, una solución de Adobe Marketing Cloud, para ofrecer experiencias del cliente personalizadas y atractivas en diferentes canales digitales. Para utilizar Adobe Target en formularios adaptables de prueba A/B, consulte [Integración de Adobe Target con AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Pasos siguientes {#next-steps}

Ha configurado un entorno para utilizar las capacidades de AEM Forms Data Capture. Ahora, los siguientes pasos para utilizar esta capacidad son:

* [Creación de su primer formulario adaptable](/help/forms/using/create-your-first-adaptive-form.md)
* [Creación de su primer formulario PDF](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/designer-quickstart.pdf)
* [Introducción a los formularios HTML5](/help/forms/using/introduction.md)
