---
title: Insertar y extraer recursos digitales para editarlos
description: Obtenga información sobre cómo extraer recursos para editarlos y volver a protegerlos una vez completados los cambios.
contentOwner: AG
feature: Administración de activos
role: User
exl-id: 0c79ed42-0acd-426e-8e14-412bb4117585
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# Archivos de desprotección y desprotección en Assets {#check-in-and-check-out-files-in-assets}

Recursos Adobe Experience Manager (AEM) permite extraer recursos para editarlos y volver a protegerlos después de completar los cambios. Después de retirar un recurso, solo puede editarlo, anotarlo, publicarlo, moverlo o eliminarlo. Si se retira un recurso, este se bloquea. Otros usuarios no pueden realizar ninguna de estas operaciones en el recurso hasta que vuelva a proteger el recurso en AEM Assets. Sin embargo, aún pueden cambiar los metadatos del recurso bloqueado.

Para poder extraer o registrar recursos, necesita tener acceso de escritura en ellos.

Esta función ayuda a evitar que otros usuarios anulen los cambios realizados por un autor en los que varios usuarios colaboran en la edición de flujos de trabajo entre equipos.

## Extraer recursos {#checking-out-assets}

1. En la interfaz de usuario de Assets, seleccione el recurso que desea retirar. También puede seleccionar varios recursos para retirarlos.

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. En la barra de herramientas, pulse o haga clic en el icono **[!UICONTROL Cierre de compra]**.

   ![chlimage_1-469](assets/chlimage_1-469.png)

   Observe que el icono **[!UICONTROL Checkout]** alterna con el icono **[!UICONTROL Checkin]** con el bloqueo abierto.

   ![chlimage_1-470](assets/chlimage_1-470.png)

   Para verificar si otros usuarios pueden editar el recurso que ha desprotegido, inicie sesión como un usuario diferente. Aparece un icono de candado en la miniatura del recurso que ha extraído.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Seleccione el recurso. Observe que la barra de herramientas no muestra ninguna opción que le permita editar, anotar, publicar o eliminar el recurso.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   Sin embargo, puede hacer clic o pulsar el icono **[!UICONTROL Ver propiedades]** para editar los metadatos del recurso bloqueado.

1. Pulse o haga clic en el icono Editar para abrir el recurso en modo de edición.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Edite el recurso y guarde los cambios. Por ejemplo, recorte la imagen y guárdela.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   También puede elegir anotar o publicar el recurso.

1. Seleccione el recurso editado en la interfaz de usuario de Assets y pulse o haga clic en el icono **[!UICONTROL Proteger]** de la barra de herramientas.

   ![chlimage_1-475](assets/chlimage_1-475.png)

   El recurso modificado se archiva en AEM Assets y está disponible para otros usuarios para su edición.

## Registro forzado {#forced-check-in}

Los administradores pueden proteger los recursos que han extraído otros usuarios.

1. Inicie sesión en AEM Assets como administrador.
1. En la interfaz de usuario de Assets, seleccione uno o varios recursos que otros usuarios hayan extraído.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. En la barra de herramientas, pulse o haga clic en el icono **[!UICONTROL Liberar bloqueo]**. El recurso se vuelve a registrar y se puede editar para otros usuarios.

   ![chlimage_1-477](assets/chlimage_1-477.png)
