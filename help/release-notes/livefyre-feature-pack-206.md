---
title: Notas de la versión de Livefyre Feature Pack 2.0.6
seo-title: Notas de la versión de Livefyre Feature Pack 2.0.6
description: Notas de la versión de Livefyre Feature Pack 2.0.6
seo-description: Notas de la versión de Livefyre Feature Pack 2.0.6
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: f1bf1545689b977a0f5074954df224db58cbd695
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---


# Notas de la versión de Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Información de la versión {#release-information}

<table> 
 <tbody>
  <tr>
   <td>Productos</td> 
   <td>Livefyre Feature Pack 2.0.6</td> 
  </tr>
  <tr>
   <td>Versión</td> 
   <td>2.0.6</td> 
  </tr>
  <tr>
   <td>Tipo</td> 
   <td>Versión de funciones</td> 
  </tr>
  <tr>
   <td>Fecha</td> 
   <td>31 de agosto de 2018</td> 
  </tr>
  <tr>
   <td>Descargar URL<br /> </td> 
   <td>Póngase en contacto con el administrador</td> 
  </tr>
  <tr>
   <td>Compatibilidad (*)</td> 
   <td>AEM 6.4 SP1, 6.4, 6.3 GA y 6.2 SP1</td> 
  </tr>
  <tr>
   <td>Descripción</td> 
   <td>Este paquete le permite integrar las capacidades de depuración líderes del sector de Livefyre con su instancia de AEM, lo que le permite publicar en su sitio en cuestión de minutos contenido valioso generado por el usuario (UGC) desde las redes sociales.</td> 
  </tr>
 </tbody>
</table>

## Qué incluye Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Este paquete integra las capacidades de depuración líderes del sector de Livefyre con su instancia de AEM, permitiéndole publicar en su sitio en cuestión de minutos contenido valioso generado por el usuario (UGC) desde las redes sociales. Este paquete incluye tres componentes diferentes:

**Importar contenido de UGC en AEM Assets**

* Importe contenido generado por usuarios de Twitter e Instagram (UGC) de Livefyre Studio a AEM Assets mediante el importador de UGC.
* Acceda a la biblioteca de Livefyre.
* Busque en tiempo real en Twitter e Instagram mediante la búsqueda social de Livefyre.
* Administrar derechos en el UGC.

**Añadir componentes de Livefyre a AEM Sites o comunidades**

* Cree y personalice al instante experiencias dinámicas y atractivas mediante un conjunto de componentes sociales que incluye mapas, galerías y paredes de medios.
* Publicar UGC en AEM Sites o comunidades.

**Importación de catálogos de productos en Livefyre con AEM Commerce**

* Integre sin problemas su catálogo de productos existente en Livefyre para impulsar la participación y conversión del usuario en sus sitios, así como para ofrecer experiencias UGC de ventas.
* Edite o elimine elementos del catálogo de productos de AEM Commerce y actualice automáticamente los cambios en Livefyre.

Para obtener ayuda con la instalación, consulte [Integración con Livefyre](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html).

### Información adicional de la versión {#additional-release-information}

Debido a las actualizaciones que afectan a la agregación de contenido de las cuentas de usuario de Instagram que no son de negocios, ya no podemos publicar comentarios en su nombre ni buscar automáticamente respuestas del autor. [Haga clic aquí para obtener más](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/)información.

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 no admite la interfaz de usuario de AEM Classic.

#### Nueva función o mejora {#new-feature-or-improvement}

* Se Añadió la capacidad de buscar UGC antes de configurar los derechos y solicitar cuentas sociales en Livefyre. Debe configurar cuentas sociales para solicitar derechos o anular la solicitud de derechos si es propietario del contenido.
* El flujo de trabajo [de solicitud de derechos](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html) UGC de Instagram y Twitter se ha actualizado para cumplir con las últimas API.
* El estado de los derechos y las acciones correspondientes ahora se muestran en la pantalla de solicitud de derechos.

#### Corrección de errores {#bug-fixes}

* Se ha corregido un problema que provocaba un error al eliminar una cuenta social en Livefyre Studio para la solicitud de derechos al cargar la biblioteca UGC en AEM.
* Se corrigió un problema en el cual el recuento de recursos en el estudio Livefyre no coincidía con el recuento de recursos en la biblioteca UGC de AEM.
* Se corrigió un problema en la biblioteca UGC donde los resultados filtrados se mostraban después de restablecer las opciones de filtro.
* Se ha corregido un problema con AEM Commerce por el que los botones de llamada a acción redirigían a los usuarios a una dirección URL incorrecta.
* Se corrigió un problema en los AEM Sites en el cual al arrastrar y soltar varios componentes en el marcador de posición parsys, desaparecía.
* Se corrigió un problema en el cual las cuentas sociales desactivadas estaban disponibles para seleccionar al enviar una solicitud de derechos.
* Se ha corregido un problema que provocaba un error al arrastrar y soltar UGC de Recursos a Sitios.
* Se corrigió un problema en el cual al arrastrar y soltar los componentes de chat y Liveblog en Sitios no se creaba la aplicación.
* Se corrigió un problema en el cual la aplicación de comentarios generaba un error cuando los usuarios intentaban comentar.
* Se corrigió un problema en el cual al agregar la aplicación Livefyre Media Wall a un sitio se creaba un nodo adicional en el repositorio de contenido Java.
* Se ha corregido un problema que provocaba saltos de página y errores de consola en la búsqueda UGC de Instagram.
* Se corrigió un problema en el cual los iconos de usuario de Instagram generaban errores de API en Recursos.
* Se ha corregido un problema que hacía que la aplicación de críticas se agregara a un sitio sin formato predefinido.
* Se ha corregido un problema con la funcionalidad de IU táctil y la edición en línea.
* Se ha corregido un problema que provocaba un error al importar determinados recursos de imagen de Instagram.
* Se corrigió un problema en el cual el cliente HTTP de Livefyre en AEM no admitía la configuración proxy.

