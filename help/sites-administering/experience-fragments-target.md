---
title: Integración de Target con fragmentos de experiencias
seo-title: Integración de Target con fragmentos de experiencias
description: Integración de Target con fragmentos de experiencias
seo-description: Integración de Target con fragmentos de experiencias
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
translation-type: tm+mt
source-git-commit: 4e5d3c0ae71f601bcf39fa768c8b5ac86decc1eb

---


# Integración de Target con fragmentos de experiencias{#target-integration-with-experience-fragments}

>[!NOTE]
>
>Esta funcionalidad requiere la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o posterior.

Puede exportar fragmentos [de experiencia](/help/sites-authoring/experience-fragments.md), creados en Adobe Experience Manager (AEM), a Adobe Target. A continuación, se pueden usar como ofertas en actividades de Target para probar y personalizar experiencias a escala. Esto le permite combinar la facilidad de uso y la potencia de AEM con las potentes funciones de Inteligencia automatizada (AI) y Aprendizaje automático (ML) en Target.

## Requisitos previos {#prerequisites}

Se requieren varias acciones:

1. Debe integrar AEM con Target. See [Integrating with Adobe Target](/help/sites-administering/target.md) for more information.
1. Los fragmentos de experiencia se exportan desde la instancia de autor, por lo que debe [configurar el Externalizador](/help/sites-developing/externalizer.md) de vínculos en la instancia de autor para garantizar que los vínculos se externalicen para la instancia de publicación.

## Agregar la configuración de nube {#add-the-cloud-configuration}

Antes de exportar un fragmento, debe agregar la Configuración **de** nube para **Adobe Target** al fragmento o carpeta:

1. Navigate to the **Experience Fragments** console.
1. Abra Propiedades **de página** para la carpeta o fragmento correspondiente.

   >[!NOTE]
   >
   >Si agrega la configuración de nube a la carpeta principal del fragmento de experiencia, todos los elementos secundarios heredarán la configuración.
   >
   >Si agrega la configuración de nube al propio fragmento de experiencias, todas las variaciones heredan la configuración.

1. Seleccione la ficha **Cloud Services** .

1. En Configuración **del servicio de** nube, seleccione **Adobe Target** en la lista desplegable.
1. En **Adobe Target**, seleccione la configuración adecuada.

1. **Guardar y cerrar**.

## Exportación de un fragmento de experiencia a Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Para los recursos de medios, como las imágenes, solo se exporta una referencia a Target. El recurso en sí permanece almacenado en Recursos AEM y se entrega desde la instancia de publicación de AEM.
>
>Debido a esto, el fragmento de experiencias, con todos los recursos relacionados, debe publicarse antes de exportar a Target.

Para exportar un fragmento de experiencia de AEM a Target (después de especificar la Configuración de nube):

1. Vaya a la consola Fragmento de experiencias.
1. Seleccione el fragmento de experiencias que desee exportar a Target.

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
   >Si selecciona** Publicar**, se publicará el fragmento de experiencia inmediatamente y se enviará a Target.

1. Toque o haga clic en **Aceptar** en el cuadro de diálogo de confirmación.

   El fragmento de experiencia debe estar ahora en Target.

>[!NOTE]
>
>Como alternativa, puede realizar la exportación desde el editor de páginas mediante comandos comparables en el menú Información [de](/help/sites-authoring/author-environment-tools.md#page-information) página.

## Uso de los fragmentos de experiencias en Target {#using-your-experience-fragments-in-target}

Después de realizar las tareas anteriores, el fragmento de experiencia se muestra en la página Ofertas de Target. Consulte la documentación [](https://experiencecloud.adobe.com/resources/help/en_US/target/target/aem-experience-fragments.html) específica de Target para obtener más información sobre lo que se puede lograr allí.

## Eliminación de un fragmento de experiencia ya exportado a Target {#deleting-an-experience-fragment-already-exported-to-target}

La eliminación de un fragmento de experiencia que ya se ha exportado a Target puede causar problemas si el fragmento ya se está utilizando en una oferta de Target. Al eliminar el fragmento, la oferta quedaría inutilizable a medida que AEM enviara el contenido del fragmento.

Para evitar tales situaciones:

* Si el fragmento de experiencias no se está utilizando actualmente en una actividad, AEM permite al usuario eliminar el fragmento sin un mensaje de advertencia.
* Si una actividad de Target está utilizando el fragmento de experiencias, aparece un mensaje de error que advierte al usuario de AEM de las posibles consecuencias que tendrá la eliminación del fragmento en la actividad.

   El mensaje de error en AEM no prohíbe al usuario (forzar)eliminar el fragmento de experiencias. Si se elimina el fragmento de experiencias:

   * La oferta de Target con el fragmento de experiencia de AEM puede mostrar un comportamiento no deseado

      * Es probable que la oferta se siga representando, ya que el HTML del fragmento de experiencias se insertó en Target
      * Es posible que las referencias del fragmento de experiencias no funcionen correctamente si los recursos a los que se hace referencia también se eliminan en AEM.
   * Por supuesto, cualquier modificación adicional del fragmento de experiencias es imposible, ya que el fragmento de experiencias ya no existe en AEM.


