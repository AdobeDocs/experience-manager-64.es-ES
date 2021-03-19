---
title: eCommerce
seo-title: comercio electrónico
description: 'AEM comercio electrónico ayuda a los especialistas en marketing a ofrecer experiencias de compra personalizadas y con marca en puntos de contacto web, móviles y sociales. '
seo-description: 'AEM comercio electrónico ayuda a los especialistas en marketing a ofrecer experiencias de compra personalizadas y con marca en puntos de contacto web, móviles y sociales. '
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: Marco de integración de Commerce
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 3%

---


# eCommerce{#ecommerce}

* [Conceptos ](/help/sites-administering/concepts.md)
* [Administración (genérica)](/help/sites-administering/generic.md)
* [Commerce Cloud SAP](/help/sites-administering/sap-commerce-cloud.md)
* [Commerce Cloud de Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

Adobe proporciona dos versiones de Commerce Integration Framework:

|  | CIF local | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versiones de AEM compatibles | AEM local o AMS 6.x | AEM AMS 6.4 y 6.5 |
| Back-end | - AEM, Java <br> - Integración monolítica, asignación previa a la compilación (plantilla)<br> - Repositorio JCR | - Magento <br>- Java y Javascript <br>: sin datos de comercio almacenados en el repositorio JCR |
| Front-end | AEM páginas procesadas del lado del servidor | Aplicación de página mixta (renderización híbrida) |
| Catálogo de productos | - Importador de productos, editor, almacenamiento en caché en AEM <br>: catálogos regulares con páginas AEM o proxy | - Sin importación de productos <br>- Plantillas genéricas <br>: datos bajo demanda a través del conector |
| Escalabilidad | - Puede admitir hasta unos pocos millones de productos (depende del caso de uso) <br> - Almacenamiento en caché en Dispatcher | - Sin limitación de volumen <br>- Almacenamiento en caché en Dispatcher o CDN |
| Modelo de datos estandarizado | No | Sí, esquema de Magento GraphQL |
| Disponibilidad | Sí:<br> - Commerce Cloud SAP (la extensión se ha actualizado para admitir AEM 6.4 e Hybris 5 (valor predeterminado) y mantiene la compatibilidad con Hybris 4 <br> - Commerce Cloud Salesforce (conector de código abierto para admitir AEM 6.4) | Sí, a través de código abierto a través de GitHub. <br> Magento Commerce (admite Magento 2.3.2 (predeterminado) y compatible con Magento 2.3.1). |
| Cuándo se utiliza | Casos de uso limitados: Para situaciones en las que sea necesario importar catálogos estáticos pequeños | Solución preferida en la mayoría de los casos de uso |

El comercio electrónico, junto con la gestión de información de productos (PIM), gestiona las actividades de un sitio web centrado en la venta de productos a través de una tienda en línea:

* Creación, duración y obsolescencia de un producto
* Gestión de precios
* Administración de transacciones
* Administración de catálogos completos
* Registros de almacenamiento activo y centralizado
* Interfaces web

AEM comercio electrónico ayuda a los especialistas en marketing a ofrecer experiencias de compra personalizadas y con marca en puntos de contacto web, móviles y sociales. El entorno de creación de AEM le permite personalizar páginas y componentes en función del contexto del visitante objetivo y las estrategias de comercialización; por ejemplo:

* Páginas de producto
* Componentes del carro de compras
* Componentes de cierre de compra

La implementación permite el acceso en tiempo real a la información del producto. Esto se puede utilizar para hacer cumplir:

* Integridad de la información del producto
* Precio
* Inventario de existencias
* Variaciones en el estado de un carro de compras

>[!NOTE]
>
>Para utilizar el marco de integración con proveedores de comercio electrónico externos, primero debe instalar los paquetes necesarios. Para obtener más información, consulte [Implementación de eCommerce](/help/sites-deploying/ecommerce.md).
>
>Para obtener información sobre la ampliación de las capacidades de comercio electrónico, consulte [Desarrollo del comercio electrónico](/help/sites-developing/ecommerce.md).

## Funciones principales {#main-features}

AEM comercio electrónico proporciona:

* Varios **componentes de AEM listos para usar** para ilustrar lo que se puede lograr para el proyecto:

   * Visualización del producto
   * Carro de compras
   * Extracción
   * Productos vistos recientemente
   * Cupones
   * y otros

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >El marco de integración proporcionado por AEM también le permite crear componentes de AEM adicionales para las funciones de comercio independientes del motor de comercio electrónico específico.

* **Buscar** : mediante:

   * la búsqueda AEM
   * la búsqueda del sistema de comercio electrónico
   * una búsqueda de terceros (como Search&amp;Promote)
   * o una combinación de ellos.

   ![chlimage_1-151](assets/chlimage_1-151.png)

* Utiliza la capacidad AEM para **presentar el contenido en varios canales**, ya sea en la ventana completa del explorador o en el dispositivo móvil. Esto ofrece el contenido en el formato que necesitan los visitantes.

   ![chlimage_1-152](assets/chlimage_1-152.png)

* La capacidad de **desarrollar su propia implementación de integración basada en el [AEM marco de comercio electrónico](#the-framework)**.

   Las dos implementaciones disponibles actualmente se crean sobre la misma base, además de la API general (el marco de trabajo). La implementación de una nueva integración solo implica implementar las funciones que necesita la integración. Las nuevas implementaciones pueden utilizar los componentes front-end, ya que utilizan interfaces (por lo que son independientes de la implementación).

* La posibilidad de desarrollar **comercio basado en la experiencia basado en los datos y la actividad del comprador**. Esto le permite dar cuenta de muchos escenarios:

   * Un ejemplo podría ser proporcionar reducciones en los costos de envío cuando el pedido total exceda una cantidad específica.
   * Otro puede permitirle proporcionar ofertas de temporada que utilicen datos de perfil (por ejemplo, ubicación). A continuación, se pueden resaltar, dependiendo de nuevo de otros factores cuando sea necesario.

   En el ejemplo siguiente, se muestra un teaser, ya que el contenido del carro de compras es inferior a 75 $:

   ![chlimage_1-153](assets/chlimage_1-153.png)

   Esto se puede cambiar cuando el contenido del carro de compras supera los 75 $:

   ![chlimage_1-154](assets/chlimage_1-154.png)

* Y otras características, entre ellas:

   * Contenido del carro de compras retenido entre sesiones
   * Historial de pedidos completo
   * Actualización del catálogo exprés

## El marco {#the-framework}

La sección [Conceptos](/help/sites-administering/concepts.md) cubre el marco de trabajo con más detalle, pero lo siguiente proporciona una vista de alto nivel y alta velocidad del marco de trabajo:

### ¿Qué? {#what}

* El marco de integración proporciona la API, una serie de componentes para ilustrar la funcionalidad y varias extensiones para proporcionar ejemplos de métodos de conexión.
* El marco proporciona la estructura básica necesaria para la ejecución de un proyecto.
* El marco es extensible.
* El marco de trabajo no proporciona un sitio listo para usar. Siempre se necesita una cierta cantidad de trabajo de desarrollo para adaptar el marco a sus especificaciones.

### ¿Por qué? {#why}

* Proporcionar los mecanismos básicos necesarios para realizar rápidamente un sitio de comercio electrónico personalizado.
* Tp proporciona la flexibilidad necesaria para desarrollar un sitio de comercio electrónico en la vida real.
* Ilustración de las prácticas recomendadas.

