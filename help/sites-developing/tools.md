---
title: Herramientas de prueba y seguimiento
seo-title: Testing and Tracking Tools
description: AEM proporciona un marco para probar la interfaz de usuario de los componentes y un mecanismo para probar y depurar componentes
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 29c43202-0a4e-41ba-9176-92fa77c627d5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 0f977264-fe58-4478-bd38-aca5c75f36aa
exl-id: 9387cdb4-f8de-4229-90d1-59218ac17561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 3%

---

# Herramientas de prueba y seguimiento{#testing-and-tracking-tools}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Pruebas {#testing}

AEM proporciona lo siguiente:

* [un marco para probar la interfaz de usuario de los componentes](/help/sites-developing/hobbes.md).
* [un mecanismo para probar y depurar componentes](/help/sites-developing/developer-mode.md).

Las siguientes son dos herramientas de prueba de código abierto:

**Selenio**

Selenium se utiliza para pruebas de funciones en un explorador con un usuario por actividad. Registra los pasos de prueba (clics) como tablas de HTML o clases Java.

Para obtener más información, consulte [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter se utiliza para rastrear solicitudes y puede utilizarse para pruebas funcionales, de rendimiento y de estrés.

Para obtener más información, consulte [http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/).

También existen muchas herramientas propietarias para automatizar pruebas y administrar planes de prueba.

## Seguimiento {#tracking}

Las siguientes herramientas están fácilmente disponibles. Sin embargo, un problema clave en todos los casos es la disponibilidad de los datos para todos los miembros del equipo del proyecto: socio y cliente.

**Bugzilla**

Un sistema de seguimiento de errores que puede configurarse según sus propios requisitos.

**Hojas de cálculo**

Aunque no se trata específicamente de una herramienta de seguimiento de errores, las hojas de cálculo suelen utilizarse incorrectamente con este fin, ya que son fáciles de comprender y la mayoría de los usuarios tienen experiencia en su funcionalidad.

Si se utilizan para el seguimiento, entonces:

* deben mantenerse simples.
* el número de hojas de cálculo individuales debe reducirse al mínimo.
* deben actualizarse periódicamente.
* solo se debe mantener una copia maestra y todos deben saber dónde está la copia maestra.
* deben ser accesibles para todos los miembros del proyecto.
* si la seguridad es un problema (a menudo ocurre en grandes empresas) y el acceso común no es posible, las copias se pueden distribuir siempre que todos entiendan que se trata de copias y no se puedan actualizar.

De nuevo, existen muchas herramientas propietarias para rastrear errores y requisitos de funciones.
