---
title: Distribuir la aplicación de AEM Forms
seo-title: Distribute AEM Forms app
description: Utilice la administración de dispositivos móviles (MDM) para implementar a gran escala aplicaciones en dispositivos móviles.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: c1bf0a0e-70f7-41dd-8b1a-c114d89a265b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 89%

---

# Distribuir la aplicación de AEM Forms {#distribute-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La administración de dispositivos móviles (MDM) permite implementar a gran escala aplicaciones en dispositivos móviles.

>[!NOTE]
>
>Esta distribución solo es aplicable a dispositivos iOS y Android.

## Características principales que generalmente proporcionan las soluciones de MDM: {#main-features-generally-provided-by-mdm-solutions}

* Habilitar la inscripción de dispositivos en su entorno empresarial
* Permitir la configuración y actualización de la configuración del dispositivo
* Aplicar el cumplimiento de seguridad.
* Acceso móvil seguro a los recursos corporativos

Una solución de MDM junto con la administración de aplicaciones móviles, le permite administrar aplicaciones internas, públicas y compradas en todos los dispositivos móviles de su empresa.

El administrador de MDM puede cargar archivos ipa y apk al servidor de MDM y controlar a los usuarios que pueden acceder a los archivos ipa o apk. El administrador también puede controlar la configuración del perfil correspondiente a cada aplicación.

## Configuración del perfil que afecta a la aplicación de AEM Forms {#profile-settings-affecting-the-aem-forms-app-br}

La siguiente configuración del perfil de su dispositivo afectará al funcionamiento de la aplicación de AEM Forms en su dispositivo:

* **Permitir el uso de la cámara** en la sección **Funcionalidad del dispositivo**

Si deshabilita **Permitir el uso de la cámara**, la función de la cámara de la [Anotación fotográfica](/help/forms/using/add-attachments.md) no funcionará. Debe habilitar esta opción para utilizar la cámara en la aplicación.

* **Requerir contraseña en el dispositivo** en la sección directivas de contraseñas

Para habilitar el **cifrado de datos de la aplicación**, se recomienda habilitar la **contraseña** en su dispositivo. Si la contraseña no está establecida en el dispositivo, los datos de la aplicación almacenados en el dispositivo no se cifrarán.
