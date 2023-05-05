---
title: Plantillas de recursos
description: Obtenga información sobre las plantillas de recursos en [!DNL Experience Manager] Recursos y cómo usar plantillas de recursos para crear material publicitario de marketing.
uuid: 7ba87c1d-70cd-4b89-86f3-971b93885f1e
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 340b62f7-2405-4d2d-846d-2c444d6cc77b
feature: Asset Management,Developer Tools
role: User
exl-id: 9b4f16e6-dd91-4179-9629-576d801fcf43
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 0%

---

# Plantillas de recursos {#asset-templates}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las plantillas de recursos son una clase especial de recursos que facilitan un reuso rápido del contenido con gran riqueza visual para medios digitales y de impresión. Una plantilla de recursos incluye dos partes, la sección de mensajería fija y la sección editable.

La sección de mensajería fija puede contener contenido propio, como el logotipo de la marca y la información de copyright que está desactivada para la edición. La sección editable puede contener contenido visual y textual en campos que se pueden editar para personalizar la mensajería.

La flexibilidad para realizar ediciones limitadas y, al mismo tiempo, asegurar las señalizaciones globales, hace que las plantillas de recursos sean componentes básicos ideales para una rápida adaptación y distribución del contenido como artefactos de contenido para diversas funciones. El repropósito del contenido ayuda a reducir el costo de la administración de canales digitales e impresos y ofrece experiencias holísticas y coherentes en todos estos canales.

Como especialista en marketing, puede almacenar y administrar plantillas dentro de [!DNL Experience Manager] Recursos y utilice una sola plantilla base para crear varias experiencias de impresión personalizadas con facilidad. Puede crear varios tipos de material publicitario de marketing, incluidos folletos, folletos, postales, tarjetas de visita, etc., para transmitir su mensaje de marketing a los clientes de forma lúcida. También puede ensamblar salidas de impresión de varias páginas a partir de salidas de impresión existentes o nuevas. Sobre todo, puede ofrecer simultáneamente experiencias digitales e impresas con facilidad para proporcionar una experiencia coherente e integrada a los usuarios.

Aunque las plantillas de recursos son en su mayoría archivos de InDesign, la competencia en el InDesign no es una barrera para la creación de artefactos estelares. No es necesario asignar los campos de la plantilla de InDesign a los campos de producto que necesita para crear catálogos. Puede editar las plantillas en modo WYSIWYG directamente en la interfaz web. Sin embargo, para que el InDesign procese los cambios de edición, primero debe configurar [!DNL Experience Manager] Recursos que se van a integrar con el servidor de InDesign.

La capacidad de editar plantillas de InDesign desde la interfaz web ayuda a fomentar la buena colaboración entre el personal creativo y de marketing, a la vez que reduce el tiempo de comercialización para las iniciativas de promoción locales.

Puede hacer lo siguiente con las plantillas de recursos:

* Modificación de campos de plantilla editables desde la interfaz web
* Controle el estilo básico del texto, por ejemplo el tamaño de fuente, el estilo y el tipo en el nivel de etiqueta
* Cambiar imágenes dentro de la plantilla mediante el selector de contenido
* Vista previa de las ediciones de plantillas
* Combinar varios archivos de plantilla para crear un artefacto de varias páginas

Al elegir una plantilla para los activos de garantía, [!DNL Assets] crea una copia de la plantilla que puede editar. Se conserva la plantilla original, lo que garantiza que la señalización global permanezca intacta y se pueda reutilizar para garantizar la coherencia de la marca.

Puede exportar el archivo actualizado dentro de la carpeta principal en los siguientes formatos:

* INDD
* PDF
* JPG

También puede descargar la salida en estos formatos en su sistema local.

## Crear una garantía {#creating-a-collateral}

Considere un escenario en el que desee crear garantías digitales imprimibles, como folletos, folletos y publicidades para una próxima campaña, y compartirlas con tiendas de venta en todo el mundo. La creación de material colateral basado en una plantilla ayuda a ofrecer una experiencia de cliente unificada en todos los canales. Los diseñadores pueden crear las plantillas de campaña (de una sola página o de varias páginas) mediante una solución creativa, como el InDesign y cargar las plantillas en [!DNL Assets] para usted. Antes de crear un colateral, haga que una o más plantillas INDD se carguen en y estén disponibles en el Experience Manager con antelación.

1. Haga clic en el [!DNL Experience Manager] y, a continuación, haga clic en **[!UICONTROL Recursos]** en la página Navegación .
1. En las opciones , elija **[!UICONTROL Plantillas]**.

   ![chlimage_1-306](assets/chlimage_1-306.png)

1. Toque o haga clic **[!UICONTROL Crear]** y, a continuación, elija el material que desea crear en el menú . Por ejemplo, elija **[!UICONTROL Folleto]**.

   ![chlimage_1-307](assets/chlimage_1-307.png)

1. Tener una o más plantillas INDD cargadas en y disponibles por adelantado en el Experience Manager. Elija una plantilla para el folleto y toque o haga clic en **[!UICONTROL Siguiente]**.

   ![chlimage_1-308](assets/chlimage_1-308.png)

1. Especifique un nombre y una descripción opcional para el folleto.

   ![chlimage_1-309](assets/chlimage_1-309.png)

1. (Opcional) Toque o haga clic en el **[!UICONTROL Etiquetas]** icono **[!UICONTROL Etiquetas]** y seleccione una o varias etiquetas para el folleto. Toque o haga clic **[!UICONTROL Confirmar]** para confirmar la selección.

   ![chlimage_1-310](assets/chlimage_1-310.png)

1. Haga clic en **[!UICONTROL Crear]**. Un cuadro de diálogo confirma que se crea un nuevo folleto. Toque o haga clic **[!UICONTROL Apertura]** para abrir el folleto en modo de edición.

   ![chlimage_1-311](assets/chlimage_1-311.png)

   Como alternativa, cierre el cuadro de diálogo y vaya a la carpeta de la página Plantillas con la que comenzó a trabajar para ver el folleto que ha creado. El tipo de garantía aparece en su miniatura en la vista de tarjeta. Por ejemplo, en este caso, el folleto se muestra en la miniatura.

   ![chlimage_1-312](assets/chlimage_1-312.png)

## Editar una garantía real {#editing-a-collateral}

Puede editar un colateral inmediatamente después de crearlo. También puede abrirlo desde la página Plantillas o la página de recursos.

1. Para abrir el material secundario para editarlo, realice una de las siguientes acciones:

   * Abra el colateral (folleto en este caso) que creó en el paso 7 de [Creación de una garantía real](asset-templates.md#creating-a-collateral).
   * En la página Plantillas , vaya a la carpeta en la que creó el material colateral y pulse o haga clic en la acción rápida Editar en la miniatura de un material colateral.
   * En la página del recurso para el material colateral, pulse o haga clic en el icono Editar de la barra de herramientas.
   * Seleccione el material secundario y pulse o haga clic en el icono Editar de la barra de herramientas.

   ![chlimage_1-313](assets/chlimage_1-313.png)

   El buscador de recursos y el editor de texto se muestran a la izquierda de la página. El editor de texto está abierto de forma predeterminada.

   Puede utilizar el editor de texto para modificar el texto que desea que se muestre en el campo de texto. Puede modificar el tamaño de fuente, el estilo, el color y el tipo en el nivel de etiqueta.

   Con el buscador de recursos, puede examinar o buscar imágenes en [!DNL Assets] y reemplace las imágenes editables de la plantilla por las imágenes que elija.

   ![chlimage_1-314](assets/chlimage_1-314.png)

   Los editables se muestran a la derecha. Para que un campo se pueda editar en [!DNL Assets], el campo correspondiente de la plantilla debe etiquetarse en InDesign. En otras palabras, deben marcarse como editables en InDesign.

   ![chlimage_1-315](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Asegúrese de que su [!DNL Experience Manager] se integra con un servidor de InDesign para habilitar [!DNL Assets] para extraer datos de la plantilla de InDesign y ponerlos a disposición para su edición. Para obtener más información, consulte [Integración [!DNL Assets] con InDesign Server](indesign.md).

1. Para modificar el texto de un campo editable, toque o haga clic en el campo de texto de la lista de campos editables y edite el texto en el campo.

   ![chlimage_1-316](assets/chlimage_1-316.png)

   Puede editar las propiedades del texto, por ejemplo el estilo de fuente, el color y el tamaño, utilizando las opciones proporcionadas.

1. Toque o haga clic en **[!UICONTROL Vista previa]** para obtener una vista previa de los cambios de texto.

   ![chlimage_1-317](assets/chlimage_1-317.png)

1. Para intercambiar una imagen, toque o haga clic en el botón **[!UICONTROL Buscador de recursos]** icono.

   ![chlimage_1-318](assets/chlimage_1-318.png)

1. Seleccione el campo de imagen de la lista de campos editables y, a continuación, arrastre una imagen desde el selector de recursos al campo editable.

   ![chlimage_1-319](assets/chlimage_1-319.png)

   También puede buscar imágenes utilizando palabras clave, etiquetas y según su estado de publicación. Puede navegar por el [!DNL Assets] y navegue hasta la ubicación de la imagen deseada.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Toque o haga clic en **[!UICONTROL Vista previa]** para previsualizar la imagen.

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Para editar una página específica en una página secundaria de varias páginas, utilice el navegador de páginas en la parte inferior.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Toque o haga clic en **[!UICONTROL Vista previa]** para obtener una vista previa de todos los cambios. Toque o haga clic **[!UICONTROL Listo]** para guardar los cambios de edición en el material.

   >[!NOTE]
   >
   >Los iconos Vista previa y Listo solo se activan cuando los campos de imagen editables del material no tienen iconos que falten. Si faltan iconos en el colateral, es porque [!DNL Experience Manager] no puede resolver las imágenes de la plantilla de InDesign. Normalmente, [!DNL Experience Manager] no puede resolver imágenes en los siguientes casos:
   >
   >* Las imágenes no están incrustadas en la plantilla de InDesign subyacente
   >* Las imágenes están vinculadas desde el sistema de archivos local

   >
   >Para habilitar [!DNL Experience Manager] para resolver las imágenes, haga lo siguiente:
   >
   >* Incrustar imágenes al crear plantillas de InDesign (consulte [Acerca de los vínculos y los gráficos incrustados](https://helpx.adobe.com/indesign/using/graphics-links.html)).
   >* Monte [!DNL Experience Manager] al sistema de archivos local y, a continuación, asigne los iconos que faltan con los existentes [!DNL Experience Manager] activos.

   >
   >Para obtener más información sobre cómo trabajar con documentos de InDesign, consulte [Prácticas recomendadas para trabajar con documentos de InDesign en [!DNL Experience Manager]](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Para generar una representación de PDF para el folleto, seleccione la opción Acrobat en el cuadro de diálogo y haga clic en **[!UICONTROL Continuar]**.
1. El material colateral se crea en la carpeta con la que comenzó. Para ver las representaciones, abra la garantía y elija **[!UICONTROL Representaciones]** de la lista de navegación global.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. Pulse o haga clic en la representación del PDF en la lista de representaciones para descargar el archivo del PDF. Abra el archivo del PDF para revisar el colateral.

   ![chlimage_1-324](assets/chlimage_1-324.png)

## Combinar material colateral {#merge-collateral}


1. Toque o haga clic en **[!UICONTROL Herramientas > Assets]**.
1. En las opciones , elija **[!UICONTROL Plantillas]**.
1. Toque o haga clic **[!UICONTROL Crear]** y elija **[!UICONTROL Combinar]** del menú .

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. En la página Combinar plantilla , pulse o haga clic en el icono Combinar .

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. Vaya a la ubicación del material que desea combinar, toque o haga clic en las miniaturas del material que desea combinar para seleccionarlas.

   ![chlimage_1-327](assets/chlimage_1-327.png)

   Incluso puede buscar plantillas desde el cuadro OmniSearch .

   ![chlimage_1-328](assets/chlimage_1-328.png)

   Puede navegar por el [!DNL Assets] repositorio o colecciones, desplácese a la ubicación de las plantillas deseadas y selecciónelas para fusionarlas.

   ![chlimage_1-329](assets/chlimage_1-329.png)

   Puede aplicar varios filtros para buscar en las plantillas que desee. Por ejemplo, puede buscar plantillas basadas en el tipo de archivo o en etiquetas.

   ![chlimage_1-330](assets/chlimage_1-330.png)

1. Toque o haga clic **[!UICONTROL Siguiente]** en la barra de herramientas.
1. En el **[!UICONTROL Vista previa y reordenación]** , reorganice las plantillas si es necesario y previsualice la selección de plantillas que desea combinar. A continuación, toque o haga clic en **[!UICONTROL Siguiente]** en la barra de herramientas.

   ![chlimage_1-331](assets/chlimage_1-331.png)

1. En la pantalla Configurar plantilla , especifique un nombre para el colateral. De forma opcional, especifique las etiquetas que considere adecuadas. Si desea exportar la salida en formato de PDF, seleccione la opción **[!UICONTROL Acrobat (.PDF)]** . De forma predeterminada, la garantía se exporta en formato de JPG y InDesign. Para cambiar la miniatura de visualización del material de varias páginas, toque o haga clic en **[!UICONTROL Cambiar miniatura]**.

   ![chlimage_1-332](assets/chlimage_1-332.png)

1. Toque o haga clic **[!UICONTROL Guardar]** y, a continuación, toque o haga clic en **[!UICONTROL OK]** en el cuadro de diálogo para cerrar el cuadro de diálogo. El material colateral de varias páginas se crea en la carpeta con la que comenzó.

   >[!NOTE]
   >
   >No se puede editar un material combinado posteriormente ni utilizarlo para crear otro material colateral.
