---
title: Reestructuración de repositorios en AEM 6.4
seo-title: Repository Restructuring in AEM 6.4
description: Obtenga información sobre los conceptos básicos y el razonamiento detrás de la reestructuración de repositorios en AEM 6.4
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 2%

---

# Reestructuración de repositorios en AEM 6.4{#repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

Antes de AEM 6.4, el código de cliente se implementaba en áreas impredecibles del JCR que estaban sujetas a cambios en las actualizaciones. Debido a esto, era común que las versiones formales de AEM sobrescribieran el código, la configuración o el contenido personalizados. Además, a veces los cambios de los clientes se sobrescriben AEM código de producto o contenido, lo que rompe la funcionalidad del producto.

Si se delinean claramente las jerarquías para AEM código de producto y código de cliente, estos conflictos se pueden evitar.

Con este fin, a partir del AEM 6.4 y que continuará en futuras versiones, el contenido se está reestructurando fuera de /etc a otras carpetas del repositorio, junto con directrices sobre qué contenido va a dónde, siguiendo las siguientes reglas de alto nivel:

* AEM código de producto siempre se colocará en /libs, que no debe sobrescribirse con código personalizado
* El código personalizado debe colocarse en /apps, /content y /conf

## Impacto en las actualizaciones de la versión 6.4 {#impact-on-upgrades}

Al actualizar a AEM 6.4, un gran subconjunto del contenido bajo /etc se duplica en otras carpetas del repositorio. Estas nuevas ubicaciones son las ubicaciones preferidas en las que se hace referencia al contenido. Sin embargo, se ha hecho todo lo posible para que la actualización AEM 6.4 sea compatible con las ubicaciones anteriores en la carpeta /etc y, por lo tanto, en la mayoría de los casos, el código AEM seguirá haciendo referencia a las ubicaciones antiguas hasta que los cambios se realicen de forma activa (y, en muchos casos, manual) en la aplicación de un cliente. Desde la perspectiva de la cronología, existen dos categorías de cambios:

* Con la actualización a la versión 6.4: algunos de los cambios de reestructuración /etc no son compatibles con versiones anteriores, por lo que las modificaciones deben planificarse e implementarse como parte de la actualización a la versión AEM 6.4.
* Antes de la actualización a la versión 6.5: la gran mayoría de los cambios de reestructuración de /etc se pueden aplazar hasta algún momento en el futuro posterior a la actualización. Como se mencionó anteriormente, AEM código 6.4 seguirá haciendo referencia a las ubicaciones antiguas hasta que las modificaciones se implementen como parte de una versión para clientes. Aunque no hay un calendario forzado para los cambios que se deben realizar, se recomienda que se realicen antes de la actualización a la versión 6.5, ya que las funciones futuras pueden depender de las nuevas ubicaciones a las que se hace referencia. Además, la documentación de una función determinada hará referencia por convención a las nuevas ubicaciones y, por lo tanto, podría resultar confuso si las ubicaciones antiguas siguen utilizándose.

### Guía de reestructuración {#restructuring-guidance}

Al planificar una actualización a AEM 6.4, se debe hacer referencia a las siguientes páginas por solución para evaluar el esfuerzo de trabajo:

* [Reestructuración de repositorios común a todas las soluciones AEM](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [Reestructuración de repositorios de AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [Reestructuración de repositorios de AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=es)
* [Reestructuración de repositorios de AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [Reestructuración de repositorios de AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [Reestructuración de repositorios de AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [Reestructuración del repositorio de AEM Commerce](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Cada página contiene dos secciones que corresponden a la urgencia de los cambios necesarios. Cualquier cosa en la sección &quot;Con actualización a la versión 6.4&quot; debe abordarse como parte del proyecto de actualización a la versión AEM 6.4. Cualquier cosa en el apartado &quot;Antes de la actualización a la versión 6.5&quot; se puede aplazar opcionalmente hasta la actualización posterior.

Cada entrada de la página incluye un campo &quot;Guía de reestructuración&quot;, que detalla la estrategia técnica recomendada para alinearse con el nuevo modelo de repositorio 6.4, de modo que se haga referencia a las nuevas ubicaciones para el contenido anteriormente ubicado en la carpeta /etc. Un campo adicional &quot;Notas&quot; proporciona cualquier contexto útil adicional.
