---
title: Actualización a la versión 6.4 de Comunidades de AEM
seo-title: Actualización a la versión 6.4 de Comunidades de AEM
description: Actualización de una versión anterior a AEM 6.4 Communities
seo-description: Actualización de una versión anterior a AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: a70f874ad7fcae59ee4c6ec20e23ffb2e339590b
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# Actualización a la versión 6.4 de Comunidades de AEM {#upgrading-to-aem-communities}

Dependiendo de la topología y las características de cada sitio, pueden ser necesarias las siguientes acciones al actualizar a AEM Communities 6.4 o instalar el último paquete de funciones.

Esta sección es específica de Comunidades y complementa la información proporcionada en [Actualización a AEM 6.4](../../help/sites-deploying/upgrade.md) (plataforma).

## Actualización desde AEM 6.1 o posterior {#upgrading-from-aem-or-later}

### Reindexar Solr {#reindex-solr}

Al instalar un nuevo paquete de funciones de Communities en una implementación configurada con MSRP, será necesario:

1. Instale el [paquete de funciones más reciente](deploy-communities.md#latestfeaturepack)
2. Instale los [últimos archivos de configuración de Solr](msrp.md#upgrading)
3. Reindexar MSRP

   consulte la sección [Herramienta de reindexación de MSRP](msrp.md#msrp-reindex-tool)

### Habilitación 2.0 {#enablement}

A partir de AEM 6.3, las funciones de habilitación ya no almacenan información de informes en MySQL. La dependencia MySQL está ahí solamente para rastrear contenido SCORM.

Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) para obtener ayuda sobre la migración de contenido desde la Habilitación 1.0.

## Actualización desde AEM 6.0 {#upgrading-from-aem}

Si es necesario conservar UGC preexistente, los medios para hacerlo dependen de si la implementación almacenó UGC [local](#on-premise-storage) o en [Adobe cloud](#adobe-cloud-storage).

### Almacenamiento en la nube de Adobe {#adobe-cloud-storage}

Si el sitio actualizado se configuró para utilizar el almacenamiento en la nube de Adobe, puede aparecer (incorrectamente) como si todos los UGC se hubieran perdido, ya que los métodos SRP no podrán localizar el UGC preexistente en la ubicación antigua.

Por lo tanto, existe la capacidad de indicar a ASRP que utilice `AEM 6.0 compatability-mode` para acceder a UGC.

Para todas las instancias de creación y publicación de AEM 6.3

1. Iniciar sesión con privilegios de administrador
2. Configurar [ASRP](asrp.md)
3. Siga estos pasos para que el UGC preexistente sea visible:
i. Vaya a la consola web, por ejemplo
   [https://&lt;host>:&lt;port> /system/console/](http://localhost:4502/system/console/configMgr)
configMgrii. Localizar la configuración **[!UICONTROL Utilidades de AEM Communities]**
iii. Seleccionar para expandir el panel de configuración
   * *Desmarcar* **`Cloud Storage`**
   * Seleccione **[!UICONTROL Guardar]**

![chlimage_1-126](assets/chlimage_1-126.png)

### Almacenamiento On-Premise {#on-premise-storage}

Si el sitio actualizado no utiliza almacenamiento en la nube, cualquier UGC preexistente debe convertirse para ajustarse a la nueva estructura introducida en AEM comunidades 6.1 en apoyo del almacén común.

Para este fin, hay disponible una herramienta de migración de código abierto en GitHub:\
[Herramienta de migración UGC de AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### API de Java {#java-apis}

Al actualizar de AEM comunidades sociales 6.0 a AEM 6.3 Communities, tenga en cuenta que muchas API se han reorganizado en paquetes diferentes. La mayoría debe resolverse fácilmente al utilizar un IDE para personalizar las funciones de Communities.

Para obtener más información sobre el paquete SocialUtils obsoleto, visite [SocialUtils Refactoring](socialutils.md).

Consulte también [Uso de Maven para Communities](maven.md).

### Sin plantillas de componente JSP {#no-jsp-component-templates}

El [marco de componentes sociales](scf.md) (SCF) utiliza el lenguaje de plantilla [HandlebarsJS](https://handlebarsjs.com/) (HBS) en lugar de las páginas del servidor Java (JSP) utilizadas antes de AEM 6.0.

En AEM 6.0, los componentes JSP permanecieron junto con los nuevos componentes del marco HBS en la misma ubicación, y los componentes HBS normalmente se encuentran en subcarpetas denominadas &quot;hbs&quot;.

A partir de AEM 6.1, los componentes JSP se eliminaron completamente. En el caso de las comunidades, se recomienda reemplazar todo uso de componentes JSP por componentes SCF.

## Herramienta de migración UGC de AEM Communities {#aem-communities-ugc-migration-tool}

La [herramienta de migración UGC de AEM Communities](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) es una herramienta de migración de código abierto disponible en GitHub que se puede personalizar para exportar UGC de versiones anteriores de AEM comunidades sociales e importarlo a AEM Communities 6.1 o posterior.

Además de mover UGC de versiones anteriores, también es posible utilizar la herramienta para mover UGC de un [SRP](working-with-srp.md) a otro, como de MSRP a DSRP.

## Actualización desde AEM 5.6.1 o anterior {#upgrading-from-aem-or-earlier}

Conceptualmente, hay tres generaciones de componentes de comunidades:

**Gen 1**: aproximadamente CQ 5.4 a AEM 5.6.0 - estos son los componentes de  **** colaboración que almacenaron UGC en el repositorio local utilizando la replicación como medio de sincronizar UGC entre plataformas. Otras diferencias incluyen la implementación mediante páginas de servidor Java (JSP), así como la función de blog que consiste en la creación solo en el entorno de creación.

**Gen 2**: de AEM 5.6.1 a AEM 6.1 - se trata de una mezcla de componentes  **** sociales y  **** de colaboración. AEM 6.0 introdujo el nuevo [marco de componentes sociales](scf.md) (SCF) y la AEM 6.2 introdujo un [almacén UGC común](working-with-srp.md) donde se accede a UGC mediante un [proveedor de recursos de almacenamiento](srp.md) (SRP).

**Gen 3**: a partir de AEM 6.2, sólo hay componentes  **** sociales, implementados en SCF como Handlebars (HBS), que requieren una elección de SRP para UGC.
