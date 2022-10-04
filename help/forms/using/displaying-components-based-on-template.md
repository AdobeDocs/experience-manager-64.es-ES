---
title: Visualización de componentes basados en la plantilla utilizada
seo-title: Displaying components based on the template used
description: Al crear un formulario, aprenda a habilitar componentes en la barra lateral en función de la plantilla seleccionada.
seo-description: When you create a form, learn how you can enable components in the sidebar based on the template selected.
uuid: 4e87f400-fb45-413d-9be8-72edbe99f210
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
content-type: reference
discoiquuid: 940e45b4-dbf1-4207-bd4a-cf677d645fb4
exl-id: a4cee2e6-a56f-4355-8176-b3ed7478a775
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 1%

---

# Visualización de componentes basados en la plantilla utilizada {#displaying-components-based-on-the-template-used}

Cuando un autor de formularios crea un formulario adaptable utilizando un [plantilla](/help/forms/using/template-editor.md), el autor del formulario puede ver y utilizar componentes específicos basados en la política de plantillas. Puede especificar una política de contenido de plantilla que le permita elegir un grupo de componentes que el autor del formulario verá en el momento de la creación del formulario.

## Modificación de la política de contenido de una plantilla {#changing-the-content-policy-of-a-template}

Al crear una plantilla, se crea en `/conf` en el repositorio de contenido. En función de las carpetas creadas en la variable `/conf` , la ruta a la plantilla es: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Realice los siguientes pasos para mostrar los componentes en la barra lateral en función de la política de contenido de una plantilla:

1. Abra CRXDE lite.

   URL: `https://<server>:<port>/crx/de/index.jsp`

1. En CRXDE, vaya a la carpeta en la que se crea la plantilla.

   Por ejemplo: `/conf/<your-folder>/`

1. En CRXDE, vaya a: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Para seleccionar un grupo de componentes, se requiere una nueva política de contenido. Para crear una directiva nueva, copie, pegue la directiva predeterminada y cambie su nombre.

   La ruta a la política de contenido predeterminada es: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   En el `gridFluidLayout` , copie y pegue la directiva predeterminada y renómbrala. Por ejemplo, `myPolicy`.

   ![Copia de directivas predeterminadas](assets/crx-default1.png)

1. Seleccione la nueva directiva que ha creado y, a continuación, seleccione la **componentes** propiedad en el panel derecho con tipo `string[]`.

   Cuando seleccione y abra la propiedad de componentes, verá el cuadro de diálogo Editar componentes . El cuadro de diálogo Editar componentes permite agregar o quitar grupos de componentes mediante la variable **+** y **-** botones. Puede agregar un grupo de componentes que incluya los componentes que desea que utilicen los autores.

   ![Agregar o quitar componentes de la directiva](assets/add-components-list1.png)

   Después de agregar un grupo de componentes, haga clic en **OK** para actualizar la lista y, a continuación, haga clic en **Guardar todo** encima de la barra de direcciones CRXDE y actualice.

1. En la plantilla , cambie la política de contenido de forma predeterminada a la nueva directiva que ha creado. ( `myPolicy` en este ejemplo).

   Para cambiar la directiva, en CRXDE, vaya a `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items`.

   En el `cq:policy` propiedad, cambiar `default` al nuevo nombre de directiva ( `myPolicy`).

   ![Política de contenido de plantilla actualizada](assets/updated-policy.png)

   Cuando cree un formulario que cree con la plantilla, podrá ver los componentes añadidos en la barra lateral.
