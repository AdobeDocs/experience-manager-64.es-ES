---
title: Elementos esenciales de SRP y UGC
seo-title: SRP and UGC Essentials
description: Resumen del proveedor de recursos de almacenamiento y contenido generado por el usuario
seo-description: Storage resource provider and user-generated content overview
uuid: a4ee8725-f554-4fcf-ac1e-34878d6c02f8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0763f236-5648-49e9-8a24-dbc8f4c77ee3
exl-id: 45b9d418-0ecb-44c9-8091-b9ce29ba730b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 1%

---

# Elementos esenciales de SRP y UGC {#srp-and-ugc-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Introducción {#introduction}

Si no está familiarizado con el proveedor de recursos de almacenamiento (SRP) y su relación con el contenido generado por el usuario (UGC), visite [Almacenamiento de contenido de la comunidad](working-with-srp.md) y [Información general del proveedor de recursos de almacenamiento](srp.md).

Esta sección de la documentación proporciona información esencial sobre SRP y UGC.

## API StorageResourceProvider {#storageresourceprovider-api}

La API de SocialResourceProvider (API SRP) es una extensión de varias API de proveedores de recursos Sling. Incluye compatibilidad con paginación e incremento atómico (útil para contar y anotar).

Las consultas son necesarias para los componentes de SCF, ya que es necesario ordenar por fecha, utilidad, número de votos, etc. Todas las opciones de SRP tienen mecanismos de consulta flexibles que no dependen de la creación de contenedores.

La ubicación de almacenamiento SRP incorpora la ruta de acceso del componente. La API de SRP siempre debe utilizarse para acceder a UGC, ya que la ruta raíz depende de la opción de SRP seleccionada, como ASRP, MSRP o JSRP.

La API de SRP no es una clase abstracta, es una interfaz. Una implementación personalizada no debería emprenderse a la ligera, ya que los beneficios de futuras mejoras en las implementaciones internas se perderían al actualizar a una nueva versión.

Los medios para usar la API de SRP son a través de las utilidades proporcionadas, como las que se encuentran en el paquete SocialResourceUtilities .

Al actualizar desde AEM 6.0 o anterior, será necesario migrar UGC para todos los SRP, para los que hay una herramienta de código abierto disponible. Consulte [Actualización a AEM Communities 6.3](upgrade.md).

>[!NOTE]
>
>Históricamente, las utilidades para acceder a UGC se encontraban en el paquete SocialUtils , que ya no existe.
>
>Para ver las utilidades de reemplazo, consulte [Refactorización de SocialUtils](socialutils.md).

## Método de utilidad para acceder a UGC {#utility-method-to-access-ugc}

Para acceder a UGC, utilice un método del paquete SocialResourceUtilities que devuelve una ruta adecuada para acceder a UGC desde SRP y reemplaza el método obsoleto que se encuentra en el paquete SocialUtils.

A continuación se muestra un ejemplo mínimo de uso del método resourceToUGCStoragePath() en un servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String ugcPath = socialResourceUtilities.resourceToUGCStoragePath(request.getResource());
  // rest of servlet
}
```

Para otras sustituciones de SocialUtils, consulte [Refactorización de SocialUtils](socialutils.md).

Para obtener instrucciones de codificación, visite [Acceso a UGC con SRP](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>La ruta que devuelve resourceToUGCStoragePath() *no es *adecuada para [Comprobación de ACL](srp.md#for-access-control-acls).

## Método de utilidad para acceder a ACL {#utility-method-to-access-acls}

Algunas implementaciones de SRP, como ASRP y MSRP, almacenan contenido de la comunidad en bases de datos que no proporcionan verificación de ACL. Los nodos de sombra proporcionan una ubicación en el repositorio local al que se pueden aplicar las ACL.

Con la API de SRP, todas las opciones de SRP realizan la misma comprobación de la ubicación de sombra antes de todas las operaciones de CRUD.

Para comprobar las ACL, utilice un método que devuelva una ruta adecuada para comprobar los permisos aplicados al UGC del recurso.

A continuación se muestra un ejemplo sencillo de uso del método resourceToACLPath() en un servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String aclPath = socialResourceUtilities.resourceToACLPath(request.getResource());
  // rest of servlet
}
```

>[!CAUTION]
>
>La ruta devuelta por resourceToACLPath() *no es *adecuada para [acceso a UGC](#utility-method-to-access-acls) en sí.

## Ubicaciones de almacenamiento de información relacionadas con UGC {#ugc-related-storage-locations}

Las siguientes descripciones de la ubicación de almacenamiento pueden ser de ayuda cuando se desarrolla con el JSRP o tal vez con el MSRP. Actualmente no hay ninguna interfaz de usuario para acceder a UGC almacenado en ASRP, ya que existe para JSRP ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) y MSRP (herramientas MongoDB).

**ubicación de los componentes**

Cuando un miembro introduce UGC en el entorno de publicación, interactúa con un componente como parte de un sitio AEM.

Un ejemplo de este componente es el [componente comentarios](http://localhost:4502/content/community-components/en/comments.html) que existe en la variable [Guía de componentes de comunidad](components-guide.md) sitio. La ruta al nodo de comentarios en el repositorio local es:

* Ruta del componente = */content/community-components/es/comments/jcr:content/content/inclusible/comments*

**ubicación del nodo sombra**

La creación de UGC también crea un [nodo sombra](srp.md#about-shadow-nodes-in-jcr) a los que se aplican las ACL necesarias. La ruta al nodo de sombra correspondiente en el repositorio local es el resultado de anteponer la ruta raíz del nodo de sombra a la ruta del componente:

* Ruta raíz = /content/usergenerated
* nodo de sombra de comentario = /content/usergenerated/content/community-components/es/comments/jcr:content/content/inclusible/comments

**Ubicación de UGC**

El UGC se crea en ninguna de esas ubicaciones y solo se debe acceder a él mediante un [método de utilidad](#utility-method-to-access-ugc) que invoca la API de SRP.

* Ruta raíz = /content/usergenerated/asi/srp-choice
* Nodo UGC para JSRP = /content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/inclusible/comments/srzd-let_it_be_

*Tenga en cuenta*, para JSRP, el nodo UGC *only* estar presente en la instancia de AEM (autor o publicación) en la que se introdujo. Si se introduce en una instancia de publicación, la moderación no será posible desde la consola de moderación del autor.

## Información relacionada {#related-information}

* [Información general del proveedor de recursos de almacenamiento](srp.md) - Introducción y descripción general del uso del repositorio
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización de SocialUtils](socialutils.md) - Asignación de métodos de utilidad obsoletos a los métodos de utilidad SRP actuales
