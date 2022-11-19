---
title: Notas de la versión de Livefyre Feature Pack 2.0.6
seo-title: Livefyre Feature Pack 2.0.6 Release Notes
description: Notas de la versión de Livefyre Feature Pack 2.0.6
seo-description: Livefyre Feature Pack 2.0.6 Release Notes
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Notas de la versión de Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Información de la versión {#release-information}

| Productos | Paquete de funciones Livefyre 2.0.6 |
|--- |--- |
| Versión | 2.0.6 |
| Tipo | Versión de funciones |
| Fecha | 31 de agosto de 2018 |
| Descargar URL | Póngase en contacto con el administrador |
| Compatibilidad (*) | AEM 6.4 SP1, 6.4, 6.3 GA y 6.2 SP1 |
| Descripción | Este paquete le permite integrar las funcionalidades de depuración líderes en el sector de Livefyre con su instancia de AEM, lo que le permite publicar en su sitio contenido valioso generado por el usuario (UGC) desde las redes sociales en cuestión de minutos. |

## Qué incluye Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Este paquete integra las funcionalidades de depuración líderes en el sector de Livefyre con su instancia de AEM, lo que le permite publicar en su sitio contenido valioso generado por el usuario (UGC) desde las redes sociales en cuestión de minutos. Hay tres componentes diferentes para este paquete:

**Importar contenido de UGC en AEM Assets**

* Importe contenido generado por el usuario (UGC) de Twitter y Instagram de Livefyre Studio a AEM Assets mediante el importador UGC.
* Acceda a su biblioteca de Livefyre.
* Busque en tiempo real en Twitter y Instagram mediante la búsqueda social de Livefyre.
* Administrar derechos en UGC.

**Añadir componentes de Livefyre a AEM Sites o comunidades**

* Cree y personalice de forma instantánea experiencias dinámicas y atractivas mediante un conjunto de componentes sociales que incluye mapas, galerías y paredes de medios.
* Publicar UGC en AEM Sites o Communities.

**Importar catálogos de productos en Livefyre con AEM Commerce**

* Integre sin problemas su catálogo de productos existente en Livefyre para impulsar la participación y conversión del usuario en sus sitios, así como para ofrecer experiencias UGC de ventas.
* Edite o elimine artículos del catálogo de productos AEM Commerce y actualice automáticamente los cambios en Livefyre.

Para obtener ayuda con la instalación, consulte [Integración con Livefyre](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html).

### Información adicional de la versión {#additional-release-information}

Debido a las actualizaciones que afectan a la agregación de contenido de cuentas de usuario de Instagram que no son de negocios, ya no podemos publicar comentarios en su nombre o comprobar automáticamente si hay respuestas del autor. [Haga clic aquí para obtener más información](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 no es compatible con AEM IU clásica.

#### Nueva función o mejora {#new-feature-or-improvement}

* Se ha agregado la capacidad de buscar UGC antes de configurar las cuentas sociales de solicitud de derechos en Livefyre. Debe configurar las cuentas sociales para solicitar derechos o anular la solicitud de derechos si es el propietario del contenido.
* Instagram y Twitter [Flujo de trabajo de solicitud de derechos UGC](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html) se ha actualizado para cumplir con las API más recientes.
* El estado de los derechos y las acciones correspondientes ahora se muestran en la pantalla de solicitud de derechos.

#### Corrección de errores {#bug-fixes}

* Se ha corregido un problema en el cual la eliminación de una cuenta social en Livefyre Studio utilizada para la solicitud de derechos provocaba un error al cargar la biblioteca UGC en AEM.
* Se ha corregido un problema en el cual el recuento de activos en Livefyre Studio no coincidía con el recuento de activos en la biblioteca UGC de AEM.
* Se ha corregido un problema en la biblioteca UGC por el cual se mostraban los resultados filtrados después de restablecer las opciones de filtro.
* Se ha corregido un problema con AEM comercio en el cual los botones de llamada a acción redirigían a los usuarios a una dirección URL incorrecta.
* Se ha corregido un problema en AEM Sites por el que, al arrastrar y soltar varios componentes en el marcador de posición parsys, desaparecía.
* Se ha corregido un problema por el cual las cuentas sociales desactivadas estaban disponibles para seleccionar al enviar una solicitud de derechos.
* Se ha corregido un problema que provocaba un error al arrastrar y soltar UGC desde Assets a Sitios .
* Se ha corregido un problema por el cual al arrastrar y soltar los componentes de Chat y Liveblog en Sitios no se creaba la aplicación.
* Se ha corregido un problema en el cual la aplicación de comentarios generaba un error cuando los usuarios intentaban realizar comentarios.
* Se ha corregido un problema por el cual, al agregar la aplicación de muro de medios de Livefyre a un sitio, se creaba un nodo adicional en el repositorio de contenido Java.
* Se ha corregido un problema que provocaba saltos de página y errores de consola en la búsqueda UGC de Instagram.
* Se ha corregido un problema en el cual los iconos de usuario de Instagram generaban errores de API en Assets.
* Se ha corregido un problema por el cual la aplicación de revisiones se agregaba a un sitio sin formato predefinido.
* Se ha corregido un problema con la funcionalidad de la interfaz de usuario táctil y la edición en línea.
* Se ha corregido un problema que provocaba un error al importar ciertos recursos de imagen de Instagram.
* Se ha corregido un problema en el cual el cliente HTTP de Livefyre en AEM no admitía la configuración proxy.
