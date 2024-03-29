---
title: Prueba de componentes principales en We.Retail
seo-title: Trying out Core Components in We.Retail
description: Prueba de componentes principales en We.Retail
seo-description: null
uuid: 8d1cea0b-99d9-49b2-b275-41f14864b1ff
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: af3cd818-61cf-4da1-bfb5-87540911ddd5
exl-id: b77d0e6b-3005-4dba-8e88-70b4d04b1eba
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 2%

---

# Prueba de componentes principales en We.Retail{#trying-out-core-components-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los componentes principales son componentes modernos y flexibles, con fácil extensibilidad y que permiten una integración sencilla en sus proyectos. Los componentes principales se han creado en torno a varios principios de diseño principales, como HTL, usabilidad predeterminada, configurabilidad, versiones y extensibilidad. We.Retail se ha creado sobre componentes principales.

## Probándolo {#trying-it-out}

1. Comience AEM con el contenido de muestra de We.Retail y abra el [Consola Componentes](/help/sites-authoring/default-components-console.md).

   **Navegación global -> Herramientas -> Componentes**

1. Al abrir el carril en la consola Componentes, puede filtrar para un grupo de componentes determinado. Los componentes principales se pueden encontrar en

   * `.core-wcm`: Los componentes principales estándar
   * `.core-wcm-form`: Componentes principales del envío de formularios

   Choose `.core-wcm`.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Tenga en cuenta que todos los componentes principales tienen un nombre **v1**, reflejando que esta es la primera versión de este componente principal. En adelante se lanzarán versiones regulares, compatibles con la versión de AEM y que facilitan la actualización para que pueda aprovechar las últimas funciones.
1. Haga clic en **Texto (v1)**.

   Consulte que la variable **Tipo de recurso** del componente es `/apps/core/wcm/components/text/v1/text`. Los componentes principales se encuentran en `/apps/core/wcm/components` y tienen versiones por componente.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Haga clic en el **Documentación** para ver la documentación del desarrollador del componente.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Vuelva a la consola Componentes. Filtro para el grupo **We.Retail** y seleccione **Texto** componente.
1. Consulte que la variable **Tipo de recurso** señala un componente como se espera en `/apps/weretail` pero la variable **Supertipo de recurso** señala al componente principal `/apps/core/wcm/components/text/v1/text`.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Haga clic en el **Uso de Live** para ver en qué páginas se está utilizando este componente. Haga clic en la primera **Gracias** para editar la página.

   ![chlimage_1-166](assets/chlimage_1-166.png)

1. En la página de agradecimiento, seleccione el componente de texto y, en el menú de edición del componente, haga clic en el icono Cancelar herencia .

   [We.Retail tiene una estructura de sitio globalizada](/help/sites-developing/we-retail-globalized-site-structure.md) donde el contenido se inserta de los maestros de idioma a [Live Copies a través de un mecanismo llamado herencia](/help/sites-administering/msm.md). Por este motivo, la herencia debe cancelarse para permitir que un usuario edite manualmente el texto.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Confirme la cancelación haciendo clic en **Sí**.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Una vez cancelada la herencia y que seleccione los componentes de texto, hay muchas más opciones disponibles. Haga clic en** Editar**.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Ahora puede ver qué opciones de edición están disponibles para el componente de texto.

   ![chlimage_1-170](assets/chlimage_1-170.png)

1. En el **Información de la página** menú seleccionar **Editar plantilla**.
1. En el Editor de plantillas de la página, haga clic en el **Política** del componente Texto en la **Contenedor de diseño** de la página.

   ![chlimage_1-171](assets/chlimage_1-171.png)

1. Los componentes principales permiten a un autor de plantillas configurar qué propiedades están disponibles para los autores de la página. Estas incluyen funciones como fuentes de pegado permitidas, opciones de formato, estilos de párrafo disponibles, etc.

   Estos cuadros de diálogo de diseño están disponibles para muchos componentes principales y funcionan de la mano con el editor de plantillas. Una vez activados, estarán disponibles para el autor a través de los editores de componentes.

   ![chlimage_1-172](assets/chlimage_1-172.png)

## Información adicional {#further-information}

Para obtener más información sobre los componentes principales, consulte el documento de creación [Componentes principales](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=es) para obtener una descripción general de las capacidades de los componentes principales y del documento para desarrolladores [Desarrollo de componentes principales](https://helpx.adobe.com/experience-manager/core-components/using/developing.html) para obtener una descripción general técnica.

También puede que desee investigar más a fondo [plantillas editables](/help/sites-developing/we-retail-editable-templates.md). Consulte el documento de creación [Creación de plantillas de página](/help/sites-authoring/templates.md) o la página del documento para desarrolladores [Plantillas: editables](/help/sites-developing/page-templates-editable.md) para obtener información detallada sobre plantillas editables.
