---
title: Notas de versión de AEM Communities
seo-title: AEM Communities
description: Notas de versión específicas de Adobe Experience Manager 6.4 Communities.
seo-description: Notas de versión específicas de Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
translation-type: tm+mt
source-git-commit: 242f60c70c7cc00871d2ff9f42d2ade4125eaa31

---


# AEM Communities Notas de la versión {#aem-communities-release-notes}

Esta sección proporciona información sobre las mejoras realizadas en AEM Communities desde la versión 6.3. Para obtener más información sobre las nuevas funciones, consulte [Novedades de AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

To obtain the latest release, see the [Deploying Communities](/help/communities/deploy-communities.md#latest-releases) section of the documentation.

## Mejoras principales {#main-improvements}

Sitios de la comunidad:

* Los administradores de la comunidad ahora pueden:

   * Eliminar permanentemente sitios de la comunidad
   * Seleccionar una carpeta de configuración contextual para sitios de la comunidad

Grupos de la comunidad:

* Los administradores de la comunidad ahora pueden:

   * Eliminar permanentemente grupos de la comunidad
   * Crear grupos de la comunidad en varios idiomas
   * Agregar catálogo de habilitación y asignaciones dentro de grupos de la comunidad

* Los administradores de habilitación ahora pueden

   * Crear y asignar recursos y rutas de aprendizaje dentro de grupos de la comunidad

Biblioteca de archivos:

* Los miembros de la comunidad ahora tienen varias mejoras en la biblioteca de archivos, por ejemplo: ordenación, etiquetado...

Notificaciones:

* Los miembros de la comunidad reciben ahora notificaciones tras la aprobación de las contribuciones que han pasado por un proceso de moderación

Moderación:

* Filtro automático de detección de correo no deseado
* Los moderadores de la comunidad tienen filtros de moderación adicionales (por ejemplo, preguntas contestadas o no contestadas)
* Los moderadores de la comunidad pueden marcar y vincular la moderación a filtros predefinidos (por ejemplo, todas las publicaciones pendientes de aprobación)

Compatibilidad general con cambios fundamentales en AEM 6.4.

Nota: todas estas funciones también están disponibles para AEM 6.3. Consulte las notas de la versión de AEM Communities para [6.3](https://helpx.adobe.com/experience-manager/6-3/release-notes.html).

## Problemas conocidos {#known-issues}

* **Moderación** : no se puede eliminar una publicación principal como una sola operación de eliminación desde la interfaz de usuario de moderación masiva (CQ-4236797)
* **Consola** : el vínculo Nombre de usuario olvidado o Contraseña se está redirigiendo a la página de inicio de sesión en lugar del formulario de recuperación de contraseña correspondiente (CQ-4237682)

## Seleccionar funciones {#select-features}

Puntuación de experto (*con tecnología Sensei*) - se utiliza para permitir la gamificación, que es una manera efectiva de alentar y recompensar el valioso comportamiento de la comunidad. También puede utilizarse para identificar a expertos con fines de recomendación o de mercadotecnia.

## Manifestaciones {#demonstrations}

Todas estas funciones se pueden demostrar con la [AEM Demo Machine](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible públicamente en GitHub.com cuando se utiliza el escenario de demostración de AEM Communities y también en la nueva implementación de referencia de We.Retail.
