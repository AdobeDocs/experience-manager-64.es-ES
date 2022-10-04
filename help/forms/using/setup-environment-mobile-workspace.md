---
title: Configuración del entorno para la aplicación AEM Forms
seo-title: Set up environment for AEM Forms app
description: Hardware, software y licencias para crear e implementar la aplicación AEM Forms.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
exl-id: 5c60d1a6-a4a2-4131-81e6-e39a5ab07dcf
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Configuración del entorno para la aplicación AEM Forms {#set-up-environment-for-aem-forms-app}

Para crear e implementar la aplicación de AEM Forms necesita el hardware, el software y las licencias siguientes:

## Para dispositivos Windows {#for-windows-devices}

* Microsoft Windows 8.1 o Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools para Apache Cordova

## Para dispositivos iOS {#for-ios-devices}

* Apple Mac basado en Intel que ejecuta Mac OS X 10.9.5 o superior
* iOS SDK 8.4 o superior
* Versión de Xcode: Xcode 6.4 para OS X o superior
* Pertenencia al programa iOS Developer Enterprise
* Certificado empresarial para la distribución de aplicaciones de iOS internas
* Apple iPad con iOS 8.4 o posterior

## Para dispositivos Android {#for-android-devices}

* Kit de herramientas de desarrollo de Android (paquete ADT) que se puede descargar de [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Si el entorno está configurado en un sistema MAC, el ADT debe instalarse en la carpeta Applications .
* Si el ADT está instalado en cualquier otra ubicación de MAC, o si el entorno está configurado en un sistema Windows, la ruta del SDK de ADT debe actualizarse en `local.properties` que está disponible en `src\android` carpeta en el archivo de origen extraído `mobileworkspace-src.zip`. En este archivo, señale la variable `sdk.dir` a la ubicación del SDK de ADT en su escritorio.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip contiene PhoneGap SDK 5.0. Asegúrese de que el SDK de PhoneGap no esté preinstalado.
