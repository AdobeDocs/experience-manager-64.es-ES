---
title: Configuración de AEM Forms para enviar datos de formulario a un proceso AEM Forms en JEE
seo-title: Configuración de AEM Forms para enviar datos de formulario a un proceso AEM Forms en JEE
description: AEM Forms permite integrar formularios adaptables con AEM Forms en procesos JEE para procesar datos de formulario.
seo-description: AEM Forms permite integrar formularios adaptables con AEM Forms en procesos JEE para procesar datos de formulario.
uuid: ee7ea442-d604-4520-9af5-ad40ec4927a1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 03619a67-d1ea-4b80-b1a6-0c65a9e9212f
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Configuración de AEM Forms para enviar datos de formulario a un proceso AEM Forms en JEE {#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Los formularios adaptables admiten el envío de datos a un proceso AEM Forms en JEE para un procesamiento posterior. Permite activar un proceso de AEM Forms en JEE con los datos disponibles en el formulario enviado. Realice los siguientes pasos para permitir que la instancia de AEM Forms envíe un formulario adaptable a AEM Forms en el proceso JEE:

## Configurar el servidor de AEM Forms {#configure-your-aem-forms-server}

Realice los siguientes pasos para permitir que el servidor de AEM formularios envíe datos a un AEM Forms en un servidor JEE:

1. Vaya a AEM consola de configuración web en https://[*host*]:[*port*]/system/console/configMgr.

1. Busque y haga clic en el componente de configuración **del SDK del cliente de LiveCycle de** Adobe.
1. Haga clic para editar la dirección URL, el nombre de usuario y la contraseña del servidor de configuración para AEM Forms en el servidor JEE.
1. Revise la configuración y haga clic en **Guardar**.

![Configuración del SDK del cliente de Adobe LiveCycle](assets/clientsdkconfiguration.jpg)

## Asignar datos a campos de proceso {#map-data-with-process-fields}

Una vez configurado el AEM Forms, asigne el XML de datos y los archivos adjuntos del formulario enviado a los campos del proceso AEM Forms en JEE. Para ello:

1. En la consola de configuración web de AEM, haga clic para editar la configuración de Localizador de procesos de LiveCycle de **guía y de Invoker** .
1. Especifique los siguientes parámetros:

   * **Nombre del parámetro** xml de datos (obligatorio): Especifique el archivo de propiedad XML del proceso AEM Forms en JEE que necesita procesar los datos enviados. The default value is **dataxml**.
   * **Nombre del parámetro** de archivos adjuntos (opcional): Especifique la lista de los objetos de documento que el proceso AEM Forms en JEE debe procesar. The default value is **fileAttachmentsList**.

1. Revise la configuración y haga clic en **Guardar**.

![Localizador de procesos de LiveCycle de guía e Invoker](assets/test3.jpg)

Una vez configurada, la acción Enviar al Forms Workflow envía listas de AEM Forms en los procesos del servidor JEE que contienen el parámetro xml de datos especificado.
