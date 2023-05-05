---
title: Novedades de AEM 6.4 Communities
description: AEM Communities ofrece un marco para que las empresas colaboren entre sus socios, clientes y empleados.
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 0%

---

# Novedades de AEM 6.4 Communities {#what-s-new-in-aem-communities}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Communities ofrece un marco para que las empresas colaboren entre sus socios, clientes y empleados. Imparte capacidades sociales a la estructura de sitios web, y ayuda a las empresas a involucrar e impartir conocimientos a sus interesados, para mejorar su valor de marca a su manera.

AEM 6.4 Communities aporta funcionalidades para mejorar las experiencias de los usuarios de la comunidad y facilitar las tareas diarias de los administradores, moderadores y administradores de la comunidad.

Siga leyendo para obtener una introducción rápida a las nuevas funciones y mejoras. Además, véase AEM 6.4 Comunidades [notas de la versión](../release-notes/communities-release-notes.md). Para AEM documentación de Communities 6.4, visite [Guía del usuario de AEM 6.4 Communities](home.md).

## Administración de subcomunidades o grupos de la comunidad {#managing-sub-communities-or-community-groups}

AEM Communities permite a los administradores de la comunidad crear grupos y subgrupos dentro del sitio de comunidades, utilizando plantillas predefinidas, en el entorno de creación. Estos grupos sirven como subcomunidades, que pueden heredar muchas configuraciones, como temas y estilos del sitio principal. Sin embargo, estos grupos pueden diferir del sitio principal, por ejemplo tener un conjunto diferente de moderadores de grupo o pueden variar en el nivel de seguridad. Estos grupos funcionan como minicomunidades independientes y de pleno derecho, que se ven potenciadas por las siguientes mejoras.

### Crear grupos de varias configuraciones regionales en un solo paso {#create-multi-locale-groups-in-single-step}

Como parte de un sitio de comunidad, se pueden crear grupos multilingües en una sola operación. **[!UICONTROL Idiomas de grupo de la comunidad disponibles adicionales]** en **[!UICONTROL Plantilla de grupo de la comunidad]** página, que está disponible al crear una [nuevo grupo de la comunidad](groups.md) dentro de un sitio de comunidad, lo hace factible.

![grupo multilingüe-1](assets/multilingualgroup-1.png)

Para crear estos grupos, los usuarios simplemente pueden navegar a la Colección de grupos del sitio de comunidades deseado desde la consola Sitios . Cree un grupo y especifique los idiomas que desee en **[!UICONTROL Idiomas de grupo de la comunidad disponibles adicionales]** campo **[!UICONTROL Plantilla de grupo de la comunidad]** página.

### Eliminar grupos de comunidades de la consola de grupos {#delete-community-groups-from-groups-console}

AEM 6.4 Comunidades proporciona el icono Eliminar grupo en los grupos de comunidades existentes, en la colección Grupos de comunidades dentro de la consola Sitios de la comunidad. Esto habilita [eliminación de grupo](groups.md#deleting-the-group) en un solo clic, junto con la eliminación de todos los elementos asociados (como contenido y membresías del usuario) al grupo.

![deletegrp](assets/deletegrp.png)

### Crear y asignar recursos de habilitación dentro de grupos {#create-and-assign-enablement-resources-within-groups}

Ahora se puede crear, administrar y publicar contenido de aprendizaje para un conjunto específico de miembros de la comunidad de destino. Debido a la disponibilidad de funciones de catálogo y asignación para grupos de la comunidad (y no solo para todo el sitio de la comunidad), los administradores de capacitación pueden [asignar recursos de habilitación](resource.md) y camino de aprendizaje a un pequeño grupo de personas también.

![assignment catalog](assets/assignmentcatalog.png)

## Moderación del contenido generado por el usuario {#moderating-user-generated-content}

AEM 6.4 Comunidades ofrece pocas mejoras en la moderación, que son fundamentales para facilitar la vida cotidiana de los moderadores de la comunidad.

### Detección automática de correo no deseado  {#automatic-spam-detection}

El nuevo motor de detección de correo no deseado ayuda a filtrar el contenido generado por el usuario no deseado y no solicitado en los sitios o grupos de la comunidad. Cuando está habilitada, esta funcionalidad puede marcar un fragmento de contenido generado por el usuario como correo no deseado o no deseado en función de un conjunto predefinido de palabras de correo no deseado. Los moderadores pueden actuar sobre el contenido para denegarlo o permitir que aparezca en la instancia de publicación. Estas acciones de moderación se pueden realizar en línea o a través de la consola de moderación masiva.

![spamdetect-1](assets/spamdetection-1.png)

[Detector de correo no deseado](moderate-ugc.md#spam-detection) encuentra y marca un determinado fragmento de contenido generado por el usuario con una precisión del 90%. Sin embargo, esta funcionalidad no está habilitada de forma predeterminada. Para habilitarlo, los administradores de la comunidad deben navegar a configMgr en el sistema/consola y agregar el Proceso de correo no deseado.

![spamprocess-1](assets/spamprocess-1.png)

### Nuevos filtros (Respondidos/No Respondidos) para el control de calidad {#new-answered-unanswered-filters-for-qna}

AEM 6.4 añade dos [nuevos filtros](moderation.md#filter-rail), denominada Respondida y No respondida para preguntas de control de calidad, para la consola de moderación masiva. Estos filtros están disponibles en Estado en Carril de filtro.

![estados](assets/statuses.png)

Al seleccionar el estado Respondido, el moderador del área de contenido puede ver todas las preguntas respondidas. Mientras que, si solo se selecciona el estado No respondido , el moderador verá todo el contenido (para todos los tipos de contenido) excepto las preguntas respondidas, ya que la propiedad responsable de la Pregunta respondida no existe en el caso de preguntas no respondidas y otro contenido como tema del foro, artículo del blog o comentarios.

### Filtros de moderación de marcadores {#bookmark-moderation-filters}

AEM Communities permite [marcador de los filtros de moderación predefinidos](moderation.md#filter-rail) en la consola de moderación. Estos marcadores guardados se pueden volver a visitar más adelante y compartir con otros usuarios.

Los usuarios simplemente deben seleccionar los filtros deseados en el Carril de filtro en la consola de moderación, para ver el UGC filtrado y marcar los filtros en sus navegadores. Estos filtros se anexan hacia el final de la cadena URL y, por lo tanto, se pueden compartir, reutilizar y volver a visitar más adelante.

## Administración de sitios de la comunidad {#managing-community-sites}

AEM 6.4 Comunidades proporciona mejoras en la administración del sitio, que garantizan que los administradores del sitio creen, gestionen y eliminen fácilmente numerosos sitios de la comunidad en distintos idiomas.

### Crear sitios de comunidad con varias configuraciones regionales en un solo paso {#create-multi-locale-community-sites-in-one-step}

AEM Communities permite crear una [sitios de comunidad multilingües](create-site.md) en una sola operación. Esto es posible debido a la disponibilidad de varios idiomas para seleccionar en **[!UICONTROL Idioma de base del sitio de la comunidad]** en **[!UICONTROL Plantilla del sitio]** mientras crea un nuevo sitio de comunidad desde la consola Sitios .

![multilocalesite](assets/multilocalesite.png)

Los usuarios pueden seleccionar carpetas de configuración, marcas y muchas otras configuraciones a la vez para todos estos sitios.

### Eliminar sitios de comunidad de la consola Sitios {#delete-community-sites-from-sites-console}

AEM 6.4 Communities proporciona un icono Eliminar sitio en los sitios de la comunidad existentes, en la consola Sitios de la comunidad. Esto habilita la variable [eliminación del sitio](create-site.md) y los elementos asociados en un clic.

![siteactions](assets/siteactions.png)

## Administración de UGC y perfiles de usuario {#managing-ugc-and-user-profiles}

AEM Communities expone la protección de los datos de los usuarios, que sigue estando en el centro de la experiencia de las comunidades [API listas para usar](user-ugc-management-service.md) y [servlet de ejemplo](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Estas API ayudan a administrar de forma masiva (eliminación masiva y exportación masiva) el contenido generado por el usuario y a eliminar perfiles de usuario, y son fundamentales para gestionar las solicitudes de cumplimiento del RGPD de la UE.

## Cambios {#what-s-changed}

* La verificación de captcha, al crear un nuevo sitio de comunidad, ya no está disponible de forma predeterminada en AEM comunidades 6.4. Sin embargo, el sitio de Communities puede personalizarse para incluir [Componente de Google reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) para una mejor seguridad.
* La opción de cargar una CSS personalizada se ha eliminado del tema de grupos y sitios de la comunidad.
* Se han añadido los iconos Solo contenido y Buscar en la Barra de filtro de la interfaz de usuario de Moderación masiva.
* Se ha añadido el filtro Ruta de contenido en Carril de filtro en la interfaz de usuario de Moderación masiva.
* El cambio al modo masivo y el modo de salida masiva se han eliminado de la interfaz de usuario de Moderación masiva. Para entrar al modo de selección múltiple, haga clic en Seleccionar ( ![selecticono](assets/selecticon.png)) en un anuncio, que aparece al pasar el ratón por encima con el ratón (escritorio) o presionando y sosteniendo un dedo sobre el anuncio (móvil).
