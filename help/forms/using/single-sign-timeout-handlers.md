---
title: Inicio de sesión único y controladores de tiempo de espera
seo-title: Single Sign On and timeout handlers
description: Establecer el valor del tiempo de espera de la sesión para AEM Forms Workspace.
seo-description: How-to set the session timeout value for AEM Forms workspace.
uuid: 17583fd5-6453-41d3-bb63-a639983fbea9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 698990a2-dd3f-480f-9d15-d87563860297
exl-id: eb7afdd3-0901-4dfb-b23c-88c46b5a4fb5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 87%

---

# Inicio de sesión único y controladores de tiempo de espera {#single-sign-on-and-timeout-handlers}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El espacio de trabajo de AEM Forms está habilitado para SSO. Si un usuario ha iniciado sesión en una aplicación de AEM Forms como Forms Manager o la interfaz de usuario del generador de PDF y accede al espacio de trabajo de AEM Forms en la misma sesión del explorador, el usuario ha iniciado sesión en AEM Forms Workspace y viceversa.

## Administrar el tiempo de espera del servidor en AEM Forms Workspace {#handling-server-timeout-in-nbsp-aem-forms-workspace}

El tiempo de espera de sesión de un usuario se puede configurar en la consola de administración.

Para establecer el tiempo de espera, inicie sesión en `https://[server]:[port]/adminui`, navegue hasta **Configuración > Administrar usuarios > Configuración > Configurar atributos avanzados del sistema** y realice la configuración que desee.

En AEM Forms, el tiempo de espera de espacio de trabajo se administra de la siguiente manera:

* La duración de la sesión de un usuario está disponible en respuesta a la llamada `initialize` que inicializa la sesión del usuario.
* Un cuadro de diálogo emergente notifica al usuario que la sesión está a punto de caducar, 15 segundos antes de que caduque la sesión.

En este cuadro de diálogo emergente:

* Haga clic en Aceptar para finalizar la sesión de usuario.
* Haga clic en Cancelar para reiniciar la sesión de usuario.

>[!NOTE]
>
>Si no se realiza ninguna acción, se cerrará la sesión del usuario de AEM Forms Workspace automáticamente tres segundos antes de la caducidad de la sesión.
