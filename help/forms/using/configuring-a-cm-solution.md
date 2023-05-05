---
title: Configurar una solución de Administración de correspondencia
seo-title: Configuring a Correspondence Management solution
description: Obtenga información sobre cómo definir una URL de instancia de autor para la restauración de la versión de la instancia de autor y definir la URL de instancia de publicación para el administrador de activación de instancias públicas.
seo-description: Learn how to define an author instance URL for the author instance version restore and define the Publish instance URL for public instance activation manager.
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 84%

---

# Configurar una solución de Administración de correspondencia {#configuring-a-correspondence-management-solution}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Definir la URL de instancia de autor para VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Siga los siguientes pasos para definir un URL de instancia de autor para la restaurar la versión de la instancia de autor:

1. Vaya a *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Inicie sesión con las credenciales de usuario de la consola de administración OSGi. Las credenciales predeterminadas son admin/admin.
1. Busque y haga clic en el icono **[!UICONTROL Editar]** junto a la configuración **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**.
1. En el campo **[!UICONTROL URL de autor de VersionRestoreManager]** especifique la dirección URL de la instancia de autor de VersionRestoreManager.

   **Cadena de URL**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Si hay varias instancias de autor (agrupadas) delante de un equilibrador de carga, especifique la URL del equilibrador de carga en el campo **[!UICONTROL URL de autor de VersionRestoreManager]**.

1. Haga clic en **[!UICONTROL Guardar]**.

## Definir la URL de instancia de publicación para ActivationManagerImpl (administrador de activación de instancias públicas) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Siga estos pasos para definir la URL de instancia de publicación para el administrador de activación de instancias públicas:

1. Vaya a *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Inicie sesión con las credenciales de usuario de la consola de administración OSGi. Las credenciales predeterminadas son admin/admin.
1. Busque y haga clic en el icono **[!UICONTROL Editar]** junto a la configuración **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]**.
1. En el campo **[!UICONTROL URL de publicación de ActivationManager]** especifique la URL para acceder a la instancia de publicación ActivationManager. Puede proporcionar las siguientes URL.

   * **URL del equilibrador de carga (recomendado)**: proporcione la URL del equilibrador de carga si tiene un servidor web que actúa como tal frente a la granja de servidores de publicación (varias instancias de publicación no agrupadas).
   * **URL de instancia de publicación**: proporcione cualquier URL de instancia de publicación, si tiene una sola instancia de publicación o el servidor web que enlaza la granja de servidores de publicación no es accesible desde el entorno de creación debido a restricciones. En caso de que la instancia de publicación especificada no funcione, existe un mecanismo de reserva para el autor.
   * **Cadena de URL**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Haga clic en **[!UICONTROL Guardar]**.

Para obtener más información sobre configurar Administración de correspondencia, consulte [Propiedades de configuración de Administración de correspondencia](https://helpx.adobe.com/es/aem-forms/6-2/cm-configuration-properties.html).
