---
title: Configurar la contraseña de administrador en la instalación
seo-title: Configure the Admin Password on Installation
description: Aprenda a cambiar la contraseña de administrador en AEM instalación.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: 6dd289ee-13fd-46be-82cd-aa69852397c9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 2%

---

# Configurar la contraseña de administrador en la instalación{#configure-the-admin-password-on-installation}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Desde la versión 6.3, AEM permite establecer la contraseña de administrador mediante la línea de comandos al instalar una nueva instancia.

Con versiones anteriores de AEM, la contraseña de la cuenta de administrador, junto con la contraseña de varias otras consolas, tuvieron que cambiarse después de la instalación.

Esta función añade la posibilidad de configurar una nueva contraseña de administrador para el repositorio y el motor Servlet durante la instalación de una instancia de AEM, eliminando así la necesidad de hacerlo manualmente posteriormente.

>[!CAUTION]
>
>Tenga en cuenta que la función no cubre la Consola Felix, para la cual la contraseña debe cambiarse manualmente. Para obtener más información, consulte la [Sección Lista de comprobación de seguridad](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## ¿Cómo Lo Utilizo? {#how-do-i-use-it}

Esta función se déclencheur automáticamente si elige instalar AEM a través de la línea de comandos, en lugar de hacer doble clic en el JAR desde un explorador del sistema de archivos.

El sintaxis general para ejecutar una instancia de AEM desde la línea de comandos es:

```shell
java -jar aem6.3.jar
```

Al ejecutar la instancia desde la línea de comandos, se le presentará la opción de cambiar la contraseña de administrador durante el proceso de instalación:

![chlimage_1-116](assets/chlimage_1-116.png)

>[!NOTE]
>
>El mensaje para cambiar la contraseña de administrador solo aparecerá durante la instalación de una nueva instancia de AEM.

## Uso del indicador -nointeractivo {#using-the-nointeractive-flag}

También puede especificar la contraseña de un archivo de propiedades. Esto se hace usando la variable `-nointeractive` indicador combinado con la variable `-Dadmin.password.file` propiedad del sistema.

A continuación se muestra un ejemplo:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

La contraseña dentro de la variable `passwordfile.properties` debe tener el siguiente formato:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Si simplemente usa la variable `-nointeractive` sin el parámetro `-Dadmin.password.file` propiedad del sistema, AEM usará la contraseña de administrador predeterminada sin pedirle que la cambie, básicamente replicando el comportamiento de versiones anteriores. Este modo no interactivo se puede utilizar para instalaciones automatizadas utilizando la línea de comandos en una secuencia de comandos de instalación.
