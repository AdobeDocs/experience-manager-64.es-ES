---
title: Implementación de Windows 10 Player
seo-title: Implementación de Windows 10 Player
description: 'Siga esta página para conocer la configuración del reproductor de Windows 10 de AEM Screens. '
seo-description: 'Siga esta página para conocer la configuración del reproductor de Windows 10 de AEM Screens. '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# Implementación de Windows 10 Player{#implementing-windows-player}

En esta sección se describe la configuración del reproductor de Windows 10 de AEM Screens. Proporciona información sobre el archivo de configuración y las opciones disponibles, así como recomendaciones sobre las opciones que se utilizarán para el desarrollo y la prueba.

## Instalación de Windows Player {#installing-windows-player}

Para implementar Windows Player para AEM Screens, instale Windows Player para AEM Screens.

Visite la página de descargas [**de **](https://download.macromedia.com/screens/)AEM 6.4 Player.

### Método ad-hoc {#ad-hoc-method}

El método ad-hoc para instalar el último Reproductor de Windows (*.exe*), visite la página de descargas [**del Reproductor de **](https://download.macromedia.com/screens/)AEM 6.4.

Una vez descargada la aplicación, siga los pasos del reproductor para completar la instalación ad-hoc:

1. Presione largo tiempo en la esquina superior izquierda para abrir el panel de administración.
1. Vaya a **Configuración** en el menú de acción de la izquierda, introduzca la ubicación (dirección) de la instancia de AEM a la que desea conectarse y haga clic en **Guardar**.

1. Haga clic en el vínculo **Registro** desde el menú de acción de la izquierda para completar el proceso de registro del dispositivo.

### Registro de varios reproductores de Windows 10 con una configuración {#registering-multiple-windows-players-with-one-configuration}

Una vez que haya instalado el reproductor de Windows, puede registrar varios reproductores con una configuración.

>[!NOTE]
>
>**Registro masivo de Windows Player**
>
>Al implementar el reproductor de Windows no es necesario configurar manualmente cada reproductor. En su lugar, puede actualizar el archivo JSON de configuración una vez que se haya probado y esté listo para la implementación.
>
>La configuración se asegurará de que todos los reproductores que hagan ping al mismo servidor proporcionado en el archivo de configuración. Aún debe registrar manualmente cada reproductor.

Siga los pasos a continuación para configurar el Reproductor de Windows 10:

1. Instale Windows Player.
1. Busque el archivo de configuración en ***%appdata%\com.adobe.aem.screen.player\config.json***.
1. Actualice el JSON de configuración con la información siguiente y copie la misma carpeta en todos los sistemas en los que reside el reproductor.

### Atributos de directiva {#policy-attributes}

La siguiente tabla resume los atributos de política con un JSON de política de ejemplo para referencia:

| **Nombre de directiva** | **Función** |
|---|---|
| server | Dirección URL del servidor de Adobe Experience Manager (AEM). |
| resolución | La resolución del dispositivo. |
| RestartSchedule | La programación para reiniciar el reproductor. |
| enableAdminUI | Habilite la interfaz de usuario del administrador para configurar el dispositivo en el sitio. Establezca en false una vez que esté completamente configurado y en producción. |
| enableOSD | Habilite la interfaz de usuario del conmutador de canal para que los usuarios cambien de canal en el dispositivo. Considere establecer en false una vez que esté completamente configurado y en producción. |
| enableActivityUI | Active esta opción para mostrar el progreso de actividades como la descarga y la sincronización. Habilite la solución de problemas y deshabilite una vez que esté completamente configurado y en producción. |

#### Ejemplo de archivo JSON de política {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

