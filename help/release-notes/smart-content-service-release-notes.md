---
title: Notas de la versión de Smart Content Service
seo-title: Notas de la versión de Smart Content Service
description: Información general sobre el servicio de contenido inteligente y problemas conocidos relacionados con el servicio.
seo-description: Información general sobre el servicio de contenido inteligente y problemas conocidos relacionados con el servicio.
uuid: 5f474b36-3451-48ea-8669-b2d793638b06
content-type: reference
products: SG_EXPERIENCEMANAGER
discoiquuid: 9f88c773-ddeb-4c66-ac07-7d3aa196c51b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 8%

---


# Notas de revisión de Smart Content Service {#smart-content-service-release-notes}

Información general sobre el servicio de contenido inteligente y problemas conocidos relacionados con el servicio.

Las organizaciones requieren que sus recursos digitales se etiqueten en función de la taxonomía que los empleados, socios y clientes utilizan para hacer referencia a los recursos digitales y realizar búsquedas en ellos. En comparación con las etiquetas genéricas, los recursos etiquetados en función de la taxonomía comercial se identifican y recuperan más fácilmente mediante búsquedas basadas en etiquetas.

El servicio de contenido inteligente utiliza la taxonomía empresarial de AEM Assets para etiquetar automáticamente los recursos digitales, lo que garantiza que los recursos más relevantes aparezcan en las búsquedas.

Debe capacitar al servicio de contenido inteligente en un conjunto depurado de etiquetas y recursos AEM para reconocer su taxonomía empresarial. Una vez formados, el servicio puede aplicar estas etiquetas en un conjunto de recursos similar.

El servicio de contenido inteligente es proporcionado por la plataforma de Adobe Sensei, que le permite capacitar al algoritmo de reconocimiento de imágenes en su taxonomía comercial. A continuación, esta inteligencia de contenido se utiliza para aplicar etiquetas relevantes a recursos similares.

## Mejoras clave {#key-improvements}

El servicio de contenido inteligente incluye las siguientes mejoras clave:

* Optimizaciones de algoritmos para mejorar aún más la precisión del modelo, recuperar valores
* Compatibilidad con la restauración de la formación de modelos para todas las etiquetas en el nivel de inquilino
* Compatibilidad con Áreas de nombres de etiquetas inteligentes mejoradas para evitar conflictos
* Nueva política de sustitución de modelos para evitar cualquier degradación debida al readiestramiento
* Monitoreo del inquilino para el uso del servicio
* Correcciones de problemas relacionados con la agrupación en clúster y la conexión, que mejoran la solidez del servicio

## Problemas solucionados {#fixed-issues}

En esta versión se han solucionado los problemas siguientes:

* Los procesos de trabajo para flujos de trabajo de etiquetado y formación finalizan si no se pueden conectar al servidor MySQL. CQ-4242886

* La puntuación sesgada de precisión no se calcula correctamente. CQ-4241797

* Cálculo de PR incorrecto para el modelo. CQ-4241381

* El flujo de trabajo de formación omite los recursos de ejemplo al procesarlos desde la cola CQ-4240901

* Mejoras en la recuperación de precisión. CQ-4239895

* Política de sustitución de modelo. CQ-4239886

* Las imágenes de la camisa masculina están etiquetadas con la etiqueta de la chaqueta femenina. CQ-4239650

* Se omiten los ejemplos de formación durante la implementación del escenario. CQ-4239483

* La validación del trabajo de formación debe realizarse en un conjunto de recursos enviados para la formación. CQ-4238834

* La creación de modelos falla en el foraging negativo aunque haya un mínimo de positivos o negativos para una etiqueta. CQ-4240741

* Entradas engañosas para la búsqueda negativa en registros de instructores. CQ-4240738

* Problema con la formación por primera vez si las etiquetas enviadas para la formación son negativas aleatorias entre sí. CQ-4240118

* Improvise registros para supervisar el uso del servicio por inquilino. CQ-4239781

## Idiomas {#languages}

El servicio de contenido inteligente está disponible para las siguientes configuraciones regionales:

* Inglés
* Alemán
* Francés
* Español
* Italiano
* Portugués
* Japonés
* Chino simplificado
* Coreano

## Vínculos {#links}

* [Página del producto Adobe Experience Manager en adobe.com](https://www.adobe.com/marketing-cloud/experience-manager.html)
* [Documentación de etiquetas inteligentes mejorada](/help/assets/enhanced-smart-tags.md)

## Asistencia y acceso al producto (sitios restringidos) {#product-access-and-support-restricted-sites}

Estos sitios solo están disponibles para los clientes. Si es cliente y necesita acceso, póngase en contacto con el administrador de cuentas de Adobe.

* [Acceso a productos](https://login.marketing.adobe.com)
* [Descarga de productos en Licensing.adobe.com](https://licensing.adobe.com/).
* Actualizaciones, parches y paquetes de productos para obtener funcionalidad adicional en [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Asistencia al cliente mediante Admin Console](https://adminconsole.adobe.com/). Para obtener más información, consulte [Nueva experiencia de asistencia al cliente de Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
