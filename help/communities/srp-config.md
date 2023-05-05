---
title: Configuración de almacenamiento
seo-title: Storage Configuration
description: Acceso a la Consola de Configuración de Almacenamiento
seo-description: How to access the Storage Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 905b6dc5-cf17-4f58-a687-27e2910a0729
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Configuración de almacenamiento {#storage-configuration}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La configuración del almacenamiento es la forma de identificar el almacenamiento elegido para el contenido de la comunidad, también conocido como contenido generado por el usuario (UGC).

Esta configuración informa al código de AEM Communities de qué implementación del proveedor de recursos de almacenamiento (SRP) se utilizará al acceder a UGC y debe reflejar la topología establecida cuando se implementó AEM.

Para consultar las opciones de almacenamiento y las topologías de implementación, visite

* [Almacenamiento de contenido de la comunidad](working-with-srp.md)
* [Topologías recomendadas](topologies.md)

## Consola de configuración de almacenamiento {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

En el entorno de creación, para llegar a la consola de configuración de almacenamiento

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Configuración de almacenamiento]**

Para seleccionar una opción de almacenamiento que no sea el JCR predeterminado:

* seleccionar una opción
* Configure correctamente

   * Consulte los detalles para [selección de MSRP](msrp.md#select-msrp)
   * Consulte los detalles para [seleccionar DSRP](dsrp.md#select-dsrp)
   * Consulte los detalles para [seleccionar ASRP](asrp.md#select-asrp)

* Seleccione **[!UICONTROL Enviar]**

### Acerca del almacenamiento JCR {#about-jcr-storage}

Tenga en cuenta que si no se realiza ninguna selección, el valor predeterminado es el repositorio AEM, JCR.

JCR es *not* una tienda común compartida por los entornos de autor y publicación. El contenido de la comunidad solo será visible desde el entorno de creación o publicación en el que se creó.

Visita [Almacenamiento JCR](jsrp.md) para obtener más información.

>[!NOTE]
>
>La ausencia del nodo `srpc`under `/etc/socialconfig` indica el valor predeterminado [Almacén JCR](jsrp.md).
