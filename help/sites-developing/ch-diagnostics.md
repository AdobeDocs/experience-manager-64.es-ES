---
title: Diagnóstico de ContextHub
seo-title: ContextHub Diagnostics
description: ContextHub proporciona una página de diagnóstico en la que puede ver información general sobre el marco de ContextHub
seo-description: ContextHub provides a diagnostics page where you can see an overview of the ContextHub framework
uuid: 94ef0696-3977-4781-ad32-9f4f117eb096
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6aa88583-5d34-4f77-a932-d47d84785eca
exl-id: 31926737-1a06-4fb9-b851-665095954875
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# Diagnóstico de ContextHub {#contexthub-diagnostics}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

ContextHub proporciona una página de diagnóstico en la que puede ver información general del marco de ContextHub. Para abrir la página, vaya a `contexthub.diagnostics.html` de la instancia de autor de AEM, por ejemplo:

`http://<host>:<port>/conf/<tenant>/settings/cloudsettings/default/contexthub.diagnostics.html`

La página Diagnósticos de ContextHub proporciona información sobre las tiendas y los módulos de interfaz de usuario que se han creado, las carpetas de la biblioteca de cliente que se han cargado y los vínculos a páginas útiles.

>[!NOTE]
>
>Para que se devuelva la información de diagnóstico, el modo de depuración debe estar habilitado; de lo contrario, la página de diagnóstico estará en blanco. Consulte [este documento](/help/sites-administering/contexthub-config.md#debugging-contexthub) para obtener más información sobre cómo habilitar el modo de depuración.

>[!NOTE]
>
>En el caso de las configuraciones de ContextHub que siguen estando debajo de sus rutas heredadas, la ubicación de la página de diagnóstico es `http://<host>:<port>/libs/settings/cloudsettings/legacy/contexthub.diagnostics.html`.

## Almacenes {#stores}

La sección Almacenes enumera todos los almacenes de ContextHub configurados. Cada elemento de la lista consta de la siguiente información:

* **Título:** La variable [tipo de tienda](/help/sites-developing/ch-samplestores.md) en el que se basa la tienda.
* **ruta:** Ruta al nodo del repositorio que contiene la configuración.
* **resourceType:** Ruta del nodo del repositorio donde se define el tipo de almacén.
* **clientlibs:** Las categorías de bibliotecas de cliente que se cargan que implementan el tipo de tienda.

## Módulos {#modules}

La sección Módulos enumera todos los módulos de IU de ContextHub que se han configurado. Cada elemento de la lista consta de la siguiente información:

* **Título:** La variable [Tipo de módulo de interfaz de usuario](/help/sites-developing/ch-samplemodules.md) en el que se basa el módulo de IU.
* **ruta:** Ruta al nodo del repositorio que contiene la configuración.
* **resourceType:** Ruta del nodo del repositorio donde se define el tipo de módulo de interfaz de usuario.
* **clientlibs:** Las categorías de bibliotecas de cliente que se cargan que implementan el tipo de módulo de interfaz de usuario.

## Clientlibs {#clientlibs}

La sección Clientlibs enumera todas las carpetas de la biblioteca de cliente que ha cargado ContextHub. Las bibliotecas de cliente se categorizan:

* **kernel.js:** Bibliotecas de cliente que implementan el marco de ContextHub, el motor de segmentos y los tipos de almacén.
* **ui.js:** Bibliotecas de cliente que implementan los tipos de módulos UI y UI de ContextHub.
* **style.css:** Archivos CSS que se cargan desde bibliotecas de cliente.

## URL {#urls}

La sección URL contiene vínculos a las funciones de ContextHub:

* **Editor de configuración:** Abre el [Página de configuración de ContextHub](/help/sites-administering/contexthub-config.md) donde puede configurar tiendas, modos de IU y módulos de IU.

* **Configuración de los módulos de ContextHub:** Abre el archivo /etc/cloudsettings/default/contexthub.config.kernel.js, que contiene la representación del objeto Javascript de las configuraciones de la tienda de ContextHub.
* **Configuración de la interfaz de usuario de ContextHub:** Abre el archivo /etc/cloudsettings/default/contexthub.config.ui.js , que contiene la representación de objeto Javascript de las configuraciones del modo de IU de ContextHub.
* **kernel.js:** Abre el archivo /etc/cloudsettings/default/contexthub.kernel.js , que contiene el código fuente de las bibliotecas de cliente que implementan el marco de ContextHub, el motor de segmentos y los tipos de almacén.
* **ui.js:** Abre el archivo /etc/cloudsettings/default/contexthub.ui.js , que contiene el código fuente de las bibliotecas de cliente que implementan los tipos de módulos UI y IU de ContextHub.
* **style.css:** Abre el archivo /etc/cloudsettings/default/contexthub.styles.css, que contiene los estilos CSS para los módulos de IU y IU de ContextHub.
