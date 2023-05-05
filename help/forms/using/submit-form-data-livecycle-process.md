---
title: Configurar AEM Forms para enviar datos de formulario a un proceso de AEM Forms en JEE
seo-title: Configuring AEM Forms to submit form data to an AEM Forms on JEE process
description: AEM Forms permite integrar formularios adaptables con AEM Forms en procesos JEE para procesar datos de formulario.
seo-description: AEM Forms allows you to integrate adaptive forms with AEM Forms on JEE processes for processing form data.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
role: Admin
exl-id: 260e405e-f59c-4aea-b83f-53ee103df94e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 92%

---

# Configurar AEM Forms para enviar datos de formulario a un proceso de AEM Forms en JEE {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Los formularios adaptables admiten el envío de datos a un proceso de AEM Forms en JEE para un procesamiento posterior. Permite almacenar en el activador un proceso de AEM Forms en JEE con los datos disponibles en el formulario enviado. Realice los siguientes pasos para permitir que la instancia de AEM Forms envíe un formulario adaptable a AEM Forms durante el proceso JEE:

## Configurar el servidor de AEM Forms {#configure-your-aem-forms-server}

Realice los siguientes pasos para permitir que el servidor de AEM Forms envíe datos a AEM Forms en un servidor JEE:

1. Vaya a la página de configuración de la web de AEM en https://[*host*]:[*port*]/system/console/configMgr.

1. Busque y haga clic en el componente **Configurar el SDK de cliente de LiveCycle de Adobe**.
1. Haga clic para editar la URL del servidor de configuración, el nombre de usuario y la contraseña para AEM Forms en el servidor JEE.
1. Revise la configuración y haga clic en **Guardar**.

![Configurar el SDK de cliente de LiveCycle de Adobe](assets/clientsdkconfiguration.jpg)

## Asignar datos a campos de proceso {#map-data-with-process-fields}

Una vez configurado AEM Forms, asigne los datos XML y los archivos adjuntos del formulario enviado a los campos del proceso de AEM Forms en JEE. Para ello, haga lo siguiente:

1. En la consola de configuración web de AEM, haga clic para editar la configuración de la **Guía de localización e invocación de procesos de LiveCycle**.
1. Especifique los siguientes parámetros:

   * **Nombre del parámetro xml de datos** (obligatorio): especifique el archivo de propiedad XML del proceso de AEM Forms en JEE que necesita procesar los datos enviados. El valor predeterminado es **dataxml**.
   * **Nombre del parámetro de archivos adjuntos** (opcional): especifique la lista de objetos de documento que debe procesar el proceso de AEM Forms en JEE. El valor predeterminado es **fileAttachmentsList**.

1. Revise la configuración y haga clic en **Guardar**.

![Guía de localización e invocación de procesos de LiveCycle](assets/test3.jpg)

Una vez configurada, la acción Enviar al flujo de trabajo de formularios envía una lista de los procesos de AEM Forms en el servidor JEE que contienen el parámetro xml de datos especificado.
