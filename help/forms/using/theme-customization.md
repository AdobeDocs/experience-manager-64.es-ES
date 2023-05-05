---
title: Personalizar temáticas
seo-title: Theme Customization
description: Personalizar la temática de su aplicación de AEM Forms.
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 89%

---

# Personalizar temáticas {#theme-customization}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede personalizar el código HTML y el archivo CSS para ofrecer a la aplicación AEM Forms una apariencia específica de la organización. Por ejemplo, puede cambiar el color de fondo y la altura de las tareas o puntos de inicio. El ejemplo siguiente indica las instrucciones para cambiar:

* Las instrucciones de visualización en lugar de la descripción.
* Número de rutas de visualización.
* Color de degradado de fondo.

## Etapas {#steps}

1. Abra su proyecto.

   * Si utiliza un dispositivo iOS, abra `Capture.xcodeproj` en Xcode.
   * Si utiliza un dispositivo Android, abra el proyecto de Android en Eclipse.
   * Para Windows, abra `MWSWindows.sln` en Visual Studio.

1. Vaya a la carpeta de plantillas.

   * En Xcode, vaya a la carpeta **Captura > www > wsmobile > js > runtime > plantillas**.
   * En Eclipse, vaya a la carpeta **Recursos > www > wsmobile > js > runtime > plantillas**.
   * En Visual Studio, vaya a la carpeta **MWSWindows > www > wsmobile > js > runtime > plantillas**.

1. Abra el archivo `template.html` para editarlo.
1. Localice la siguiente cadena:

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   Sustitúyala por `<%`.

1. Localice el código siguiente en el archivo `template.html`:

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. Comente la siguiente línea y guarde el archivo.

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. Vaya a la carpeta css.

   * En Xcode, vaya a **Captura > www > wsmobile > css**.
   * En Eclipse, vaya a **recursos > www > wsmobile > css**.
   * En Visual Studio, vaya a **MWSWindows > www > wsmobile > css**.

1. Abra el archivo `_style.css` para editarlo.
1. Para la imagen de fondo, cambie `#323232` a `#fff`.
1. Guarde los cambios y cierre el archivo `_style.css`.
1. Abra la aplicación de AEM Forms.

   La aplicación de AEM Forms ahora muestra instrucciones en lugar de la descripción.
