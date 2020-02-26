---
title: Implementación de Android Player
seo-title: Implementación de Android Player
description: 'Siga esta página para conocer la implementación de Android Watchdog, una solución para recuperar el reproductor de los bloqueos. '
seo-description: 'Siga esta página para conocer la implementación de Android Watchdog, una solución para recuperar el reproductor de los bloqueos. '
uuid: 37527a6a-dcc5-4256-abeb-e1f95ff80be4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: e6ec1641-4323-4c79-b932-b857feb1df21
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Implementación de Android Player {#implementing-android-player}

Un ***Watchdog*** es una solución para recuperar al jugador de los bloqueos. Una aplicación debe registrarse en el servicio de vigilancia y luego enviar periódicamente mensajes al servicio de que está viva. En caso de que el servicio de vigilancia no reciba un mensaje de mantenimiento en el plazo estipulado, el servicio intentará reiniciar el dispositivo para una recuperación limpia (si tiene los privilegios suficientes) o reiniciar la aplicación.

## Implementación de Android Watchdog {#implementing-android-watchdog}

Debido a la arquitectura de Android, el reinicio del dispositivo requiere que la aplicación tenga privilegios de sistema. Para ello, debe firmar el apk con las claves de firma del fabricante; de lo contrario, Watchdog reiniciará la aplicación del reproductor y no reiniciará el dispositivo.

### Señalización de los apks de Android mediante claves de fabricante {#signage-of-android-apks-using-manufacturer-keys}

Para acceder a algunas de las API privilegiadas de Android, como *PowerManager* o *HDMIControlServices*, debe firmar el apk android con las claves del fabricante.

>[!CAUTION]
>
>Requisitos previos:
>
>Debe tener instalado el SDK de android antes de realizar los siguientes pasos.

Siga los pasos a continuación para firmar el apk androide con las claves del fabricante:

1. Descargue el paquete desde Google Play o desde la página de descargas [de](https://download.macromedia.com/screens/) AEM Screens Player
1. Obtenga las claves de plataforma del fabricante para obtener un *pk8* y un archivo *pem*

1. Localice la herramienta apksigner en el sdk android usando find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Busque la ruta a la herramienta de alineación de código postal en el sdk android
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensalign.apk
1. Instalar ***aemscreensalign.apk*** mediante la instalación de adb en el dispositivo

## Implementación de Android Watchdog {#android-watchdog-implementation}

El servicio de vigilancia de Android cruzado se implementa como un complemento de Cordova mediante *AlarmManager*.

El siguiente diagrama muestra la implementación del servicio de vigilancia:

![chlimage_1-43](assets/chlimage_1-43.png)

**1. Inicialización** En el momento de la inicialización del complemento de cordova, se comprueban los permisos para ver si tenemos privilegios del sistema y, por lo tanto, el permiso de reinicio. Si se cumplen estos dos criterios, se crea una intención de reinicio pendiente; de lo contrario, se crea una intención pendiente de reiniciar la aplicación (según su actividad de inicio).

**2. Mantener activo Temporizador** Se utiliza un temporizador de mantenimiento para activar un evento cada 15 segundos. En ese caso, debe cancelar la intención pendiente existente (para reiniciar o reiniciar la aplicación) y registrar una nueva intención pendiente durante los mismos 60 segundos en el futuro (principalmente posponiendo el reinicio).

>[!NOTE]
>
>En Android, *AlarmManager* se utiliza para registrar las *intenciones* pendientes que se pueden ejecutar incluso si la aplicación se ha bloqueado y su entrega de alarma no es exacta desde la API 19 (Kitkat). Mantenga cierto espacio entre el intervalo del temporizador y la alarma del *AlarmManager* *pendingIntent* .

**3. Bloqueo** de la aplicación En caso de bloqueo, el parámetro pendingIntent para el reinicio registrado con AlarmManager ya no se restablece y, por tanto, ejecuta un reinicio o reinicio de la aplicación (según los permisos disponibles en el momento de la inicialización del complemento de Cordova).
