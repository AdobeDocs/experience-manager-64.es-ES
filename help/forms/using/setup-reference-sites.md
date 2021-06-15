---
title: Configuración de sitios de referencia de AEM Forms
seo-title: Configuración de sitios de referencia de AEM Forms
description: Los sitios de referencia de AEM Forms muestran cómo puede utilizar AEM Forms para implementar un flujo de trabajo completo en una organización.
seo-description: Los sitios de referencia de AEM Forms muestran cómo puede utilizar AEM Forms para implementar un flujo de trabajo completo en una organización.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: 933084f92d116111dbfea55d52b1ad60ae691505
workflow-type: tm+mt
source-wordcount: '2936'
ht-degree: 2%

---

# Configuración de los sitios de referencia de AEM Forms {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms proporciona implementación de sitios de referencia para demostrar cómo AEM Forms ayuda a las organizaciones gubernamentales y del sector de servicios financieros a transformar sus complejas transacciones en experiencias digitales simples y atractivas en cualquier lugar, en cualquier momento y en cualquier dispositivo.

Los sitios de referencia de We.Finance y We.Gov dibujan casos de uso en la vida real para interactuar con clientes existentes y potenciales, desde el primer contacto hasta la administración de correspondencias y transacciones de una manera personalizada y rentable.

Los sitios de referencia permiten explorar y mostrar las siguientes funciones clave de AEM Forms.

* Experiencia de creación simplificada de formularios adaptables interactivos y atractivos y comunicaciones interactivas.
* Comunicaciones interactivas para crear comunicaciones de clientes interactivas, personalizadas y adaptables que se adapten a la configuración y el diseño del dispositivo.
* Integración de datos para conectarse a distintos orígenes de datos para rellenar previamente y enviar datos de formulario a través de un modelo de datos de formulario.
* Flujo de trabajo de Forms para automatizar procesos y flujos de trabajo empresariales.
* Funciones avanzadas de administración y procesamiento de datos de usuario.
* Integración con Adobe Sign para firmar y enviar formularios adaptables de forma segura.
* Integración con Adobe Target para ofrecer recomendaciones dirigidas y realizar pruebas A/B para maximizar el ROI de un formulario.
* Integración con Adobe Analytics para medir el rendimiento de un formulario o una campaña y tomar decisiones informadas.
* Se ha mejorado la experiencia de cumplimentación de formularios.

Los sitios de referencia proporcionan recursos reutilizables que puede utilizar como plantillas para crear sus propios recursos.

* Integración con Adobe Sign para firmar y enviar formularios adaptables de forma segura.

* Integración con Adobe Sign para firmar y enviar formularios adaptables de forma segura.

## Requisitos previos y pasos para configurar los sitios de referencia {#prerequisites-and-steps-to-set-up-reference-sites}

Antes de configurar el sitio de referencia, asegúrese de que dispone de lo siguiente:

* **Aspectos básicos del AEM**

   AEM paquete de complementos de AEM Forms, QuickStart y paquetes de sitios de referencia. Consulte [Versiones de AEM Forms](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html) para obtener más información sobre los paquetes de complementos y sitios de referencia.

* **Un**
servicio SMTPPuede utilizar cualquier servicio SMTP.

* **Cuenta de desarrollador de Adobe Sign y aplicación de API de Adobe Sign**

   Para utilizar las funciones de firma digital, se requiere una cuenta de desarrollador de Adobe Sign. Consulte [Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html).

* Instancia en ejecución de Microsoft Dynamics 365 para integrarla con AEM Forms. Para ejecutar el sitio de referencia, importe los datos de ejemplo en la instancia de Microsoft Dynamics para rellenar previamente la comunicación interactiva utilizada en el sitio de referencia.
* Instancia en ejecución de AEM 6.4 con el paquete de complementos de Forms. Para obtener más información, consulte [Instalación y configuración de AEM Forms](installing-configuring-aem-forms-osgi.md).

Realice los siguientes pasos en la secuencia recomendada para configurar los sitios de referencia.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Etapa</strong></th> 
   <th><strong>Configuración</strong></th> 
   <th><strong>Notas</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Instalación y configuración de AEM Forms</a></td> 
   <td>Creación y publicación</td> 
   <td>Instale y configure instancias de creación y publicación de AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">Configuración de SSL</a></td> 
   <td>Autor y publicación<br /> </td> 
   <td>Habilite HTTP sobre SSL para comunicaciones seguras con Adobe Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Configurar la configuración del externalizador Day CQ Link</a></p> </td> 
   <td>Autor y publicación<br /> </td> 
   <td><p>Los casos de uso del sitio de referencia envían correos electrónicos para diferentes transacciones. Esta configuración es necesaria para la entrega de newsletters por correo electrónico. Garantiza que las URL y las imágenes apunten a la instancia de publicación. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Configurar el servicio Day CQ Mail</a></td> 
   <td>Creación y publicación</td> 
   <td>Necesario para la comunicación por correo electrónico.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Anular la configuración XSS predeterminada</a></td> 
   <td>Publicación</td> 
   <td>Se utiliza para anular los caracteres $, { y } bloqueados por xss security.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">Configuración de AEM DS</a></td> 
   <td>Autor</td> 
   <td>Configure AEM DS para el envío de formularios en la instancia de publicación y los flujos de trabajo de procesamiento en la instancia de autor.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Implementación de paquetes de sitios de referencia</a></td> 
   <td>Autor</td> 
   <td>Implemente paquetes de sitios de referencia en la instancia de autor de AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importar datos de ejemplo en Microsoft Dynamics</a></td> 
   <td>Creación y publicación</td> 
   <td>Importar datos de muestra para la aplicación de tarjeta de crédito, la aplicación de hipoteca de origen y el tutorial de la aplicación de seguro de vivienda</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Configurar el servicio en la nube OAuth para Microsoft Dynamics</a></td> 
   <td>Creación y publicación</td> 
   <td>Configure el servicio en la nube OAuth en AEM Forms para habilitar la comunicación entre AEM Forms y Microsoft Dynamics. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Configuración del planificador de Adobe Sign</a></td> 
   <td>Autor y publicación<br /> </td> 
   <td>Cambie la configuración del planificador para comprobar el estado cada dos minutos.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Configuración del Cloud Service de referencia de Adobe Sign del sitio</a></td> 
   <td>Autor y publicación<br /> </td> 
   <td>Una configuración que viene con paquetes de sitios de referencia y necesita reconfiguración con credenciales válidas.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Configuración del servicio de configuración común de Forms para usuarios anónimos</a></td> 
   <td>Publicación</td> 
   <td>La configuración permite el envío, la firma y la generación de documentos de registros para usuarios anónimos.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">Modificar el archivo de intercambio de servicio de descanso para el modelo de datos de formulario</a></td> 
   <td>Autor y publicación<br /> </td> 
   <td>Modifique el servicio para su entorno.</td> 
  </tr> 
 </tbody> 
</table>

## Instalación y configuración de AEM Forms {#install-and-configure-aem-forms}

Instale e implemente AEM Forms tal como se describe en [Instalación y configuración de AEM Forms en OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Configure los agentes de replicación y de replicación inversa si hay más de una instancia de publicación o si las instancias de autor y publicación están en equipos diferentes.

## Configuración de SSL {#ssl}

La configuración SSL es necesaria para comunicarse con los servidores de Adobe Sign. Para ver los pasos detallados, consulte [Habilitación de HTTP sobre SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>No configure la fuerza SSL en la carpeta `/etc/map`.

## Configurar la configuración del externalizador Day CQ Link {#externalizer}

En AEM, **Externalizer** es un servicio OSGI que le permite transformar mediante programación una ruta de recursos (p. ej. /path/to/my/page) en una dirección URL externa y absoluta (por ejemplo, https://www.mycompany.com/path/to/my/page) prefiriendo la ruta con un DNS preconfigurado. Consulte [Externalización de direcciones URL](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>No externalice a la URL HTTPS si utiliza un certificado autofirmado para SSL.
>
>Además, utilice localhost en lugar de su nombre de host para el servidor local.

Siga estos pasos en las instancias de autor y publicación:

1. Vaya a Configuración OSGi en https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Busque y pulse la configuración **[!UICONTROL Day CQ Link Externalizer]**.

   Se abre el cuadro de diálogo Externalizador de vínculos de CQ de día para editar la configuración.

1. En el cuadro de diálogo Externalizador de vínculos de CQ de día, en el campo Dominios :

   * En la instancia de autor, especifique una URL de publicación a la que se pueda acceder desde un sistema externo. Por ejemplo, un nombre de host o un servidor web de publicación.
   * En la instancia de publicación, especifique las direcciones URL de autor y publicación.

1. En las instancias de autor y publicación, asegúrese de que la URL del servidor local esté especificada en el campo Dominios .
1. Toque **[!UICONTROL Guardar]**. Espere un rato para que se reinicien todos los servicios.

## Configurar el servicio Day CQ Mail {#cqmail}

La implementación del sitio de referencia requiere que se envíen correos electrónicos a los usuarios de muestra cuando rellenen y envíen formularios. La configuración del servicio de correo de Day CQ permite proporcionar detalles del servicio SMTP para enviar correos electrónicos automatizados a los clientes. Consulte [Configuración de notificaciones por correo electrónico](/help/sites-administering/notification.md).

Realice los siguientes pasos para configurar el servicio de correo en la instancia de publicación:

1. Vaya a Configuración OSGi en https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr.
1. Busque y pulse **[!UICONTROL Day CQ Mail Service]** para abrirlo y configurarlo.
1. Proporcione valores de puerto y nombre de host del servidor SMTP.
1. Toque **[!UICONTROL Guardar]**.

>[!NOTE]
>
>Puede utilizar su servicio SMTP corporativo o servicios públicos como Gmail. Para configurar el servicio SMTP, consulte la documentación del servicio SMTP.

## Anular la configuración XSS predeterminada {#xss}

Las plantillas de correo electrónico del sitio de referencia de We.Finance contienen vínculos personalizados en los correos electrónicos. Estos vínculos tienen un marcador de posición como `${placeholder}`. Estos marcadores de posición se sustituyen por valores reales antes de enviar correos electrónicos. La configuración de protección XSS predeterminada para AEM no permite llaves (**{ }**) en la dirección URL en el contenido HTML. Sin embargo, puede anular la configuración predeterminada realizando los siguientes pasos en la instancia de publicación:

1. Copie `/libs/cq/xssprotection/config.xml` en `/apps/cq/xssprotection/config.xml`.
1. Abra `/apps/cq/xssprotection/config.xml`.
1. En la sección `common-regexps`, modifique la entrada `onsiteURL` de la siguiente manera y guarde el archivo.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Las llaves (**{ }**) se incluyen como caracteres aceptados en la dirección URL del contenido HTML.

Después de configurar el servidor SMTP, intente rellenar un formulario utilizando el perfil de Sarah Rose y guárdelo como borrador. Al guardar como borrador, se obtiene una opción para recibir el borrador mediante correo electrónico. Al pulsar el botón **Send Email**, si recibe un correo electrónico con un vínculo al borrador de la aplicación, la configuración del correo electrónico se realiza correctamente. Asegúrese de iniciar sesión utilizando las credenciales de Sarah para ver el borrador.

## Configuración de AEM DS {#aemds}

AEM Se requiere la configuración del servicio DS en la instancia de publicación para las comunicaciones por correo electrónico en los casos de uso del sitio de referencia. Para ver los pasos detallados para configurar AEM servicio DS en la instancia Publicar, consulte [Configuración de AEM configuración de DS](/help/forms/using/configuring-the-processing-server-url-.md).

Para los sitios de referencia de AEM Forms, en el Servicio de configuración de AEM DS, especifique la URL del servidor de publicación en lugar de la URL del servidor de procesamiento.

>[!CAUTION]
>
>No ponga `/lc` en la URL del servidor de procesamiento si lo está configurando para OSGi de AEM Forms.

## Implementación de paquetes de sitios de referencia {#refsite}

Instale los siguientes paquetes de sitios de referencia mediante Distribución de software.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Para obtener más información sobre cómo utilizar los paquetes, consulte [Cómo trabajar con paquetes](/help/sites-administering/package-manager.md).

Después de instalar los paquetes e iniciar las instancias de autor y publicación, visite las siguientes direcciones URL en su explorador:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Si la instalación se realiza correctamente, puede acceder a las páginas de aterrizaje de los sitios de referencia de We.Gov y We.Finance .

## (Opcional) Importe datos de ejemplo en Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

Los sitios de referencia de la aplicación de hipoteca de origen y la aplicación de seguro automático están configurados para utilizar registros de Microsoft Dynamics. El paquete de sitio de referencia instala una entidad personalizada y registros de ejemplo que puede importar en Microsoft Dynamics para ejecutar el sitio de referencia. Siga estos pasos para migrar y configurar los datos de ejemplo:

Para importar la entidad personalizada para la aplicación de seguro automático:

1. Descargue el paquete de soluciones **WeFinanceAutoInsurance_1_0.zip** de `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` en su instancia de autor de AEM.
1. En la instancia de Microsoft Dynamics, vaya a **[!UICONTROL Soluciones]** en el menú **[!UICONTROL Configuración]** y haga clic en **[!UICONTROL Importar]**. Seleccione e importe el paquete.

Para importar la entidad personalizada para la aplicación de seguro automático:

1. Descargue el paquete **AEMFormsFSIRefsite_1_0.zip** de https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip. Seleccione e importe el paquete.

1. En la instancia de Microsoft Dynamics, vaya a **[!UICONTROL Soluciones]** en el menú **[!UICONTROL Configuración]** y haga clic en **[!UICONTROL Importar]**. Seleccione e importe el paquete.

Para importar los registros de pólizas de seguro y de cliente:

1. Descargue los archivos de datos **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv** y **home hipoage** de las siguientes ubicaciones en la instancia de autor de AEM:

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. En la instancia de Microsoft Dynamics, haga lo siguiente:

   * Vaya a **[!UICONTROL Sales > We.Finance Customers]** y haga clic en **[!UICONTROL Import]**.
   * Vaya a **[!UICONTROL Sales > We.Finance Auto Insurance]** y haga clic en **[!UICONTROL Import]**.
   * Vaya a **[!UICONTROL Sales > We.Finance Home Mortgage]** y haga clic en **[!UICONTROL Import]**.

## Configurar el servicio en la nube OAuth para Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Configure el servicio en la nube OAuth en AEM Forms para habilitar la comunicación entre AEM Forms y Microsoft Dynamics. Realice los siguientes pasos para configurar el Cloud Service de OAuth en AEM instancias de autor y publicación:

1. En AEM instancia de autor, vaya a **[!UICONTROL Herramientas > Cloud Services > Fuentes de datos > global]**. Pulse el icono **[!UICONTROL Refsite Dynamics Integration]** y pulse **[!UICONTROL Properties]**.
1. Vaya a la cuenta de Microsoft Azure Active Directory. Añada la URL de configuración del servicio de nube copiada en la configuración **[!UICONTROL Reply URL]** de la aplicación registrada. Guarde la configuración.
1. En la pestaña Configuración de autenticación , especifique **[!UICONTROL Service Root]**, **[!UICONTROL Client Id]**, **[!UICONTROL Client Secret]** y **[!UICONTROL Resource URL]** para la instancia de Microsoft Dynamics. Haga clic en **[!UICONTROL Conectarse a OAuth]** que redirige a la página de inicio de sesión de Microsoft Dynamics.
1. Proporcione sus credenciales de inicio de sesión. Una vez que haya iniciado sesión, se le redirigirá a la página de configuración del servicio en la nube de AEM Forms. Haga clic en **[!UICONTROL Guardar y cerrar]**. La configuración del servicio de nube se guarda.
1. Vaya a **[!UICONTROL Forms > Integraciones de datos > We.Finance]**. Seleccione Segmentación automática (Dynamics) y haga clic en Editar. Las entidades de Microsoft Dynamics se muestran en la ficha Fuentes de datos . Espere hasta que todas las entidades se recuperen de Microsoft Dynamics y se enumeran en la ficha de fuentes de datos.
1. Seleccione **[!UICONTROL AutoInsuranceRenewal entity]** y haga clic en **[!UICONTROL Test Model Object]**. En la sección de solicitud de entrada, especifique el valor del ID de cliente como &quot;900001&quot; y haga clic en **[!UICONTROL Test]**. La sección Salida muestra los registros recuperados de Microsoft Dynamics para el ID de cliente 900001.
1. En la sección de solicitud de entrada, especifique el valor del ID de cliente como &quot;900001&quot; y haga clic en **[!UICONTROL Test]**. La sección Salida muestra los registros recuperados de Microsoft Dynamics para el ID de cliente 900001.
1. Repita los pasos del 1 al 6 en la instancia de publicación.

## Configuración del planificador de Adobe Sign {#scheduler}

Haga lo siguiente en las instancias de autor y publicación:

1. Vaya a AEM consola Configuración web en `https://[server]:[host]/system/console/configMgr`.
1. Busque y pulse **[!UICONTROL Adobe Sign Configuration Service]** para abrirlo y configurarlo.
1. Configure **[!UICONTROL Status Update Scheduler Expression]** como **0 0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >La configuración del planificador anterior comprueba el estado del servicio Adobe Sign cada dos minutos.

1. Toque **[!UICONTROL Guardar]**.

## Configure el servicio de nube Adobe Sign del sitio de referencia {#sign-service}

Haga lo siguiente en las instancias de autor y publicación:

1. Vaya a **[!UICONTROL Herramientas > Cloud Services > Adobe Sign > global]**. Seleccione **[!UICONTROL AEM Forms Reference Site Sign]** y pulse **[!UICONTROL Properties]**.

   >[!CAUTION]
   >
   >Asegúrese de que la URL https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html se agrega a la lista de URL de redireccionamiento de la configuración de OAuth de la aplicación de API de Adobe Sign.

1. Especifique el ID de cliente y el secreto de la configuración OAuth de la aplicación Adobe Sign.
1. (Opcional) Seleccione la opción **[!UICONTROL Habilitar Adobe Sign para archivos adjuntos también]** y pulse **[!UICONTROL Conectarse a Adobe Sign]**. Agrega los archivos adjuntos a un formulario adaptable al documento de Adobe Sign correspondiente enviado para firmar.
1. Toque **[!UICONTROL Conectarse a Adobe Sign]** e inicie sesión con sus credenciales de Adobe Sign.

## Configuración del servicio de configuración común de Forms {#anonymous}

Haga lo siguiente en la instancia de publicación para permitir el acceso a usuarios anónimos:

1. Vaya a AEM consola Configuración web en `https://[server]:[port]/system/console/configMgr`.
1. Busque y pulse **[!UICONTROL Servicio de configuración común de Forms]** para abrirlo y configurarlo.
1. Configure el campo **[!UICONTROL Permitir]** para **[!UICONTROL Todos los usuarios]**.
1. Toque **[!UICONTROL Guardar]**.

## Modificación del servicio de descanso para el modelo de datos de formulario {#fdm}

Haga lo siguiente en las instancias de autor y publicación:

1. Vaya a CRXDE en `https://[server]:[port]/crx/de/index.jsp`.
1. Vaya a **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** y abra el archivo swagger.
1. Actualice la configuración del host y del puerto según su entorno.
1. Guarde la configuración.
1. (**Instancia de autor solamente**) Vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Fuentes de datos]** > **[!UICONTROL global]**. Seleccione **[!UICONTROL roi-rest]** y pulse **[!UICONTROL Properties]**. Pulse **[!UICONTROL Configuración de autenticación]** y establezca **[!UICONTROL Tipo de autenticación]** en **[!UICONTROL Autenticación básica]**. Especifique `admin`/ `admin`como nombre de usuario/contraseña para acceder al servicio. Toque **[!UICONTROL Guardar y cerrar]**.

## Integrar con Marketing Cloud {#integrate-with-marketing-cloud}

Puede integrar AEM Forms con Adobe Analytics y Adobe Target. Aunque Adobe Analytics le ayuda a generar informes y analizar el rendimiento de los formularios adaptables, Adobe Target le ayuda a ofrecer experiencias personalizadas y a realizar pruebas A/B en formularios adaptables.

Haga lo siguiente para configurar Adobe Analytics y Adobe Target en AEM Forms.

### Configurar Adobe Analytics {#configure-adobe-analytics}

La integración de AEM Forms con Adobe Analytics le permite supervisar y analizar cómo interactúan sus clientes con sus formularios y documentos. Le ayuda a identificar y corregir áreas problemáticas y a aumentar la tasa de conversión.

Para experimentar esta funcionalidad en el sitio de referencia, configure su cuenta de Analytics como se describe en [Configuración de análisis e informes](/help/forms/using/configure-analytics-forms-documents.md).

Para generar un informe, los datos semilla se incluyen en los sitios de referencia. Antes de utilizar los datos semilla, haga lo siguiente:

1. Asegúrese de que las configuraciones de análisis de We.Finance y We.Gov estén disponibles en los servicios de nube de AEM. Puede encontrar servicios de nube de una de las siguientes maneras:

   * Vaya a **[!UICONTROL Tools>Cloud Services>Legacy Cloud Services]** o vaya a https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html.
   * En la página **[!UICONTROL Cloud Services]**, en la sección **[!UICONTROL Adobe Analytics]**, haga clic en `Show Configurations`. Puede ver las configuraciones de We.Finance y We.Gov disponibles. Haga clic en para abrir la configuración. En la página de configuración, haga clic en **[!UICONTROL Editar]**. Proporcione una empresa, un nombre de usuario, un secreto compartido (contraseña) y un centro de datos válidos y haga clic en **[!UICONTROL Conectarse a Analytics]**. Una vez que la conexión se haya realizado correctamente, haga clic en **[!UICONTROL OK]** en el cuadro de diálogo de configuración. Configure el marco en la configuración de Analytics como se describe en [Configuración de Analytics e informes](/help/forms/using/configure-analytics-forms-documents.md).

1. Vaya a https://&lt;*host*>:&lt;*port*>/system/console/configMgr y haga lo siguiente:

   * En la página **[!UICONTROL Configuración de la consola web]**, busque y haga clic en **[!UICONTROL Configuración de AEM Forms Analytics]**.
   * En el campo **[!UICONTROL SiteCatalyst Framework]** del cuadro de diálogo Configuración de AEM Forms Analytics, seleccione we-finance(we-finance) o we-gov(we-gov).
   * Haga clic en **[!UICONTROL Guardar]** y deje que la página se actualice.

1. Vaya al administrador de formularios en https://&lt;host>:&lt;port>/aem/forms y haga lo siguiente:

   * Abra la carpeta We.Finance o We.Gov y seleccione el formulario para el que desea ver el informe.
   * Haga clic en Habilitar Analytics en la barra de herramientas Acciones. Una vez que haya habilitado Analytics para el formulario, haga clic en Informe de Analytics. Se puede ver un informe en blanco generado. Después de generar un informe en blanco, debe proporcionar los datos de origen enviados con el paquete refsite para generar un informe de analytics para fines de demostración.

   Los sitios de referencia proporcionan a los informes de análisis datos semilla para los casos de uso de tarjetas de crédito, hipotecas de viviendas y soporte infantil. Para obtener información sobre la configuración de los datos semilla, consulte [Recorrido por el sitio de referencia de We.Finance](/help/forms/using/finance-reference-site-walkthrough.md) y [Recorrido por el sitio de referencia de We.Gov](/help/forms/using/gov-reference-site-walkthrough.md).

### Configurar Target {#configure-target}

El sitio de referencia muestra la integración de AEM Forms con Adobe Target que le permite incluir contenido personalizado y dirigido en documentos adaptables. También permite crear pruebas A/B para formularios adaptables.

Para experimentar la integración en el sitio de referencia, haga lo siguiente para configurar Target en AEM:

1. Inicie el inicio rápido del autor con el argumento jvm `-Dabtesting.enabled=true` para habilitar la prueba A/B en el servidor.

   **Nota**: Si la instancia de AEM se está ejecutando en JBoss, que se inicia como un servicio desde la instalación de Turnkey, añada el  `-Dabtesting.enabled=true` parámetro en la siguiente entrada del  `jboss\bin\standalone.conf.bat` archivo, :

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Acceda a https://&lt;*hostname*:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. En la sección **[!UICONTROL Adobe Target]**, haga clic en **[!UICONTROL Mostrar configuraciones]**. Puede ver la Configuración de destino de We.Finance disponible. Haga clic en para abrir la configuración. En la página de configuración, haga clic en **[!UICONTROL Editar]**. Se abre el cuadro de diálogo **[!UICONTROL Editar componente]** para la configuración.

1. Especifique el código de cliente, el correo electrónico y la contraseña asociados a su cuenta de Target. Seleccione el tipo de API como **[!UICONTROL REST]**.
1. Haga clic en **[!UICONTROL Connect to Adobe target]**. Una vez configurada correctamente la cuenta de Target, haga clic en **[!UICONTROL OK]**. Puede ver que la configuración empaquetada tiene un Target Framework.

1. Vaya a https://&lt;*hostname*:&lt;*port*>/system/console/configMgr.

1. Haga clic en **[!UICONTROL Configuración de AEM Forms Target]**.
1. Seleccione un marco de Target.
1. En el campo **[!UICONTROL Target URLs]**, especifique la dirección URL de AEM Forms. Por ejemplo: https://&lt;*hostname*>:&lt;*port*>.

1. Haga clic en **[!UICONTROL Guardar]**.

Los casos de uso de las aplicaciones de tarjetas de crédito e hipotecas domésticas demuestran cómo realizar pruebas A/B y mostrar un informe con fines de demostración. Para obtener tutoriales, consulte [Recorrido por el sitio web de referencia de We.Finance](/help/forms/using/finance-reference-site-walkthrough.md).

## Paso siguiente {#next-step}

Ahora todos están listos para explorar el sitio de referencia. Para obtener más información sobre el flujo de trabajo y los pasos del sitio de referencia, consulte:

* [Recorrido por el sitio web de referencia de We.Finance](/help/forms/using/finance-reference-site-walkthrough.md)
* [Recorrido por el sitio web de referencia de We.Gov](/help/forms/using/gov-reference-site-walkthrough.md)

* [Recorrido por el sitio de referencia de autoservicio para empleados](/help/forms/using/employee-self-service-reference-site.md)
