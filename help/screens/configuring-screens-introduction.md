---
title: Configuración e implementación de pantallas AEM
seo-title: Configurar e implementar Screens
description: El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows. En esta página se describe la configuración y la implementación de AEM Screens y también se resumen las directrices de selección h/w para el dispositivo de reproducción.
seo-description: El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows. En esta página se describe la configuración y la implementación de AEM Screens y también se resumen las directrices de selección h/w para el dispositivo de reproducción.
uuid: 8ee5311f-b377-4035-af77-e1391a840745
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: a94d0891-d75f-482e-8d2a-e0cbf953a9de
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Configuring and Deploying AEM Screens{#configuring-and-deploying-aem-screens}

Esta página muestra cómo instalar y configurar los reproductores de Pantallas en sus dispositivos y cubre los siguientes temas:

* Instalación de AEM Screens Player
* Configuración del servidor
* Directrices de selección de hardware para el dispositivo reproductor
* Pasos siguientes

## Instalación de AEM Screens Player {#installing-aem-screens-player}

El reproductor de AEM Screens está disponible para Android, Chrome OS, iOS y Windows.

Para descargar **AEM Screens Player**, visite la página de descargas [**de **](https://download.macromedia.com/screens/)AEM 6.4 Player.

>[!NOTE]
>
>Una vez descargado el último reproductor (*.exe*), siga los pasos del reproductor para completar la instalación ad-hoc:
>
>1. Presione largo tiempo en la esquina superior izquierda para abrir el panel de administración.
>1. Vaya a **Configuración** en el menú de acción de la izquierda, introduzca la dirección de ubicación de la instancia de AEM en el **servidor** y haga clic en **Guardar**.
   >
   >
1. Haga clic en el vínculo **Registro** desde el menú de acción de la izquierda y en los pasos siguientes para completar el proceso de registro del dispositivo.
>



### Additional Resources {#additional-resources}

Consulte los siguientes temas para obtener información detallada:

* Para descargar Android Player, visite **Google Play**. Para obtener más información sobre la implementación de Android Watchdog, consulte **[Implementación de un reproductor](implementing-android-player.md)**de Android.

* Para implementar Chrome OS Player, consulte la Consola [de administración de](implementing-chrome-os-player.md) Chrome para obtener más información.
* Para configurar AEM Screens Windows Player, consulte [Implementación de Windows Player](implementing-windows-player.md).

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>El reproductor de AEM Screens no utiliza el distintivo de falsificación de solicitudes entre sitios (CSRF). Por lo tanto, para configurar y que el servidor AEM esté listo para usar en AEM Screens, omita el filtro de referente permitiendo que los referentes estén vacíos.

### Requisitos previos {#prerequisites}

Los siguientes puntos clave ayudan a configurar y a que el servidor AEM esté listo para su uso en AEM Screens:

#### Permitir solicitudes de referente vacías {#allow-empty-referrer-requests}

Siga los pasos a continuación para habilitar el filtro de referente de sling de Apache que permite vaciar. Esto es necesario para el funcionamiento óptimo del protocolo de control entre AEM Screens Player y el servidor de AEM Screens.

1. Vaya a **Configuración de la consola web de Adobe Experience Manager **mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

   ![screen_shot_2019-02-11at15405pm](assets/screen_shot_2019-02-11at15405pm.png)

1. **Se abre la configuración** de la consola web de Adobe Experience Manager. Busque el referente sling.

   Para buscar la propiedad del referente sling, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

   ![screen_shot_2019-02-11at15629pm](assets/screen_shot_2019-02-11at15629pm.png)

1. Marque la opción **Permitir vacío** , como se muestra en la figura siguiente.

   ![screen_shot_2018-12-04at22911pm](assets/screen_shot_2018-12-04at22911pm.png)

1. Haga clic en **Guardar** para habilitar el filtro de referente de sling de Apache que permite vaciar.

#### Activar IU táctil para AEM Screens {#enable-touch-ui-for-aem-screens}

AEM Screens requiere la IU TÁCTIL y no funcionará con la IU CLÁSICA de Adobe Experience Manager (AEM).

1. Vaya a *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Asegúrese de que el modo **predeterminado de la IU de creación esté establecido en** TOUCH ****, como se muestra en la figura siguiente

También puede realizar la misma configuración con*&lt;yourAuthorInstance> *->* herramientas (icono de martillo)* -> **Operaciones** ->Consola **** web y buscar el servicio **de modo de IU de creación de** WCM.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Siempre puede habilitar la IU clásica para usuarios específicos mediante las preferencias de usuario.

#### AEM en modo de ejecución NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

La ejecución de AEM en producción utiliza el modo de ejecución **NOSAMPLECONTENT** . Elimine el encabezado *X-Frame-Options=SAMEORIGIN* (en la sección de encabezado de respuesta adicional) de

[http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet](http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet).

Esto es necesario para que AEM Screens Player pueda reproducir los canales en línea.

#### Restricciones de contraseña {#password-restrictions}

Con los últimos cambios en ***DeviceServiceImpl***, no es necesario eliminar las restricciones de contraseña.

Puede configurar ***DeviceServiceImpl*** desde el vínculo siguiente para habilitar la restricción de contraseña al crear la contraseña para los usuarios de dispositivos de pantalla:

[http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService](http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService)

Siga los pasos a continuación para configurar ***DeviceServiceImpl***:

1. Vaya a Configuración **de la consola web de** Adobe Experience Manager mediante la instancia de AEM —> icono de martillo —> **Operaciones** —> Consola **** web.

1. **Se abre la configuración** de la consola web de Adobe Experience Manager. Busque deviceService. Para buscar la propiedad, pulse **Comando+F** para **Mac** y **Control+F** para **Windows**.

![screen_shot_2019-02-21at24951pm](assets/screen_shot_2019-02-21at24951pm.png)

#### Dispatcher Configuration {#dispatcher-configuration}

Para **Dispatcher, **agregar encabezados de cliente a .any. Permitir los siguientes encabezados a través de:

* &quot;X-Requested-With&quot;
* &quot;X-SET-HEARTBEAT&quot;
* &quot;X-REQUEST-COMMAND&quot;

#### Codificación de Java {#java-encoding}

Establezca la codificación ****** Java en Unicode. Por ejemplo, *Dfile.encoding=Cp1252* no funcionará.

>[!NOTE]
>
>**Recomendación:**
>
>Se recomienda utilizar HTTPS para AEM Screens Server en el uso de producción.

## Directrices de selección de hardware para el dispositivo reproductor {#hardware-selection-guidelines-for-player-device}

La siguiente sección proporciona las directrices de selección de hardware para un proyecto de pantallas:

* Utilice siempre componentes de ***categoría comercial*** o ***industrial*** tanto para el reproductor de PC como para el panel de visualización o el proyector.

* Siempre interactúes con proveedores que sirven al mercado de la publicidad dinámica.
* Consideremos siempre factores ambientales como la temperatura ambiente y la humedad relativa.
* Revise siempre los requisitos de alimentación y el acondicionamiento de alimentación.
* Revise cuidadosamente las necesidades de rendimiento y los puertos de E/S requeridos para la aplicación.

La siguiente tabla resume las configuraciones de hardware con casos de uso típicos de un proyecto de AEM Screens:

<table> 
 <tbody> 
  <tr> 
   <td>Configuración del reproductor</td> 
   <td>Procesador</td> 
   <td>Memoria</td> 
   <td>SSD de almacenamiento</td> 
   <td>GPU</td> 
   <td>Mostrar</td> 
   <td>E/S</td> 
   <td>Casos de uso habituales</td> 
  </tr> 
  <tr> 
   <td>Básico</td> 
   <td>Procesador Intel® Atom de doble núcleo, i3 o de cuatro núcleos básico</td> 
   <td><p>4 GB de memoria</p> <p>2 MB de caché</p> </td> 
   <td><p>・ChromeOS 32 GB</p> <p>・Windows 128 GB</p> </td> 
   <td>OnBoard</td> 
   <td>1920x1080</td> 
   <td>DVI, <br /> Ethernet/inalámbrico,<br /> 2 x USB</td> 
   <td> 
    <ul> 
     <li>Bucle estándar de pantalla completa <br /> </li> 
     <li>Partición de día</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Estándar</td> 
   <td>Procesador Intel® Core i5 de cuatro núcleos</td> 
   <td><p>8 GB de memoria</p> <p>4 MB de caché</p> </td> 
   <td>128 GBB</td> 
   <td>OnBoard</td> 
   <td>3840 x 2160 (4K)</td> 
   <td>DVI, HDMI<br /> Ethernet/inalámbrico,<br /> 2 x USB</td> 
   <td> 
    <ul> 
     <li>Contenido dinámico de origen único </li> 
     <li>Interactivo simple</li> 
     <li> 1-3 diseños de zona</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Avanzado </td> 
   <td>Cuatro núcleos con hipersubprocesos, procesador Intel® Core i7</td> 
   <td><p>16 GB de memoria</p> <p>8 MB de caché</p> </td> 
   <td>256 GB</td> 
   <td>GPU discreta</td> 
   <td>3840 x 2160 (4K)</td> 
   <td>DVI, HDMI<br /> Ethernet / inalámbrico,<br /> 4 x USB</td> 
   <td> 
    <ul> 
     <li>4 o más zonas de contenido, reproducción de vídeo simultáneo</li> 
     <li> Interactivo de varias páginas</li> 
     <li>Desencadenadores de datos de varias fuentes</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Pasos siguientes {#the-next-steps}

Una vez que haya instalado y configurado el reproductor de Screens, siga los temas siguientes para empezar:

1. [Crear y gestionar proyecto de pantallas](creating-a-screens-project.md)
1. [Crear y administrar canales](managing-channels.md)
1. [Crear y administrar ubicaciones](managing-locations.md)
1. [Crear y administrar pantallas](managing-displays.md)
1. [Asignar canales](channel-assignment.md)
1. [Administrar dispositivos](managing-devices.md)
1. [Registro de un dispositivo](device-registration.md)
1. [Asignar dispositivos](managing-devices.md)
1. [Crear y administrar programaciones](managing-schedules.md)
1. [Reproductor de AEM Screens](working-with-screens-player.md)
1. [Resolución de problemas del centro de control de dispositivos](monitoring-screens.md)

