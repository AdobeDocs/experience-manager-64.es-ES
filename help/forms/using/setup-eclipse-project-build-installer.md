---
title: Creación de la aplicación AEM Forms Android
seo-title: Creación de la aplicación AEM Forms Android
description: Pasos para configurar el proyecto de Android Studio y crear el archivo .apk para la aplicación de AEM Forms para Android
seo-description: Pasos para configurar el proyecto de Android Studio y crear el archivo .apk para la aplicación de AEM Forms para Android
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Creación de la aplicación AEM Forms Android {#build-the-aem-forms-android-app}

Realice los siguientes pasos en la secuencia recomendada para crear la aplicación de Android para AEM Forms.

1. [Descargar el paquete de código fuente de la aplicación de AEM Forms](#download-android-zip)
1. [Establecer las variables de entorno](#set-environment-variable-android)
1. [Compilación de una aplicación de AEM Forms estándar](#set-up-the-xcode-project)

## Descargar el paquete de código fuente de la aplicación de AEM Forms {#download-android-zip}

El paquete de código fuente de la aplicación de AEM Forms hace referencia al `adobe-lc-mobileworkspace-src-<version>.zip` archivo. Este archivo incluye el código fuente necesario para crear una aplicación de AEM Forms personalizada. El archivo se incluye en el `adobe-aemfd-forms-app-src-pkg-<version>.zip`paquete disponible en la distribución de software.

Realice los siguientes pasos para descargar el `adobe-aemfd-forms-app-src-pkg-<version>.zip` archivo:

1. Abra Distribución [de software](https://experience.adobe.com/downloads). Necesita un Adobe ID para iniciar sesión en la distribución de software.
1. Toque **[!UICONTROL Adobe Experience Manager]** disponible en el menú de encabezado.
1. En la sección **[!UICONTROL Filtros]** :
   1. Seleccione **[!UICONTROL Forms]** en la lista desplegable **[!UICONTROL Solución]** .
   2. Seleccione la versión y escriba el paquete. También puede utilizar la opción **[!UICONTROL Buscar descargas]** para filtrar los resultados.
1. Toque el nombre del paquete aplicable a su sistema operativo, seleccione **[!UICONTROL Aceptar los términos]** del EULA y toque **[!UICONTROL Descargar]**.
1. Abra el Administrador [de paquetes](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) y haga clic en **[!UICONTROL Cargar paquete]** para cargar el paquete.
1. Select the package and click **[!UICONTROL Install]**.
1. Para descargar el archivo de código fuente, abra **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileWorkspace-src-&lt;version>.zip** en el explorador. El archivo .zip de la aplicación de Android se descarga en el dispositivo.
1. Extraiga el contenido del archivo .zip en una carpeta del sistema de archivos local. Por ejemplo, *C:\Folder Structure\adobe-lc-mobileworkspace-src-2.4.20*

La siguiente imagen muestra la estructura de la `adobe-lc-mobileworkspace-src-<version>.zip\android`carpeta.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Establecer las variables de entorno {#set-environment-variable-android}

Defina las siguientes variables de entorno antes de iniciar el proceso de compilación para la aplicación de AEM Forms:

* Establezca la variable de entorno JAVA_HOME en la ubicación del software JDK en el sistema de archivos local. Por ejemplo, C:\Program Files\Java\jdk1.8.0_181
* Establezca la variable de entorno del `ANDROID_SDK_ROOT` sistema en la ubicación del SDK para Android. Por ejemplo, C:\Users\username\AppData\Local\Android\Sdk
* Configure la variable de entorno del `Path` sistema para que incluya las ubicaciones de carpetas de herramientas y herramientas de la plataforma para Android. Por ejemplo, C:\Users\username\AppData\Local\Android\Sdk\platform-tools and C:\Users\username\AppData\Local\Android\Sdk\tools.

## Compilación de una aplicación de AEM Forms estándar {#set-up-the-xcode-project}

Una vez que haya guardado el archivo adobe-lc-mobileWorkspace-src-&lt;version>.zip en el sistema de archivos local y haya establecido las variables de entorno, cree una aplicación de AEM Forms Android estándar con cualquiera de las siguientes opciones:

* [Creación de una aplicación de AEM Forms con Android Studio](#using-android-studio)
* [Generar archivo .apk con Android Studio](#generate-apk-android-studio)

### Creación de una aplicación de AEM Forms con Android Studio {#using-android-studio}

Siga estos pasos para crear una aplicación de AEM Forms con Android Studio:

1. Inicie la aplicación Android Studio en su equipo.
1. Haga clic en **Abrir un proyecto** existente de Android Studio. Si el cuadro de diálogo para abrir un proyecto existente no aparece automáticamente, seleccione **Archivo** > **Abrir**.
1. Vaya a *adobe-lc-mobileWorkspace-src-&lt;version>.zip/android* en el sistema de archivos local y haga clic en **Aceptar**.

   La opción **androide** se muestra en el panel izquierdo.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Seleccione **android** en el panel izquierdo y haga clic en **Ejecutar** > **Ejecutar &#39;android&#39;**.
1. Seleccione el dispositivo Android en la sección Dispositivos conectados del cuadro de diálogo Seleccionar Destinatario de implementación y haga clic en Aceptar.

   Una vez creado el entorno de desarrollo correctamente, ahora puede aplicar personalizaciones en la aplicación. Utilice los siguientes artículos para personalizar la aplicación:

   * [Personalización de promoción de la marca](/help/forms/using/branding-customization.md)
   * [Personalización de temas](/help/forms/using/theme-customization.md)
   * [Personalización de gestos](/help/forms/using/gesture-customization.md)

   Después de aplicar las personalizaciones adecuadas a la aplicación, puede generar el archivo .apk para su distribución.

### Generar archivo .apk con Android Studio {#generate-apk-android-studio}

Realice los siguientes pasos para generar el archivo .apk mediante Android Studio:

1. Inicie la aplicación Android Studio en su equipo.
1. Seleccione **Abrir un proyecto** existente de Android Studio. Si el cuadro de diálogo para abrir un proyecto existente no aparece automáticamente, seleccione **Archivo** > **Abrir**.
1. Vaya a *adobe-lc-mobileWorkspace-src-&lt;version>.zip/android* en el sistema de archivos local y haga clic en **Aceptar**.

   La opción androide se muestra en el panel izquierdo.

1. Seleccione **Generar** > **Generar APK** para generar el archivo .apk.

   Si lo desea, seleccione **Generar** > **Generar APK** firmado para generar una versión [](https://developer.android.com/studio/publish/app-signing) firmada del archivo .apk.

## Uso de Android Debug Bridge {#build-android-debug-bridge}

Una vez generado el archivo .apk, ejecute el siguiente comando para instalar la aplicación en un dispositivo Android mediante el puente [de depuración de](https://developer.android.com/tools/help/adb.html)Android.

**Usuarios de Windows:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Usuarios de MAC:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
