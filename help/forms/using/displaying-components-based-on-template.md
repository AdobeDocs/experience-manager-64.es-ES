---
title: Visualización de componentes basados en la plantilla utilizada
seo-title: Visualización de componentes basados en la plantilla utilizada
description: Al crear un formulario, aprenda a activar los componentes en la barra lateral en función de la plantilla seleccionada.
seo-description: Al crear un formulario, aprenda a activar los componentes en la barra lateral en función de la plantilla seleccionada.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
translation-type: tm+mt
source-git-commit: 74d51d46d61b005930f382a33278ae0bea6435e2
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---


# Visualización de componentes basados en la plantilla utilizada {#displaying-components-based-on-the-template-used}

Cuando un autor de un formulario crea un formulario adaptable con una [plantilla](/help/forms/using/template-editor.md), el autor del formulario puede ver y utilizar componentes específicos basados en la política de plantillas. Puede especificar una directiva de contenido de plantilla que le permita elegir un grupo de componentes que el autor verá en el momento de la creación del formulario.

## Cambio de la directiva de contenido de una plantilla {#changing-the-content-policy-of-a-template}

Al crear una plantilla, ésta se crea en `/conf` en el repositorio de contenido. Según las carpetas que haya creado en el directorio `/conf`, la ruta de acceso a la plantilla es: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Realice los siguientes pasos para mostrar los componentes de la barra lateral en función de la política de contenido de una plantilla:

1. Abra la lista CRXDE.

   URL: `https://<server>:<port>/crx/de/index.jsp`

1. En CRXDE, desplácese a la carpeta en la que se ha creado la plantilla.

   Por ejemplo: `/conf/<your-folder>/`

1. En CRXDE, vaya a: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Para seleccionar un grupo de componentes, se requiere una nueva directiva de contenido. Para crear una nueva directiva, copie y pegue la directiva predeterminada y cámbiele el nombre.

   La ruta a la directiva de contenido predeterminada es: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   En la carpeta `gridFluidLayout`, copie y pegue la directiva predeterminada y cámbiele el nombre. Por ejemplo, `myPolicy`.

   ![Copia de directivas predeterminadas](assets/crx-default1.png)

1. Seleccione la nueva directiva que cree y seleccione la propiedad **components** en el panel derecho con el tipo `string[]`.

   Al seleccionar y abrir la propiedad components, aparece el cuadro de diálogo Editar componentes. El cuadro de diálogo Editar componentes permite agregar o quitar grupos de componentes mediante los botones **+** y **-**. Puede agregar un grupo de componentes que incluya componentes que desee que utilicen los autores.

   ![Añadir o quitar componentes de la directiva](assets/add-components-list1.png)

   Después de agregar un grupo de componentes, haga clic en **Aceptar** para actualizar la lista y, a continuación, haga clic en **Guardar todo** encima de la barra de direcciones CRXDE y actualice.

1. En la plantilla, cambie la directiva de contenido de forma predeterminada a la nueva directiva que haya creado. ( `myPolicy` en este ejemplo.)

   Para cambiar la directiva, en CRXDE, vaya a `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   En la propiedad `cq:policy`, cambie `default` por el nuevo nombre de directiva ( `myPolicy`).

   ![Directiva de contenido de plantilla actualizada](assets/updated-policy.png)

   Al crear un formulario que cree con la plantilla, podrá ver los componentes agregados en la barra lateral.

