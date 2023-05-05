---
title: Integración de Target con fragmentos de experiencias
seo-title: Target Integration with Experience Fragments
description: Integración de Target con fragmentos de experiencias
seo-description: Target Integration with Experience Fragments
uuid: 621f57d4-3b8d-49ea-b193-8530c8fbd74e
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6911c8e3-b12c-466e-8255-5dcd09557d35
exl-id: dbde3cb6-4132-4462-bd4c-0e4439110e2e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 76%

---

# Integración de Target con fragmentos de experiencias{#target-integration-with-experience-fragments}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>Esta funcionalidad requiere la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0)](/help/release-notes/sp-release-notes.md) o posterior.

Puede exportar [Fragmentos de experiencias](/help/sites-authoring/experience-fragments.md), creado en Adobe Experience Manager (AEM), en Adobe Target. Luego pueden utilizarse como ofertas en actividades de Target para probar y personalizar experiencias a escala. Esto le permite combinar la facilidad de uso y la potencia de AEM con las potentes capacidades de Inteligencia automatizada (AI) y Aprendizaje automático (ML) en Target.

## Requisitos previos {#prerequisites}

Se requieren varias acciones:

1. Tiene que integrar AEM con Target. Consulte [Integración con Adobe Target](/help/sites-administering/target.md) para obtener más información.
1. Los fragmentos de experiencias se exportan desde la instancia de autor, por lo que debe [Configuración del externalizador de vínculos](/help/sites-developing/externalizer.md) en la instancia de autor para asegurarse de que los vínculos se externalicen para la instancia de publicación.

## Agregar la configuración de nube {#add-the-cloud-configuration}

Antes de exportar un fragmento, debe agregar la **Configuración de nube** para **Adobe Target** al fragmento o carpeta:

1. Vaya a la consola de **fragmentos de experiencias**.
1. Abra **Propiedades de página** para la carpeta o fragmento correspondiente.

   >[!NOTE]
   >
   >Si agrega la configuración de nube a la carpeta principal del fragmento de experiencia, la configuración la heredan todos los elementos secundarios.
   >
   >Si agrega la configuración de nube al propio fragmento de experiencia, esta se hereda de todas las variaciones.

1. Seleccione la pestaña **Cloud Services**.

1. En **Configuración del Cloud Service**, seleccione **Adobe Target** en la lista desplegable.
1. En **Adobe Target**, seleccione la configuración adecuada.

1. **Guardar y cerrar**.

## Exportación de un fragmento de experiencia a Target {#exporting-an-experience-fragment-to-target}

>[!NOTE]
>
>Para los activos de medios, como las imágenes, solo se exporta una referencia a Target. El recurso en sí permanece almacenado en AEM Assets y se entrega desde la instancia de publicación de AEM.
>
>Debido a esto, el fragmento de experiencia, con todos los activos relacionados, debe publicarse antes de exportarse a Target.

Para exportar un fragmento de experiencia de AEM a Target (después de especificar la Configuración de nube):

1. Vaya a la consola Fragmento de experiencias.
1. Seleccione el fragmento de experiencia que desea exportar a target.

   >[!NOTE]
   >
   >Debe ser una variación web del Fragmento de experiencia.

1. Toque o haga clic en **Exportar a Adobe Target**.

   >[!NOTE]
   >
   >Si el fragmento de experiencia ya se ha exportado, seleccione **Actualización del estado en Adobe Target**.

1. Toque o haga clic en **Exportación sin publicación** o **Publicación** según sea necesario.

   >[!NOTE]
   >
   >Si selecciona** Publicar**, el fragmento de experiencia se publicará de inmediato y se enviará a Target.

1. Toque o haga clic en **Aceptar** en el cuadro de diálogo de confirmación.

   El fragmento de experiencia debería estar en Target.

>[!NOTE]
>
>También puede realizar la exportación desde el editor de páginas utilizando comandos comparables en el menú [Información de la página](/help/sites-authoring/author-environment-tools.md#page-information).

## Uso de los fragmentos de experiencias en Target {#using-your-experience-fragments-in-target}

Después de realizar las tareas anteriores, el fragmento de experiencia se muestra en la página Ofertas de Target. Consulte la [documentación específica de Target](https://experiencecloud.adobe.com/resources/help/es_ES/target/target/aem-experience-fragments.html) para aprender lo que se puede lograr allí.

## Eliminación de un fragmento de experiencia ya exportado a Target {#deleting-an-experience-fragment-already-exported-to-target}

La eliminación de un fragmento de experiencia que ya se ha exportado a Target puede causar problemas si el fragmento ya se está utilizando en una oferta de Target. Si se elimina el fragmento, la oferta quedaría inutilizable, ya que AEM está entregando el contenido del fragmento.

Para evitar estas situaciones, haga lo siguiente:

* Si el fragmento de experiencia no se está utilizando en una actividad, AEM permite al usuario eliminar el fragmento sin un mensaje de advertencia.
* Si una actividad de Target está utilizando actualmente el fragmento de experiencia, un mensaje de error advierte al usuario de AEM de las posibles consecuencias que tendrá la eliminación del fragmento en la actividad.

   El mensaje de error de AEM no impide que el usuario elimine (a la fuerza) el fragmento de experiencia. Si se elimina el fragmento de experiencia:

   * La oferta de Target con el fragmento de experiencia de AEM puede mostrar un comportamiento no deseado

      * Es probable que la oferta se siga procesando, ya que el HTML del fragmento de experiencia se insertó en Target
      * Puede que cualquier referencia en el fragmento de experiencia no funcione correctamente si también se eliminaron activos a los que se hace referencia en AEM.
   * Por supuesto, cualquier modificación adicional en el fragmento de experiencia es imposible, ya que el fragmento de experiencia ya no existe en AEM.
