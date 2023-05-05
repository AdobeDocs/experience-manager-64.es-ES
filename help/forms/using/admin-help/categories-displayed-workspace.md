---
title: Administrar las categorías mostradas en Workspace
seo-title: Managing the categories displayed in Workspace
description: En Workspace, los procesos que un usuario puede iniciar se muestran en categorías en el panel de navegación izquierdo. Descubra cómo puede administrar estas categorías que se muestran en Workspace.
seo-description: In Workspace, the processes that a user can start are displayed in categories in the left navigation pane. Learn how you can manage these categories displayed in Workspace.
uuid: c2a275f5-872e-467f-9f07-4b130631e8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0d1536a2-10ac-4031-bd7f-264b02d0d75f
exl-id: 5a2bd0ea-2c5e-4e0c-aff1-dba06be6a5b7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 3%

---

# Administrar las categorías mostradas en Workspace {#managing-the-categories-displayed-in-workspace}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En Workspace, los procesos que un usuario puede iniciar se muestran en categorías en el panel de navegación izquierdo. Puede configurar las categorías en la consola de administración o los diseñadores de procesos pueden configurarlas en Workbench. Cuando los diseñadores de procesos crean procesos, los asignan a categorías.

Cuando especifique nombres de categoría, créelos para que aparezcan correctamente en el panel de navegación de Workspace. De forma predeterminada, el panel de navegación izquierdo tiene una anchura fija de 210 píxeles, que es de aproximadamente 24 caracteres. Si el nombre de categoría especificado es demasiado largo para ajustarse al ancho fijo del panel de navegación izquierdo, se trunca. El nombre completo solo aparece cuando el puntero del ratón se pone en pausa sobre él. Intente evitar nombres de categoría que se trunquen. Los siguientes ejemplos ilustran los nombres de categorías que se ajustan y los que se truncan:

**Nombre de categoría que se ajusta a:** Asistencia y licencia

**Nombre de la categoría truncado:** Asistencia y licencia (Estados Unidos)

En Workspace, los procesos de una categoría suelen mostrarse como tarjetas en la página Iniciar proceso . En general, se pueden mostrar seis tarjetas en la pantalla para una categoría antes de que el usuario deba desplazarse para ver las tarjetas restantes. Como el desplazamiento dificulta la búsqueda de un proceso, considere la posibilidad de limitar cada categoría a seis procesos o, según la resolución, limitar el número de procesos que se pueden mostrar en la pantalla sin necesidad de desplazarse.

Si utiliza MySQL como base de datos de formularios AEM, la Consola de administración no puede diferenciar entre dos nombres de categoría que difieran sólo en el uso de caracteres extendidos. Por ejemplo, si crea una categoría denominada abcde y una categoría denominada âbcdè, se consideran iguales.

## Añadir una categoría {#add-a-category}

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de categorías.
1. Haga clic en Agregar. Si desea agregar una subcategoría, seleccione una categoría y haga clic en Agregar.
1. En el cuadro Nombre, escriba un nombre para la categoría y, en el cuadro Descripción, escriba una descripción de la categoría.
1. Haga clic en Agregar. La categoría se muestra en la página Administración de categorías .

   ***nota **: Al crear categorías, solo se pueden agregar hasta cinco niveles de jerarquía.*

## Editar una categoría {#edit-a-category}

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de categorías.
1. Seleccione la categoría que desee editar y haga clic en Editar. También puede hacer doble clic en una categoría para editarla.
1. Edite el nombre de la categoría en el cuadro Nombre.

## Eliminar una categoría {#remove-a-category}

Solo puede eliminar las categorías que no estén en uso.

1. En la consola de administración, haga clic en Servicios > Aplicaciones y servicios > Administración de categorías.
1. En la página Administración de categorías, active la casilla de verificación de la categoría que desea eliminar y haga clic en Quitar. La categoría ya no se muestra.
