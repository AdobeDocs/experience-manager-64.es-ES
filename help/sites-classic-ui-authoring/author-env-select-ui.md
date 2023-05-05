---
title: Selección de la IU
seo-title: Selecting your UI
description: Para facilitar la labor de los usuarios que crean contenido, la IU táctil permite cambiar a la IU clásica cuando es necesario.
seo-description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
uuid: 755e513e-990c-4dba-8316-623f17bf5c33
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: dcac2a3a-3241-47de-96ce-982ab0bc05eb
exl-id: 997040d4-cf8f-4240-8423-a98d562aae02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 3%

---

# Selección de la IU{#selecting-your-ui}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Dado que la IU táctil sustituye a la IU clásica, el usuario o administrador de la instancia de AEM debe tomar una decisión activa para continuar utilizando la IU clásica. Como la IU clásica ya no se mantiene, no hay forma de que el usuario autor cambie de la IU clásica al equivalente en la IU táctil.

Para facilitar la labor de los usuarios que crean contenido, la IU táctil permite cambiar a la IU clásica cuando es necesario. Consulte la [Selección de la IU](/help/sites-authoring/select-ui.md) en la documentación de creación estándar para obtener más información.

>[!NOTE]
>
>Las instancias actualizadas desde una versión anterior conservarán la IU clásica para la creación de páginas.
>
>Después de la actualización, la creación de páginas no cambiará automáticamente a la IU táctil, pero puede configurarla con el [Configuración de OSGi](/help/sites-deploying/configuring-osgi.md) del **Servicio de modo de IU de creación WCM** ( `AuthoringUIMode` ). Consulte [Omisiones de IU del editor](#uioverridesfortheeditor).

## Configuración de la IU predeterminada para su instancia {#configuring-the-default-ui-for-your-instance}

Un administrador del sistema puede configurar la IU que se ve al inicio y al iniciar sesión mediante [Asignación de raíz](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

Esto puede anularse por los valores predeterminados del usuario o por la configuración de la sesión.
