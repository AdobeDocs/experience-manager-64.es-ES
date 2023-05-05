---
title: Compatibilidad con cifrado para propiedades de configuración
seo-title: Encryption Support for Configuration Properties
description: Compatibilidad con cifrado para propiedades de configuración
seo-description: null
uuid: 26dc5e46-9332-4d9b-8874-895b90391e8c
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: security
discoiquuid: 4e08c297-aa4b-44cf-84c8-1e11582d9ebb
exl-id: 077a940d-19de-4d19-ad99-61f465e68205
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 2%

---

# Compatibilidad con cifrado para propiedades de configuración{#encryption-support-for-configuration-properties}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Esta función permite almacenar todas las propiedades de configuración de OSGi en una forma cifrada protegida en lugar de en un texto claro. El formulario de la interfaz de usuario de la consola web se utiliza para crear texto cifrado a partir de texto sin formato utilizando la clave maestra de cifrado de todo el sistema.

Se agregó compatibilidad con el complemento de configuración OSGi para descifrar la propiedad antes de que la utilice un servicio.

>[!NOTE]
>
>Los servicios que esperan un valor cifrado deben utilizar la comprobación IsProtection para ver si el valor está cifrado antes de intentar descifrarlo, ya que es posible que ya se haya descifrado.

## Habilitación de la compatibilidad con el cifrado {#enabling-encryption-support}

Estos pasos muestran cómo cifrar la contraseña SMTP para el servicio de correo. Puede completar estos pasos para una propiedad OSGI que desee codificar.

1. Vaya a la consola web de AEM en *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. En la esquina superior izquierda, vaya a **Principal: Compatibilidad con Crypto**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. La variable **Compatibilidad con criptografía de la consola web de Adobe Experience Manager** se muestra.

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. En el **Texto sin formato** , introduzca el texto de los datos confidenciales que desea proteger.
1. Select **Protect**. El texto protegido se muestra como texto cifrado.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Copie el Texto protegido del paso 5 y péguelo en el valor del formulario OSGI. En este ejemplo, el **Contraseña SMTP** se agrega a la variable *Day CQ Mail Service*.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Guarde las propiedades de Day CQ Mail Service. La contraseña SMTP ahora se envía como valor cifrado.

## Compatibilidad con descifrado {#decryption-support}

AEM ahora proporciona un complemento de configuración para descifrar las propiedades de configuración. Este complemento de AEM descifrará automáticamente y recuperará las propiedades de texto limpio.
