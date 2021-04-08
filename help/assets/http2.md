---
title: Entrega HTTP2 de contenido
seo-title: Entrega HTTP2 de contenido
description: HTTP/2 mejora la forma en que se comunican los exploradores y los servidores, lo que permite una transferencia de información más rápida y, al mismo tiempo, reduce la cantidad de potencia de procesamiento necesaria.
seo-description: HTTP/2 mejora la forma en que se comunican los exploradores y los servidores, lo que permite una transferencia de información más rápida y, al mismo tiempo, reduce la cantidad de potencia de procesamiento necesaria.
uuid: d9deb945-bdf5-4d6b-95c8-8bae4442e618
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: c8e145ad-f021-4043-8190-62151775e296
exl-id: 59cd9f8c-6d01-448d-bf57-bdc9fd2e381b
feature: Administración de activos
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 2%

---

# Entrega HTTP2 de contenido {#http-delivery-of-content}

Adobe anuncia la disponibilidad del envío de contenido HTTP/2 con el beneficio general de mejorar el rendimiento.

## ¿Qué es HTTP/2? {#what-is-http}

HTTP/2 mejora la forma en que se comunican los exploradores y los servidores, lo que permite una transferencia de información más rápida y, al mismo tiempo, reduce la cantidad de potencia de procesamiento necesaria.

El siguiente sitio web describe HTTP/2 y sus ventajas de una manera breve y simple:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## ¿Cuáles son las ventajas clave del paso a HTTP/2 para la entrega de contenido? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

La mejora del rendimiento varía ampliamente en función de factores como el código del sitio web, cómo está utilizando Dynamic Media, el dispositivo, la pantalla y la ubicación del consumidor, etc.

Las propias pruebas de Adobe dieron los siguientes resultados:

* En el caso de las imágenes, el tiempo de respuesta mejoró del 7 % al 28 % en función del dispositivo y el navegador. Las mejoras de rendimiento más notables se produjeron en dispositivos iOS.
* Para los visores, el rendimiento del tiempo de carga ha mejorado un 15%.

La siguiente demostración ilustra la diferencia entre la carga HTTP/1 y HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## ¿Puedo cambiar a HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Para utilizar HTTP/2, debe cumplir los siguientes requisitos:

* Utilice HTTPS seguro para sus solicitudes de medios enriquecidos.
* Utilice la CDN (red de entrega de contenido) incluida en la Adobe como parte de su licencia de Dynamic Media.
* Utilice un dominio dedicado (que no sea company-h.assetsadobe#.com).

   Si ya tiene un dominio dedicado, puede optar por utilizar la asistencia técnica.

   Si no tiene un dominio dedicado, Adobe programará la transición a HTTP/2 en 2018.

## ¿Cuál es el proceso para habilitar HTTP/2 para mi cuenta de Dynamic Media? {#what-is-the-process-for-enabling-http-for-my-dynamic-media-account}

Debe iniciar la solicitud para cambiar a HTTP/2; no se realiza automáticamente.

1. Inicie una solicitud de asistencia técnica para cambiar a HTTP2. Consulte [Acceso al Portal de Soporte AEM](https://helpx.adobe.com/experience-manager/kb/accessing-aem-support-portal.html).

   1. Proporcione la siguiente información en su solicitud de asistencia:

      1. Nombre de contacto principal, correo electrónico, teléfono.
      1. Todos los dominios que se van a transferir a HTTP2.
      1. Compruebe que está utilizando HTTPS seguro para solicitudes de medios enriquecidos.
      1. Compruebe que está utilizando la CDN a través de la Adobe y que no se administran con una relación directa.
      1. Compruebe que está utilizando un dominio dedicado. Si usa Dynamic Media, entonces ya estará usando un dominio dedicado.
   1. La asistencia técnica le agregará a la lista de espera de clientes HTTP/2 en función del orden en que se enviaron las solicitudes.
   1. Cuando el Adobe esté listo para gestionar su solicitud, el servicio de asistencia técnica se pondrá en contacto con usted para coordinar la transición y establecer una fecha objetivo.
   1. Se le notificará una vez finalizada y podrá verificar la transición correcta a HTTP2.

      Dado que el explorador no indica este hecho, es necesario descargar una extensión.

      Para Firefox y Chrome hay una extensión llamada &quot;HTTP/2 e indicador SPDY&quot;. Los navegadores solo admiten http/2 de forma segura, por lo que es necesario llamar a una URL con https para verificarla. Si se admite http/2, esto lo indica la extensión en forma de símbolo de Flash azul y un encabezado &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.


## ¿Cuándo puedo esperar que se pase a HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

Las solicitudes se procesarán en el orden en que sean recibidas por el servicio de asistencia técnica.

>[!NOTE]
>
>Puede haber un largo tiempo de espera porque la transición a HTTP/2 implica borrar la caché. Por lo tanto, solo se pueden gestionar algunas transiciones de cliente a la vez.

## ¿Cuáles son los riesgos de pasar a HTTP/2? {#what-are-the-risks-with-moving-to-http}

La transición a HTTP/2 borra la caché en la CDN porque implica pasar a una nueva configuración de CDN.

El contenido no almacenado en caché llega directamente a los servidores de origen del Adobe hasta que se vuelve a crear la caché. Debido a esto, Adobe planea manejar algunas transiciones de clientes a la vez para mantener un rendimiento aceptable al extraer solicitudes de nuestro origen.

## ¿Cómo se puede verificar si una URL o un sitio web está activado con HTTP/2? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Dado que el explorador no indica este hecho, es necesario descargar una extensión.

Para Firefox y Chrome hay una extensión llamada &quot;HTTP/2 e indicador SPDY&quot;. Los navegadores solo admiten http/2 de forma segura, por lo que es necesario llamar a una URL con https para verificarla. Si se admite http/2, esto lo indica la extensión en forma de símbolo de Flash azul y un encabezado &quot;X-Firefox-Spdy&quot; : &quot;h2&quot;.
