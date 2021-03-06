---
title: Distribuir aplicación de AEM Forms
seo-title: Distribuir aplicación de AEM Forms
description: Utilice Mobile Device Management (MDM) para la implementación a gran escala de aplicaciones en dispositivos móviles.
seo-description: Utilice Mobile Device Management (MDM) para la implementación a gran escala de aplicaciones en dispositivos móviles.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Distribuir la aplicación de AEM Forms {#distribute-aem-forms-app}

La administración de dispositivos móviles (MDM) permite la implementación a gran escala de aplicaciones en dispositivos móviles.

>[!NOTE]
>
>Esta distribución solo se aplica a dispositivos iOS y Android.

## Características principales generalmente proporcionadas por las soluciones MDM: {#main-features-generally-provided-by-mdm-solutions}

* Habilitar la inscripción de dispositivos en el entorno empresarial
* Permitir la configuración y actualización de la configuración del dispositivo
* Aplicar el cumplimiento de la seguridad.
* Acceso móvil seguro a los recursos corporativos

Una solución MDM junto con la administración de aplicaciones móviles le permite administrar aplicaciones internas, públicas y adquiridas en todos los dispositivos móviles de su empresa.

El administrador de MDM puede cargar archivos ipa y apk al servidor de MDM y controlar a los usuarios que pueden acceder a los archivos ipa o apk. El administrador también puede controlar la configuración de perfil correspondiente a cada aplicación.

## Configuración de perfil que afecta a la aplicación de AEM Forms {#profile-settings-affecting-the-aem-forms-app-br}

La siguiente configuración de Perfil del dispositivo afectará al funcionamiento de la aplicación de AEM Forms en el dispositivo:

* **Permitir el uso de la** cámara en la sección  **de** funcionalidad del dispositivo

Si deshabilita **Permitir el uso de cámara**, la función de cámara de la [anotación de fotografía](/help/forms/using/add-attachments.md) no funcionará. Debe activar esta opción para utilizar la cámara en la aplicación.

* **Requerir clave en el** dispositivo en la sección Directivas de contraseñas

Para habilitar el **cifrado de datos de la aplicación**, se recomienda habilitar el **código de acceso** en el dispositivo. Si el código de acceso no está establecido en el dispositivo, los datos de la aplicación almacenados en el dispositivo no se cifran.
