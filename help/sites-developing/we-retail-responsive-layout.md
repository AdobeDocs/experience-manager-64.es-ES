---
title: Probar un diseño interactivo en We.Retail
seo-title: Trying out Responsive Layout in We.Retail
description: Probar un diseño interactivo en We.Retail
seo-description: null
uuid: d9613655-f54e-458f-9175-d07bb868f58b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 2d374e88-ea09-43d5-986c-5d77b0705b93
exl-id: ccb792f7-e837-4790-818f-e2c446328e71
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 3%

---

# Probar un diseño interactivo en We.Retail{#trying-out-responsive-layout-in-we-retail}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Todas las páginas de We.Retail utilizan el componente Contenedor de diseño para implementar un diseño interactivo. El contenedor de diseño proporciona un sistema de párrafos que le permite colocar componentes en una cuadrícula interactiva. Esta cuadrícula puede reorganizar el diseño según el tamaño y el formato del dispositivo o la ventana. El componente se utiliza junto con la variable **Diseño** en el editor de páginas, que le permite crear y editar su diseño interactivo en función del dispositivo.

## Probándolo {#trying-it-out}

1. Edite la página Surfing Ártico en la sección Experiencias de la rama maestra de idioma.

   http://localhost:4502/editor.html/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.html

1. Cambie a **Vista previa** para ver la página tal como se representaría a un visitante del sitio web. Desplácese hacia abajo hasta el contenido del artículo *Espíritus Aloha en el norte de Noruega*.

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Cambie el tamaño de la ventana del explorador y observe cómo el diseño se adapta dinámicamente al cambio de tamaño.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Cambie al modo Diseño . La barra de herramientas del emulador se muestra automáticamente, lo que le permite planificar el diseño para cada dispositivo de destino.

   Al seleccionar un componente, se muestran las opciones de flotación y ocultamiento en el menú de edición, junto con los controles de cambio de tamaño del componente.

   ![chlimage_1-180](assets/chlimage_1-180.png)

1. Al capturar y arrastrar el controlador de cambio de tamaño del componente, se muestra automáticamente la cuadrícula de diseño para ayudarle a cambiar el tamaño.

   ![chlimage_1-181](assets/chlimage_1-181.png)

## Información adicional {#further-information}

Para obtener más información, consulte el documento de creación [Diseño interactivo](/help/sites-authoring/responsive-layout.md) o el documento de administrador [Configuración del contenedor de diseño y el modo de diseño](/help/sites-administering/configuring-responsive-layout.md) para obtener todos los detalles técnicos.
