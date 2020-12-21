---
title: Configuración de entorno para la aplicación de AEM Forms
seo-title: Configuración de entorno para la aplicación de AEM Forms
description: Hardware, software y licencias para crear e implementar la aplicación de AEM Forms.
seo-description: Hardware, software y licencias para crear e implementar la aplicación de AEM Forms.
uuid: 0c8f5259-8e9f-45ce-ade4-e14f1a41c0de
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 72c3a451-fa57-4b12-8d25-fc2e6fa98adb
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# Configurar entorno para la aplicación de AEM Forms {#set-up-environment-for-aem-forms-app}

Necesita el hardware, el software y las licencias siguientes para crear e implementar la aplicación de AEM Forms:

## Para dispositivos Windows {#for-windows-devices}

* Microsoft Windows 8.1 o Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools para Apache Cordova

## Para dispositivos iOS {#for-ios-devices}

* Apple Mac basado en Intel que ejecuta Mac OS X 10.9.5 o superior
* iOS SDK 8.4 o superior
* Versión de Xcode: Xcode 6.4 para OS X o superior
* Membresía de iOS Developer Enterprise programa
* Certificado empresarial para distribuir aplicaciones internas de iOS
* Apple iPad con iOS 8.4 o posterior

## Para dispositivos Android {#for-android-devices}

* Kit de herramientas de desarrollo de Android (paquete ADT) que se puede descargar de [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Si el entorno está configurado en un sistema MAC, ADT debe estar instalado en la carpeta Aplicaciones.
* Si ADT está instalado en cualquier otra ubicación en MAC o si el entorno está configurado en un sistema Windows, la ruta del SDK de ADT debe actualizarse en el archivo `local.properties` que está disponible en la carpeta `src\android` del archivo de origen extraído `mobileworkspace-src.zip`. En este archivo, señale la variable `sdk.dir` a la ubicación del SDK de ADT en el escritorio.

>[!NOTE]
>
>El adobe-lc-mobilespace-src.zip contiene el SDK de PhoneGap 5.0. Asegúrese de que el SDK de PhoneGap no está preinstalado.
