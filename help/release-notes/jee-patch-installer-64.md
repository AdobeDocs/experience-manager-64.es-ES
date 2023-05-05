---
title: Instalador de parches JEE de AEM Forms
description: Instalador de parches JEE de AEM Forms
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
exl-id: ce5300ce-03f4-4e7b-bc5b-01a9968ebe06
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 24%

---

# Instalador de parches JEE de AEM Forms {#aem-forms-jee-patch-installer}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>[Contacto con el servicio de asistencia](https://www.adobe.com/account/sign-in.supportportal.html) para obtener más información o para obtener el parche.

## Acerca del instalador de parches {#about-the-patch-installer}

El instalador de parches AEM 6.4 Forms JEE incluye todos los problemas corregidos para todos los componentes de AEM 6.4 Forms JEE disponibles hasta el lanzamiento de este parche. Consulte las últimas  [Notas de la versión del paquete de correcciones acumulativas](cfp-release-notes.md) para obtener una lista completa de los problemas corregidos.

## Requisitos previos para instalar el parche {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Instalación y configuración del parche {#installing-and-configuring-the-patch}

1. Haga una copia de seguridad de &lt;*AEM_forms_root*>/implementar carpeta. Es necesaria si decide desinstalar la corrección rápida.
1. Detenga el servidor de aplicaciones.
1. Extraiga el archivo del programa de instalación del parche en el disco duro.
1. En el directorio denominado según el sistema operativo que esté utilizando:

   * **Windows**
Vaya al directorio correspondiente del medio de instalación o la carpeta del disco duro donde copió el instalador y haga doble clic en el botón 
`aemforms64_cfp_install.exe` archivo.

      * (Windows de 32 bits) `Windows\Disk1\InstData\VM`
      * (Windows de 64 bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris, AIX**
Vaya al directorio correspondiente y, desde el símbolo del sistema, escriba 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Esto inicia un asistente de instalación que le guiará a través de la instalación.

1. En el panel Introducción, haga clic en **[!UICONTROL Siguiente]**.
1. En la pantalla Elegir carpeta de instalación, verifique que la ubicación predeterminada que se muestra sea correcta para la instalación existente o haga clic en **[!UICONTROL Examinar]** para seleccionar la carpeta alternativa donde están instalados AEM formularios y haga clic en **[!UICONTROL Siguiente]**.

1. Lea la información de resumen de parches de corrección rápida y haga clic en **[!UICONTROL Siguiente]**.
1. Lea la información del resumen previo a la instalación y haga clic en **[!UICONTROL Instalar]**.
1. Cuando finalice la instalación, haga clic en **[!UICONTROL Siguiente]**para aplicar las actualizaciones de correcciones rápidas a los archivos instalados.
1. [Solo Windows] Realice uno de los siguientes pasos:

   * Anule la selección de la opción Iniciar administrador de configuración antes de hacer clic en Listo. Ejecute el Administrador de configuración más tarde utilizando el `ConfigurationManager.bat` archivo ubicado en `[aem-forms root]\configurationManager\bin`. Uso `ConfigurationManager.bat` ayuda a evitar la actualización manual del nombre de axis.jar en archivos .lax
   * Anule la selección de la opción Iniciar administrador de configuración antes de hacer clic en Listo. Antes de ejecutar el administrador de configuración mediante **ConfigurationManager.exe** o **ConfigurationManager_IPv6.exe**, vaya a *&lt;aemforms_install_dir>\configurationManager\bin* directorio y actualizar **axis.jar** a **axis-1.4.1.1.jar** en los siguientes archivos:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Solo basado en Unix) La casilla de verificación Iniciar Administrador de configuración está seleccionada de forma predeterminada. Haga clic en **[!UICONTROL Listo]** para ejecutar el Administrador de configuración.

   Para ejecutar el Administrador de configuración más adelante, anule la selección de la opción Inicio del Administrador de configuración antes de hacer clic en Listo. Puede iniciar Configuration Manager más adelante utilizando la secuencia de comandos adecuada en la `[AEM_forms_root]/configurationManager/bin` directorio.

1. Según el servidor de aplicaciones, elija uno de los siguientes documentos y siga las instrucciones de la sección *Configuración e implementación de AEM formularios* para obtener más información.

   * [Instalación e implementación de formularios AEM para JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Instalación e implementación de AEM formularios para WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Instalación e implementación de formularios AEM para WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (Solo JBoss) Después de instalar el parche y configurar el servidor, elimine los directorios tmp y de trabajo del servidor de aplicaciones JBoss.

## Configuraciones posteriores a la implementación {#post-deployment-configurations}

### Configuraciones SAML {#saml-configurations}

Si tenía configurada la autenticación SAML y tiene problemas con los metadatos de IDP grandes, haga lo siguiente después de instalar el parche:

1. Establezca la siguiente propiedad del sistema en el servidor de aplicaciones:\
   `um.saml.enable.large.xml=true`

1. Reiniciar el servidor.
1. Elimine los proveedores de autenticación SAML existentes y agréguelos de nuevo para los dominios existentes, tal como se describe en la configuración de SAML.

## Módulos afectados {#impacted-modules}

* Servicios de documentos
* Seguridad de los documentos
* Base JEE
* Servicio PDFG

[Contacto con el servicio de asistencia](https://www.adobe.com/account/sign-in.supportportal.html)
