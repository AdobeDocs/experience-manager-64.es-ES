---
title: Enrutamiento de modelo SPA
seo-title: SPA Model Routing
description: Para las aplicaciones de una sola página en AEM, la aplicación es responsable del enrutamiento. Este documento describe el mecanismo de enrutamiento, el contrato y las opciones disponibles.
seo-description: For single page applications in AEM, the app is responsible for the routing. This document describes the routing mechanism, the contract, and options available.
uuid: 93b4f85a-a240-42d4-95e2-e8b790df7723
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: d9f1e24e-51a9-4f28-b2cd-2e97aed63a24
exl-id: 865f524d-6b54-43c8-9b28-86a766e010a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---

# Enrutamiento de modelo SPA{#spa-model-routing}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para las aplicaciones de una sola página en AEM, la aplicación es responsable del enrutamiento. Este documento describe el mecanismo de enrutamiento, el contrato y las opciones disponibles.

>[!NOTE]
>
>La función Editor de aplicaciones de una sola página (SPA) requiere AEM 6.4 service pack 2 o posterior.
>
>El Editor de SPA es la solución recomendada para proyectos que requieren SPA procesamiento del lado del cliente basado en el marco de trabajo (por ejemplo, React o Angular).

## Enrutamiento de proyectos {#project-routing}

La aplicación es propietaria del enrutamiento y luego los desarrolladores del front-end del proyecto la implementan. Este documento describe el enrutamiento específico del modelo devuelto por el servidor AEM. La estructura de datos del modelo de página expone la dirección URL del recurso subyacente. El proyecto front-end puede utilizar cualquier biblioteca personalizada o de terceros que proporcione funcionalidades de enrutamiento. Una vez que una ruta espera un fragmento de modelo, una llamada a la función `PageModelManager.getData()` se puede realizar. Cuando la ruta de un modelo ha cambiado, se debe activar un evento para advertir a bibliotecas de escucha como el Editor de páginas.

## Arquitectura {#architecture}

Para obtener una descripción detallada, consulte la [PageModelManager](/help/sites-developing/spa-blueprint.md#pagemodelmanager) del documento Modelo de SPA.

## ModelRouter {#modelrouter}

La variable `ModelRouter` - cuando está habilitado - encapsula las funciones de la API History de HTML5 `pushState` y `replaceState` para garantizar que un fragmento determinado del modelo es accesible y se obtiene previamente. A continuación, notifica al componente frontal registrado que el modelo se ha modificado.

## Enrutamiento manual frente al modelo automático {#manual-vs-automatic-model-routing}

La variable `ModelRouter` automatiza la recuperación de fragmentos del modelo. Pero como cualquier herramienta automatizada viene con limitaciones. Cuando sea necesario, la variable `ModelRouter` puede deshabilitarse o configurarse para ignorar las rutas mediante meta propiedades (consulte la sección Meta propiedades de la sección [Componente de página SPA](/help/sites-developing/spa-page-component.md) documento). Los desarrolladores de front-end pueden implementar su propia capa de enrutamiento de modelo solicitando la `PageModelManager` para cargar cualquier fragmento de modelo determinado mediante la variable `getData()` función.

>[!NOTE]
>
>Actualmente, el proyecto React de muestra de We.Retail Journal ilustra el enfoque automatizado, mientras que el proyecto de Angular ilustra el manual. Un enfoque semiautomatizado también sería un caso de uso válido.

>[!CAUTION]
>
>La versión actual de `ModelRouter` solo admiten el uso de direcciones URL que apunten a la ruta de recurso real de los puntos de entrada del modelo Sling. No admite el uso de URL o alias de Vanity.

## Contrato de enrutamiento {#routing-contract}

La implementación actual se basa en el supuesto de que el proyecto SPA utiliza la API de historial de HTML5 para enrutar a las diferentes páginas de aplicación.

### Configuración {#configuration}

La variable `ModelRouter` admite el concepto de enrutamiento de modelo a medida que escucha `pushState` y `replaceState` llamadas a para recuperar previamente fragmentos de modelo. Internamente déclencheur el `PageModelManager` para cargar el modelo que corresponde a una URL determinada y activa un `cq-pagemodel-route-changed` que otros módulos pueden escuchar.

De forma predeterminada, este comportamiento se activa automáticamente. Para deshabilitarlo, el SPA debe renderizar la siguiente meta propiedad:

```
<meta property="cq:pagemodel_router" content="disable"\>
```

Tenga en cuenta que cada ruta del SPA debe corresponder a un recurso accesible en AEM (por ejemplo, &quot; `/content/mysite/mypage"`) desde el `PageModelManager` intentará cargar automáticamente el modelo de página correspondiente una vez seleccionada la ruta. Aunque, si es necesario, el SPA también puede definir una &quot;lista de bloqueados&quot; de rutas que el `PageModelManager`:

```
<meta property="cq:pagemodel_route_filters" content="route/not/found,^(.*)(?:exclude/path)(.*)"/>
```
