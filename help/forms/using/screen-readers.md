---
title: Lectores de pantalla para formularios HTML5
seo-title: Screen readers for HTML5 forms
description: Enumera los lectores de pantalla compatibles con los formularios HTML5.
seo-description: Lists the screen readers supported with HTML5 forms.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: Mobile Forms
exl-id: c27eb771-d390-4534-8e67-f1277550e760
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# Lectores de pantalla para formularios HTML5 {#screen-readers-for-html-forms}

Los componentes de formularios HTML5 representan la plantilla de formulario XFA en formato HTML5. Todos los navegadores estándar compatibles con HTML5 pueden procesar estos formularios. Para ofrecer compatibilidad con una experiencia de captura de datos similar en los formularios PDF y HTML5, la presentación de los PDF forms se conserva en los formularios HTML5.

Los formularios HTML5 utilizan construcciones HTML estándar que permiten utilizar herramientas de accesibilidad normales para HTML con estos formularios. Si un formulario está diseñado según las prácticas recomendadas para formularios accesibles, funciona con cualquier lector de pantalla admitido. Además, estos formularios están habilitados para la navegación mediante el teclado.

## Normas de accesibilidad {#accessibility-standards}

Los formularios HTML5 cumplen con la sección 508 para accesibilidad con excepciones conocidas. Consulte [VPAT para formularios HTML5](http://wwwimages.adobe.com/content/dam/acom/en/accessibility/compliance/pdfs/livecycle-mobile-forms-es4-section-508-vpat.pdf) para obtener más información.

## Lectores de pantalla certificados para formularios HTML5 {#certified-screen-readers-for-html-forms}

* JAWS 14.0 en Microsoft Windows
* VoiceOver en Mac OS X y iPad

### JAWS {#jaws}

Todos los accesos directos y las pulsaciones de teclas predeterminados funcionan en los formularios HTML5. Para obtener más información sobre el uso de JAWS, visite [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/jaws-hq.asp).

### VoiceOver {#voiceover}

Los formularios HTML5 admiten todas las pulsaciones de teclas y gestos de voz predeterminados. Para obtener más información sobre la configuración y el uso de VoiceOver, consulte [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Problemas conocidos {#known-issues}

* **(Solo para el Explorador interno 9)** En los formularios HTML5, las páginas se cargan bajo demanda (de forma dinámica). La carga de página a petición causa problemas con el funcionamiento de los lectores de pantalla. Cuando el foco del lector de pantalla está en el último campo de la página y el usuario pulsa la pestaña , en lugar de definir el enfoque en el primer campo de la siguiente página, el lector de pantalla vuelve a centrarse en el primer campo de la primera página del formulario.
* **(Solo para el Explorador interno 9)** No se puede acceder al control del selector de fechas de los formularios HTML5 mediante el teclado. En el control Selector de fecha, si pulsa las teclas Subir/Bajar varias veces, se cerrará el control Selector de fecha y el enfoque pasará al campo siguiente/último.

* VoiceOver no puede detectar teclas de flecha en el widget de fecha en iPad safari.
