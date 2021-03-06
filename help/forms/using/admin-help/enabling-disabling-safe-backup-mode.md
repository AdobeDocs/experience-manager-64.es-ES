---
title: Activación y desactivación del modo de respaldo seguro
seo-title: Activación y desactivación del modo de respaldo seguro
description: En la página Configuración de copia de seguridad, puede utilizar formularios AEM en modo de copia de seguridad segura para que pueda realizar una copia de seguridad fiable de la base de datos y del directorio de Almacenamiento de Documento global (GDS). Obtenga información sobre cómo habilitar y deshabilitar el modo de copia de seguridad segura.
seo-description: En la página Configuración de copia de seguridad, puede utilizar formularios AEM en modo de copia de seguridad segura para que pueda realizar una copia de seguridad fiable de la base de datos y del directorio de Almacenamiento de Documento global (GDS). Obtenga información sobre cómo habilitar y deshabilitar el modo de copia de seguridad segura.
uuid: 2fdeaeaf-e969-40a4-8aee-1f2b627d3942
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9fda71e4-78a1-4581-9d02-bf06a75c3bcb
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Activación y desactivación del modo de backup seguro {#enabling-and-disabling-safe-backup-mode}

En la página Configuración de copia de seguridad, puede utilizar formularios AEM en modo de copia de seguridad segura para que pueda realizar una copia de seguridad fiable de la base de datos y del directorio de Almacenamiento de Documento global (GDS).

Aunque AEM formularios se encuentran en modo de copia de seguridad segura, funcionan normalmente, excepto que no eliminan activamente archivos del directorio GDS.

>[!NOTE]
>
>La configuración de esta opción no realiza una copia de seguridad del sistema; prepara el sistema para realizar copias de seguridad.

## Habilitar el modo de backup seguro {#enable-safe-backup-mode}

1. En la consola de administración, haga clic en Configuración > Configuración de sistemas principales > Configuración de copia de seguridad.
1. En la página Ajustes de copia de seguridad, seleccione Operar en modo de copia de seguridad segura y haga clic en Aceptar.

>[!NOTE]
>
>Si el sistema ya se está ejecutando en modo de copia de seguridad segura, no se creará una nueva reserva al hacer clic en Aceptar.

## Deshabilitar el modo de backup seguro {#disable-safe-backup-mode}

1. En la consola de administración, haga clic en Configuración > Configuración de sistemas principales > Configuración de copia de seguridad.
1. En la página Ajustes de copia de seguridad, anule la selección de Operar en modo de copia de seguridad segura y haga clic en Aceptar.

