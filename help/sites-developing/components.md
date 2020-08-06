---
title: Componentes Información general
seo-title: Componentes
description: Los componentes son unidades modulares que cuentan con una funcionalidad específica para presentar el contenido en el sitio web
seo-description: Los componentes son unidades modulares que cuentan con una funcionalidad específica para presentar el contenido en el sitio web
uuid: fb39aeb8-8f43-4091-8083-ebfab89e6e63
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: 45efff93-2fe5-4313-83a0-0e23a540da93
translation-type: tm+mt
source-git-commit: b6a5b222bf6629dc14a16531972a2a50e2b5ed37
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 8%

---


# Información general de componentes{#components-overview}

Esta página proporciona información general sobre los componentes de Adobe Experience Manager (AEM), como los [utilizados para la creación](/help/sites-authoring/default-components-foundation.md)de páginas.

## ¿Qué son los componentes? {#what-exactly-is-a-component}

* Unidades modulares que proporcionan una funcionalidad específica para presentar el contenido en el sitio web.
* Reutilizable.
* Desarrollado como unidades independientes dentro de una carpeta del repositorio.
* No tiene archivos de configuración ocultos.
* Puede contener otros componentes.
* Puede ejecutarse en cualquier lugar dentro de cualquier sistema AEM. También pueden limitarse a ejecutarse en componentes específicos.
* Tener una interfaz de usuario estandarizada.
* Tener un comportamiento de edición que se pueda configurar.
* Utilizar cuadros de diálogo creados con subelementos basados en componentes Granite UI
* Se desarrollan con [HTL](https://helpx.adobe.com/experience-manager/htl/user-guide.html) (recomendado) o JSP.
* Se puede desarrollar para crear componentes personalizados que extiendan la funcionalidad predeterminada.

Debido a que los componentes son modulares, puede:

* Desarrolle un nuevo componente en la instancia local.
* Implementarlo en el entorno de prueba.
* Implementarla en el entorno de creación en directo, donde permite a los autores y/o administradores agregar y configurar contenido.
* Implíquelo en los entornos de publicación activa, donde se utilizan para procesar contenido para visitantes en el sitio web. Ciertos componentes, por ejemplo para Comunidades, también aceptan datos introducidos por los usuarios.

Cada componente AEM:

* Es un tipo de recurso.
* Es una colección de secuencias de comandos que realizan completamente una función específica.
* Puede funcionar *aisladamente*, es decir, dentro de AEM o en un portal.

## Componentes listos para usar dentro de AEM {#out-of-the-box-components-within-aem}

AEM comes with a variety of [out-of-the-box components](/help/sites-authoring/default-components.md) that provide comprehensive functionality including:

* Sistema de párrafos ( `parsys`)
* Página ( `responsivegrid` - solo IU táctil)
* Texto
* Imagen, con el texto que acompaña
* Barra de herramientas

Los componentes proporcionados y su uso dentro de los sitios web [We.Retail de](/help/sites-developing/we-retail.md) muestra ilustran cómo implementar y utilizar los componentes. Los componentes se proporcionan con todo el código fuente y pueden utilizarse tal cual o como puntos de partida para componentes modificados o ampliados.

### Componentes principales y componentes básicos {#core-components-and-foundation-components}

Hay dos conjuntos de componentes de AEM proporcionados por Adobe disponibles:

* [Componentes principales](https://docs.adobe.com/content/help/es-ES/experience-manager-core-components/using/introduction.html)
* [Componentes de base](/help/sites-authoring/default-components-foundation.md)

**Los componentes** principales se introdujeron con AEM 6.3 y la funcionalidad de creación flexible y con muchas funciones de oferta. El sitio [de referencia](/help/sites-developing/we-retail.md) We.Retail ilustra cómo se pueden utilizar los componentes principales y representa las optimizaciones actuales del desarrollo de componentes.

**Los componentes** básicos han estado disponibles con AEM para muchas versiones y están disponibles de forma predeterminada en una instalación AEM estándar. Aunque aún se admite, la mayoría de ellas han quedado obsoletas, ya no se mejoran y se basan en tecnologías heredadas.

>[!NOTE]
>
>[Los componentes](https://docs.adobe.com/content/help/es-ES/experience-manager-core-components/using/introduction.html) principales representan las prácticas recomendadas actuales para el diseño y el desarrollo de componentes y sirven como implementaciones de referencia.
>
>[AEM herramientas](modernization-tools.md) de modernización pueden ayudar a migrar a componentes principales.

### Visualización de componentes disponibles {#viewing-available-components}

Para obtener una descripción general de todos los componentes disponibles en la instancia de AEM, utilice la consola [](/help/sites-authoring/default-components-console.md)Componentes.

También puede utilizar CRXDE Lite para obtener una lista de todos los componentes disponibles en el repositorio.

1. En **[!UICONTROL CRXDE Lite]**, seleccione **[!UICONTROL Herramientas]** en la barra de herramientas y, a continuación, **[!UICONTROL Consulta]**, que abre la ficha **[!UICONTROL Consulta]** .

1. En la ficha **[!UICONTROL Consulta]** , seleccione `XPath` como **[!UICONTROL Tipo]**.

1. En el campo de entrada **[!UICONTROL Consulta]**, escriba la cadena siguiente:

   `//element(*, cq:Component)`

1. Haga clic en **[!UICONTROL Ejecutar]** y se enumerarán los componentes.

## Recursos adicionales {#further-reading}

Las páginas siguientes proporcionan información más detallada sobre el desarrollo de estos (y otros) componentes:

* [Componentes AEM: conceptos básicos](/help/sites-developing/components-basics.md)
* [Desarrollo de componentes AEM](/help/sites-developing/developing-components.md)
* [Desarrollo de componentes de AEM: ejemplos de código](/help/sites-developing/developing-components-samples.md)
* [Configuración de varios editores in situ](/help/sites-developing/multiple-inplace-editors.md)
* [Modo de desarrollador](/help/sites-developing/developer-mode.md)
* [Prueba de la IU](/help/sites-developing/hobbes.md)
* [Componentes para fragmentos de contenido](/help/sites-developing/components-content-fragments.md)
* [Obtención de información de la página en formato JSON](/help/sites-developing/pageinfo.md)
* [Internacionalización de componentes](/help/sites-developing/i18n.md)
* [Componentes principales](https://docs.adobe.com/content/help/es-ES/experience-manager-core-components/using/introduction.html)
* [Uso de Ocultar condiciones](/help/sites-developing/hide-conditions.md)
* IU clásica

   * [Componentes AEM (IU clásica)](/help/sites-developing/developing-components-classic.md)
   * [Uso y ampliación de utilidades (IU clásica)](/help/sites-developing/widgets.md)
   * [Uso de xtypes (IU clásica)](/help/sites-developing/xtypes.md)
   * [Desarrollo de Forms (IU clásica)](/help/sites-developing/developing-forms.md)

