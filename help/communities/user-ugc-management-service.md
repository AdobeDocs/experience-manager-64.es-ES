---
title: Servicio de administración de usuarios y UGC en AEM Communities
seo-title: User and UGC Management Service in AEM Communities
description: Utilice las API para eliminar de forma masiva y exportar de forma masiva contenido generado por el usuario, y para deshabilitar la cuenta de usuario.
seo-description: Use APIs to bulk delete and bulk export user generated content, and disable user account.
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
role: Admin
exl-id: f4adc53d-6809-4d89-a3dd-5d783e938a63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 1%

---

# Servicio de administración de usuarios y UGC en AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!IMPORTANT]
>
>El RGPD se utiliza como ejemplo en las secciones siguientes, pero los detalles cubiertos son aplicables a todas las normas de protección de datos y privacidad; como el RGPD, la CCPA, etc.

AEM Communities expone las API listas para usar para administrar perfiles de usuario y administrar de forma masiva el contenido generado por el usuario (UGC). Una vez activada, la variable **UserUgcManagement** permite a los usuarios privilegiados (administradores de la comunidad y moderadores) desactivar perfiles de usuario, y eliminar o exportar UGC de forma masiva para usuarios específicos. Estas API también permiten que los controladores y procesadores de datos de clientes cumplan con las normas generales de protección de datos (RGPD) de la Unión Europea y otros mandatos de privacidad inspirados en el RGPD.

Para obtener más información, consulte [Página del RGPD en el Centro de privacidad de Adobe](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Si ha configurado [Adobe Analytics en AEM Communities](analytics.md) sitio, los datos de usuario capturados se envían al servidor de Adobe Analytics. Adobe Analytics proporciona API que le permiten acceder, exportar y eliminar datos de usuario y cumplir con el RGPD. Para obtener más información, consulte [Envío de solicitudes de acceso y eliminación](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Para que estas API se utilicen, debe habilitar la variable `/services/social/ugcmanagement` al activar el servicio UserUgcManagement. Para activar este servicio, instale la variable [servlet de ejemplo](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) disponible en [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). A continuación, pulse el punto final en la instancia de publicación del sitio de comunidades con los parámetros apropiados mediante una solicitud http, similar a la siguiente:

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

Sin embargo, también puede crear una interfaz de usuario (interfaz de usuario) para administrar los perfiles de usuario y el contenido generado por el usuario en el sistema.

Estas API permiten realizar las siguientes funciones.

## Recuperar el UGC de un usuario {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` ayuda a exportar todo el UGC de un usuario desde el sistema.

* **usuario**: ID autorizado de un usuario.
* **outputStream**: el resultado se devuelve como flujo de salida, que es un archivo zip que incluye el contenido generado por el usuario (como archivo json) y archivos adjuntos (que incluyen imágenes o vídeos cargados por el usuario).

Por ejemplo, para exportar el UGC de un usuario llamado Weston McCall, que utiliza weston.mccall@dodgit.com como ID autorizado para iniciar sesión en el sitio de Communities, puede enviar una solicitud de GET http similar a la siguiente:

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Eliminar el UGC de un usuario {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, usuario de cadena)** ayuda a eliminar todo el UGC de un usuario del sistema.

* **usuario**: ID autorizado del usuario.

Por ejemplo, para eliminar el UGC de un usuario que tenga un ID autorizado weston.mccall@dodgit.com a través de una solicitud http-POST, utilice los parámetros siguientes:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### Eliminar UGC de Adobe Analytics {#delete-ugc-from-analytics}

Para eliminar datos de usuario de Adobe Analytics, siga el flujo de trabajo de análisis del RGPD; ya que la API no elimina los datos de usuario de Adobe Analytics.

Para las asignaciones de variables de Adobe Analytics que utiliza AEM Communities, consulte la siguiente imagen:

![Asignación de variables de comunidades AEM para Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## Deshabilitar una cuenta de usuario {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, usuario de cadena)** ayuda a deshabilitar una cuenta de usuario.

* **usuario**: ID autorizado del usuario.

>[!NOTE]
>
>Al deshabilitar un usuario, se elimina todo el contenido generado por el usuario que tenga en el servidor.

Por ejemplo, para eliminar el perfil de un usuario que tiene un ID autorizado weston.mccall@dodgit.com a través de una solicitud del POST http, utilice los parámetros siguientes:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>deleteUserAccount() API solo deshabilita un perfil de usuario en el sistema y elimina el UGC. Sin embargo, para eliminar un perfil de usuario del sistema, vaya a **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de), busque el nodo de usuario y elimínelo.
