---
title: Referencia de predicados del generador de consultas
seo-title: Query Builder Predicate Reference
description: Referencia de predicado completa para la API de Query Builder.
seo-description: Complete predicate reference for the Query Builder API.
uuid: af0e269e-7d52-4032-b22e-801c7b5dccfa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 94a05894-743a-4ace-a292-bfee90ba9068
exl-id: 2bcc2be9-1e8a-44b5-add2-370b9ff80de8
source-git-commit: 31d6111a82a3cbfef22970d05280b0d3fd1c0de7
workflow-type: tm+mt
source-wordcount: '2310'
ht-degree: 3%

---

# Referencia de predicados del generador de consultas{#query-builder-predicate-reference}

## General {#general}

* [root](#root)
* [grupo](#group)
* [orderby](#orderby)

## Predicados {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [excludepaths](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [texto completo](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [language](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [mainasset](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [memberOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodename](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [path](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [propiedad](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [savedquery](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [similar](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [etiqueta](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagsearch](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [tipo](/help/sites-developing/querybuilder-predicate-reference.md#type)

### boolproperty {#boolproperty}

Coincide con las propiedades BOOLEAN de JCR. Solo acepta los valores &quot; `true`&quot; y &quot; `false`&quot;. En el caso de &quot; `false`&quot;, coincidir?? si la propiedad tiene el valor &quot; `false`&quot; o si no existe en absoluto. Esto puede resultar ??til para comprobar los indicadores booleanos que solo se establecen cuando est??n activados.

El par??metro heredado &quot; `operation`&quot; no tiene significado.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada valor `true` o `false`, pero solo para las propiedades existentes.

#### Propiedades {#properties}

* ****
boolpropertyrelativamente path to property, por ejemplo 
`myFeatureEnabled` o `jcr:content/myFeatureEnabled`

* ****
valor para comprobar la propiedad, &quot; 
`true`&quot; o &quot; `false`&quot;

### contentfragment {#contentfragment}

Restringe el resultado a fragmentos de contenido.

No admite el filtrado.

No admite la extracci??n de facetas.

#### Propiedades {#properties-1}

* ****
contentfragmentSe puede utilizar con cualquier valor para comprobar si hay fragmentos de contenido.

### dateComparison {#datecomparison}

Compara dos propiedades JCR DATE entre s??. Puede comprobar si son iguales, desiguales, buenos o buenos que o iguales.

Se trata de un predicado de solo filtrado y no puede aprovechar un ??ndice de b??squeda.

#### Propiedades {#properties-2}

* **property1**

   ruta a la propiedad first date

* **property2**

   ruta a la propiedad de segunda fecha

* **operation**

   &quot; `=`&quot; para la coincidencia exacta, &quot; `!=`&quot; para la comparaci??n de desigualdad, &quot; `>`&quot; para la propiedad1 buena que la propiedad2, &quot; `>=`&quot; para la propiedad1 buena o igual a la propiedad2. El valor predeterminado es &quot; `=`&quot;.

### daterange {#daterange}

Coincide con las propiedades de FECHA JCR con un intervalo de fecha y hora. Utiliza la norma ISO8601\
formato para fechas y horas ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) y tambi??n permite representaciones parciales, como `YYYY-MM-DD`. Alternativamente, la marca de tiempo se puede proporcionar como n??mero de milisegundos desde 1970 en la zona horaria UTC, el formato de tiempo unix.

Puede buscar cualquier cosa entre dos marcas de tiempo, cualquier cosa m??s reciente o anterior que una fecha determinada, y tambi??n elegir entre intervalos abiertos e inclusivos.

Admite la extracci??n de facetas. Proporcionar?? bloques &quot;hoy&quot;, &quot;esta semana&quot;, &quot;este mes&quot;, &quot;??ltimos 3 meses&quot;, &quot;este a??o&quot;, &quot;el a??o pasado&quot; y &quot;anteriores al a??o pasado&quot;.

No admite el filtrado.

#### Propiedades {#properties-3}

* **propiedad**

   ruta relativa a una propiedad `DATE`, por ejemplo `jcr:lastModified`

* **lowerBound**

   fecha inferior enlazada para comprobar la propiedad, por ejemplo `2014-10-01`

* **lowerOperation**

   &quot; `>`&quot; (m??s reciente) o &quot; `>=`&quot; (m??s reciente o m??s reciente), se aplica a `lowerBound`. El valor predeterminado es &quot; `>`&quot;.

* **upperBound**

   l??mite superior para comprobar la propiedad, por ejemplo `2014-10-01T12:15:00`

* **upperOperation**

   &quot; `<`&quot; (anterior) o &quot; `<=`&quot; (anterior o anterior), se aplica a `upperBound`. El valor predeterminado es &quot; `<`&quot;.

* **timeZone**

   ID de la zona horaria que se debe usar cuando no se proporcione como cadena de fecha ISO-8601. El valor predeterminado es la zona horaria predeterminada del sistema.

### excludepaths {#excludepaths}

Excluye los nodos del resultado donde su ruta coincide con una expresi??n regular.

Se trata de un predicado de solo filtrado y no puede aprovechar un ??ndice de b??squeda.

No admite la extracci??n de facetas.

#### Propiedades {#properties-4}

* **excludepaths**

   la expresi??n regular coincide con las rutas de resultados, excluyendo las coincidentes del resultado.

### texto completo {#fulltext}

Busca t??rminos en el ??ndice de texto completo.

No admite el filtrado.

No admite la extracci??n de facetas.

#### Propiedades {#properties-5}

* **texto completo**

   los t??rminos de b??squeda de texto completo

* **relPath**

   la ruta relativa para buscar en la propiedad o subnodo. Esta propiedad es opcional.

### grupo {#group}

Permite crear condiciones anidadas. Los grupos pueden contener grupos anidados. Todo en una consulta querybuilder est?? impl??citamente en un grupo ra??z, que tambi??n puede tener par??metros `p.or` y `p.not`.

Ejemplo para hacer coincidir una de las dos propiedades con un valor:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Conceptualmente es `(1_property` O `2_property)`.

Ejemplo para grupos anidados:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Esto busca el t??rmino &quot;**Administraci??n**&quot; dentro de las p??ginas en `/content/geometrixx/en` o en los recursos en `/content/dam/geometrixx`.

Conceptualmente es `fulltext AND ( (path AND type) OR (path AND type) )`. Tenga en cuenta que estas uniones O necesitan buenos ??ndices para el rendimiento.

#### Propiedades {#properties-6}

* **p.o**

   si se establece en &quot; `true`&quot;, solo debe coincidir un predicado del grupo. El valor predeterminado es &quot; `false`&quot;, lo que significa que todas deben coincidir

* **p.not**

   si se establece en &quot; `true`&quot;, anula el grupo (el valor predeterminado es &quot; `false`&quot;)

* **&lt;predicate>**

   agrega predicados anidados

* **N_&lt;predicate>**

   agrega varios predicados anidados del mismo tiempo, como `1_property, 2_property, ...`

### hasPermission {#haspermission}

Restringe el resultado a elementos en los que la sesi??n actual tiene los [privilegios JCR](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) especificados.

Se trata de un predicado de solo filtrado y no puede aprovechar un ??ndice de b??squeda. No admite la extracci??n de facetas.

#### Propiedades {#properties-7}

* **hasPermission**

   privilegios JCR separados por comas que la sesi??n de usuario actual debe tener ALL para el nodo en cuesti??n; por ejemplo `jcr:write`, `jcr:modifyAccessControl`

### language {#language}

Busca p??ginas de CQ en un idioma espec??fico. Esto examina tanto la propiedad idioma de la p??gina como la ruta de la p??gina, que a menudo incluye el idioma o la configuraci??n regional en una estructura de sitio de nivel superior.

Se trata de un predicado de solo filtrado y no puede aprovechar un ??ndice de b??squeda.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada c??digo de idioma ??nico.

#### Propiedades {#properties-8}

* **language**

   C??digo de idioma ISO, por ejemplo &quot; `de`&quot;

### mainasset {#mainasset}

Comprueba si un nodo es un recurso principal DAM y no un subrecurso. B??sicamente se trata de todos los nodos que no est??n dentro de un nodo de &quot;subactivos&quot;. Tenga en cuenta que esto no comprueba el tipo de nodo `dam:Asset`. Para utilizar este predicado, simplemente configure &quot; `mainasset=true`&quot; o &quot; `mainasset=false`&quot;, no hay m??s propiedades.

Se trata de un predicado de solo filtrado y no puede aprovechar un ??ndice de b??squeda.

Admite la extracci??n de facetas. Proporcionar?? 2 bloques para los recursos principales y subactivos.

#### Propiedades {#properties-9}

* **mainasset**

   booleano, &quot; `true`&quot; para recursos principales, &quot; `false`&quot; para subrecursos

### memberOf {#memberof}

Busca elementos que son miembros de una [colecci??n de recursos de sling](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) espec??fica.

Se trata de un predicado de solo filtrado y no puede aprovechar un ??ndice de b??squeda. No admite la extracci??n de facetas.

#### Propiedades {#properties-10}

* **memberOf**

   ruta de la recopilaci??n de recursos de Sling

### nodename {#nodename}

Coincide con los nombres de nodo de JCR.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada nombre de nodo ??nico (nombre de archivo).

#### Propiedades {#properties-11}

* **nodename**

   patr??n de nombre de nodo que permite comodines: `*` = cualquier car??cter o no, `?` = cualquier car??cter, `[abc]` = solo caracteres entre corchetes

### notexpired {#notexpired}

Coincide con elementos comprobando si una propiedad JCR DATE es buena o igual a la hora del servidor actual. Esto se puede usar para comprobar una propiedad de fecha de tipo &quot; `expiresAt`&quot; y limitar solo a las que a??n no han caducado ( `notexpired=true`) o que ya han caducado ( `notexpired=false`).

No admite el filtrado.

Admite la extracci??n de facetas del mismo modo que el predicado de intervalo de fechas.

#### Propiedades {#properties-12}

* **notexpired**

   booleano, &quot; `true`&quot; para a??n no caducado (fecha futura o igual), &quot; `false`&quot; para caducado (fecha anterior) (obligatorio)

* **propiedad**

   ruta relativa a la propiedad `DATE` para comprobar (obligatorio)

### orderby {#orderby}

Permite ordenar el resultado. Si se requiere ordenar por varias propiedades, este predicado debe agregarse varias veces utilizando el prefijo num??rico, como `1_orderby=first`, `2_oderby=second`.

#### Propiedades {#properties-13}

* **orderby**

   o bien el nombre de la propiedad JCR indicado por un @ inicial, por ejemplo `@jcr:lastModified` o `@jcr:content/jcr:title`, u otro predicado en la consulta, por ejemplo `2_property`, en el que ordenar

* **ordenar**

   direcci??n de clasificaci??n, ya sea &quot; `desc`&quot; para descendente o &quot; `asc`&quot; para ascendente (predeterminado)

* **case**

   si se establece en &quot; `ignore`&quot;, la clasificaci??n no distingue entre may??sculas y min??sculas, lo que significa que &quot;a&quot; viene antes que &quot;B&quot;; si est?? vac??o o no se tiene en cuenta, la ordenaci??n distingue entre may??sculas y min??sculas, lo que significa que &quot;B&quot; viene antes que &quot;a&quot;.

### ruta {#path}

B??squedas dentro de una ruta determinada.

No admite la extracci??n de facetas.

#### Propiedades {#properties-14}

* **path**

   patr??n de ruta; dependiendo de lo exacto, el sub??rbol completo coincidir?? (como anexar `//*` en xpath, pero tenga en cuenta que esto no incluye la ruta base) (exacto=false, predeterminado) o solo coincidir?? una ruta exacta, que puede incluir caracteres comod??n ( `*`); si se establece self, se buscar?? en todo el sub??rbol, incluido el nodo base

* **exacto**

   si `exact` es true/on, la ruta exacta debe coincidir, pero puede contener comodines simples ( `*`), que coincidan con nombres, pero no &quot; `/`&quot;; si es false (predeterminado), se incluyen todos los descendientes (opcional)

* **plano**

   busca solo los elementos secundarios directos (como anexar &quot; `/*`&quot; en xpath) (solo se usa si &quot; `exact`&quot; no es verdadero, opcional)

* **self**

   busca en el sub??rbol pero incluye el nodo base dado como ruta (sin comodines)

### propiedad {#property}

Coincide con las propiedades JCR y sus valores.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada valor de propiedad ??nico en los resultados.

#### Propiedades {#properties-15}

* **propiedad**

   ruta relativa a la propiedad, por ejemplo `jcr:title`

* **seleccionado**

   valor para comprobar la propiedad; sigue al tipo de propiedad JCR a las conversiones de cadena

* **N_value**

   utilice `1_value`, `2_value`, ... para comprobar si hay varios valores (combinados con `OR` de forma predeterminada, con `AND` si y=true) (desde 5.3)

* **y**

   se establece en true para combinar varios valores ( `N_value`) con AND (desde 5.3)

* **operation**

   &quot; `equals`&quot; para coincidencia exacta (predeterminada), &quot; `unequals`&quot; para comparaci??n de desigualdad, &quot; `like`&quot; para usar la funci??n xpath `jcr:like` (opcional), &quot; `not`&quot; para no coincidir (p. ej. &quot; `not(@prop)`&quot; en xpath, se ignorar?? el par??metro de valor) o &quot; `exists`&quot; para la comprobaci??n de existencia (el valor puede ser true - la propiedad debe existir, el valor predeterminado - o false - igual que &quot; `not`&quot;)

* **depth**

   n??mero de niveles comod??n debajo de los cuales puede existir la propiedad/ruta relativa (por ejemplo, `property=size depth=2` comprobar?? el nodo/tama??o, nodo/&amp;ast;/size y nodo/&amp;ast;/&amp;ast;/size)

### rangeproperty {#rangeproperty}

Coincide con una propiedad JCR con un intervalo. Esto se aplica a propiedades con tipos lineales como `LONG`, `DOUBLE` y `DECIMAL`. Para `DATE` consulte el predicado de intervalo de fechas que ha optimizado la entrada de formato de fecha.

Puede definir un l??mite inferior y un l??mite superior o solo uno de ellos. La operaci??n (p. ej. &quot;menor que&quot; o &quot;menor o igual que&quot;) tambi??n se pueden especificar individualmente para los l??mites inferior y superior.

No admite la extracci??n de facetas.

#### Propiedades {#properties-16}

* **propiedad**

   ruta relativa a la propiedad

* **lowerBound**

   l??mite inferior para comprobar la propiedad

* **lowerOperation**

   &quot; `>`&quot; (predeterminado) o &quot; `>=`&quot;, se aplica a `lowerValue`

* **upperBound**

   l??mite superior para comprobar la propiedad

* **upperOperation**

   &quot; `<`&quot; (predeterminado) o &quot; `<=`&quot;, se aplica a `lowerValue`

* **decimal**

   &quot; `true`&quot; si la propiedad marcada es del tipo Decimal

### relativedaterange {#relativedaterange}

Coincide con las propiedades `JCR DATE` con un intervalo de fecha y hora mediante desplazamientos de tiempo relativos a la hora actual del servidor. Puede especificar `lowerBound` y `upperBound` utilizando un valor de milisegundos o la sintaxis de barras `1s 2m 3h 4d 5w 6M 7y` (un segundo, dos minutos, tres horas, cuatro d??as, cinco semanas, seis meses, siete a??os). Prefijo con &quot; `-`&quot; para indicar un desplazamiento negativo antes de la hora actual. Si solo especifica `lowerBound` o `upperBound`, el otro tendr?? el valor predeterminado 0, es decir, la hora actual.

Por ejemplo:

* `upperBound=1h` (y no  `lowerBound`) seleccionar??a cualquier cosa en la siguiente hora
* `lowerBound=-1d` (y no  `upperBound`) seleccionar??a nada en las ??ltimas 24 horas
* `lowerBound=-6M` y  `upperBound=-3M` seleccionar??a cualquier cosa de 6 meses a 3 meses de edad
* `lowerBound=-1500` y  `upperBound=5500` seleccionar??a cualquier cosa entre 1500 milisegundos en el pasado y 5500 milisegundos en el futuro
* `lowerBound=1d` y  `upperBound=2d` seleccionar??a cualquier cosa en el d??a siguiente a ma??ana

Tenga en cuenta que no toma a??os bisiestos en consideraci??n y que todos los meses son 30 d??as.

No admite el filtrado.

Admite la extracci??n de facetas del mismo modo que el predicado de intervalo de fechas.

#### Propiedades {#properties-17}

* **upperBound**

   l??mite de fecha superior en milisegundos o `1s 2m 3h 4d 5w 6M 7y` (un segundo, dos minutos, tres horas, cuatro d??as, cinco semanas, seis meses, siete a??os) en relaci??n con el tiempo del servidor actual, utilice &quot;-&quot; para el desplazamiento negativo

* **lowerBound**

   fecha menor enlazada en milisegundos o `1s 2m 3h 4d 5w 6M 7y` (un segundo, dos minutos, tres horas, cuatro d??as, cinco semanas, seis meses, siete a??os) en relaci??n con el tiempo actual del servidor, utilice &quot;-&quot; para el desplazamiento negativo

### root {#root}

Grupo de predicados ra??z. Admite todas las funciones de un grupo y permite establecer par??metros de consulta globales.

El nombre &quot;root&quot; nunca se utiliza en una consulta, est?? impl??cito.

#### Propiedades {#properties-18}

* **p.offset**

   n??mero que indica el inicio de la p??gina de resultados, es decir, cu??ntos elementos se deben omitir

* **p.limit**

   n??mero que indica el tama??o de la p??gina

* **p.supongoTotal**

   recomendado: evite calcular el total del resultado completo, que puede resultar costoso; un n??mero que indica el total m??ximo que se va a contar (por ejemplo, 1000, un n??mero que proporciona a los usuarios suficientes comentarios sobre el tama??o aproximado y los n??meros exactos para resultados m??s peque??os) o &quot; `true`&quot; para contar solo hasta el m??nimo necesario `p.offset` + `p.limit`

* **p.excerpt**

   si se configura como &quot; `true`&quot;, incluya el extracto de texto completo en el resultado

* **p.hits**

   (solo para el servlet JSON) seleccione la forma en que se escriben las visitas como JSON, con estas visitas est??ndar (ampliables mediante el servicio ResultHitWriter):

   * **simple**:

      elementos m??nimos como `path`, `title`, `lastmodified`, `excerpt` (si est??n configurados)

   * **completa**:

      renderizaci??n JSON de sling del nodo, con `jcr:path` indicando la ruta de la visita: de forma predeterminada, solo enumera las propiedades directas del nodo, incluya un ??rbol m??s profundo con `p.nodedepth=N`, con 0 que significa todo el sub??rbol infinito; agregue `p.acls=true` para incluir los permisos JCR de la sesi??n actual en el elemento de resultado dado (asignaciones: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`)

   * **selectivo**:

      solo las propiedades especificadas en `p.properties`, que es una lista de rutas relativas separados por espacios (utilice &quot;+&quot; en las direcciones URL); si la ruta relativa tiene una profundidad > 1, se representar??n como objetos secundarios; la propiedad especial jcr:path incluye la ruta de la visita

### savedquery {#savedquery}

Incluye todos los predicados de una consulta de querybuilder persistente en la consulta actual como un predicado de subgrupo.

Tenga en cuenta que esto no ejecutar?? una consulta adicional sino que extender?? la consulta actual.

Las consultas se pueden mantener mediante programaci??n utilizando `QueryBuilder#storeQuery()`. El formato puede ser una propiedad String de varias l??neas o un nodo `nt:file` que contenga la consulta como archivo de texto en formato de propiedades Java.

No admite la extracci??n de facetas para los predicados de la consulta guardada.

#### Propiedades {#properties-19}

* **savedquery**

   ruta a la consulta guardada (propiedad String o nodo `nt:file`)

### similar {#similar}

B??squeda por similitudes usando `rep:similar()` de JCR XPath.

No admite el filtrado. No admite la extracci??n de facetas.

#### Propiedades {#properties-20}

* ****
ruta similar absoluta al nodo para el que encontrar nodos similares

* ****
ruta relativa de locala a un nodo descendiente o 
`.` para el nodo actual (opcional, el valor predeterminado es &quot;  `.`&quot;)

### etiqueta {#tag}

Busca contenido etiquetado con una o m??s etiquetas, especificando las rutas de t??tulo de las etiquetas.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada etiqueta ??nica, utilizando la ruta de t??tulo de la etiqueta actual.

#### Propiedades {#properties-21}

* **etiqueta**

   ruta de t??tulo de etiqueta que se va a buscar, por ejemplo &quot;Propiedades de los recursos : Orientaci??n / Horizontal&quot;

* **N_value**

   utilice `1_value`, `2_value`, ... para buscar varias etiquetas (combinadas con `OR` de forma predeterminada, con `AND` si y=true) (desde 5.6)

* **propiedad**

   propiedad (o ruta relativa a la propiedad) que se va a ver (predeterminado &quot; `cq:tags`&quot;)

### tagid {#tagid}

Busca contenido etiquetado con una o m??s etiquetas, especificando los ID de las etiquetas.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada etiqueta ??nica, utilizando su ID de etiqueta actual.

#### Propiedades {#properties-22}

* **tagid**

   id de etiqueta que se va a buscar, por ejemplo &quot; `properties:orientation/landscape`&quot;

* **N_value**

   utilice `1_value`, `2_value`, ... para comprobar si hay varios identificadores (combinados con `OR` de forma predeterminada, con `AND` si y=true) (desde 5.6)

* **propiedad**

   propiedad (o ruta relativa a la propiedad) que se va a ver (predeterminado &quot; `cq:tags`&quot;)

### tagsearch {#tagsearch}

Busca contenido etiquetado con una o m??s etiquetas, especificando palabras clave. Primero buscar?? las etiquetas que contengan estas palabras clave en sus t??tulos y luego restringir?? el resultado a solo los elementos etiquetados con ellas.

No admite la extracci??n de facetas.

#### Propiedades {#Properties-1}

* **tagsearch**

   palabra clave que se busca en los t??tulos de etiquetas

* **propiedad**

   propiedad (o ruta relativa a la propiedad) que se va a ver (predeterminado &quot; `cq:tags`&quot;)

* **lang**

   para buscar solo en un t??tulo de etiqueta localizado determinado (p. ej. &quot; `de`&quot;)

* **all**

   (bool) buscar todo el texto completo de la etiqueta, es decir, todos los t??tulos, descripci??n, etc. (tiene prioridad sobre &quot;l `ang`&quot;)

### tipo {#type}

Restringe los resultados a un tipo de nodo JCR espec??fico, tanto del tipo de nodo principal como del tipo de mezcla. Esto tambi??n encontrar?? subtipos de ese tipo de nodo. Tenga en cuenta que los ??ndices de b??squeda del repositorio deben cubrir los tipos de nodos para una ejecuci??n eficiente.

Admite la extracci??n de facetas. Proporcionar?? bloques para cada tipo ??nico en los resultados.

#### Propiedades {#Properties-2}

* **tipo**

   tipo de nodo o nombre de mezcla que se va a buscar, por ejemplo `cq:Page`
