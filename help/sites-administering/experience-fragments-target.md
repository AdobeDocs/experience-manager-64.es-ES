---
title: Integración de Destinatario con fragmentos de experiencia
seo-title: Integración de Destinatario con fragmentos de experiencia
description: Integración de Destinatario con fragmentos de experiencia
seo-description: Integración de Destinatario con fragmentos de experiencia
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# Integración de Destinatario con fragmentos de experiencia{#target-integration-with-experience-fragments}

>[!NOTE]
>
>Esta funcionalidad requiere la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o posterior.

Puede exportar fragmentos [de experiencias](/help/sites-authoring/experience-fragments.md), creados en Adobe Experience Manager (AEM), a Adobe Target. A continuación, se pueden utilizar como ofertas en actividades de Destinatario para probar y personalizar experiencias a escala. Esto le permite combinar la facilidad de uso y el poder de AEM, con las potentes capacidades de Inteligencia automatizada (AI) y Aprendizaje automático (ML) en Destinatario.

## Requisitos previos {#prerequisites}

Se requieren varias acciones:

1. Hay que integrar AEM con Destinatario. See [Integrating with Adobe Target](/help/sites-administering/target.md) for more information.
1. Los fragmentos de experiencia se exportan desde la instancia de autor, por lo que debe [configurar el Externalizador](/help/sites-developing/externalizer.md) de vínculos en la instancia de autor para garantizar que los vínculos se externalicen para la instancia de publicación.

## Añadir la configuración de la nube {#add-the-cloud-configuration}

Antes de exportar un fragmento, debe agregar la Configuración **de** nube para **Adobe Target** al fragmento o carpeta:

1. Navigate to the **Experience Fragments** console.
1. Abra Propiedades **de página** para la carpeta o fragmento correspondiente.

   >[!NOTE]
   >
   >Si agrega la configuración de nube a la carpeta principal del fragmento de experiencia, todos los elementos secundarios heredarán la configuración.
   >
   >Si agrega la configuración de nube al propio fragmento de experiencias, todas las variaciones heredan la configuración.

1. Seleccione la ficha **Cloud Services** .

1. En Configuración **de** Cloud Service, seleccione **Adobe Target** en la lista desplegable.
1. En **Adobe Target**, seleccione la configuración adecuada.

1. **Guardar y cerrar**.

## Exportación de un fragmento de experiencia a un Destinatario {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Para los recursos de medios, como las imágenes, solo se exporta una referencia a Destinatario. El recurso en sí permanece almacenado en AEM Assets y se entrega desde la instancia de publicación de AEM.
>
>Debido a esto, el fragmento de experiencias, con todos los recursos relacionados, debe publicarse antes de exportar a Destinatario.

Para exportar un fragmento de experiencia de AEM a Destinatario (después de especificar la Configuración de nube):

1. Vaya a la consola Fragmento de experiencias.
1. Seleccione el fragmento de experiencias que desee exportar a destinatario.

   >[!NOTE]
   >
   >Debe ser una variación web de fragmento de experiencia.

1. Toque o haga clic en **Exportar a Adobe Target**.

   >[!NOTE]
   >
   >Si el fragmento de experiencias ya se ha exportado, seleccione **Actualizar en Adobe Target**.

1. Toque o haga clic en **Exportar sin publicar** ni **publicar** según sea necesario.

   >[!NOTE]
   >
   >Si selecciona** Publicar**, se publicará el fragmento de experiencia inmediatamente y se enviará a Destinatario.

1. Toque o haga clic en **Aceptar** en el cuadro de diálogo de confirmación.

   El fragmento de experiencia debe estar en Destinatario.

>[!NOTE]
>
>Como alternativa, puede realizar la exportación desde el editor de páginas mediante comandos comparables en el menú Información [de](/help/sites-authoring/author-environment-tools.md#page-information) página.

## Uso de los fragmentos de experiencia en Destinatario {#using-your-experience-fragments-in-target}

Después de realizar las tareas anteriores, el fragmento de experiencia se muestra en Destinatario en la página Ofertas. Por favor, eche un vistazo a la documentación [](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) específica del Destinatario para conocer lo que puede lograr allí.

## Eliminación de un fragmento de experiencia ya exportado a Destinatario {#deleting-an-experience-fragment-already-exported-to-target}

La eliminación de un fragmento de experiencia que ya se ha exportado a Destinatario puede causar problemas si el fragmento ya se está utilizando en una oferta de Destinatario. Al eliminar el fragmento, la oferta quedaría inutilizable a medida que AEM el contenido del fragmento lo enviara.

Para evitar tales situaciones:

* Si el fragmento de experiencia no se está utilizando en una actividad, AEM permite al usuario eliminar el fragmento sin un mensaje de advertencia.
* Si un fragmento de experiencia está siendo utilizado actualmente por una actividad en Destinatario, un mensaje de error advierte al usuario AEM de las posibles consecuencias que tendrá en la actividad la eliminación del fragmento.

   El mensaje de error de AEM no prohíbe al usuario (forzar) la eliminación del fragmento de experiencias. Si se elimina el fragmento de experiencias:

   * La oferta de Destinatario con AEM fragmento de experiencias puede mostrar un comportamiento no deseado

      * Es probable que la oferta se siga procesando, ya que el HTML del fragmento de experiencias se insertó en el Destinatario
      * Es posible que las referencias del fragmento de experiencias no funcionen correctamente si también se eliminaron los recursos a los que se hace referencia en AEM.
   * Por supuesto, cualquier modificación adicional del fragmento de experiencias es imposible, ya que el fragmento de experiencias ya no existe en AEM.


