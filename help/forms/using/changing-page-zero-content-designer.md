---
title: Cambio del contenido de página cero en Designer
seo-title: Cambio del contenido de página cero en Designer
description: ¿Sabe cómo puede cambiar el mensaje mostrado en la página cero de un archivo PDF XFA al visualizarlo en un visor que no es de Adobe PDF?
seo-description: ¿Sabe cómo puede cambiar el mensaje mostrado en la página cero de un archivo PDF XFA al visualizarlo en un visor que no es de Adobe PDF?
uuid: 5697f203-bb24-437d-a692-bc4bc2609b88
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: f458054e-885c-4c7a-afcd-ad1e4465e0c1
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 1%

---


# Cambio del contenido de página cero en Designer {#changing-page-zero-content-in-designer}

El contenido de Página cero se muestra de forma predeterminada cuando un visor que no es de Adobe PDF, como el visor de PDF predeterminado en Chrome o Firefox, no puede leer el contenido del formulario PDF/XFA. El mensaje predeterminado Página cero se muestra a continuación.

![defaultpage0message](assets/defaultpage0message.png)

La versión 1 de AEM Forms Feature Pack 1 de Designer permite cambiar el mensaje que se muestra en la página cero. Para cambiar el mensaje Página cero, realice los siguientes pasos:

1. Asegúrese de tener instalada la versión 1 de AEM Forms Feature Pack de Designer. Puede comprobar la versión desde la pantalla Acerca de del diseñador.

1. Abra el formulario para el que desea cambiar el contenido de Página cero.

1. Click **File > Form Properties**.

1. En el cuadro de diálogo Propiedades del formulario, haga clic en ![más](assets/plus.png) (icono de signo más) para agregar una propiedad personalizada.

1. Especifique **_pagezerocontent** como nombre de la propiedad.
1. Añada el nuevo mensaje Página cero, en formato de texto enriquecido, como valor. Por ejemplo:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </span></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </span>https://www.adobe.com/go/acrreader.</p></body>`

1. Guarde el formulario como PDF.

1. Vista el formulario PDF en el navegador para confirmar que el mensaje se ha actualizado. El valor de ejemplo anterior aparece de la siguiente manera:

   ![change message](assets/changedmessage.png)

>[!NOTE]
>
>Es posible que la propiedad personalizada que acaba de crear no aparezca correctamente en el cuadro de diálogo Propiedades del formulario al volver a abrir el formulario. Sin embargo, funciona bien y el formulario muestra el mensaje Página cero actualizado.

