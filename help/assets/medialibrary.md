---
title: Usar Media Library para la administración básica de recursos digitales
description: '"[!DNL Experience Manager Assets] y Media Library para la administración de recursos".'
contentOwner: AG
feature: Asset Management
role: Architect,Leader
exl-id: f0afdae4-5777-464c-9203-e9d19c6d62f6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 1%

---

<!--

Define Media Lib
Define req for it
Define use cases
Define what is not included

-->

# Usar Media Library para la administración básica de recursos {#manage-assets-using-media-library}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

[!DNL Adobe Experience Manager] platform proporciona diferentes funciones para administrar recursos. Media Library permite a los usuarios cargar un pequeño número de recursos en el repositorio, buscarlos y utilizarlos en las páginas web y realizar tareas sencillas de administración de recursos en los recursos.

Media Library es una solución ligera de administración de activos digitales (DAM) que se suministra de forma gratuita con [!DNL Adobe Experience Manager Sites] licencia. [!DNL Sites] es una oferta de administración de contenido web (WCM). Media Library funciona con todas las funcionalidades de Experience Manager.

[!DNL Adobe Experience Manager Assets] la licencia está disponible por separado para su compra. [!DNL Experience Manager Assets] permite una gestión sólida de los recursos mediante casos de uso empresariales, personalizaciones de metadatos, esquemas, búsquedas e interfaz de usuario, y muchas otras funciones además de las que proporciona Media Library.

## Requisitos de licencia {#avail-media-library-license}

Clientes que tienen [!DNL Sites] Las licencias de tienen derecho a utilizar Media Library. Funciona con todos los componentes de [!DNL Experience Manager].

Media Library se instala como parte de Sites. No se requiere licencia o paquete adicional más allá de la licencia e instalación de Sites.

## [!DNL Assets] versus Media Library {#assets-and-media-library}

Experience Manager Assets proporciona funcionalidad de DAM de nivel empresarial. La funcionalidad de los recursos se suministra con [!DNL Experience Manager] en un solo paquete. Sin embargo, los usuarios que no hayan adquirido una licencia de Assets no tienen derecho a utilizar las funciones avanzadas de DAM. Sin licencia de Assets, solo [Funciones de Media Library](#use-media-library) están disponibles.

Si desea evitar el uso no intencionado de [!DNL Assets] características que no tiene licencia, luego elimine todas las [!DNL Assets]flujos de trabajo, componentes, taxonomías, opciones específicos y [!DNL Assets] administrador de [!DNL Experience Manager]. Al hacerlo, evitará que sus usuarios utilicen accidentalmente [!DNL Assets] características que no obtuvo licencia.

## Uso de Media Library {#use-media-library}

Media Library abarca en general los siguientes casos de uso:

* Proporcionar funciones básicas de DAM para páginas web creadas mediante [!DNL Adobe Experience Manager Sites].
* Formularios y comunicaciones adaptables creados mediante [!DNL Adobe Experience Manager Forms].
* Experiencias de pantalla digital creadas con [!DNL Adobe Experience Manager Screens].
* [!DNL Assets] API HTTP REST para operaciones sin encabezado.

<!-- TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.

* Static renditions
-->

Para utilizar la funcionalidad de Media Library, puede utilizar la variable predeterminada [!DNL Experience Manager] interfaz de usuario. Media Library forma parte del [!DNL Experience Manager Sites] no se requiere interfaz ni complemento separados. Con la interfaz existente, los usuarios de Media Library tienen derecho a realizar las siguientes tareas:

* Cree carpetas para organizar los recursos.
* Carga de activos.
* Publicar recursos.
* Editar, mover y copiar recursos.
* Examinar, filtrar y buscar recursos (incluye la búsqueda por similitudes).
* Agregue valores a y edite los valores en los campos de metadatos, excepto el campo Etiquetas inteligentes , que están disponibles en el campo [!UICONTROL Básico] pestaña de un recurso [!UICONTROL Propiedades] de forma predeterminada.
* Añada y elimine representaciones estáticas.
* Descargue carpetas, recursos y representaciones de recursos.
* Crear versiones de recursos.
* Cree y realice tareas de revisión en los recursos.
* Anotar recursos.
* Agregar recursos a [!DNL Sites] a través del Buscador de contenido.
* Uso [!DNL Content Fragments].
* Utilice las API de HTTP REST y GraphQL para [!DNL Content Fragments] y recursos multimedia a los que se hace referencia, bajo licencia de Sites.
* Integración de Marketing Cloud.
* Personalice y amplíe la interfaz de usuario de administración de recursos.
* Acceda al Generador de consultas (API) para ampliar la funcionalidad de búsqueda.
* Crear etiquetas estáticas.
* Cree proyectos y tareas.
* Flujo de actividad (línea de tiempo).
* Comentarios y anotaciones.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we don't have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Muchos casos de uso de DAM avanzados los cumple [!DNL Experience Manager Assets]. La licencia de Media Library le da derecho a cumplir únicamente los casos de uso enumerados con Media Library. Si un caso de uso no aparece en la lista, no lo utilice con la licencia de Media Library. Si tiene alguna consulta, póngase en contacto con el servicio de atención al cliente de Adobe.

Tenga en cuenta que no puede utilizar etiquetas inteligentes, [!DNL Asset] vínculo, [!DNL Asset] selector, etiquetado masivo, modificación de flujos de trabajo de recursos o estándar [!DNL Adobe Experience Manager] interfaz de usuario para acceder a Media Library sin [!DNL Assets] licencia.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [Funciones DAM en [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-64/assets/home.html)

