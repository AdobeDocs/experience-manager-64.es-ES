---
title: Marco de trabajo de etiquetado de AEM
seo-title: AEM Tagging Framework
description: Etiquetar contenido y aprovechar la infraestructura de etiquetado de AEM
seo-description: Tag content and leverage the AEM Tagging infrastructure
uuid: 55ba5977-217b-4b0f-a794-ddb9216ee62b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 4b680d17-383b-4173-a444-0b7bdb24e6c8
feature: Tagging
exl-id: bae592db-dc36-409f-b841-0582c464c3f6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1800'
ht-degree: 1%

---

# Marco de trabajo de etiquetado de AEM{#aem-tagging-framework}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para etiquetar contenido y aprovechar la infraestructura de etiquetado de AEM :

* La etiqueta debe existir como nodo de tipo [`cq:Tag`](#tags-cq-tag-node-type) en el [nodo raíz de taxonomía.](#taxonomy-root-node)
* El nodo de contenido etiquetado `NodeType` debe incluir el [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.
* La variable [TagID](#tagid) se agrega al nodo de contenido [`cq:tags`](#tagged-content-cq-tags-property) y se resuelve en un nodo de tipo [`cq:Tag`.](#tags-cq-tag-node-type)

## Etiquetas : cq:Tag Node Type  {#tags-cq-tag-node-type}

La declaración de una etiqueta se captura en el repositorio en un nodo de tipo `cq:Tag.`

Una etiqueta puede ser una palabra simple (p. ej. `fruit`) o representan una taxonomía jerárquica (p. ej. `fruit/apple`, es decir, frutas en general y la manzana más específica).

Las etiquetas se identifican mediante un TagID único.

Una etiqueta tiene información meta opcional, como un título, títulos localizados y una descripción. El título debe mostrarse en las interfaces de usuario en lugar del `TagID`, cuando esté presente.

El marco de etiquetado también permite restringir el uso de etiquetas predefinidas específicas por parte de los autores y visitantes del sitio.

### Características de las etiquetas {#tag-characteristics}

* El tipo de nodo es `cq:Tag`.
* El nombre del nodo es un componente de la variable [`TagID`.](#tagid)
* La variable [`TagID`](#tagid) siempre incluye un [espacio de nombres.](#tag-namespace)
* Opcional `jcr:title` propiedad (el título que se mostrará en la interfaz de usuario)
* Opcional `jcr:description` property
* Cuando contiene nodos secundarios, se denomina [contenedor .](#container-tags)
* Se almacena en el repositorio debajo de una ruta base denominada [nodo raíz de taxonomía.](#taxonomy-root-node)

### ID de etiqueta {#tagid}

A `TagID` identifica una ruta que se resuelve en un nodo de etiqueta en el repositorio.

Normalmente, la variable `TagID` es un método abreviado que comienza con el área de nombres o puede ser absoluto a partir del [nodo raíz de taxonomía](#taxonomy-root-node).

Cuando el contenido está etiquetado, si aún no existe, la variable [`cq:tags`](#tagged-content-cq-tags-property) se añade al nodo de contenido y a la variable `TagID` se agrega al valor de matriz de cadenas de la propiedad.

La variable `TagID` consiste en un [namespace](#tag-namespace) seguido por el `TagID`. [Etiquetas de contenedor](#container-tags) tienen subetiquetas que representan un orden jerárquico en la taxonomía. Las subetiquetas se pueden usar para hacer referencia a las etiquetas del mismo modo que cualquier etiqueta local `TagID`. Por ejemplo, etiquetar contenido con `fruit` está permitido, incluso si es una etiqueta contenedora con subetiquetas, como `fruit/apple` y `fruit/banana`.

### Nodo raíz de taxonomía {#taxonomy-root-node}

El nodo raíz de taxonomía es la ruta base para todas las etiquetas del repositorio. El nodo raíz de taxonomía no debe ser de tipo `cq:Tag`.

En AEM, la ruta base es `/content/cq:tags` y el nodo raíz es del tipo `cq:Folder`.

### Área de nombres de la etiqueta {#tag-namespace}

Los espacios de nombres permiten agrupar elementos. El caso de uso más típico es tener un área de nombres por sitio (por ejemplo, pública, interna y portal) o por aplicación más grande (por ejemplo, Sitios, Recursos, Forms), pero las áreas de nombres se pueden usar para otras necesidades. Los espacios de nombres se utilizan en la interfaz de usuario para mostrar solo el subconjunto de etiquetas (es decir, etiquetas de un determinado espacio de nombres) que se aplica al contenido actual.

El espacio de nombres de la etiqueta es el primer nivel del subárbol de taxonomía, que es el nodo inmediatamente inferior al [nodo raíz de taxonomía](#taxonomy-root-node). Un área de nombres es un nodo de tipo `cq:Tag` cuyo padre no es un `cq:Tag` tipo de nodo.

Todas las etiquetas tienen un espacio de nombres. Si no se especifica ningún espacio de nombres, la etiqueta se asigna al espacio de nombres predeterminado, que es `TagID` `default` (el título es `Standard Tags`) que es `/content/cq:tags/default`.

### Etiquetas de contenedor {#container-tags}

Una etiqueta contenedora es un nodo de tipo `cq:Tag` que contenga cualquier número y tipo de nodos secundarios, lo que permite mejorar el modelo de etiquetas con metadatos personalizados.

Además, las etiquetas de contenedor (o superetiquetas) de una taxonomía sirven como subsuma de todas las subetiquetas. Por ejemplo, contenido etiquetado con `fruit/apple` se considera que está etiquetado con `fruit` también. Esto significa que la búsqueda de contenido solo está etiquetada con `fruit` también encontrará el contenido etiquetado con `fruit/apple`.

### Resolución de TagID {#resolving-tagids}

Si el ID de etiqueta contiene dos puntos `:`, los dos puntos separan el área de nombres de la etiqueta o subtaxonomía, que luego se separan con barras inclinadas normales `/`. Si el ID de etiqueta no tiene dos puntos, se da a entender el espacio de nombres predeterminado.

La ubicación estándar y única de las etiquetas es inferior a `/content/cq:tags`.

Etiquetado que hace referencia a rutas o rutas no existentes que no apuntan a una `cq:Tag` se consideran no válidos y se ignoran.

La siguiente tabla muestra algunos ejemplos `TagIDs`, sus elementos y cómo `TagID` responde a una ruta absoluta en el repositorio.

| `TagID` | Espacio de nombres | ID local | Etiquetas de contenedores | Etiqueta de hoja | Ruta absoluta del repositorio |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Ninguno | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Ninguno | Ninguno | Ninguno | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Localización del título de la etiqueta {#localization-of-tag-title}

Cuando la etiqueta incluye la cadena de título opcional (`jcr:title`) es posible localizar el título para mostrar añadiendo la propiedad `jcr:title.<locale>`.

Para obtener más información, consulte:

* [Etiquetas en diferentes idiomas,](/help/sites-developing/building.md#tags-in-different-languages) que describe el uso de las API.
* [Administración de etiquetas en diferentes idiomas,](/help/sites-administering/tags.md#managing-tags-in-different-languages) que describe el uso de la consola Etiquetado .

### Control de acceso {#access-control}

Las etiquetas existen como nodos en el repositorio en el [nodo raíz de taxonomía.](#taxonomy-root-node) Permitir o denegar a los autores y visitantes del sitio la capacidad de crear etiquetas en un espacio de nombres determinado se puede lograr estableciendo las ACL adecuadas en el repositorio.

Además, negar permisos de lectura para ciertas etiquetas o áreas de nombres controlará la capacidad de aplicar etiquetas a contenido específico.

Una configuración típica incluye:

* Permitiendo el `tag-administrators` acceso de escritura de grupo/función a todas las áreas de nombres (añadir/modificar en `/content/cq:tags`).
   * Este grupo viene con AEM listo para usar.
* Permitir que los usuarios/autores lean acceso a todas las áreas de nombres que deberían ser legibles para ellos (en su mayoría, todas).
* Permitir que los usuarios/autores escriban acceso a las áreas de nombres en las que los usuarios/autores deben definir las etiquetas libremente (`add_node` under `/content/cq:tags/some_namespace`)

## Contenido etiquetable : cq:Mezcla etiquetable {#taggable-content-cq-taggable-mixin}

Para que los desarrolladores de aplicaciones puedan adjuntar etiquetas a un tipo de contenido, el registro del nodo ([CND](https://jackrabbit.apache.org/node-type-notation.html)) debe incluir el `cq:Taggable` mezcla o `cq:OwnerTaggable` mixin.

La variable `cq:OwnerTaggable` mixin, que hereda de `cq:Taggable`, está pensado para indicar que el contenido puede ser clasificado por el propietario/autor. En AEM, solo es un atributo de la variable `cq:PageContent` nodo . La variable `cq:OwnerTaggable` la mezcla no es necesaria para el marco de etiquetado.

>[!NOTE]
>
>Se recomienda habilitar únicamente las etiquetas en el nodo de nivel superior de un elemento de contenido agregado (o en su `jcr:content` nodo ). Algunos ejemplos son:
>
>* Páginas ( `cq:Page`) donde la variable `jcr:content`el nodo es de tipo `cq:PageContent` que incluye el `cq:Taggable` mixin.
>* Recursos ( `cq:Asset`) donde la variable `jcr:content/metadata` el nodo siempre tiene la variable `cq:Taggable` mixin.


### Anotación de tipo de nodo (CND) {#node-type-notation-cnd}

Las definiciones de Tipo de nodo existen en el repositorio como archivos CND. La notación CND se define como parte de la documentación de JCR [here](https://jackrabbit.apache.org/node-type-notation.html).

Las definiciones esenciales para los tipos de nodo incluidos en AEM son las siguientes:

```text
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Contenido etiquetado: cq:tags (propiedad) {#tagged-content-cq-tags-property}

La variable `cq:tags` es una matriz de cadenas que se utiliza para almacenar una o más `TagID`s cuando los autores o los visitantes del sitio los aplican al contenido. La propiedad solo tiene significado cuando se agrega a un nodo que se define con la variable [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.

>[!NOTE]
>
>Para aprovechar AEM funcionalidad de etiquetado, las aplicaciones desarrolladas a medida no deben definir propiedades de etiqueta que no sean `cq:tags`.

## Mover y combinar etiquetas {#moving-and-merging-tags}

A continuación, se muestra una descripción de los efectos que se producen en el repositorio al mover o combinar etiquetas utilizando la variable [Consola de etiquetado](/help/sites-administering/tags.md):

* Cuando una etiqueta A se mueve o combina en la etiqueta B debajo de `/content/cq:tags`:

   * La etiqueta A no se elimina y obtiene un `cq:movedTo` propiedad.
   * La etiqueta B se crea (en caso de un movimiento) y obtiene un `cq:backlinks` propiedad.

* `cq:movedTo` apunta a la etiqueta B.

   * Esta propiedad significa que la etiqueta A se ha movido o combinado en la etiqueta B.
   * Al mover la etiqueta B se actualizará esta propiedad según corresponda. Por lo tanto, la etiqueta A está oculta y solo se mantiene en el repositorio para resolver los ID de etiqueta en los nodos de contenido que apuntan a la etiqueta A.
   * El recolector de residuos de etiquetas elimina etiquetas como la etiqueta A una vez que más nodos de contenido no señalan a ellas.
   * Un valor especial para la variable `cq:movedTo` la propiedad es `nirvana`: se aplica cuando se elimina la etiqueta, pero no se puede eliminar del repositorio porque hay subetiquetas con un `cq:movedTo` eso debe mantenerse.

      >[!NOTE]
      >
      >La variable `cq:movedTo` solo se agrega a la etiqueta movida o combinada si se cumple cualquiera de estas condiciones:
      >
      >1. La etiqueta se utiliza en el contenido (lo que significa que tiene una referencia).
      >1. La etiqueta tiene elementos secundarios que ya se han movido.


* `cq:backlinks` mantiene las referencias en la otra dirección, es decir, mantiene una lista de todas las etiquetas que se han movido a la etiqueta B o que se han combinado con ella.

   * Esto es necesario principalmente para mantener `cq:movedTo`propiedades actualizadas cuando la etiqueta B también se mueve, combina o elimina, o cuando la etiqueta B está activada, en cuyo caso todas sus etiquetas backlinks también deben activarse.

>[!NOTE]
>
>La variable `cq:backlinks` solo se agrega a la etiqueta movida o combinada si se cumple cualquiera de estas condiciones:
>
>1. La etiqueta se utiliza en el contenido (lo que significa que tiene una referencia).
>1. La etiqueta tiene elementos secundarios que ya se han movido.


* Leer un `cq:tags` la propiedad de un nodo de contenido implica la siguiente resolución:

   1. Si no hay coincidencia en `/content/cq:tags`, no devuelve ninguna etiqueta.
   1. Si la etiqueta tiene un `cq:movedTo` conjunto de propiedades, se sigue el ID de etiqueta al que se hace referencia.

      * Este paso se repite siempre y cuando la etiqueta siguiente tenga una `cq:movedTo` propiedad.
   1. Si la etiqueta siguiente no tiene un valor `cq:movedTo` , se lee la etiqueta .


* Para publicar el cambio cuando una etiqueta se ha movido o combinado, la variable `cq:Tag` y todos sus vínculos secundarios deben replicarse.
   * Esto se realiza automáticamente cuando la etiqueta está activada en la consola de administración de etiquetas.

* Actualizaciones posteriores en el informe `cq:tags` limpie automáticamente las referencias &quot;antiguas&quot;.
   * Esto se activa porque la resolución de una etiqueta movida a través de la API devuelve la etiqueta de destino, proporcionando así el ID de etiqueta de destino.

## Migración de etiquetas {#tags-migration}

A partir de Adobe Experience Manager 6.4, las etiquetas se almacenan en `/content/cq:tags`. Sin embargo, en los casos en que Adobe Experience Manager se haya actualizado desde la versión anterior, las etiquetas siguen presentes en la ubicación antigua `/etc/tags`. En sistemas actualizados, es necesario migrar las etiquetas a `/content/cq:tags`.

>[!NOTE]
>
>En la página Propiedades de página de etiquetas , se recomienda utilizar el ID de etiqueta (por ejemplo `geometrixx-outdoors:activity/biking`) en lugar de codificar la ruta de base de etiquetas (por ejemplo, `/etc/tags/geometrixx-outdoors/activity/biking`).
>
>Para enumerar etiquetas, `com.day.cq.tagging.servlets.TagListServlet` se puede usar.

>[!NOTE]
>
>Se recomienda utilizar la API del administrador de etiquetas como recurso.

### Si la instancia de AEM actualizada es compatible con la API de TagManager**

1. Al principio del componente, la API de TagManager detecta si se trata de una instancia de AEM actualizada. En el sistema actualizado, las etiquetas se almacenan en `/etc/tags`.

1. A continuación, la API de TagManager se ejecuta en modo de compatibilidad con versiones anteriores, lo que significa que la API utiliza `/etc/tags` como ruta base. Si no es así, utiliza una nueva ubicación `/content/cq:tags`.

1. Actualice la ubicación de las etiquetas.

1. Después de migrar las etiquetas a la nueva ubicación, ejecute la siguiente secuencia de comandos.

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
        def tagPath = node.path;
        println "tag = ${tagPath}";

        if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags")){

                def movedTo = node.getProperty("cq:movedTo").getValue().toString();

                println "cq:movedTo = ${movedTo} \n";

                movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
                node.setProperty("cq:movedTo",movedTo);
        } else if(node.hasProperty("cq:backlinks")){

               String[] backLinks = node.getProperty("cq:backlinks").getValues();
               int count = 0;

               backLinks.each { value ->
                       if(value.startsWith("/etc/tags")){
                               println "cq:backlinks = ${value}\n";
                               backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
                       count++;
               }

               node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

La secuencia de comandos recupera todas las etiquetas que tienen `/etc/tags` en el valor de `cq:movedTo/cq:backLinks` propiedad. A continuación, se repite a través del conjunto de resultados recuperados y resuelve el `cq:movedTo` y `cq:backlinks` valores de propiedad a `/content/cq:tags` rutas (en caso de que `/etc/tags` se detecta en el valor ).

### Si la instancia de AEM actualizada se ejecuta en la IU clásica**

>[!NOTE]
>
>La IU clásica no es compatible con el tiempo de inactividad cero y no admite la nueva ruta de base de etiquetas. Si desea utilizar la IU clásica que `/etc/tags` debe crearse seguido de `cq-tagging` reiniciar el componente.

En caso de que las instancias de AEM actualizadas sean compatibles con la API de TagManager y se ejecuten en la IU clásica:

1. Una vez hace referencia a la ruta de base de etiquetas antigua `/etc/tags` se reemplazan utilizando tagId o una nueva ubicación de etiqueta `/content/cq:tags`, puede migrar etiquetas a la nueva ubicación `/content/cq:tags` en CRX DE seguido del reinicio de componentes.

1. Después de migrar las etiquetas a la nueva ubicación, ejecute el script mencionado anteriormente.
