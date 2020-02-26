---
title: Zona única a toma de varias zonas
seo-title: Zona única para la toma de control de multizone
description: 'Siga esta página para conocer la zona única para la toma de control multizone en un proyecto de AEM Screens.  '
seo-description: 'Siga esta página para conocer la zona única para la toma de control multizone en un proyecto de AEM Screens.    '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Zona única a toma de varias zonas {#single-zoneto-multizone}

## Descripción de caso de uso {#use-case-description}

En esta sección se describe un ejemplo de caso de uso que hace hincapié en cómo configurar un canal de diseño de varias zonas que se alterne con un canal de diseño de una sola zona. Cada canal tiene una secuencia de recursos de imagen y vídeo.

### Condiciones previas {#preconditions}

Antes de comenzar este caso de uso, asegúrese de comprender cómo:

* **[Crear y administrar canales](/help/screens/managing-channels.md)**
* **[Crear y administrar ubicaciones](/help/screens/managing-locations.md)**
* **[Crear y administrar programaciones](/help/screens/managing-schedules.md)**
* **[Registro de dispositivos](/help/screens/device-registration.md)**

### Actores principales {#primary-actors}

Autores de contenido

## Configuración del proyecto {#setting-up-the-project}

Siga los pasos a continuación para configurar un proyecto:

1. Cree un proyecto de AEM Screens denominado **ZonesDemo**, como se muestra a continuación.

   >[!NOTE]
   >
   >Para obtener más información sobre la creación y administración de proyectos en AEM Screens, consulte [Creación de un proyecto](/help/screens/creating-a-screens-project.md).

   ![screen_shot_2019-02-21at35809pm](assets/SZtoMZ1.png)

1. **Creación de un canal de secuencia con una imagen**

   1. Seleccione la carpeta **Canales** y haga clic en **Crear** en la barra de acciones para abrir el asistente y crear un canal.
   1. Seleccione Canal **de secuencia** en el asistente y cree el canal titulado **FullScreenOne**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ2.png)
   1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para abrir el editor y arrastrar y soltar una imagen en ese canal, como se muestra a continuación.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **Creación de un canal 2X2 con cuatro imágenes**

   1. Seleccione la carpeta **Canales** y haga clic en **Crear** en la barra de acciones para abrir el asistente y crear un canal.

   1. Seleccione **2X2 Dividir plantilla de canal** de pantalla en el asistente y cree el canal con el título **Dos canalesDosDos**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para abrir el editor y arrastrar y soltar cuatro imágenes (cuatro zonas diferentes) en ese canal, como se muestra a continuación.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **Creación de un canal de pantalla dividido 1X2 con dos imágenes**

   1. Seleccione la carpeta **Canales** y haga clic en **Crear** en la barra de acciones para abrir el asistente y crear un canal.

   1. Seleccione **1X2 Dividir plantilla de canal** de pantalla en el asistente y cree el canal con el título **OnebyTwoChannel**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para abrir el editor y arrastrar y soltar dos imágenes (dos zonas diferentes) en ese canal, como se muestra a continuación.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **Creación de un canal con un vídeo de pantalla completa**

   1. Seleccione la carpeta **Canales** y haga clic en **Crear** en la barra de acciones para abrir el asistente y crear un canal.

   1. Seleccione la plantilla Canal **de secuencia** en el asistente y cree el canal titulado **FullScreensVideo**.

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. Seleccione el canal y haga clic en **Editar** en la barra de acciones para abrir el editor, arrastrar y soltar el componente de vídeo en ese canal y, a continuación, agregar el vídeo deseado, como se muestra a continuación.
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)

## Configuración del canal de adquisición para la transición de una zona única a una zona múltiple {#takeover-channel-setup}

1. **Edición del canal de una sola zona para la adquisición de varias zonas**

   1. Seleccione el canal (**FullScreenOne)** que creó en el paso 1.
   1. Haga clic en **Editar** en la barra de acciones para abrir el editor. Arrastre y suelte dos componentes de canal y un componente de vídeo en el editor.
   ![screen_shot_2019-02-21at40516pm](assets/SZtoMZ10.png)

1. **Rellenado de los componentes agregados al canal FullScreenOne**

   1. Seleccione el primer componente de canal en el editor de **FullScreenOne** y haga clic en **Configurar** para señalar al canal creado en los pasos anteriores. Agregue la ruta al canal en Ruta **del** canal a los dos componentes del canal y arrastre y suelte el vídeo en el componente de vídeo como se muestra a continuación.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo1.gif)

1. **Configuración de la duración de los canales durante la transición**

   >[!NOTE]
   >
   >De forma predeterminada, los recursos se transitarán cada 8 segundos, pero si desea que los recursos se transiten después de una duración específica, siga el paso siguiente.

   1. Seleccione el segundo componente de canal en el editor de **FullScreenOne** y haga clic en **Configuración** para configurar la duración de tiempo de este canal. Del mismo modo, configure la duración de tiempo para el canal dos, como se muestra a continuación.
En este ejemplo, el tiempo se establece en 3 segundos.
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo2.gif)

## Vista previa del resultado {#previewing-result}

Puede hacer clic en **Vista previa** desde el editor y comprobar cómo se van a realizar las transiciones de los recursos de una sola zona a una multizona.

![](assets/SZ_MZvideo3.gif)
