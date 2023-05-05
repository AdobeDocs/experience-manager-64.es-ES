---
title: Notas de la versión de AEM Communities
seo-title: AEM Communities
description: Notas de la versión específicas de Adobe Experience Manager 6.4 Communities.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Communities.
uuid: 2de9f511-2a61-4003-9b2c-d6728bc9d57a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 55a0b70e-5212-408b-8560-6e758bd8bb10
exl-id: 3a341e72-01c5-4c63-8942-6320e5b08440
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 6%

---

# Notas de la versión de AEM Communities {#aem-communities-release-notes}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta sección proporciona información sobre las mejoras realizadas en AEM Communities desde la versión 6.3. Para obtener más información sobre las nuevas funciones con buenos detalles, consulte [Novedades de AEM 6.4 Communities](/help/communities/whats-new-aem-communities.md).

Para obtener la última versión, consulte la [Implementación de comunidades](/help/communities/deploy-communities.md#latest-releases) de la documentación.

## Mejoras principales {#main-improvements}

Sitios de la comunidad:

* Los administradores de la comunidad ahora pueden:

   * Eliminar permanentemente sitios de la comunidad
   * Seleccionar una carpeta de configuración según el contexto para sitios de la comunidad

Grupos de la comunidad:

* Los administradores de la comunidad ahora pueden:

   * Eliminar permanentemente grupos de la comunidad
   * Crear grupos de comunidades en varios idiomas
   * Agregar catálogo de habilitación y asignaciones dentro de grupos de la comunidad

* Los administradores de habilitación ahora pueden

   * Crear y asignar recursos y rutas de aprendizaje dentro de los grupos de la comunidad

Biblioteca de archivos:

* Los miembros de la comunidad ahora tienen varias mejoras en la biblioteca de archivos, por ejemplo: ordenar pedidos, etiquetar..

Notificaciones:

* Los miembros de la comunidad reciben ahora notificaciones tras la aprobación de las contribuciones que han pasado por un proceso de moderación

Moderación:

* Filtro de detección automatizada de correo no deseado
* Los moderadores de la comunidad tienen filtros de moderación adicionales (p. ej., preguntas contestadas o no contestadas)
* Los moderadores de la comunidad pueden agregar marcadores y vincular moderación a filtros predefinidos (por ejemplo, todas las publicaciones pendientes de aprobación)

Compatibilidad global con cambios fundamentales en AEM 6.4.

Nota: todas estas funciones también están disponibles para AEM 6.3. Compruebe las notas de la versión de AEM Communities para [6,3](https://helpx.adobe.com/es/experience-manager/6-3/release-notes.html).

## Problemas conocidos {#known-issues}

* **Moderación** - No se puede eliminar la publicación principal como una sola operación de eliminación desde la interfaz de usuario de moderación masiva (CQ-4236797)
* **Consola** - El nombre de usuario olvidado o el vínculo Contraseña se redirigen a la página de inicio de sesión en lugar del formulario correspondiente de recuperación de contraseña (CQ-4237682)

## Seleccionar características {#select-features}

Puntuación de expertos (*Con la tecnología de Sensei*) - se utiliza para permitir la gamificación, que es una manera efectiva de alentar y recompensar el valioso comportamiento de la comunidad. También se puede utilizar para identificar expertos con fines de recomendación o marketing.

## Manifestaciones {#demonstrations}

Todas estas características se pueden demostrar utilizando la variable [AEM de demostración](https://github.com/Adobe-Marketing-Cloud/aem-demo-machine/wiki) disponible públicamente en GitHub.com al usar el escenario de demostración de AEM Communities y también dentro de la nueva implementación de referencia de We.Retail.
