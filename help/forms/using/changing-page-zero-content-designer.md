---
title: Cambiar el contenido de la página cero en Designer
seo-title: Changing Page Zero content in Designer
description: ¿Sabe cómo puede cambiar el mensaje que se muestra en la página cero de un PDF XFA cuando se visualiza en un visor que no es Adobe PDF?
seo-description: Do you know how you can change the message displayed on Page Zero of an XFA PDF when viewing it in a non-Adobe PDF viewer?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
feature: Adaptive Forms
exl-id: 0ae34ddd-9a8d-48df-af2d-80c3fe6abd62
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 67%

---

# Cambiar el contenido de la página cero en Designer {#changing-page-zero-content-in-designer}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El contenido Página cero se muestra de forma predeterminada cuando un visor que no es de Adobe PDF, como el visor predeterminado del PDF en Chrome o Firefox, no puede leer el contenido del formulario PDF/XFA. A continuación, se muestra el mensaje predeterminado de la página cero.

![defaultpage0message](assets/defaultpage0message.png)

La versión 1 del paquete de funciones de AEM Forms de Designer permite cambiar el mensaje que se muestra en la página cero. Para cambiar el mensaje de la página cero, realice los siguientes pasos:

1. Asegúrese de tener instalada la versión de AEM Forms Feature Pack 1 de Designer. Puede comprobar la versión desde la pantalla Acerca de Designer.

1. Abra el formulario para el cual desea cambiar el contenido de la página cero.

1. Haga clic en **Archivo > Propiedades del formulario**.

1. En el cuadro de diálogo Propiedades del formulario, haga clic en ![plus](assets/plus.png) (icono + ) para añadir una propiedad personalizada.

1. Especifique **_pagezerocontent** como el nombre de la propiedad.
1. Agregue el nuevo mensaje de la página cero en formato de texto enriquecido como valor. Por ejemplo:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Guarde el formulario como PDF.

1. Vea el formulario PDF en el explorador para confirmar que el mensaje se ha actualizado. El valor del ejemplo anterior aparece de la siguiente forma:

   ![change.message](assets/changedmessage.png)

>[!NOTE]
>
>Es posible que la propiedad personalizada que acaba de crear no aparezca correctamente en el cuadro de diálogo Propiedades del formulario cuando vuelva a abrir el formulario. Sin embargo, funciona bien, y el formulario muestra el mensaje de la página cero actualizado.
