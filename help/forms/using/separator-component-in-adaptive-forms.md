---
title: Componente Separador en formularios adaptables
seo-title: Separator component in adaptive forms
description: Puede utilizar el componente Separador para separar visualmente las secciones de un formulario.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 82%

---

# Componente Separador en formularios adaptables {#separator-component-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede utilizar el componente separador para separar visualmente los paneles de un formulario. Puede definir el aspecto general y el estilo de un componente Separador especificando las siguientes propiedades del componente Separador:

* **Nombre del elemento:** especifica el nombre del componente. Las expresiones SOM se dirigen al componente con el valor especificado en el campo Nombre del elemento.
* **Grosor:** especifica el grosor del componente Separador en píxeles.
* **Colspan:** Especifica el número de columnas que ocupa un componente separador.
* **Clase CSS:** especifica la clase CSS personalizada para el componente Separador.
* **Estilos en línea:** con AEM Forms, ahora puede aplicar estilos CSS en línea a componentes de formulario adaptable individuales y previsualizar los cambios en tiempo real.

Para especificar las propiedades de un componente Separador:

1. Seleccione un componente Separador y pulse ![cmppr](assets/cmppr.png). Las propiedades se abren en la barra lateral.
1. Haga clic en una pestaña de la sección Propiedades CSS en línea para especificar las propiedades CSS. Por ejemplo: a. En la pestaña Campo, haga clic en **Agregar elemento**. Se añade una fila con dos campos.
1. En el primer campo de la izquierda, especifique la propiedad CSS3 que desee aplicar. Por ejemplo, **border**. También puede seleccionar una propiedad haciendo clic en el botón de flecha hacia abajo. La lista desplegable no es exhaustiva y puede especificar cualquier nombre de propiedad CSS3 admitido en este campo.
1. En el campo adyacente, especifique un valor válido para la propiedad CSS3 especificada. Por ejemplo, **3px solid black**.
1. Haga clic en **Agregar elemento** para especificar otra propiedad y su valor.
1. Haga clic en **Vista previa** para previsualizar los cambios en el formulario.
1. Haga clic en **OK** para confirmar los cambios o **Cancelar **para salir del cuadro de diálogo sin ningún cambio.
