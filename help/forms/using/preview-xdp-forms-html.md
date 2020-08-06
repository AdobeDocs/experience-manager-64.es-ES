---
title: Generar previsualización HTML5 de un formulario XDP
seo-title: Generar previsualización HTML5 de un formulario XDP
description: La ficha HTML de Previsualización en LiveCycle Designer se puede utilizar para crear previsualizaciones de formularios tal como aparecen en un explorador.
seo-description: La ficha HTML de Previsualización en LiveCycle Designer se puede utilizar para crear previsualizaciones de formularios tal como aparecen en un explorador.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
translation-type: tm+mt
source-git-commit: 801941c060e1a912f3969bca1e89962241e7fbe0
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 15%

---


# Generar previsualización HTML5 de un formulario XDP {#generate-html-preview-of-an-xdp-form}

Al diseñar un formulario en AEM Forms Designer, además de obtener una vista previa de la representación en PDF de un formulario, también se puede realizar una previsualización de una representación en HTML5 del mismo. Puede utilizar la ficha **Previsualización HTML** para realizar la previsualización de un formulario tal como aparecería en un explorador.

## Habilitar Previsualización HTML para formularios XDP en Designer {#html-preview-of-forms-in-forms-designer}

Para permitir que Designer genere previsualizaciones HTML de formularios XDP, realice las siguientes configuraciones:

* Configuración del servicio de autenticación Apache Sling
* Deshabilitar modo protegido
* Proporcionar detalles del servidor de AEM Forms

### Configuración del servicio de autenticación Apache Sling {#configure-apache-sling-authentication-service}

1. Vaya a `https://[server]:[port]/system/console/configMgr` en AEM Forms que se ejecute en OSGi o

   `https://[server]:[port]/lc/system/console/configMgr` en AEM Forms que se ejecuta en JEE.

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

El modo [](/help/forms/using/get-xdp-pdf-documents-aem.md) protegido está activado de forma predeterminada. Manténgalo habilitado para los entornos de producción. Puede deshabilitarlo para un entorno de desarrollo para la previsualización de HTML5 Forms en Designer. Realice los siguientes pasos para deshabilitarlo:

1. Inicie sesión en AEM consola web como administrador.

   * La dirección URL de AEM Forms en OSGi es `https://[server]:[port]/system/console/configMgr`
   * La dirección URL de AEM Forms en JEE es `https://[server]:[port]/lc/system/console/configMgr`

1. Abra Configuraciones **[!UICONTROL móviles de Forms]** para editarlas.
1. Anule la selección de la opción Modo **** protegido y haga clic en **[!UICONTROL Guardar]**.

### Proporcionar detalles del servidor de AEM Forms {#provide-details-of-aem-forms-server}

1. En Designer, vaya a **Herramientas** > **Opciones**.
1. En la ventana Opciones, seleccione la página Opciones **** del servidor, proporcione los siguientes detalles y haga clic en **Aceptar**.

   * **URL** del servidor: URL del servidor de AEM Forms.
   * **Número** de puerto HTTP: AEM puerto del servidor. El valor predeterminado es 4502.
   * **Contexto de Previsualización HTML:** Ruta del perfil para procesar formularios XFA. Se utilizan los siguientes perfiles predeterminados para la previsualización del formulario en Designer. Sin embargo, también puede especificar la ruta a un perfil personalizado.

      * `/content/xfaforms/profiles/default.html` (AEM Forms en OSGi)
      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms en JEE)
   * **Contexto de Forms Manager:** Ruta de contexto en la que se implementa la interfaz de usuario de Forms Manager. Los valores predeterminados son:

      * `/aem/forms` (AEM Forms en OSGi)
      * `/lc/forms` (AEM Forms en JEE)

   **Nota:** *Asegúrese de que el servidor de AEM Forms está activo y en ejecución. The HTML preview connects to the CRX server to* generate *a preview.*

   ![Opciones de AEM Forms Designer ](assets/server_options.png)

   Opciones de AEM Forms Designer

1. Para previsualización de un formulario en HTML, haga clic en la ficha **Previsualización HTML** .

   >[!NOTE]
   >
   >Si la ficha Previsualización HTML está cerrada, pulse F4 para abrir la ficha HTML de la Previsualización. También puede seleccionar HTML de Previsualización en el menú Vista para abrir la ficha HTML de Previsualización.

   >[!NOTE]
   >
   >La previsualización HTML no admite documentos PDF, la previsualización HTML solo es para documentos XDP.

## Obtener una vista previa de un formulario mediante datos de ejemplo {#to-preview-a-form-using-sample-data}

Designer permite obtener una vista previa del formulario y probarlo con datos XML de ejemplo. Se recomienda probar con frecuencia el formulario con datos de ejemplo para asegurarse de que el formulario se procesa correctamente.

Si no dispone de datos de ejemplo, Designer puede crearlos o puede hacerlo usted mismo. (Consulte [Generar automáticamente datos de ejemplo para previsualizar el formulario](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) y [Crear datos de ejemplo para previsualizar el formulario](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

Al probar su formulario mediante el uso de datos de ejemplo le garantiza la asignación de datos y campos, además de que los subformularios de repetición se repitan como se espera. Puede crear una presentación equilibrada del formulario que ofrezca el espacio apropiado para que cada objeto muestre los datos combinados.

1. Select **File > Form Properties**.

1. Click the **Preview** tab and, in the Data File box, type the full path to your test data file. También puede utilizar el botón Examinar para desplazarse hasta el archivo.

1. Haga clic en **Aceptar**. The next time you preview the form in the **Preview HTML** tab, the data values from the sample XML file will appear in the respective objects.

## Formularios de Previsualización ubicados en un repositorio {#html-preview-of-forms-in-forms-manager}

En AEM Forms, puede realizar previsualizaciones de formularios y documentos en un repositorio. La Previsualización ayuda a saber exactamente cómo se ven y se comportan los formularios cuando se utilizan para los usuarios finales.

[**Comuníquese con la asistencia técnica **](https://www.adobe.com/account/sign-in.supportportal.html)
