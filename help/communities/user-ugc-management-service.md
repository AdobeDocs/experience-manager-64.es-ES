---
title: Servicio de administración de usuarios y usuarios por usuario en AEM Communities
seo-title: Servicio de administración de usuarios y usuarios por usuario en AEM Communities
description: 'Utilice las API para eliminar de forma masiva y exportar de forma masiva contenido generado por el usuario, y para deshabilitar la cuenta de usuario. '
seo-description: 'Utilice las API para eliminar de forma masiva y exportar de forma masiva contenido generado por el usuario, y para deshabilitar la cuenta de usuario. '
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Servicio de administración de usuarios y usuarios por usuario en AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>El RGPD se utiliza como ejemplo en las secciones que figuran a continuación, pero los detalles abarcados son aplicables a todas las normas de protección de datos y privacidad; como el RGPD, la CCPA, etc.

AEM Communities expone las API integradas para administrar los perfiles de los usuarios y el contenido generado por los usuarios (UGC) de forma masiva. Una vez activado, el servicio **UserUgcManagement** permite a los usuarios privilegiados (administradores de la comunidad y moderadores) desactivar los perfiles de usuario y eliminar o exportar de forma masiva UGC para usuarios específicos. Estas API también permiten que los controladores y los procesadores de datos de los clientes cumplan con las Normas Generales de Protección de Datos (RGPD) de la Unión Europea y otros mandatos de privacidad inspirados en el RGPD.

Para obtener más información, consulte la página del [RGPD en el Centro](https://www.adobe.com/privacy/general-data-protection-regulation.html)de Privacidad del Adobe.

>[!NOTE]
>
>Si ha configurado [Adobe Analytics en el sitio de AEM Communities](analytics.md) , los datos de usuario capturados se envían al servidor de Adobe Analytics. Adobe Analytics proporciona API que le permiten acceder, exportar y eliminar datos de usuario y cumplir con el RGPD. Para obtener más información, consulte [Enviar solicitudes](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html)de acceso y eliminación.

Para poner estas API en uso, debe habilitar el extremo activando el servicio UserUgcManagement `/services/social/ugcmanagement` . Para activar este servicio, instale el servlet de [muestra](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) disponible en [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet). A continuación, toque el extremo en la instancia de publicación del sitio de comunidades con los parámetros adecuados mediante una solicitud http, similar a la siguiente:

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Sin embargo, también puede crear una interfaz de usuario (interfaz de usuario) para administrar los perfiles de usuario y el contenido generado por el usuario en el sistema.

Estas API permiten realizar las siguientes funciones.

## Recuperar el UGC de un usuario {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` ayuda a exportar todo el UGC de un usuario desde el sistema.

* **usuario**: ID autorizable de un usuario.
* **outputStream**: el resultado se devuelve como flujo de salida, que es un archivo zip que incluye el contenido generado por el usuario (como archivo json) y los archivos adjuntos (que incluyen imágenes o vídeos cargados por el usuario).

Por ejemplo, para exportar el UGC de un usuario llamado Weston McCall, que utiliza weston.mccall@dodgit.com como ID autorizada para iniciar sesión en el sitio de comunidades, puede enviar una solicitud de GET http similar a la siguiente:

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Eliminar el UGC de un usuario {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, usuario de cadena)** ayuda a eliminar todo el UGC de un usuario del sistema.

* **usuario**: ID autorizable del usuario.

Por ejemplo, para eliminar el UGC de un usuario con un ID autorizado weston.mccall@dodgit.com mediante una solicitud de http-POST, utilice los parámetros siguientes:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Eliminar UGC de Adobe Analytics {#delete-ugc-from-analytics}

Para eliminar datos de usuario del Adobe Analytics, siga el flujo de trabajo de GDPR Analytics; ya que la API no elimina datos de usuario de Adobe Analytics.

Para las asignaciones de variables de Adobe Analytics utilizadas por AEM Communities, consulte la siguiente imagen:

![Asignación de variables de comunidades AEM para Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Deshabilitar una cuenta de usuario {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, usuario de cadena)** ayuda a deshabilitar una cuenta de usuario.

* **usuario**: ID autorizable del usuario.

>[!NOTE]
>
>Al deshabilitar un usuario, se elimina todo el contenido generado por el usuario que tiene en el servidor.

Por ejemplo, para eliminar el perfil de un usuario con un ID autorizado weston.mccall@dodgit.com mediante una solicitud de http-POST, utilice los parámetros siguientes:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>la API deleteUserAccount() solo deshabilita un perfil de usuario en el sistema y elimina el UGC. Sin embargo, para eliminar un perfil de usuario del sistema, vaya al **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), busque el nodo de usuario y elimínelo.
