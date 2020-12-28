---
title: Reestructuración del repositorio en AEM 6.4
seo-title: Reestructuración del repositorio en AEM 6.4
description: Obtenga información sobre los conceptos básicos y el razonamiento de la reestructuración del repositorio en AEM 6.4
seo-description: Obtenga información sobre los conceptos básicos y el razonamiento de la reestructuración del repositorio en AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
translation-type: tm+mt
source-git-commit: 7b39a715166eeefdf20eb22a4449068ff1ed0e42
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Reestructuración del repositorio en AEM 6.4{#repository-restructuring-in-aem}

## Introducción {#introduction}

Antes de AEM 6.4, el código de cliente se implementaba en áreas impredecibles del JCR que estaban sujetas a cambios en las actualizaciones. Debido a esto, era común que las versiones de AEM formales sobrescribieran el código personalizado, la configuración o el contenido. Además, los cambios de cliente a veces sobrescriben el contenido o el código AEM producto, lo que rompe la funcionalidad del producto.

Al delimitar claramente las jerarquías para AEM código de producto y código de cliente, estos conflictos se pueden evitar.

Con este fin, a partir del AEM 6.4 y que se continuará en futuras versiones, el contenido se está reestructurando de /etc a otras carpetas del repositorio, junto con directrices sobre qué contenido se va a utilizar, respetando las siguientes normas de alto nivel:

* AEM código de producto siempre se colocará en /libs, que no debe sobrescribirse con código personalizado
* El código personalizado debe colocarse en /apps, /content y /conf

## Impacto en las actualizaciones de 6.4 {#impact-on-upgrades}

Al actualizar a AEM 6.4, un gran subconjunto del contenido en /etc se duplicará en otras carpetas del repositorio. Estas nuevas ubicaciones son las ubicaciones preferidas en las que se hace referencia al contenido. Sin embargo, se ha hecho todo lo posible para que la actualización AEM 6.4 sea retrocompatible con las ubicaciones anteriores de la carpeta /etc y, por lo tanto, en la mayoría de los casos, el código AEM seguirá haciendo referencia a las ubicaciones antiguas hasta que los cambios se realicen activamente, y en muchos casos manualmente, en la aplicación del cliente. Desde una perspectiva de línea de tiempo, hay dos categorías de cambios:

* Con la actualización 6.4: algunos de los cambios de reestructuración /etc no son compatibles con versiones anteriores y, por lo tanto, las modificaciones deben planificarse e implementarse como parte de la actualización AEM 6.4.
* Antes de la actualización a la versión 6.5: la gran mayoría de los cambios de reestructuración /etc se pueden posponer hasta algún momento en el futuro posterior a la actualización. Como se mencionó anteriormente, AEM código 6.4 seguirá haciendo referencia a las ubicaciones antiguas hasta que las modificaciones se implementen como parte de una versión del cliente. Aunque no hay un cronograma obligatorio para el cual se deben realizar los cambios, se recomienda que se realicen antes de la actualización a la versión 6.5, ya que las funciones futuras pueden basarse en las nuevas ubicaciones a las que se hace referencia. Además, la documentación de una función determinada hará referencia, por convención, a las nuevas ubicaciones y, por tanto, podría resultar confusa si se siguen utilizando las ubicaciones antiguas.

### Directrices de reestructuración {#restructuring-guidance}

Al planificar una actualización a AEM 6.4, se debe hacer referencia a las siguientes páginas por solución para evaluar el esfuerzo de trabajo:

* [Reestructuración del repositorio común a todas las soluciones AEM](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de AEM Assets](/help/sites-deploying/assets-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de comercio AEM](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Cada página contiene dos secciones que corresponden a la urgencia de los cambios necesarios. Cualquier cosa en la sección &quot;Con actualización 6.4&quot; debe abordarse como parte del proyecto de actualización AEM 6.4. Todo lo que se encuentre debajo de la actualización &quot;anterior a la actualización 6.5&quot; se puede posponer de forma opcional hasta la actualización posterior.

Cada entrada de la página incluye un campo &quot;Guía de reestructuración&quot;, que detalla la estrategia técnica recomendada para alinearse con el nuevo modelo de repositorio 6.4, de modo que se haga referencia a las nuevas ubicaciones para el contenido que se encontraba anteriormente en la carpeta /etc. Un campo adicional &quot;Notas&quot; proporciona cualquier contexto útil adicional.
