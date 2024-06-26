---
title: Introducción y tutorial de SPA
seo-title: SPA Introduction and Walkthrough
description: Este artículo presenta los conceptos de un SPA y explica cómo usar una aplicación de SPA básica para la creación, mostrando cómo se relaciona con el Editor de SPA de AEM subyacente.
seo-description: This article introduces the concepts of a SPA and walks through using a basic SPA application for authoring, showing how it relates to the underlying AEM SPA Editor.
uuid: 97a199af-b684-433d-b7b1-a8378513cb3d
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 77b42490-15db-41d5-9757-17009f1c1efd
exl-id: 85179139-a841-42b0-8590-d1fb88c1ebbf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 59%

---

# Introducción y tutorial de SPA{#spa-introduction-and-walkthrough}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las aplicaciones de una sola página (SPA) pueden ofrecer experiencias atractivas para los usuarios de sitios web. Los desarrolladores quieren poder generar sitios usando marcos de SPA y los autores quieren editar contenido dentro de AEM para un sitio generado usando dichos marcos.

El Editor de SPA ofrece una solución completa para admitir las SPA dentro de AEM. Este artículo presenta el uso de una aplicación SPA básica para la creación y muestra cómo se relaciona con el Editor de SPA de AEM subyacente.

>[!NOTE]
>
>La función Editor de aplicaciones de una sola página (SPA) requiere AEM 6.4 service pack 2 o posterior.
>
>El Editor de SPA es la solución recomendada para proyectos que requieren SPA procesamiento del lado del cliente basado en el marco de trabajo (por ejemplo, React o Angular).

## Introducción {#introduction}

### Objetivo del artículo {#article-objective}

Este artículo presenta los conceptos básicos de las SPA antes de guiar al lector a través de un tutorial del editor de SPA utilizando una sencilla aplicación de SPA para demostrar la edición básica del contenido. A continuación, se profundiza en la construcción de la página y en cómo se relaciona la aplicación SPA con el Editor de SPA de AEM y cómo interactúa con ella.

La meta de esta introducción y tutorial es demostrar a un desarrollador AEM por qué los SPA son relevantes, cómo funcionan en general, cómo el editor de SPA gestiona las SPA y cómo es diferente de una aplicación AEM estándar.

El tutorial se basa en la funcionalidad de AEM estándar y en la aplicación de diario We.Retail de ejemplo. Deben cumplirse los siguientes requisitos:

* [AEM versión 6.4 con Service Pack 2 o posterior](/help/release-notes/sp-release-notes.md)
* [Instale la aplicación de muestra de We.Retail Journal disponible en GitHub aquí.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)

>[!CAUTION]
>
>Este documento utiliza la variable [Aplicación de diario We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) únicamente con fines de demostración. No debe utilizarse para ningún trabajo de proyecto.
>
>Cualquier proyecto AEM debería aprovechar el [Tipo de archivo del proyecto AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=es), que admite proyectos de SPA que utilizan React o Angular y aprovecha el SDK de SPA.

### ¿Qué es una SPA? {#what-is-a-spa}

Una aplicación de una sola página (SPA) difiere de una página convencional en que se procesa en el lado del cliente y principalmente está dirigida por JavaScript, y se basa en llamadas Ajax para cargar datos y actualizar la página de forma dinámica. La mayoría o todo el contenido se recupera una vez en una carga de una sola página con recursos adicionales cargados asincrónicamente según sea necesario en función de la interacción del usuario con la página.

Esto reduce la necesidad de actualizaciones de la página y presenta al usuario una experiencia que es fluida, rápida y se parece más a una experiencia nativa de la aplicación.

El Editor de SPA de AEM permite a los desarrolladores de front-end crear SPA que se pueden integrar en un sitio AEM, lo que permite a los autores de contenido editar el contenido SPA tan fácilmente como cualquier otro contenido de AEM.

### ¿Por qué una SPA? {#why-a-spa}

Al ser más rápido, fluido y más parecido a una aplicación nativa, una SPA se convierte en una experiencia muy atractiva no solo para el visitante de la página web, sino también para los especialistas en marketing y desarrolladores debido a la naturaleza de cómo funcionan las SPA.

![screen_shot_2018-08-20at135550](assets/screen_shot_2018-08-20at135550.png)

**Visitantes**

* Los visitantes desean experiencias nativas cuando interactúan con el contenido.
* Hay datos claros de que cuanto más rápida sea una página, más probable será que se produzca una conversión.

**Especialistas en marketing**

* Los especialistas en marketing desean ofrecer experiencias ricas y nativas para atraer visitantes a fin de que participen plenamente en el contenido.
* La personalización puede hacer que estas experiencias sean aún más atractivas.

**Desarrolladores**

* Los desarrolladores quieren una separación clara de las preocupaciones entre el contenido y la presentación.
* La separación limpia hace que el sistema sea más extensible y permite el desarrollo independiente del front-end.

### ¿Cómo funciona una SPA? {#how-does-a-spa-work}

La idea principal de una SPA es que las llamadas y la dependencia de un servidor se reducen para minimizar los retrasos causados por las llamadas al servidor de modo que el SPA se aproxime a la capacidad de respuesta de una aplicación nativa.

En una página web secuencial tradicional, solo se cargan los datos necesarios para la página inmediata. Esto significa que cuando el visitante se mueve a otra página, se llama al servidor para obtener los recursos adicionales. Pueden ser necesarias llamadas adicionales, ya que el visitante interactúa con los elementos de la página. Estas llamadas múltiples pueden dar una sensación de retardo o retraso, ya que la página tiene que estar al día con las solicitudes del visitante.

![screen_shot_2018-08-20at140449](assets/screen_shot_2018-08-20at140449.png)

Para una experiencia más fluida, que se acerca a lo que un visitante espera de las aplicaciones móviles nativas, un SPA carga todos los datos necesarios para el visitante en la primera carga. Aunque esto puede tardar un poco más al principio, elimina la necesidad de realizar llamadas al servidor adicionales.

Al realizar el procesamiento en el lado del cliente, el elemento de página reacciona más rápido y las interacciones con la página por parte del visitante son inmediatas. Cualquier dato adicional que se necesite se llama asincrónicamente para maximizar la velocidad de la página.

>[!NOTE]
>
>Para obtener detalles técnicos sobre cómo SPA funciona en AEM, consulte el artículo [Introducción a SPA en AEM](/help/sites-developing/spa-getting-started-react.md).
>
>Para obtener más información sobre el diseño, la arquitectura y el flujo de trabajo técnico del Editor de SPA, consulte el artículo [Información general del Editor de SPA](/help/sites-developing/spa-overview.md).

## Experiencia de edición de contenido con SPA {#content-editing-experience-with-spa}

Cuando se crea un SPA para aprovechar el AEM SPA Editor, el autor del contenido no observa ninguna diferencia al editar y crear contenido. La funcionalidad común de AEM está disponible y no se requieren cambios en el flujo de trabajo del autor.

>[!NOTE]
>
>El tutorial se basa en la funcionalidad de AEM estándar y en la aplicación de diario We.Retail de ejemplo. Deben cumplirse los siguientes requisitos:
>
>* [AEM versión 6.4 con Service Pack 2](/help/release-notes/sp-release-notes.md)
>* [Instale la aplicación de muestra de We.Retail Journal disponible en GitHub aquí.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)
>


1. Edite la aplicación de diario We.Retail en AEM.

   `http://localhost:4502/editor.html/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at142533](assets/screen_shot_2018-06-07at142533.png)

1. Seleccione un componente de encabezado y observe que aparece una barra de herramientas como cualquier otro componente. Seleccione **[!UICONTROL Editar]**.

   ![screen_shot_2018-06-07at142937](assets/screen_shot_2018-06-07at142937.png)

1. Edite el contenido como de costumbre dentro de AEM y note que los cambios se mantienen.

   ![screen_shot_2018-06-07at143419](assets/screen_shot_2018-06-07at143419.png)

   >[!NOTE]
   >Consulte la [Información general del Editor de SPA](spa-overview.md#requirements-limitations) para obtener más información sobre el editor de texto in situ y el SPA.

1. Utilice el explorador de recursos para arrastrar y soltar una nueva imagen en un componente de imagen.

   ![screen_shot_2018-06-07at143530](assets/screen_shot_2018-06-07at143530.png)

1. El cambio se mantendrá.

   ![screen_shot_2018-06-07at143732](assets/screen_shot_2018-06-07at143732.png)

Se admiten herramientas de creación adicionales, como arrastrar y soltar componentes adicionales en la página, reorganizar componentes y modificar el diseño, como en cualquier aplicación que no sea de SPA.

>[!NOTE]
>
>El Editor de SPA no modifica el DOM de la aplicación. El propio SPA es responsable del DOM.
>
>Para ver cómo funciona esto, continúe con la siguiente sección de este artículo. [Aplicaciones de SPA y el Editor de SPA de AEM](/help/sites-developing/spa-walkthrough.md#spa-apps-and-the-aem-spa-editor).

## Aplicaciones SPA y el Editor de SPA de AEM {#spa-apps-and-the-aem-spa-editor}

Experimentar cómo se comporta un SPA para el usuario final y luego inspeccionar la página SPA ayuda a comprender mejor cómo funciona una aplicación SAP con el SPA Editor en AEM.

### Uso de la aplicación SPA {#using-an-spa-application}

1. Cargue la aplicación de diario We.Retail en el servidor de publicación o utilice la opción **[!UICONTROL Ver tal y como aparece publicado]** de la variable **Información de la página** en el editor de páginas.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-08at102650](assets/screen_shot_2018-06-08at102650.png)

   Tenga en cuenta la estructura de las páginas, incluida la navegación a páginas secundarias, widget meteorológico y artículos.

1. Vaya a una página secundaria usando el menú y vea que la página se carga inmediatamente sin necesidad de actualizar.

   ![screen_shot_2018-06-08at102815](assets/screen_shot_2018-06-08at102815.png)

1. Abra las herramientas de desarrollador integradas del explorador y supervise la actividad de red a medida que navega por las páginas secundarias.

   ![screen_shot_2018-06-08at103922](assets/screen_shot_2018-06-08at103922.png)

   Hay muy poco tráfico a medida que se mueve de página en página en la aplicación. La página no se vuelve a cargar y solo se solicitan las imágenes nuevas.

   El SPA administra el contenido y el enrutamiento por completo en el lado del cliente.

Por lo tanto, si la página no se vuelve a cargar al navegar por las páginas secundarias, ¿cómo se carga?

La siguiente sección, [Carga de una aplicación SPA](/help/sites-developing/spa-walkthrough.md#loading-an-spa-application), profundiza en la mecánica de carga del SPA y en cómo se puede cargar el contenido sincrónica y asincrónicamente.

### Carga de una aplicación SPA {#loading-an-spa-application}

1. Si aún no se ha cargado, cargue la aplicación We.Retail Journal en el servidor de publicación o utilizando la opción **[!UICONTROL Ver tal y como aparece publicado]** de la variable **Información de la página** en el editor de páginas.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at144736](assets/screen_shot_2018-06-07at144736.png)

1. Utilice la herramienta integrada de su navegador para ver la fuente de la página.
1. Tenga en cuenta que el contenido de la fuente es extremadamente limitado.

   ```
   <!DOCTYPE HTML>
   <html lang="en-CH">
       <head>
       <meta charset="UTF-8">
       <title>We.Retail Journal</title>
   
       <meta name="template" content="we-retail-react-template"/>
   
   <link rel="stylesheet" href="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.css" type="text/css">
   
   <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
   
   </head>
       <body class="page basicpage">
   
   <div id="page"></div>
   
   <script type="text/javascript" src="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.js"></script>
   
       </body>
   </html>
   ```

   La página no tiene contenido dentro de su cuerpo. Se compone principalmente de hojas de estilo y una llamada a un script React, `we-retail-journal-react.js`.

   Este script React es el controlador principal de esta aplicación y es responsable de procesar todo el contenido.

1. Utilice las herramientas integradas de su explorador para inspeccionar la página. Consulte el contenido del DOM completamente cargado.

   ![screen_shot_2018-06-07at151848](assets/screen_shot_2018-06-07at151848.png)

1. Cambie a la pestaña Red en el Inspector y vuelva a cargar la página.

   Ignorando las solicitudes de imagen, note que los recursos principales cargados para la página son la página en sí, CSS, React Javascript, sus dependencias, así como los datos JSON de la página.

   ![screen_shot_2018-06-07at152155](assets/screen_shot_2018-06-07at152155.png)

1. Cargue el `react.model.json` en una pestaña nueva.

   `/content/we-retail-journal/react.model.json`

   ![screen_shot_2018-06-07at152636](assets/screen_shot_2018-06-07at152636.png)

   El Editor de SPA de AEM aprovecha [Servicios de contenido de AEM](/help/assets/content-fragments.md) para entregar todo el contenido de la página como un modelo JSON.

   Al implementar interfaces específicas, los modelos Sling proporcionan la información necesaria para la SPA. El envío de los datos JSON se delega hacia abajo en cada componente (de página, a párrafo, a componente, etc.).

   Cada componente elige lo que expone y cómo se procesa (lado del servidor con HTL o lado del cliente con React). Por supuesto, este artículo se centra en la renderización del lado del cliente con React.

1. El modelo también puede agrupar las páginas de forma que se carguen sincrónicamente, lo que reduce el número de recargas de página necesarias.

   En el ejemplo de We.Retail Journal, la variable `home`, `blog`y `aboutus` las páginas se cargan sincrónicamente, ya que los visitantes suelen visitar todas esas páginas. Sin embargo, la variable `weather` se carga de forma asíncrona, ya que es menos probable que los visitantes la visiten.

   Este comportamiento no es obligatorio y es totalmente definible.

   ![screen_shot_2018-06-07at153945](assets/screen_shot_2018-06-07at153945.png)

1. Para ver esta diferencia de comportamiento, vuelva a cargar la página  y borre la actividad de red del inspector. Vaya al blog y a las páginas de uso en el menú de página y vea que no hay actividad de red reportada.

   Vaya a la página del tiempo y compruebe que la variable `weather.model.json` se llama asincrónicamente.

   ![screen_shot_2018-06-07at155738](assets/screen_shot_2018-06-07at155738.png)

### Interacción con el Editor de SPA {#interaction-with-the-spa-editor}

Con la aplicación de ejemplo We.Retail Journal, está claro cómo se comporta y se carga la aplicación cuando se publica, aprovechando los servicios de contenido para la entrega de contenido JSON, así como la carga asincrónica de recursos.

Además, para el autor del contenido, la creación de contenido mediante un editor de SPA es continua dentro de AEM.

En la siguiente sección analizaremos el contrato que permite al Editor de SPA relacionar componentes dentro del SPA con componentes de AEM y lograr esta experiencia de edición sin problemas.

1. Cargue la aplicación de diario We.Retail en el editor y cambie a **Vista previa** en el menú contextual.

   `http://localhost:4502/editor.html/content/we-retail-journal/react.html`

1. Con las herramientas de desarrollador incorporadas del explorador, inspeccione el contenido de la página. Usando la herramienta de selección, seleccione un componente editable en la página y vea los detalles del elemento.

   Tenga en cuenta que el componente tiene un nuevo atributo de datos `data-cq-data-path`.

   ![screen_shot_2018-06-08at095124](assets/screen_shot_2018-06-08at095124.png)

   Por ejemplo

   `data-cq-data-path="root/responsivegrid/paragraph_1`

   Estas rutas permiten la recuperación y asociación del objeto de configuración de contexto de edición de cada componente.

   Este es el único atributo de marcado necesario para que el editor reconozca este componente como editable dentro del SPA. En función de este atributo, el Editor de SPA determinará qué configuración editable está asociada al componente, de modo que el marco, la barra de herramientas, etc. correctos. se carga.

   También se agregan algunos nombres de clase específicos para marcar marcadores de posición y para la funcionalidad de arrastrar y soltar.

   >[!NOTE]
   >
   >Este es un cambio en el comportamiento de las páginas procesadas del lado del servidor en AEM, donde hay un `cq` elemento insertado para cada componente editable.
   >
   >Este método en SPA elimina la necesidad de insertar elementos personalizados, basándose únicamente en un atributo de datos adicional, lo que simplifica el marcado para el desarrollador de front-end.

## Pasos siguientes {#next-steps}

Ahora que comprende la experiencia de edición de SPA en AEM y cómo se relaciona un SPA con el Editor de SPA, profundice en la comprensión de cómo se crea una SPA.

* [Introducción a SPA en AEM](/help/sites-developing/spa-getting-started-react.md) muestra cómo se crea una SPA básica para trabajar con el Editor de SPA en AEM
* La [Información general del Editor de SPA](/help/sites-developing/spa-overview.md) profundiza en el modelo de comunicación entre AEM y el SPA.
* [Desarrollo de SPA para AEM](/help/sites-developing/spa-architecture.md) describe cómo involucrar a los desarrolladores de front-end para que desarrollen una SPA para AEM, así como cómo las SPA interactúan con la arquitectura de AEM.
