---
title: Instalador de parches de AEM Forms JEE
description: nulo
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---


# Instalador de parches de AEM Forms JEE {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Póngase en contacto con la asistencia](https://www.adobe.com/account/sign-in.supportportal.html) para obtener más información o para obtener el parche.

## Acerca del instalador de parches {#about-the-patch-installer}

El instalador de parches de Forms JEE de AEM 6.4 incluye todos los problemas solucionados para todos los componentes de AEM 6.4 Forms JEE disponibles hasta el lanzamiento de este parche. Consulte las últimas notas [de la versión del paquete de correcciones](cfp-release-notes.md) acumulativas para obtener una lista completa de los problemas solucionados.

## Requisitos previos para instalar el parche {#prerequisites-to-installing-the-patch}

* AEM 6.4 Forms

## Instalación y configuración del parche {#installing-and-configuring-the-patch}

1. Realice una copia de seguridad de la carpeta &lt;*AEM_forms_root*>/deploy. Es necesario si decide desinstalar la corrección rápida.
1. Detenga el servidor de aplicaciones.
1. Extraiga el archivo de archivo del instalador de parches en el disco duro.
1. En el directorio denominado según el sistema operativo que esté utilizando:

   * **Windows** Vaya al directorio correspondiente del medio de instalación o de la carpeta del disco duro donde copió el programa de instalación y haga clic con el doble en el 
`aemforms64_cfp_install.exe` archivo.

      * (Windows de 32 bits) `Windows\Disk1\InstData\VM`
      * (Windows de 64 bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux, Solaris y AIX** Navegue al directorio adecuado y, desde un símbolo del sistema, escriba 
`./aem64_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   Esto inicia un asistente de instalación que lo guiará a través de la instalación.

1. En el panel Introducción, haga clic en **[!UICONTROL Siguiente]**.
1. En la pantalla Elegir carpeta de instalación, compruebe que la ubicación predeterminada que se muestra es correcta para la instalación existente, o haga clic en **[!UICONTROL Examinar]** para seleccionar la carpeta alternativa donde se instalan AEM formularios y haga clic en **[!UICONTROL Siguiente]**.

1. Lea la información de Resumen de parches de Corrección rápida y haga clic en **[!UICONTROL Siguiente]**.
1. Lea la información del resumen previo a la instalación y haga clic en **[!UICONTROL Instalar]**.
1. Una vez finalizada la instalación, haga clic en **[!UICONTROL Siguiente]*** para aplicar las actualizaciones rápidas a los archivos instalados.
1. [Windows solamente] Realice uno de los siguientes pasos:

   * Anule la selección de la opción Administrador de configuración de Inicio antes de hacer clic en Finalizado. Ejecute Configuration Manager más adelante utilizando el `ConfigurationManager.bat` archivo ubicado en `[aem-forms root]\configurationManager\bin`. El uso `ConfigurationManager.bat` ayuda a evitar la actualización manual del nombre de axis.jar en archivos .lax
   * Anule la selección de la opción Administrador de configuración de Inicio antes de hacer clic en Finalizado. Antes de ejecutar el administrador de configuración mediante **ConfigurationManager.exe** o **ConfigurationManager_IPv6.exe**, navegue hasta *&lt;AEMForms_Install_Dir>\configurationManager\bin* y actualice **axis.jar** a **axis-1.4.1.1.jar** en los siguientes archivos:

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. (Solo basado en Unix) La casilla de verificación Administrador de configuración de Inicio está seleccionada de forma predeterminada. Haga clic en **[!UICONTROL Listo]** para ejecutar el Administrador de configuración.

   Para ejecutar Configuration Manager más adelante, anule la selección de la opción Administrador de configuración de Inicio antes de hacer clic en Finalizado. Puede inicio Configuration Manager más adelante utilizando la secuencia de comandos adecuada en el `[AEM_forms_root]/configurationManager/bin` directorio.

1. Según el servidor de aplicaciones, elija uno de los siguientes documentos y siga las instrucciones de la sección *Configuración e implementación de AEM formularios* .

   * [Instalación e implementación de formularios AEM para JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [Instalación e implementación de formularios AEM para WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [Instalación e implementación de formularios AEM para WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. (Solo JBoss) Después de instalar el parche y configurar el servidor, elimine los directorios tmp y de trabajo del servidor de aplicaciones JBoss.

## Configuraciones posteriores a la implementación {#post-deployment-configurations}

### Configuraciones SAML {#saml-configurations}

Si tiene configurada la autenticación SAML y tiene problemas con metadatos de IDP de gran tamaño, haga lo siguiente después de instalar el parche:

1. Establezca la siguiente propiedad del sistema en el servidor de aplicaciones:\
   `um.saml.enable.large.xml=true`

1. Reinicie el servidor.
1. Elimine los proveedores de autenticación de SAML existentes y agréguelos de nuevo para los dominios existentes, tal como se describe en la configuración de SAML.

## Módulos afectados {#impacted-modules}

* Servicios de documentos
* :Seguridad de los documentos
* Base JEE
* Servicio PDFG

[Comuníquese con la asistencia técnica](https://www.adobe.com/account/sign-in.supportportal.html)
