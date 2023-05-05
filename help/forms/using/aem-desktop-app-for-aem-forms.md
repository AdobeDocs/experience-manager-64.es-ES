---
title: Aplicación de escritorio para AEM Forms
seo-title: AEM desktop app for AEM Forms
description: La aplicación de escritorio de AEM le permite asignar el repositorio de recursos de Adobe Experience Manager (AEM) y los archivos binarios de AEM Forms a un directorio de red del sistema. Obtenga más información sobre los recursos compatibles con AEM aplicación de escritorio y cómo habilitar AEM Forms para AEM aplicación de escritorio.
seo-description: AEM desktop app lets you map the Adobe Experience Manager (AEM) Assets repository and AEM Forms binary files to a network directory on your system. Learn more about the assets supported in AEM desktop app and how to enable AEM Forms for AEM desktop app.
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
role: Admin
exl-id: 26cd0851-cadf-4a8f-b3bf-59f77671f584
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 83%

---

# Aplicación de escritorio para AEM Forms {#aem-desktop-app-for-aem-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La aplicación de escritorio de AEM le permite asignar el repositorio de recursos de Adobe Experience Manager (AEM) y los archivos binarios de AEM Forms a un directorio de red del sistema. Puede ver los recursos sincronizados y los archivos binarios en un explorador de archivos y usar varias aplicaciones para editar los archivos como desee. Además de ver los archivos, también puede crear, cargar y eliminar los archivos binarios. También puede abrir, editar y guardar archivos directamente desde el software. Por ejemplo, puede abrir y editar directamente un archivo XDP desde Designer. Los cambios que realice en los recursos localmente se reflejarán en el repositorio de AEM Assets y en la interfaz de usuario de AEM Forms.

Puede descargar la aplicación desde una instancia de AEM. Para obtener información detallada sobre cómo descargar la aplicación, consulte [Notas de la versión de la aplicación de escritorio de AEM](https://helpx.adobe.com/es/experience-manager/desktop-app/release-notes.html).

## Recursos de AEM Forms compatibles con la aplicación de escritorio de AEM {#aem-forms-assets-supported-in-aem-desktop-app}

Puede utilizar la aplicación para sincronizar archivos binarios de AEM Forms del siguiente tipo: Plantillas de formulario (.xdp), Formulario PDF (.pdf), Documento (.pdf), Imágenes, Esquema XML (.xsd), Hojas de estilo (.xfs). La aplicación enumera todos los demás archivos (archivos no compatibles) como archivos de 0 bytes. La lista de archivos no compatibles como los archivos de 0 bytes garantiza que el usuario conozca la existencia de otros recursos disponibles en el servidor de AEM Forms.

>[!NOTE]
>
>Un nombre de archivo solo puede contener caracteres alfanuméricos, guiones o guiones bajos.

## Habilitar AEM Forms para la aplicación de escritorio de AEM {#enable-aem-forms-for-aem-desktop-app}

AEM aplicación de escritorio utiliza el protocolo WebDAV en Microsoft Windows y SMB1 en Mac OS X para conectarse a un servidor de AEM Forms. De serie, el servidor de AEM Forms no está habilitado para sincronizar archivos binarios y otros recursos con un cliente WebDAV o SMB. Siga estos pasos para habilitar AEM Forms para AEM aplicación de escritorio:

1. Inicie sesión en AEM Forms como administrador.
1. En la instancia de autor, haga clic en ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Herramientas]** ![hammer](assets/hammer.png) **[!UICONTROL > Implementación > Operaciones> Consola Web]**. La consola web se abre en una nueva ventana.
1. En la ventana de la consola web, busque y abra la opción **[!UICONTROL Configuración del complemento FormsManager]**.
1. En el cuadro de diálogo Configuración del complemento FormsManager, anule la selección de **[!UICONTROL Sincronizar recursos asincrónicamente]** y haga clic en **[!UICONTROL Guardar]**.
1. Reinicie el servidor de AEM Forms. Después reiniciarlo, el servidor de AEM Forms estará habilitado para aceptar y compartir contenido con la aplicación de escritorio de AEM.
1. Abra la aplicación y conéctese al servidor de AEM Forms.

   Si la conexión se realiza correctamente, la aplicación rellenará las carpetas `content/dam` y `content/dam/formsanddocuments`. Junto con Mover archivos de carpetas anteriores a carpetas locales y viceversa, puede utilizar la aplicación para mover contenido entre carpetas rellenadas automáticamente.
