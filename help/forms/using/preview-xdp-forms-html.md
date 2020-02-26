---
title: Generar vista previa HTML5 de un formulario XDP
seo-title: Generar vista previa HTML5 de un formulario XDP
description: La ficha Vista previa de HTML en LiveCycle Designer se puede utilizar para obtener una vista previa de los formularios tal como aparecen en un explorador.
seo-description: La ficha Vista previa de HTML en LiveCycle Designer se puede utilizar para obtener una vista previa de los formularios tal como aparecen en un explorador.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d

---


# Generar vista previa HTML5 de un formulario XDP {#generate-html-preview-of-an-xdp-form}

Al diseñar un formulario en AEM Forms Designer, además de obtener una vista previa de la representación en PDF de un formulario, también puede obtener una vista previa de una representación en HTML5 del mismo. Puede utilizar la ficha **Vista previa de HTML** para obtener una vista previa de un formulario tal como aparecería en un explorador.

## Activar vista previa HTML para formularios XDP en Designer {#html-preview-of-forms-in-forms-designer}

Para habilitar Designer para generar la vista previa HTML de formularios XDP, realice las siguientes configuraciones:

* Configuración del servicio de autenticación Apache Sling
* Deshabilitar modo protegido
* Proporcionar detalles del servidor de AEM Forms

### Configuración del servicio de autenticación Apache Sling {#configure-apache-sling-authentication-service}

1. Vaya a https://[*server*]:[*port*]/system/console/configMgr en AEM Forms que se ejecutan en OSGi o

   https://[*server*]:[*port*]/lc/system/console/configMgr en AEM Forms que se ejecutan en JEE.

1. Busque y haga clic en la configuración del servicio **de autenticación Sling de** Apache para abrirlo en modo de edición.

1. Según si ejecuta AEM Forms en OSGi o JEE, agregue lo siguiente en el campo Requisitos **de** autenticación:

   * AEM Forms en JEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM Forms en OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms
   >[!NOTE]
   >
   >No copie y pegue el valor especificado en el campo Requisitos de autenticación, ya que podría dañar los caracteres especiales del valor. En su lugar, escriba el valor especificado en el campo.

1. Especifique un nombre de usuario y una contraseña en los campos Nombre **[!UICONTROL de usuario]** anónimo y Contraseña **[!UICONTROL de usuario]** anónimo, respectivamente. Las credenciales especificadas se utilizan para gestionar la autenticación anónima y permitir el acceso a usuarios anónimos.
1. Click **Save** to save the configuration.

### Deshabilitar modo protegido {#disable-protected-mode}

El modo [](/help/forms/using/get-xdp-pdf-documents-aem.md) protegido está activado de forma predeterminada. Manténgalo habilitado para los entornos de producción. Puede desactivarlo para que un entorno de desarrollo pueda previsualizar formularios HTML5 en Designer. Realice los siguientes pasos para deshabilitarlo:

1. Inicie sesión en AEM Web Console como administrador.

   * La URL de AEM Forms en OSGi es https://[server]:[port]/system/console/configMgr
   * La URL de AEM Forms en JEE es https://[*server*]:[*port*]/lc/system/console/configMgr

1. Abra Configuraciones **[!UICONTROL de formularios]** móviles para editarlas.
1. Anule la selección de la opción Modo **** protegido y haga clic en **[!UICONTROL Guardar]**.

### Proporcionar detalles del servidor de AEM Forms {#provide-details-of-aem-forms-server}

1. En Designer, vaya a **Herramientas** > **Opciones**.
1. En la ventana Opciones, seleccione la página Opciones **** del servidor, proporcione los siguientes detalles y haga clic en **Aceptar**.

   * **URL** del servidor: URL del servidor de AEM Forms.
   * **Número** de puerto HTTP: Puerto del servidor AEM. El valor predeterminado es 4502.
   * **** Contexto de vista previa de HTML: Ruta del perfil para procesar formularios XFA. Los siguientes perfiles predeterminados se utilizan para obtener una vista previa del formulario en Designer. Sin embargo, también puede especificar la ruta a un perfil personalizado.

      * `/content/xfaforms/profiles/default.html` (AEM Forms en OSGi)
      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms en JEE)
   * **** Contexto de Forms Manager: Ruta de contexto en la que se implementa la interfaz de usuario de Forms Manager. Los valores predeterminados son:

      * `/aem/forms` (AEM Forms en OSGi)
      * `/lc/forms` (AEM Forms en JEE)
   **** Nota: *Asegúrese de que el servidor de AEM Forms está activo y en ejecución. The HTML preview connects to the CRX server to* generate *a preview.*

   ![Opciones de AEM Forms Designer ](assets/server_options.png)

   Opciones de AEM Forms Designer

1. Para obtener una vista previa de un formulario en HTML, haga clic en la ficha **Vista previa de HTML** .

   >[!NOTE]
   >
   >Si la ficha Vista previa de HTML está cerrada, presione F4 para abrir la ficha Vista previa de HTML. También puede seleccionar Vista previa de HTML en el menú Ver para abrir la ficha Vista previa de HTML.

   >[!NOTE]
   >
   >La vista previa HTML no admite documentos PDF, la vista previa HTML solo es para documentos XDP.

## Obtener una vista previa de un formulario mediante datos de ejemplo {#to-preview-a-form-using-sample-data}

Designer permite obtener una vista previa del formulario y probarlo con datos XML de ejemplo. Se recomienda probar con frecuencia el formulario con datos de ejemplo para asegurarse de que el formulario se procesa correctamente.

Si no dispone de datos de ejemplo, Designer puede crearlos o puede hacerlo usted mismo. (Consulte [Generar automáticamente datos de ejemplo para previsualizar el formulario](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) y [Crear datos de ejemplo para previsualizar el formulario](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

Al probar su formulario mediante el uso de datos de ejemplo le garantiza la asignación de datos y campos, además de que los subformularios de repetición se repitan como se espera. Puede crear una presentación equilibrada del formulario que ofrezca el espacio apropiado para que cada objeto muestre los datos combinados.

1. Select **File > Form Properties**.

1. Haga clic en la ficha **Vista previa **y, en el cuadro Archivo de datos, escriba la ruta completa del archivo de datos de prueba. También puede utilizar el botón Examinar para desplazarse hasta el archivo.

1. Haga clic en **Aceptar**. The next time you preview the form in the **Preview HTML** tab, the data values from the sample XML file will appear in the respective objects.

## Vista previa de formularios ubicados en un repositorio {#html-preview-of-forms-in-forms-manager}

En AEM Forms, puede obtener una vista previa de formularios y documentos en un repositorio. La vista previa ayuda a conocer exactamente el aspecto y el comportamiento de los formularios, ya que se utilizarán para los usuarios finales.

[**Comuníquese con la asistencia técnica **](https://www.adobe.com/account/sign-in.supportportal.html)
