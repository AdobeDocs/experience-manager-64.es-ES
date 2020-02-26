---
title: Resolución de problemas del centro de control de dispositivos
seo-title: Monitoreo de pantallas
description: Siga esta página para monitorear y solucionar problemas de rendimiento en la actividad y el dispositivo del reproductor de pantallas con el panel Dispositivo.
seo-description: Siga esta página para monitorear y solucionar problemas de rendimiento en la actividad y el dispositivo del reproductor de pantallas con el panel Dispositivo.
uuid: 9e3d87c4-a5ff-43cb-a0b0-8919a6086586
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: troubleshoot
discoiquuid: 58738b4e-90ba-4656-85a7-2283e54d7919
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Resolución de problemas del centro de control de dispositivos{#troubleshooting-device-control-center}

Puede supervisar y solucionar problemas de rendimiento para la actividad y el dispositivo del reproductor de pantallas mediante el panel de control del dispositivo. Esta página proporciona información sobre cómo supervisar y solucionar problemas de rendimiento percibidos para el reproductor de pantallas y los dispositivos asignados.

## Monitorear y solucionar problemas desde el Centro de control de dispositivos {#monitor-and-troubleshoot-from-device-control-center}

Puede supervisar la actividad y, por lo tanto, solucionar problemas del reproductor de pantallas, mediante el panel de dispositivos.

### Tablero de dispositivos {#device-dashboard}

Siga los pasos a continuación para navegar al tablero del dispositivo:

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --> ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Seleccione el dispositivo que desee supervisar.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. La página muestra la información, la actividad y los detalles del dispositivo que le permiten supervisar las actividades y funciones del dispositivo.

   ![chlimage_1-53](assets/chlimage_1-53.png)

### Monitorear la actividad del dispositivo {#monitor-device-activity}

El panel **Actividad** muestra el último ping del reproductor de pantallas con la marca de tiempo. El último ping corresponde a la última vez que el dispositivo se puso en contacto con el servidor.

![chlimage_1-54](assets/chlimage_1-54.png)

Además, haga clic en **Recopilar registros** en la esquina superior derecha del panel **Actividad** para ver los registros del reproductor.

### Actualizar detalles del dispositivo {#update-device-details}

Consulte el panel Detalles **del** dispositivo para ver la IP del dispositivo, el uso del almacenamiento, la versión del firmware y el tiempo de actividad del reproductor del dispositivo.

![chlimage_1-55](assets/chlimage_1-55.png)

Además, haga clic en **Borrar caché** y **Actualizar** para borrar la caché del dispositivo y actualizar la versión del [firmware](screens-glossary.md) , respectivamente, desde este panel.

**Además, haga clic en el**... en la esquina superior derecha del panel Detalles **del** dispositivo para reiniciar o actualizar el estado del reproductor.

![chlimage_1-56](assets/chlimage_1-56.png)

### Actualizar información del dispositivo {#update-device-information}

Consulte el panel **INFORMACIÓN** DEL DISPOSITIVO para ver la actualización de configuración, el dispositivo, la plataforma, la versión y la visualización asociada al dispositivo.

![chlimage_1-57](assets/chlimage_1-57.png)

Además, haga clic en (**...**) en la esquina superior derecha del panel Información del dispositivo para ver las propiedades o actualizar el dispositivo.

![chlimage_1-58](assets/chlimage_1-58.png)

Haga clic en **Propiedades** para ver el cuadro de diálogo Propiedades **del dispositivo** . Puede editar el título del dispositivo o elegir la opción para las actualizaciones de configuración como **Manual** o **Automático**.

>[!NOTE]
>
>Para obtener más información acerca de los eventos asociados con las actualizaciones automáticas o manuales del dispositivo, consulte la sección Actualizaciones ***automáticas contra manuales del panel*** del dispositivo en [Administración de canales](managing-channels.md).

![chlimage_1-59](assets/chlimage_1-59.png)

### Ver captura de pantalla del reproductor {#view-player-screenshot}

Puede ver la captura de pantalla del reproductor desde el dispositivo desde el panel **PLAYER SCREENSHOT **.

Haga clic (**...**) en la esquina superior derecha del panel Captura de pantalla del reproductor y seleccione **Actualizar captura de pantalla **para ver la instantánea del reproductor en ejecución.

![chlimage_1-60](assets/chlimage_1-60.png)

### Administrar preferencias {#manage-preferences}

El panel **PREFERENCIAS** permite al usuario cambiar las preferencias para la interfaz de usuario **del** administrador, el conmutador **de** canal y la depuración **remota** para el dispositivo.

>[!NOTE]
>
>Para obtener más información sobre estas opciones, consulte [AEM Screens Player](working-with-screens-player.md).

![chlimage_1-61](assets/chlimage_1-61.png)

Además, haga clic en **Ver preferencias** en la esquina superior derecha para actualizar la URL del servidor y la resolución.

![chlimage_1-62](assets/chlimage_1-62.png)

## Resolución de problemas de configuración de OSGI {#troubleshoot-osgi-settings}

Debe habilitar el referente vacío para permitir que el dispositivo publique datos en el servidor. Por ejemplo, si la propiedad referrer vacía está deshabilitada, el dispositivo no puede publicar una captura de pantalla de vuelta.

Actualmente, algunas de estas funciones solo están disponibles si el filtro *Apache Sling Referrer Allow Empty* está habilitado en la configuración OSGI. El tablero puede mostrar una advertencia de que la configuración de seguridad puede impedir que algunas de estas funciones funcionen.

Siga los pasos a continuación para habilitar el filtro de referente de Sling de Apache para permitir que esté vacío

1. Vaya a Configuración [de la consola web de](http://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter)Adobe Experience Manager.
1. Active la opción **allow.empty **.
1. Haga clic en **Guardar**.

![chlimage_1-63](assets/chlimage_1-63.png)

### Recomendaciones {#recommendations}

En la siguiente sección se recomienda supervisar los vínculos de red, el servidor y los reproductores para comprender el estado y reaccionar a los problemas.

AEM proporciona supervisión integrada para:

* *Heartbeat* cada 5 segundos para indicar que AEM Screens Player está en funcionamiento.
* *Captura de pantalla* del Reproductor que muestra lo que se muestra actualmente en el Reproductor.
* La versión de firmware *del reproductor de* AEM Screens instalada en el reproductor.
* *Espacio* de almacenamiento gratuito en el reproductor.

Recomendaciones para la supervisión remota con software de terceros:

* Uso de CPU en Reproductores.
* Compruebe si se está ejecutando el proceso de AEM Screens Player.
* Reinicio/reinicio remoto del reproductor.
* Notificaciones en tiempo real.

Se recomienda implementar el hardware y el sistema operativo del reproductor de forma que permita el inicio de sesión remoto para diagnosticar problemas y reiniciar el reproductor.

#### Additional Resources {#additional-resources}

Consulte Configuración y solución de problemas [de reproducción de](troubleshoot-videos.md) vídeo para depurar y solucionar problemas de los vídeos que se reproducen en el canal.
