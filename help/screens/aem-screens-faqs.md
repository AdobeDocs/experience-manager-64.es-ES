---
title: Preguntas más frecuentes sobre AEM Screens
seo-title: Preguntas más frecuentes sobre AEM Screens
description: Siga esta página para obtener respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.
seo-description: Siga esta página para obtener respuestas a las preguntas más frecuentes relacionadas con un proyecto de AEM Screens.
uuid: e394b1bd-1e63-4bd1-b669-923b2a298743
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
content-type: reference
topic-tags: troubleshoot
discoiquuid: 558a7c2f-b32e-428e-89f6-123d72ca1108
translation-type: tm+mt
source-git-commit: 9f505017b80fe54e228daea9b248fb0a7db93ca2

---


# Preguntas más frecuentes sobre AEM Screens {#aem-screens-faqs}

La siguiente sección proporciona respuestas a algunas de las preguntas más frecuentes más frecuentes relacionadas con un proyecto de AEM Screens.

## Administración de canales {#channel-management}

### ¿Cuál es la diferencia entre un canal en línea y otro sin conexión? {#what-is-the-difference-between-an-online-and-an-offline-channel}

Un ***canal en línea*** mostrará el contenido actualizado en el entorno en tiempo real, mientras que ***un canal sin conexión*** muestra el contenido almacenado en caché.

### ¿Cómo hago un canal en línea? {#how-do-i-make-a-channel-online}

Seleccione el canal y vaya a las propiedades del canal desde la barra de acciones. Marque el modo **Desarrollador (forzar a que el canal esté en línea)** en la ficha **Canal** para que el canal esté en línea.

### ¿Cuál es el uso del campo Función de canal? {#what-is-the-use-of-the-channel-role-field}

La función de canal es la abstracción del canal real que se ejecuta para que el autor pueda centrarse directamente en la experiencia genérica. Puede considerarlo una especie de etiqueta que identifica de forma exclusiva al canal en su contexto (visualización o programación).

### ¿Cómo se produce la resolución real del canal? {#how-does-actual-channel-resolution-happen}

Para las referencias ** estáticas, la resolución simplemente sigue la ruta especificada.

En el caso de las referencias ** dinámicas, la resolución se produce una vez que el canal está asignado a la visualización (no a la programación). La ruta de visualización se convierte en el contexto para el canal y la resolución se produce de la siguiente manera (de la prioridad más alta a la más baja):

1. La pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La pantalla tiene un nodo del mismo nivel que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia
1. La ubicación principal de la pantalla tiene un nodo secundario que coincide con el nombre del canal al que se hace referencia

Y así sucesivamente, hasta que llegue a la carpeta de ubicaciones y se detenga allí en este momento (por lo que no puede hacer referencia a un canal que estaría en la carpeta de canales, por ejemplo, solo los canales en el subárbol de ubicaciones).

## Registro de dispositivos {#device-registration}

### Si descubro extremos como solicitudes de integración y registro de dispositivos, puedo crear un script con un gran número de dispositivos y registrar estos dispositivos. Además de bloquear esto a una sucursal Wi-Fi, ¿es posible asegurar estas solicitudes? {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

Actualmente, el registro solo es posible en la instancia de autor. Aunque el servicio de registro no está autenticado, solo creará un dispositivo pendiente en AEM y no registrará el dispositivo ni asignará ninguna visualización.

Para registrar un dispositivo (lo que significa crear un usuario para el dispositivo en AEM), debe autenticarse en AEM y seguir manualmente el asistente para el registro para completar el registro. En teoría, un usuario malintencionado puede crear varios dispositivos pendientes pero no puede registrarse sin un inicio de sesión de AEM.

### ¿Existe alguna forma de transformar las solicitudes HTTP GET en HTTP POST con alguna forma de autenticación? {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

La solicitud de registro es una solicitud POST.

Se recomienda obtener el ID del dispositivo de la sesión en lugar de pasarlo como parámetro. Esto limpiaría los registros del servidor, la caché del explorador, etc. Actualmente no se trata de un problema de seguridad. Tenga en cuenta que GET semánticamente se utiliza cuando no hay ningún cambio de estado en el servidor y POST se utiliza cuando hay un cambio de estado.

### ¿Existe alguna forma de rechazar una solicitud de registro de dispositivo?

No puede rechazar las solicitudes de registro. En su lugar, las solicitudes de registro deben caducar tras un tiempo de espera configurado en la consola web de Adobe Experience Manager.

De forma predeterminada, este valor se establece en un día y se almacena en una caché de memoria.

## Informes de estado y supervisión de dispositivos {#device-monitoring-and-health-reports}

### ¿Cómo puedo solucionar problemas si mi reproductor de AEM Screens muestra la pantalla en blanco? {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

Compruebe las siguientes posibilidades para solucionar el problema de la pantalla en blanco:

* AEM no puede insertar el contenido sin conexión
* El canal no tiene contenido
* Ninguno de los recursos está programado para mostrarse en este momento

### ¿Qué puedo hacer si el reproductor de AEM Screens no se puede registrar y su estado se muestra como Error? {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Debe habilitar el filtro de referente Sling de Apache para permitir que esté vacío. Esto es necesario para el funcionamiento óptimo del protocolo de control entre AEM Screens Player y el servidor de AEM Screens.

1. Vaya a Configuración de la consola web de **Adobe Experience Manager**
1. Active la opción **allow.empty **.
1. Haga clic en **Guardar**.

### ¿Cómo solucionar problemas si al registrar un reproductor de AEM Screens, el dispositivo muestra FALLO y los registros de la consola muestran el error ENAME_NOT_FOUND? {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

Este problema puede producirse si el reproductor no puede encontrar el DNS del servidor de pantallas de AEM. Puede intentar utilizar la dirección IP para conectarse. Para obtener la IP del servidor, utilice: *arp &lt;server_dns_name>*.

### ¿AMS recomienda implementar un Watchdog para Android en todos los dispositivos? ¿Se incluye el complemento Watchdog (Cordova) como parte de la APK? {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

Un organismo de control de Android multiplataforma que utiliza API de Android puras ya forma parte del paquete. No se necesita ningún software adicional, pero en función del dispositivo que utilice, es posible que tenga que renunciar al apk para obtener privilegios del sistema para un ciclo de alimentación completo (PowerManager api). Si no se renuncia usando las claves del fabricante, se cerrará y reiniciará la aplicación pero no el ciclo de alimentación.

Para obtener más información sobre cómo implementar el Reproductor de Android, consulte [**Implementación de dicho Reproductor **](implementing-android-player.md).

### ¿Qué herramientas (software) de supervisión y alerta remota de terceros recomienda Adobe/AMS para supervisar cada dispositivo?  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

Según lo que desee del monitoreo y las alertas, una nueva función del servicio de notificaciones de pantallas de AEM le notifica si un dispositivo no ha pasado un rato. Las herramientas de terceros dependerán del sistema operativo (SO), sus capacidades y las necesidades específicas del cliente.

Para obtener más información sobre dónde puede supervisar la actividad de los dispositivos, consulte el servicio [**de notificaciones de pantallas de **](screens-notifications-service.md)AEM.

### Con la topología del dispositivo de publicación con Smart Sync, ¿los dispositivos siguen conectados directamente a la instancia de creación para las funciones de instantáneas y latidos de corazón?

No, los dispositivos no están conectados directamente al autor. Informan a las instancias de publicación y el autor sondeará las instancias de publicación para ver si hay actualizaciones.

## Reproductor de AEM Screens {#aem-screens-player}

### ¿Cómo instalar el reproductor ChromeOS como complemento Chrome Browser? {#how-to-install-chromeos-player-as-chrome-browser-plugin}

El reproductor ChromeOS se puede instalar como complemento Chrome Browser en el modo de desarrollador sin necesidad de un dispositivo de reproducción Chrome. Para la instalación, siga los pasos a continuación:

1. Haga clic [aquí](https://download.macromedia.com/screens/) para descargar la versión más reciente de Chrome Player.
1. Descomprima y guárdelo en el disco.
1. Abra el navegador Chrome y haga clic en el menú de 3 puntos y seleccione **Más herramientas** —> **Extensiones** en la esquina superior derecha o navegue directamente a ***chrome://extensions***.
1. Encienda el modo **de** desarrollador desde la esquina superior derecha.
1. Haga clic en **Cargar sin empaquetar **desde la esquina superior izquierda y cargue el reproductor Chrome sin comprimir.
1. Compruebe **AEM Screens Chrome Player** si está disponible en la lista de extensiones.
1. Abra una nueva ficha y haga clic en el icono **Aplicaciones** en la esquina superior izquierda o navegue directamente a ***chrome://apps***.
1. Haga clic en **AEM Screens** Plugin para iniciar Chrome Player. De forma predeterminada, el reproductor se inicia en modo de pantalla completa. Pulse **esc** para salir del modo de pantalla completa.

### ¿Cómo solucionar problemas si el reproductor de Pantallas no puede autenticarse mediante la instancia de publicación con un controlador de error personalizado? {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

Cuando se inicia el reproductor de AEM Screens, realiza una solicitud a ***/content/screens/svc.ping.json***, cuando el reproductor recibe un error 404. El reproductor inicia una solicitud de autenticación para autenticarse con la instancia de publicación. Si hay un controlador de error personalizado en la instancia de publicación, asegúrese de devolver el código de estado 404 para un usuario anónimo en ***/content/screens/svc.ping.json***.

### ¿Cómo configurar la permanencia de la pantalla del dispositivo en un reproductor de Android?

Siga los pasos a continuación para activar Permanecer despierto en cualquier reproductor de Android:

1. Vaya a la configuración del reproductor de Android -> **Acerca de**
1. Puntee 7 veces en el número de compilación para habilitar las opciones de desarrollador en Configuración
1. Vaya a Opciones **de desarrollador**
1. Habilitar **Permanecer despierto**

### Si se envía una actualización desde AEM y el reproductor está sin conexión, ¿existe un mecanismo de reintento que compruebe si el dispositivo está de nuevo en línea para entregar el contenido actualizado? Además, ¿cuánto tiempo intenta hacerlo?

El siguiente ping desde el dispositivo que entra verá una hora de última modificación que es más reciente que la que tiene y descargará este contenido nuevo.
Intentará para siempre hasta que un ping tenga éxito.

### Uso de recursos {#using-assets}

### ¿Cómo usar vídeos en un canal de AEM Screens de más de 2 GB? {#how-to-use-videos-in-an-aem-screens-channel-larger-than-gb}

De forma predeterminada, la IU táctil de AEM Assets no permite cargar recursos que superen los 2 GB debido a un límite de tamaño de archivo en un canal de AEM Screens. Sin embargo, puede sobrescribir este límite si ingresa a CRXDE Lite y crea un nodo en el directorio /apps.

Para obtener información detallada sobre cómo configurar un límite de tamaño de archivo superior (por ejemplo, 30 GB) en el directorio */aplicaciones* , consulte *Configuración para cargar recursos de vídeo de más de 2 GB* en [Administración de recursos](/help/assets/managing-video-assets.md)de vídeo.

### Sugerencias generales para la resolución de problemas {#general-troubleshooting}

### ¿Cómo desactivar Livefyre para evitar un error en las pantallas A/P?

Para deshabilitar Livefyre para evitar errores de registro:

**Desactivación del paquete Livefyre:**

1. Ir a `http://<host>:<port>/system/console/bundles`
1. Busque el paquete de AEM Livefyre:  *com.adobe.cq.social.cq-social-livefyre*
1. Haga clic en **Detener**.

**Desactivación del sondeo de Livefyre:**

1. En CRXDE Lite, vaya a */etc/importing/polling/livefyre-poller/jcr:content*
1. Agregar un nuevo tipo habilitado para una propiedad Boolean
1. Establecer la propiedad **** enabled en **false**
