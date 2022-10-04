---
title: Configuración del programador de sincronización
seo-title: Configuring the synchronization scheduler
description: Obtenga información sobre cómo migrar y sincronizar recursos, configurar el programador de sincronización y utilizar carpetas para organizar los recursos.
seo-description: Learn how to migrate and sync assets, configure sync scheduler, and use folders to arrange assets.
uuid: a6445b45-9c1c-4483-a32e-453648c488c5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 2c8cea3c-8d8b-41d4-8ef9-a0ada8f86be6
role: Admin
exl-id: 7f1c4bac-accf-43e4-9439-89c5420d50f2
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 1%

---

# Configuración del programador de sincronización {#configuring-the-synchronization-scheduler}

De forma predeterminada, el programador de sincronización se ejecuta cada 3 minutos para sincronizar todos los recursos modificados y actualizados en el repositorio mediante LiveCycle Workbench 11. Las aplicaciones que contienen formularios y recursos son visibles en la interfaz de usuario de AEM Forms una vez finalizado el proceso de sincronización.

## Cambiar el intervalo del programador de sincronización {#change-interval-of-the-synchronization-scheduler}

Realice los siguientes pasos para cambiar el intervalo del programador de sincronización:

1. Inicie sesión en AEM Administrador de configuración. La dirección URL del Administrador de configuración es `https://[Server]:[Port]/lc/system/console/configMgr`

1. Busque y abra el **FormsManagerConfiguration** paquete.

1. Especifique un nuevo valor para la variable **Frecuencia del planificador de sincronización** .

   La unidad de la frecuencia es minutos. Por ejemplo, para configurar el planificador para que se ejecute después de cada 60 minutos, especifique 60.

## Sincronización de recursos {#synchronizing-assets}

Puede usar la variable **Sincronizar recursos del repositorio** para sincronizar manualmente los recursos. Realice los siguientes pasos para sincronizar manualmente los recursos:

1. Inicie sesión en AEM Forms. El URL predeterminado es `https://[Server]:[Port]/lc/aem/forms/`.

   ![Interfaz de usuario de AEM Forms](assets/aem_forms_ui.png)

   **Figura:** *Interfaz de usuario de AEM Forms*

1. Haga clic en el ![aem6forms_sync](assets/aem6forms_sync.png) en la barra de herramientas. Si no tiene ningún recurso en la última ruta configurada, seleccione el cuadro de diálogo como se muestra a continuación. Haga clic en **Inicio** para iniciar la sincronización.

   ![Cuadro de diálogo Sincronización](assets/migrate-and-syncronize.png)

   **Figura:** *Cuadro de diálogo Sincronización*

## Solución de problemas de sincronización {#troubleshooting-synchronization-error}

Puede crear nuevas aplicaciones en el diseñador de flujos de trabajo (Área de trabajo de LiveCycle).

Si la aplicación recién creada y una carpeta en /content/dam/formsanddocuments tienen un nombre idéntico, se produce el error &quot;*Ya existe un recurso con el mismo nombre que esta aplicación en el nivel raíz.*&quot; está registrado.

Para resolver el conflicto, cambie el nombre de la aplicación y sincronice manualmente los recursos.

![Conflictos en el cuadro de diálogo de sincronización de recursos](assets/sync-conflict.png)

**Figura:** *Conflictos en el cuadro de diálogo de sincronización de recursos*
