---
title: Instalación y configuración de las capacidades de captura de datos
seo-title: Instalación y configuración de las capacidades de captura de datos
description: Instale y configure formularios adaptables, PDF forms y HTML5 Forms. Configure Adobe Analytics y Adobe Target para formularios adaptables a fin de analizar el uso de los formularios y dirigirse a los usuarios según su perfil.
seo-description: Instale y configure formularios adaptables, PDF forms y HTML5 Forms. Configure Adobe Analytics y Adobe Target para formularios adaptables a fin de analizar el uso de los formularios y dirigirse a los usuarios según su perfil.
uuid: ce253b5a-eeb2-47d2-a6c9-e6f59384159a
contentOwner: khsingh
topic-tags: installing
discoiquuid: 1bb8360c-5543-484e-9712-590822211298
role: Admin
exl-id: 45b0fb99-9f7f-47e6-a4de-4db321867f8f
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '1836'
ht-degree: 4%

---

# Instalación y configuración de las capacidades de captura de datos {#install-and-configure-data-capture-capabilities}

Instale y configure formularios adaptables, PDF forms y HTML5 Forms. Configure Adobe Analytics y Adobe Target para formularios adaptables a fin de analizar el uso de los formularios y dirigirse a los usuarios según su perfil.

## Introducción {#introduction}

AEM Forms proporciona un conjunto de formularios para obtener datos del usuario final: formularios adaptables, HTML5 Forms y PDF forms. También proporciona herramientas para enumerar todos los formularios disponibles en una página web, analizar el uso de los formularios y dirigirse a los usuarios según su perfil. Estas funciones se incluyen en el paquete de complementos de AEM Forms. El paquete de complementos se implementa en una instancia de Autor o Publicación de AEM.

**Formularios adaptables:** Estos formularios cambian de apariencia en función del tamaño de pantalla del dispositivo, son atractivos y de naturaleza interactiva. Forms adaptable también se puede integrar con Adobe Analytics, Adobe Sign y Adobe Target. Esto le permitió ofrecer formularios personalizados y experiencias orientadas al proceso a los usuarios en función de su demografía y otras características. También puede integrar formularios adaptables con Adobe Sign.

**Los** formularios PDF son adecuados para la impresión perfecta en píxeles y la captura de información digital dentro de un documento PDF. En el avatar digital, puede utilizar Adobe Acrobat o Acrobat Reader para rellenar estos formularios. Puede alojar estos formularios en su sitio web o utilizar el portal de formularios para enumerarlos en un sitio AEM. También puede enviar por correo electrónico estos formularios a otros usuarios como archivos adjuntos. Estos formularios son los más adecuados para entornos de escritorio.

**Los** formularios HTML5 son la versión compatible con el explorador de los PDF forms. HTML5 Forms es adecuado para entornos que no admiten complementos PDF. HTML5 Forms permite procesar formularios basados en XFA en dispositivos móviles y navegadores de escritorio en los que no se admite PDF basado en XFA. Estos formularios son los más adecuados para los entornos de escritorio y tabletas.

AEM Forms es una potente plataforma de clase empresarial y la captura de datos (formularios adaptables, PDF forms y HTML5 Forms) es solo una de las funciones de AEM Forms. Para obtener la lista completa de las funcionalidades, consulte [Introducción a AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Topología de implementación {#deployment-topology}

El paquete de complementos de AEM Forms es una aplicación implementada en AEM. Solo necesita un mínimo de una instancia de AEM Author y AEM Publish para ejecutar las funciones de captura de datos de AEM Forms. Se sugiere la siguiente topología para ejecutar las capacidades de captura de datos de AEM Forms AEM Forms. Para obtener información detallada sobre la topología, consulte [Arquitectura y topologías de implementación para AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![topología recomendada](assets/recommended-topology.png)

## Requisitos del sistema {#system-requirements}

Antes de empezar a instalar y configurar la capacidad de captura de datos en AEM Forms, asegúrese de que:

* La infraestructura de hardware y software está implementada. Para obtener una lista detallada del hardware y el software compatibles, consulte [requisitos técnicos](/help/sites-deploying/technical-requirements.md).

* La ruta de instalación de la instancia de AEM no contiene espacios en blanco.
* Se está ejecutando una instancia de AEM. En AEM terminología, una &quot;instancia&quot; es una copia de AEM que se ejecuta en un servidor en modo de autor o publicación. Se requieren al menos dos [instancias de AEM (un autor y una publicación)](/help/sites-deploying/deploy.md) para ejecutar las capacidades de captura de datos de AEM Forms:

   * **Autor**: Instancia de AEM utilizada para crear, cargar y editar contenido y para administrar el sitio web. Una vez que el contenido está listo para su lanzamiento, se duplica en la instancia de publicación.
   * **Publicar**: Instancia de AEM que sirve el contenido publicado al público a través de Internet o una red interna.

* Se cumplen los requisitos de memoria. El paquete de complementos de AEM Forms requiere:

   * 15 GB de espacio temporal para instalaciones basadas en Microsoft Windows.
   * 6 GB de espacio temporal para instalaciones basadas en UNIX.

* Se establece la replicación y la replicación inversa para las instancias de autor y publicación. Para obtener más información, consulte [Replicación](/help/sites-deploying/replication.md).
* Requisitos adicionales para sistemas basados en UNIX: Si está utilizando el sistema operativo basado en UNIX, instale los siguientes paquetes del medio de instalación del sistema operativo correspondiente.

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

## Instalación del paquete de complementos de AEM Forms {#install-aem-forms-add-on-package}

El paquete de complementos de AEM Forms es una aplicación implementada en AEM. El paquete contiene captura de datos de AEM Forms y otras funciones. Siga estos pasos para instalar el paquete de complementos:

1. Abra [Distribución de software](https://experience.adobe.com/downloads). Necesitará un Adobe ID para iniciar sesión en la distribución de software.
1. Pulse **[!UICONTROL Adobe Experience Manager]**, disponible en el menú del encabezado.
1. En la sección **[!UICONTROL Filters]**:
   1. Seleccione **[!UICONTROL Forms]** en la lista desplegable **[!UICONTROL Solución]**.
   2. Seleccione la versión y el tipo del paquete. También puede utilizar la opción **[!UICONTROL Search Downloads]** para filtrar los resultados.
1. Pulse el nombre del paquete aplicable a su sistema operativo, seleccione **[!UICONTROL Aceptar términos EULA]** y pulse **[!UICONTROL Descargar]**.
1. Abra [Administrador de paquetes](https://docs.adobe.com/content/help/es-ES/experience-manager-65/administering/contentmanagement/package-manager.html) y haga clic en **[!UICONTROL Cargar paquete]** para cargar el paquete.
1. Seleccione el paquete y haga clic en **[!UICONTROL Install]**.

   También puede descargar el paquete a través del enlace directo que aparece en el artículo [AEM Forms releases](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html).

1. Una vez instalado el paquete, se le pedirá que reinicie la instancia de AEM. **No reinicie el servidor inmediatamente.** Antes de detener el servidor AEM Forms, espere hasta que los mensajes ServiceEvent REGISTER y ServiceEvent UNREGISTER dejen de aparecer en el archivo  [AEM-Installation-Directory]/crx-quickstart/logs/error.log y el registro sea estable.
1. Repita los pasos del 1 al 7 en todas las instancias de Autor y Publicación.

## Configuraciones posteriores a la instalación {#post-installation-configurations}

AEM Forms tiene algunas configuraciones obligatorias y opcionales. Las configuraciones obligatorias incluyen la configuración de las bibliotecas de BouncyCastle y el agente de serialización. Las configuraciones opcionales incluyen la configuración de Dispatcher, el portal de Forms, Adobe Sign, Adobe Analytics y Adobe Target.

### Configuraciones posteriores a la instalación obligatorias {#mandatory-post-installation-configurations}

#### Configuración de las bibliotecas RSA y BouncyCastle  {#configure-rsa-and-bouncycastle-libraries}

Realice los siguientes pasos en todas las instancias de Autor y Publicación para iniciar y delegar las bibliotecas:

1. Detenga la instancia de AEM subyacente.
1. Abra el archivo [AEM installation directory]\crx-quickstart\conf\sling.properties para editarlo.

   Si ha utilizado [AEM directorio de instalación]\crx-quickstart\bin\start.bat para comenzar AEM, edite las propiedades sling que se encuentran en [AEM_root]\crx-quickstart\.

1. Agregue las siguientes propiedades al archivo sling.properties :

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Solo AIX) Agregue las siguientes propiedades al archivo sling.properties :

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Guarde y cierre el archivo e inicie la instancia de AEM.
1. Repita los pasos del 1 al 4 en todas las instancias de Autor y Publicación .

#### Configuración del agente de serialización {#configure-the-serialization-agent}

Siga estos pasos en todas las instancias de Autor y Publicación para añadir el paquete a la lista de permitidos:

1. Abra AEM Administrador de configuración en una ventana del explorador. La dirección URL predeterminada es `https://[server]:[port]/system/console/configMgr`.
1. Busque y abra **[!UICONTROL Deserialization Firewall Configuration]**.
1. Agregue el paquete **[!UICONTROL sun.util.calendar]** al campo **[!UICONTROL lista de permitidos]**. Haga clic en **[!UICONTROL Guardar]**.
1. Repita los pasos del 1 al 3 en todas las instancias de Autor y Publicación .

### Configuraciones posteriores a la instalación opcionales {#optional-post-installation-configurations}

#### Configurar Dispatcher {#configure-dispatcher}

Dispatcher es una herramienta de almacenamiento en caché y equilibrio de carga para AEM. AEM Dispatcher también ayuda a proteger AEM servidor de los ataques. Puede aumentar la seguridad de la instancia de AEM utilizando Dispatcher junto con un servidor web de clase empresarial. Si utiliza [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html), realice las siguientes configuraciones para AEM Forms:

1. Configure el acceso para AEM Forms:

   Abra el archivo dispatcher.any para editarlo. Vaya a la sección de filtros y añada el siguiente filtro a la sección de filtros:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Guarde y cierre el archivo. Para obtener información detallada sobre los filtros, consulte [Documentación de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configure el servicio de filtros del referente:

   Inicie sesión en el gestor de configuración de Apache Felix como administrador. La dirección URL predeterminada del administrador de configuración es `https://[server]:[port_number]/system/console/configMgr`. En el menú **[!UICONTROL Configurations]**, seleccione la opción **[!UICONTROL Apache Sling Referrer Filter]**. En el campo Permitir hosts , introduzca el nombre de host del Dispatcher para permitirlo como referente y haga clic en **[!UICONTROL Guardar]**. El formato de la entrada es `https://[server]:[port]`.

#### Configurar caché {#configure-cache}

El almacenamiento en caché es un mecanismo para reducir los tiempos de acceso a los datos, reducir la latencia y mejorar las velocidades de entrada y salida (E/S). La caché de formularios adaptables almacena únicamente contenido HTML y estructura JSON de un formulario adaptable sin guardar datos precargados. Ayuda a reducir el tiempo necesario para procesar un formulario adaptable.

* Al utilizar la caché de formularios adaptables, utilice el [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) para almacenar en caché las bibliotecas de cliente (CSS y JavaScript) de un formulario adaptable.
* Mientras desarrolla componentes personalizados, mantenga deshabilitada la caché de formularios adaptables en el servidor utilizado para el desarrollo.

Realice los siguientes pasos para configurar la caché de formularios adaptables:

1. Vaya a AEM administrador de configuración de la consola web en `https://[server]:[port]/system/console/configMgr`.
1. Haga clic en **[!UICONTROL Configuración del canal web de formulario adaptable y comunicación interactiva]** para editar sus valores de configuración. En el cuadro de diálogo editar valores de configuración, especifique el número máximo de formularios o documentos que una instancia del servidor de AEM Forms puede almacenar en caché en el campo **[!UICONTROL Number of Adaptive Forms]**. El valor predeterminado es 100. Haga clic en **[!UICONTROL Guardar]**.

   >[!NOTE]
   >
   >Para deshabilitar la caché, establezca el valor en el campo Número de Forms adaptable en **0**. La caché se restablece y todos los formularios y documentos se eliminan de la caché cuando se desactiva o cambia la configuración de la caché.

#### Configuración de la comunicación SSL para el modelo de datos de formulario {#configure-ssl-communcation-for-form-data-model}

Puede activar la comunicación SSL para el modelo de datos de formulario. Para habilitar la comunicación SSL para el modelo de datos de formulario, antes de iniciar cualquier instancia de AEM Forms, agregue certificados al almacén de confianza de Java de todas las instancias. Puede ejecutar el comando siguiente para añadir los certificados: &quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Configuración de Adobe Sign {#configure-adobe-sign}

Adobe Sign permite los flujos de trabajo de firma electrónica para formularios adaptables. Las firmas electrónicas mejoran los flujos de trabajo para procesar documentos para áreas legales, de ventas, de nómina, de gestión de recursos humanos y muchas otras áreas.

En un escenario típico de Adobe Sign y formularios adaptables, un usuario rellena un formulario adaptable para solicitar un servicio. Por ejemplo, una solicitud de tarjeta de crédito y un formulario de beneficios para los ciudadanos. Cuando un usuario rellena, envía y firma el formulario de solicitud, este se envía al proveedor de servicios para que realice más acciones. El proveedor de servicios revisa la aplicación y utiliza Adobe Sign para marcar la aplicación aprobada. Para habilitar flujos de trabajo de firma electrónica similares, puede integrar Adobe Sign con AEM Forms.

Para usar Adobe Sign con AEM Forms, [Integre Adobe Sign con AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Configuración de Adobe Analytics {#configure-adobe-analytics}

AEM Forms se integra con Adobe Analytics, lo que le permite capturar y rastrear las métricas de rendimiento de los formularios y documentos publicados. El objetivo detrás del análisis de estas métricas es tomar decisiones informadas basadas en los datos sobre los cambios necesarios para que los formularios o documentos sean más utilizables.

Para usar Adobe Analytics con AEM Forms, consulte [Configuración de análisis e informes](/help/forms/using/configure-analytics-forms-documents.md).

#### Integrar Adobe Target {#integrate-adobe-target}

Es probable que los clientes abandonen un formulario si la experiencia que ofrece no es atractiva. Aunque resulta frustrante para los clientes, también puede aumentar el volumen y el coste de asistencia para su organización. Es fundamental, además de todo desafío, identificar y ofrecer la experiencia correcta del cliente que aumenta la tasa de conversión. AEM formularios es la clave de este problema.

AEM formularios se integra con Adobe Target, una solución de Adobe Marketing Cloud, para ofrecer experiencias de cliente personalizadas y atractivas en varios canales digitales. Para utilizar Adobe Target para los formularios adaptables de prueba A/B, [Integre Adobe Target con AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Pasos siguientes {#next-steps}

Ha configurado un entorno para utilizar las funciones de captura de datos de AEM Forms. Ahora, los siguientes pasos para utilizar esta capacidad son:

* [Cree su primer formulario adaptable](/help/forms/using/create-your-first-adaptive-form.md)
* [Crear el primer formulario PDF](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/pdf/designer-quickstart.pdf)
* [Introducción a HTML5 Forms](/help/forms/using/introduction.md)
