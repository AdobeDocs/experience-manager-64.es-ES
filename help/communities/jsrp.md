---
title: 'JSRP: proveedor de recursos de almacenamiento JCR'
seo-title: JSRP - JCR Storage Resource Provider
description: JSRP es generalmente el más adecuado para entornos de demostración o desarrollo de una instancia de publicación y una instancia de autor
seo-description: JSRP is generally best suited for demonstration or development environments of one publish instance and one author instance
uuid: 358a43c1-4137-4300-8443-c0d7166968ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: f5316a73-84e2-4a18-98c1-a384eeaa77cf
role: Admin
exl-id: 73c59497-43fe-4e15-afda-e3cf5264696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 2%

---

# JSRP: proveedor de recursos de almacenamiento JCR {#jsrp-jcr-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Acerca de JSRP {#about-jsrp}

Cuando AEM Communities utiliza JSRP como opción de almacenamiento (la predeterminada), el contenido de la comunidad se almacena en JCR y el contenido generado por el usuario (UGC) solo es accesible desde la instancia de autor o publicación en la que se publicó.

Debido a la simplicidad de la implementación, JSRP es generalmente el más adecuado para entornos de demostración o desarrollo de una instancia de publicación y una instancia de autor.

Consulte también [Características de las opciones de SRP](working-with-srp.md#characteristics-of-srp-options) y [Topologías recomendadas](topologies.md).

## Configuración {#configuration}

### Seleccionar JSRP {#select-jsrp}

De forma predeterminada, JSRP es la opción de almacenamiento para UGC.

La variable [Consola de configuración de almacenamiento](srp-config.md) permite seleccionar la configuración de almacenamiento predeterminada, que identifica qué implementación de SRP utilizar.

En el entorno de creación, para llegar a la consola de configuración de almacenamiento

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Configuración de almacenamiento]**

![chlimage_1-234](assets/chlimage_1-234.png)

* Select **[!UICONTROL Proveedor de recursos de almacenamiento JCR (JSRP)]**
* Seleccione **[!UICONTROL Enviar]**

### Publicación de la configuración {#publishing-the-configuration}

Aunque JSRP es la configuración predeterminada, para garantizar que la configuración idéntica esté establecida en el entorno de publicación:

* Sobre el autor:

   * Desde la navegación global: **[!UICONTROL Herramientas > Implementación > Replicación]**
   * Select **[!UICONTROL Activar árbol]**
   * **[!UICONTROL Ruta de inicio]**:

      * Vaya a `/conf/global/settings/community/srpc/`
   * Select **[!UICONTROL Activar]**


## Administración de datos de usuario {#managing-user-data}

Para obtener información sobre *usuarios*, *perfiles de usuario* y *grupos de usuarios*, introducidos a menudo en el entorno de publicación, visita

* [Sincronización de usuarios](sync.md)
* [Administración de usuarios y grupos de usuarios](users.md)

## Solución de problemas {#troubleshooting}

### UGC no visible en JCR {#ugc-not-visible-in-jcr}

Asegúrese de que JSRP se haya configurado para ser el proveedor predeterminado comprobando la configuración de la opción de almacenamiento. De forma predeterminada, el proveedor de recursos de almacenamiento es JSRP.

En todas las instancias de creación y publicación de AEM, vuelva a la consola Configuración de almacenamiento o compruebe el repositorio de AEM:

* en JCR, si [/conf/global/settings/community](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community)

   * No contiene un [srpc](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc) , significa que el proveedor de almacenamiento es JSRP
   * Si el nodo srpc existe y contiene el nodo [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/conf/global/settings/community/srpc/defaultconfiguration), las propiedades de configuración predeterminada deben definir JSRP para que sea el proveedor predeterminado

### UGC no visible en la instancia de autor {#ugc-not-visible-on-author-instance}

Este no es un error. Una característica de JSRP es que el contenido de la comunidad introducido en el entorno de publicación solo será visible en el entorno de publicación.

### UGC no visible en la instancia de publicación {#ugc-not-visible-on-publish-instance}

Si se implementa una instancia de publicación única o un clúster de publicación, siga las instrucciones para [UGC no visible en JCR](#ugc-not-visible-in-jcr).

Si se implementa un conjunto de servidores de publicación, una característica de JSRP es que el contenido de la comunidad solo será visible en la instancia de publicación en la que se publicó.

Para que UGC sea visible desde cualquier instancia de publicación, se requiere un clúster de publicación.
