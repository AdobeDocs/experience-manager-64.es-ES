---
title: Configuración de componentes en modo de diseño
seo-title: Configuring Components in Design Mode
description: Cuando AEM instancia está instalada de forma predeterminada, una selección de componentes está disponible inmediatamente en la barra de tareas. Además de estos, también hay otros componentes disponibles. Puede utilizar el modo Diseño para activar o desactivar dichos componentes.
seo-description: When AEM instance is installed out-of-the-box, a selection of components are immediately available in the sidekick. In addition to these, various other components are also available. You can use Design mode to Enable/disable such components.
page-status-flag: de-activated
uuid: 57249965-3a30-49ce-9fb0-864c5daaa262
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 93f98f7b-7ab8-4d9c-b179-dc99b80ffc91
exl-id: af6c383b-f8fd-442c-8fc5-3cdd40657c6a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---

# Configuración de componentes en modo de diseño{#configuring-components-in-design-mode}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cuando AEM instancia está instalada de forma predeterminada, una selección de componentes está disponible inmediatamente en la barra de tareas.

Además de estos, también hay otros componentes disponibles. Puede utilizar el modo Diseño para [Habilitar o deshabilitar estos componentes](#enabledisablecomponentsusingdesignmode). Cuando esté habilitado y ubicado en su página, puede usar el modo Diseño para [configuración de aspectos del diseño de componentes](#configuringcomponentsusingdesignmode) editando los parámetros del atributo.

>[!NOTE]
>
>Se debe tener cuidado al editar estos componentes. La configuración de diseño suele formar parte integral del diseño de todo el sitio web, por lo que solo debe modificarla alguien con los privilegios (y la experiencia) adecuados, normalmente un administrador o desarrollador. Consulte [Desarrollo de componentes](/help/sites-developing/components.md) para obtener más información.

Esto implica añadir o eliminar los componentes permitidos en el sistema de párrafos de la página. El sistema de párrafos ( `parsys`) es un componente compuesto que contiene todos los demás componentes de párrafo. El sistema de párrafos permite a los autores añadir componentes de distintos tipos a una página, ya que contiene todos los demás componentes de párrafos. Cada tipo de párrafo se representa como un componente.

Por ejemplo, el contenido de una página de producto puede contener un sistema de párrafos que incluya lo siguiente:

* Una imagen del producto (en forma de imagen o párrafo de imagen de texto)
* La descripción del producto (como párrafo de texto)
* Una tabla con datos técnicos (como párrafo de tabla)
* Un formulario que rellenan los usuarios (como comienzo de formulario, elemento de formulario y párrafo final de formulario)

>[!NOTE]
>
>Consulte [Desarrollo de componentes](/help/sites-developing/components.md#paragraphsystem) y [Directrices para el uso de plantillas y componentes](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) para obtener más información sobre `parsys`.

## Habilitar/deshabilitar componentes {#enable-disable-components}

En el modo Diseño, la barra de tareas se minimiza y es posible configurar los componentes accesibles para la creación:

1. Para entrar al modo Diseño, abra una página para editarla y utilice el icono de la barra de tareas:

   ![](do-not-localize/chlimage_1.png)

1. Haga clic en **Editar** en el sistema de párrafos (**Diseño de par**).

   ![screen_shot_2012-02-08at102726am](assets/screen_shot_2012-02-08at102726am.png)

1. Se abrirá un cuadro de diálogo en el que se enumerarán los grupos de componentes que se muestran en la barra de tareas junto con los componentes individuales que contienen.

   Seleccione los componentes que desee añadir o quitar de la barra de tareas.

   ![screen_shot_2012-02-08at103407am](assets/screen_shot_2012-02-08at103407am.png)

1. La barra de tareas se minimiza en el modo Diseño. Al hacer clic en la flecha, puede maximizar la barra de tareas y volver al modo de edición:

   ![](do-not-localize/sidekick-collapsed.png)

## Configuración del diseño de un componente {#configuring-the-design-of-a-component}

En el modo Diseño, también se pueden configurar atributos para los componentes individuales. Cada componente tiene sus propios parámetros. El siguiente ejemplo muestra la variable **Imagen** componente:

1. Para entrar al modo Diseño, abra una página para editarla y utilice el icono de la barra de tareas:

   ![](do-not-localize/chlimage_1-1.png)

1. Puede configurar el diseño de los componentes.

   Por ejemplo, si hace clic en **Editar** en el componente Imagen (**Diseño de la imagen**) puede configurar los parámetros específicos del componente:

   ![imagen_1-12](assets/chlimage_1-12.png)

1. Haga clic en **OK** para guardar los cambios.

1. La barra de tareas se minimiza en el modo Diseño. Al hacer clic en la flecha, puede maximizar la barra de tareas y volver al modo de edición:

   ![](do-not-localize/sidekick-collapsed-1.png)
