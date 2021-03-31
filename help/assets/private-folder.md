---
title: Uso compartido de carpetas privadas
description: Obtenga información sobre cómo crear una carpeta privada en Adobe Experience Manager (AEM) Assets, compartirla con otros usuarios y asignarles distintos privilegios.
contentOwner: AG
feature: Colaboración
role: Profesional empresarial
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 7%

---


# Uso compartido de carpetas privadas {#private-folder-sharing}

Puede crear una carpeta privada en la interfaz de usuario de Adobe Experience Manager (AEM) Assets que solo está disponible para usted. Puede compartir esta carpeta privada con otros usuarios y asignarles varios privilegios. En función del nivel de privilegios que asigne, los usuarios pueden realizar varias tareas en la carpeta, como ver los recursos dentro de la carpeta o editar los recursos.

1. En la consola Assets, pulse o haga clic en **[!UICONTROL Crear]** en la barra de herramientas y, a continuación, elija **[!UICONTROL Carpeta]** en el menú.

   ![chlimage_1-411](assets/chlimage_1-411.png)

1. En el cuadro de diálogo **[!UICONTROL Agregar carpeta]**, introduzca un título y un nombre (opcional) para la carpeta y seleccione **[!UICONTROL Privado]**.

   ![chlimage_1-412](assets/chlimage_1-412.png)

1. Toque o haga clic en **[!UICONTROL Crear]**. Se crea una carpeta privada en la interfaz de usuario de .

   ![chlimage_1-413](assets/chlimage_1-413.png)

1. Para compartir la carpeta con otros usuarios y asignarles privilegios, seleccione la carpeta y pulse o haga clic en el icono **[!UICONTROL Propiedades]** de la barra de herramientas.

   ![chlimage_1-414](assets/chlimage_1-414.png)

   >[!NOTE]
   >
   >Ningún otro usuario puede ver la carpeta hasta que la comparta.

1. En la página Propiedades de la carpeta, seleccione un usuario de la lista **[!UICONTROL Agregar usuario]**, asigne una función al usuario de la carpeta privada y haga clic en **[!UICONTROL Agregar]**.

   ![chlimage_1-415](assets/chlimage_1-415.png)

   >[!NOTE]
   >
   >Puede asignar varias funciones, como Editor, Propietario o Visualizador, al usuario con el que comparte la carpeta. Si asigna una función Propietario al usuario, este tiene privilegios de Editores en la carpeta. Además, el usuario puede compartir la carpeta con otros usuarios. Si asigna una función de editor, el usuario puede editar los recursos de la carpeta privada. Si asigna una función de visor, el usuario solo puede ver los recursos de la carpeta privada.

1. Haga clic en **[!UICONTROL Guardar]**. Según la función que asigne, al usuario se le asignará un conjunto de privilegios en su carpeta privada cuando inicie sesión en AEM Assets.
1. Haga clic en **[!UICONTROL Ok]** para cerrar el mensaje de confirmación.
1. El usuario con el que comparte la carpeta recibe una notificación para compartir. Inicie sesión en AEM Assets con las credenciales del usuario para ver la notificación.

   ![chlimage_1-416](assets/chlimage_1-416.png)

1. Toque o haga clic en el icono Notification para abrir la lista de notificaciones.

   ![chlimage_1-417](assets/chlimage_1-417.png)

1. Toque o haga clic en la entrada de la carpeta privada compartida por el administrador para abrir la carpeta.

>[!NOTE]
>
>Para poder crear una carpeta privada, necesita permisos de lectura y edición de ACL en la carpeta principal en la que desea crear una carpeta privada. Si no es administrador, estos permisos no están habilitados para usted de forma predeterminada en */content/dam*. En este caso, obtenga primero estos permisos para su ID o grupo de usuarios antes de intentar crear carpetas privadas o ver la configuración de carpetas.

