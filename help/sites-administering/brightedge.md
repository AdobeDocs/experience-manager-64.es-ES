---
title: Integración con BrightEdge Content Optimizer
seo-title: Integrating with BrightEdge Content Optimizer
description: Obtenga información sobre la integración de AEM con BrightEdge Content Optimizer.
seo-description: Learn about integrating AEM with BrightEdge Content Optimizer.
uuid: 7075dd3c-2fd6-4050-af1c-9b16ad4366ec
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: cf25c9a8-0555-4c67-8aa5-55984fd8d301
exl-id: 46d0513c-04b2-41ed-bb56-e0778fa5fd10
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# Integración con BrightEdge Content Optimizer{#integrating-with-brightedge-content-optimizer}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cree una configuración de nube de BrightEdge para que AEM pueda conectarse con las credenciales de su cuenta de BrightEdge. Puede crear varias configuraciones si utiliza varias cuentas.

Al crear la configuración, debe especificar un título. El título debe ser descriptivo para que las personas puedan correlacionar la configuración con la cuenta de BrightEdge . Cuando un autor de páginas o un administrador asocian una página web con la cuenta de BrightEdge, este título se presenta en una lista desplegable.

1. En el carril , haga clic en Herramientas > Operaciones > Nube > Cloud Services.
1. Haga clic en el vínculo que aparece en la sección Optimizador de contenido de BrightEdge . Si se ha creado una configuración de BrightEdge determina el texto del vínculo:

   * Configurar ahora: Este vínculo aparece cuando no se ha creado ninguna configuración.
   * Mostrar configuraciones: Este vínculo aparece cuando se han creado una o más configuraciones.

   ![Chlimage_1-4](assets/chlimage_1-4.png)

1. Si ha hecho clic en Mostrar configuraciones, haga clic en el vínculo + situado junto a Configuraciones disponibles.
1. Escriba un título para la configuración. Opcionalmente, escriba un nombre para el nodo que se utiliza para almacenar la configuración en el repositorio. Haga clic en Crear.
1. En el cuadro de diálogo Configuración de BrightEdge Content Optimizer, escriba el nombre de usuario y la contraseña de la cuenta de BrightEdge y, a continuación, haga clic en Aceptar.

## Edición de una configuración de BrightEdge {#editing-a-brightedge-configuration}

Modifique el nombre de usuario y la contraseña de una configuración de BrightEdge cuando sea necesario. Las modificaciones afectan a todas las páginas que utilizan la configuración.

1. En el carril , haga clic en Herramientas > Operaciones > Nube > Cloud Services.
1. En la sección Optimizador de contenido de BrightEdge , haga clic en Mostrar configuraciones.

   ![Chlimage_1-5](assets/chlimage_1-5.png)

1. Haga clic en el nombre de la configuración que desee editar.
1. Haga clic en Editar, modifique los valores de las propiedades y, a continuación, haga clic en Aceptar.

## Asociación de páginas con una configuración de BrightEdge {#associating-pages-with-a-brightedge-configuration}

Asocie páginas con una configuración de BrightEdge para enviar datos de página al servicio BrightEdge para su análisis. Cuando asocia una página con una configuración, las páginas secundarias heredan la asociación. Normalmente, se asocia la página principal del sitio para que los datos de todas las páginas se envíen a BrightEdge.

1. Abra la consola Sitios web clásica . ([http://localhost:4502/siteadmin#/content](http://localhost:4502/siteadmin#/content))
1. En el árbol Sitios web, seleccione la carpeta o página que contiene la página que desea asociar con la configuración de BrightEdge.
1. En la lista de páginas, haga clic con el botón derecho en la página para configurarla y haga clic en Propiedades.
1. En la ficha Cloud Services, haga clic en el botón Añadir servicio y, en el cuadro de diálogo Cloud Services, seleccione Optimizador de contenido de BrightEdge y, a continuación, haga clic en Aceptar.
1. En la lista Optimizador de contenido de BrightEdge , seleccione la configuración de BrightEdge que desea asociar a la página y, a continuación, haga clic en Aceptar.

   ![Chlimage_1-6](assets/chlimage_1-6.png)

## Activación de una configuración de BrightEdge {#activating-a-brightedge-configuration}

Active una configuración de BrightEdge para replicarla en la instancia de publicación y permitir que las páginas publicadas interactúen con el servicio BrightEdge.

1. En el carril, haga clic en Sitios y, a continuación, busque y seleccione la página asociada a la configuración de BrightEdge.
1. Toque o haga clic en el icono Publicar y, a continuación, toque o haga clic en Publicar .

   ![Chlimage_1-7](assets/chlimage_1-7.png)

1. En la lista de configuraciones que aparecen, asegúrese de que la configuración de BrightEdge esté seleccionada y, a continuación, haga clic en Publicar.

   ![Chlimage_1-8](assets/chlimage_1-8.png)
