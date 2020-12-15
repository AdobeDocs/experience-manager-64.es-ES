---
title: Plantillas de recursos
description: Obtenga información sobre las plantillas de recursos en AEM Assets y cómo utilizar las plantillas de recursos para crear material publicitario de marketing.
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
translation-type: tm+mt
source-git-commit: b6f0dc15244f71ecdb8d937810d3c5d393a7712f
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 0%

---


# Plantillas de recursos {#asset-templates}

Las plantillas de recursos son una clase especial de recursos que facilitan la reutilización rápida de contenido con gran riqueza visual para medios digitales e impresos. Una plantilla de recurso incluye dos partes, la sección de mensajería fija y la sección editable.

La sección de mensajes fijos puede contener contenido propio, como el logotipo de la marca y la información de copyright que está desactivada para la edición. La sección editable puede contener contenido visual y textual en los campos que se pueden editar para personalizar la mensajería.

La flexibilidad para realizar ediciones limitadas mientras se aseguran los letreros globales hace que las plantillas de recursos sean los componentes básicos ideales para una rápida adaptación y distribución del contenido como artefactos de contenido para diversas funciones. El rediseño del contenido ayuda a reducir el coste de la administración de canales digitales e impresos y ofrece experiencias holísticas y coherentes en estos canales.

Como especialista en mercadotecnia, puede almacenar y administrar plantillas dentro de AEM Assets y utilizar una única plantilla base para crear varias experiencias de impresión personalizadas con facilidad. Puede crear varios tipos de material publicitario de marketing, como folletos, volantes, postales, tarjetas de presentación, etc., para transmitir con lentitud su mensaje de marketing a los clientes. También puede montar salidas de impresión de varias páginas a partir de salidas de impresión nuevas o existentes. Por encima de todo, puede ofrecer simultáneamente experiencias digitales y de impresión con facilidad para ofrecer una experiencia coherente e integrada a los usuarios.

Aunque las plantillas de recursos son principalmente archivos InDesign, la competencia en el InDesign no es una barrera para la creación de artefactos estelares. No es necesario asignar los campos de la plantilla de InDesign a los campos de producto que, de lo contrario, se requieren al crear catálogos. Puede editar las plantillas en modo WYSIWYG directamente en la interfaz web. Sin embargo, para que InDesign procese los cambios de edición, primero debe configurar AEM Assets para que se integre con el servidor de InDesign.

La capacidad de editar plantillas de InDesign desde la interfaz web ayuda a fomentar la buena colaboración entre el personal creativo y de marketing, al tiempo que reduce el tiempo de comercialización de las iniciativas de promoción locales.

Puede hacer lo siguiente con plantillas de recursos:

* Modificación de campos de plantilla editables desde la interfaz web
* Controlar el estilo básico del texto, por ejemplo, el tamaño de fuente, el estilo y el tipo en el nivel de etiqueta
* Cambiar imágenes dentro de la plantilla mediante el selector de contenido
* Ediciones de plantillas de previsualización
* Combinar varios archivos de plantilla para crear un artefacto de varias páginas

Al elegir una plantilla para el material promocional, AEM Assets crea una copia de la plantilla que puede editar. Se conserva la plantilla original, lo que garantiza que la señalización global permanezca intacta y se pueda reutilizar para reforzar la coherencia de la marca.

Puede exportar el archivo actualizado en la carpeta principal con los siguientes formatos:

* INDD
* PDF
* JPG

También puede descargar la salida en estos formatos al sistema local.

## Crear un colateral {#creating-a-collateral}

Considere un escenario en el que desee crear material publicitario digital imprimible, como folletos, volantes y publicidades para una próxima campaña y compartirlo con tiendas de venta en todo el mundo. La creación de material publicitario basado en una plantilla ayuda a ofrecer una experiencia unificada al cliente en todos los canales. Los diseñadores pueden crear las plantillas de campaña (de una sola página o de varias páginas) mediante una solución creativa, como el InDesign, y cargar las plantillas a AEM Assets por usted. Antes de crear un colateral, tenga una o varias plantillas INDD cargadas y disponibles con antelación por parte del Experience Manager.

1. Toque o haga clic en el logotipo de AEM y, a continuación, toque o haga clic en **[!UICONTROL Recursos]** en la página de navegación.
1. En las opciones, elija **[!UICONTROL Plantillas]**.

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. Toque o haga clic **[!UICONTROL Crear]** y, a continuación, elija el material que desee crear en el menú. Por ejemplo, elija **[!UICONTROL Folleto]**.

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. Cargue una o más plantillas INDD y disponga de ellas con antelación. Elija una plantilla para el folleto y toque o haga clic **[!UICONTROL Siguiente]**.

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. Especifique un nombre y una descripción opcional para el folleto.

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. (Opcional) Toque o haga clic en el icono **[!UICONTROL Etiquetas]** situado junto al campo **[!UICONTROL Etiquetas]** y seleccione una o varias etiquetas para el folleto. Toque o haga clic **[!UICONTROL Confirmar]** para confirmar la selección.

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. Haga clic en **[!UICONTROL Crear]**. Un cuadro de diálogo confirma que se crea un nuevo folleto. Toque o haga clic **[!UICONTROL Abrir]** para abrir el folleto en modo de edición.

   ![chlimage_1-310](assets/chlimage_1-311.png)

   De forma alternativa, cierre el cuadro de diálogo y vaya a la carpeta de la página Plantillas con la que comenzó a crear la vista del folleto que ha creado. El tipo de garantía aparece en su miniatura en la vista de la tarjeta. Por ejemplo, en este caso, el folleto se muestra en la miniatura.

   ![chlimage_1-312](assets/chlimage_1-312.png)

## Editar una garantía {#editing-a-collateral}

Puede editar un colateral inmediatamente después de crearlo. También puede abrirlo desde la página Plantillas o desde la página de recursos.

1. Para abrir el material publicitario para la edición, realice una de las siguientes acciones:

   * Abra el colateral (folleto en este caso) que creó en el paso 7 de [Creación de un colateral](asset-templates.md#creating-a-collateral).
   * En la página Plantillas, desplácese hasta la carpeta en la que haya creado el colateral y toque o haga clic en la acción rápida Editar en la miniatura de un colateral.
   * En la página de recursos del material promocional, toque o haga clic en el icono Editar de la barra de herramientas.
   * Seleccione el colateral y toque o haga clic en el icono Editar de la barra de herramientas.

   ![chlimage_1-313](assets/chlimage_1-313.png)

   El buscador de recursos y el editor de texto se muestran a la izquierda de la página. El editor de texto está abierto de forma predeterminada.

   Puede utilizar el editor de texto para modificar el texto que desea que se muestre en el campo de texto. Puede modificar el tamaño, el estilo, el color y el tipo de fuente en el nivel de etiqueta.

   Con el buscador de recursos, puede buscar o buscar imágenes en AEM Assets y reemplazar las imágenes editables en la plantilla por las imágenes que desee.

   ![chlimage_1-314](assets/chlimage_1-314.png)

   Los editables se muestran a la derecha. Para que un campo pueda editarse en AEM Assets, el campo correspondiente de la plantilla debe etiquetarse en InDesign. En otras palabras, deben ser marcados como editables en InDesign.

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Asegúrese de que la instancia de AEM esté integrada con un servidor de InDesign para permitir que AEM Assets extraiga datos de la plantilla de InDesign y que esté disponible para su edición. Para obtener más información, consulte [Integración de AEM Assets con InDesign Server](indesign.md).

1. Para modificar el texto de un campo editable, toque o haga clic en el campo de texto de la lista de campos editables y edite el texto del campo.

   ![chlimage_1-316](assets/chlimage_1-316.png)

   Puede editar las propiedades del texto, por ejemplo, el estilo de fuente, el color y el tamaño, mediante las opciones proporcionadas.

1. Toque o haga clic en el icono **[!UICONTROL Previsualización]** para previsualización de los cambios de texto.

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. Para intercambiar una imagen, toque o haga clic en el icono **[!UICONTROL Buscador de recursos]**.

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. Seleccione el campo de imagen de la lista de campos editables y, a continuación, arrastre una imagen deseada del selector de recursos al campo editable.

   ![chlimage_1-319](assets/chlimage_1-319.png)

   También puede buscar imágenes mediante palabras clave, etiquetas y según su estado de publicación. Puede navegar por el repositorio de AEM Assets y navegar hasta la ubicación de la imagen deseada.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Toque o haga clic en el icono **[!UICONTROL Previsualización]** para previsualización de la imagen.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Para editar una página específica en una página secundaria de varias páginas, utilice el navegador de páginas en la parte inferior.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Toque o haga clic en el icono **[!UICONTROL Previsualización]** de la barra de herramientas para previsualización de todos los cambios. Toque o haga clic **[!UICONTROL Listo]** para guardar los cambios de edición en el colateral.

   >[!NOTE]
   >
   >Los iconos Previsualización y Finalizado solo se activan cuando los campos de imagen editables del material no tienen iconos que falten. Si falta algún icono en el colateral, es porque AEM no puede resolver las imágenes en la plantilla de InDesign. Normalmente, AEM no puede resolver las imágenes en los siguientes casos:
   >
   >* Las imágenes no se incrustan en la plantilla de InDesign subyacente
   >* Las imágenes están vinculadas desde el sistema de archivos local

   >
   >Para habilitar AEM para resolver imágenes, haga lo siguiente:
   >
   >* Incruste imágenes al crear plantillas de InDesign (consulte [Acerca de los vínculos y los gráficos incrustados](https://helpx.adobe.com/indesign/using/graphics-links.html)).
   >* Monte AEM en el sistema de archivos local y, a continuación, asigne los iconos que faltan a los recursos AEM existentes.

   >
   >Para obtener más información sobre cómo trabajar con documentos de InDesign, consulte [Prácticas recomendadas para trabajar con Documentos de InDesign en AEM](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Para generar una representación en PDF del folleto, seleccione la opción Acrobat en el cuadro de diálogo y haga clic en **[!UICONTROL Continuar]**.
1. El colateral se crea en la carpeta en la que se inició. Para realizar la vista de las representaciones, abra el colateral y elija **[!UICONTROL Representaciones]** en la lista GlobalNav.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. Toque o haga clic en la representación PDF desde la lista de representaciones para descargar el archivo PDF. Abra el archivo PDF para revisar el material promocional.

   ![chlimage_1-324](assets/chlimage_1-324.png)

## Combinar material promocional {#merge-collateral}


1. Toque o haga clic en **[!UICONTROL Herramientas > Recursos]**.
1. En las opciones, elija **[!UICONTROL Plantillas]**.
1. Toque o haga clic **[!UICONTROL Crear]** y elija **[!UICONTROL Combinar]** en el menú.

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. En la página Combinar plantillas, toque o haga clic en el icono Combinar.

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. Vaya a la ubicación del material que desea combinar, toque o haga clic en las miniaturas del material que desea combinar para seleccionarlas.

   ![chlimage_1-327](assets/chlimage_1-327.png)

   Incluso puede buscar plantillas desde el cuadro OmniSearch.

   ![chlimage_1-328](assets/chlimage_1-328.png)

   Puede navegar por el repositorio o las colecciones de AEM Assets, navegar hasta la ubicación de las plantillas que desee y seleccionarlas para combinarlas.

   ![chlimage_1-329](assets/chlimage_1-329.png)

   Puede aplicar varios filtros para buscar en las plantillas que desee. Por ejemplo, puede buscar plantillas basadas en el tipo de archivo o las etiquetas.

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. Toque o haga clic **[!UICONTROL Siguiente]** en la barra de herramientas.
1. En la pantalla **[!UICONTROL Previsualización y reordenación]**, reorganice las plantillas si es necesario y previsualización la selección de las plantillas que se van a combinar. A continuación, toque o haga clic **[!UICONTROL Siguiente]** en la barra de herramientas.

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. En la pantalla Configurar plantilla, especifique un nombre para el colateral. De forma opcional, especifique las etiquetas que considere adecuadas. Si desea exportar la salida en formato PDF, seleccione la opción **[!UICONTROL Acrobat (.PDF)]**. De forma predeterminada, la garantía se exporta en formato JPG y InDesign. Para cambiar la miniatura de visualización del material publicitario de varias páginas, toque o haga clic en **[!UICONTROL Cambiar miniatura]**.

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. Toque o haga clic **[!UICONTROL Guardar]** y, a continuación, toque o haga clic **[!UICONTROL Aceptar]** en el cuadro de diálogo para cerrar el cuadro de diálogo. El colateral de varias páginas se crea en la carpeta en la que se inició.

   >[!NOTE]
   >
   >No puede editar una garantía combinada posteriormente ni utilizarla para crear otra garantía.

