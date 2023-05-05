---
title: Explicación de la estructura de carpetas
seo-title: Understanding the folder structure
description: Obtenga más información sobre la estructura de carpetas del código fuente de AEM Forms Workspace que se va a personalizar.
seo-description: How to understand the folder structure of AEM Forms workspace source code to customize.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
exl-id: 192c436d-a507-4883-bd68-a6863a6664e0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 84%

---

# Explicación de la estructura de carpetas {#understanding-the-folder-structure}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los componentes de AEM Forms Workspace han sido diseñados sobre arquitectura MVC mediante Backbone. Cada componente tiene un archivo para:

* El modelo, que contiene lógica empresarial.
* La plantilla, es decir, un archivo HTML que contiene controles de interfaz.
* La vista, que actúa como una clase de controlador para la plantilla.

Los archivos de todos los componentes se colocan en la estructura de carpetas que se describe a continuación. Para acceder a los archivos, inicie sesión en CRXDE Lite y desplácese hasta `/libs/ws/js/runtime/`.

**models** Contiene modelos de Backbone.

**views** Contiene vistas de Backbone.

**templates** Contiene únicamente las plantillas HTML de los componentes.

**routes** Contiene rutas universales. La carpeta templates dentro de routes contiene el código HTML y las referencias a los componentes.

**services** Contiene la interfaz de servicio para llamar a las API del servidor de Adobe Experience Manager en el extremo REST.

**util** Contiene utilidades genéricas que se pueden utilizar en varios componentes.
