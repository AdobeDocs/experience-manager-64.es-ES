---
title: Implementación de un evaluador de predicados personalizado para el generador de consultas
seo-title: Implementing a Custom Predicate Evaluator for the Query Builder
description: El Generador de consultas ofrece una forma sencilla de consultar el repositorio de contenido
seo-description: The Query Builder offers an easy way of querying the content repository
uuid: 5b599b60-a149-4425-b7ac-7fbe7e048bca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 08bdade7-fdad-445d-80fe-8fc06596dace
exl-id: afa7f346-fefa-4faa-bf2d-7480a7e5a5ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 1%

---

# Implementación de un evaluador de predicados personalizado para el generador de consultas{#implementing-a-custom-predicate-evaluator-for-the-query-builder}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En esta sección se describe cómo ampliar el [Generador de consultas](/help/sites-developing/querybuilder-api.md) implementando un evaluador de predicado personalizado.

## Información general {#overview}

La variable [Generador de consultas](/help/sites-developing/querybuilder-api.md) ofrece una forma sencilla de consultar el repositorio de contenido. AEM incluye un conjunto de evaluadores predicados que le ayudan a tratar sus datos.

Sin embargo, es posible que desee simplificar las consultas mediante la implementación de un evaluador de predicados personalizado que oculte cierta complejidad y garantice una mejor semántica.

Un predicado personalizado también podría realizar otras cosas no directamente posibles con XPath, por ejemplo:

* buscar algunos datos de algún servicio
* filtrado personalizado basado en el cálculo

>[!NOTE]
>
>Se deben tener en cuenta los problemas de rendimiento al implementar un predicado personalizado.

>[!NOTE]
>
>Puede encontrar ejemplos de consultas en la [Generador de consultas](/help/sites-developing/querybuilder-api.md) para obtener más información.

CÓDIGO DE GITHUB

Puede encontrar el código de esta página en GitHub

* [Abra el proyecto aem-search-custom-predicate-evaluator en GitHub](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
* Descargue el proyecto como [un archivo ZIP](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)

## Predicar evaluador en detalle {#predicate-evaluator-in-detail}

Un evaluador predicado gestiona la evaluación de ciertos predicados, que son las restricciones de definición de una consulta.

Asigna una restricción de búsqueda de nivel superior (como &quot;anchura > 200&quot;) a una consulta JCR específica que se ajusta al modelo de contenido real (por ejemplo, metadata/@width > 200). O puede filtrar manualmente los nodos y comprobar sus restricciones.

>[!NOTE]
>
>Para obtener más información sobre la variable `PredicateEvaluator` y `com.day.cq.search` ver el [Documentación de Java](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/search/package-summary.html).

## Implementación de un evaluador de predicados personalizado para metadatos de replicación {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

Como ejemplo, en esta sección se describe cómo crear un evaluador de predicado personalizado que ayude a crear datos basados en los metadatos de replicación:

* `cq:lastReplicated` que almacena la fecha de la última acción de replicación

* `cq:lastReplicatedBy` que almacena el id del usuario que activó la última acción de replicación

* `cq:lastReplicationAction` que almacena la última acción de replicación (por ejemplo, Activación, Desactivación)

### Consulta de metadatos de replicación con evaluadores de predicados predeterminados {#querying-replication-metadata-with-default-predicate-evaluators}

La siguiente consulta obtiene la lista de nodos de `/content` rama activada por `admin` desde principios de año.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

Esta consulta es válida pero difícil de leer y no resalta la relación entre las tres propiedades de replicación. La implementación de un evaluador de predicado personalizado reducirá la complejidad y mejorará la semántica de esta consulta.

### Objetivos {#objectives}

El objetivo de `ReplicationPredicateEvaluator` es para admitir la consulta anterior utilizando la siguiente sintaxis.

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

Agrupar predicados de metadatos de replicación con un evaluador de predicado personalizado ayuda a crear una consulta significativa.

### Actualización de dependencias de Maven {#updating-maven-dependencies}

>[!NOTE]
>
>La configuración de nuevos proyectos de AEM usando maven está documentada por [Cómo crear AEM proyectos con Apache Maven](/help/sites-developing/ht-projects-maven.md).

Primero debe actualizar las dependencias Maven del proyecto. La variable `PredicateEvaluator` forma parte del `cq-search` artefacto para que sea necesario agregarlo al archivo pom de Maven.

>[!NOTE]
>
>El ámbito de aplicación del `cq-search` la dependencia está configurada en `provided` Porque `cq-search` será proporcionado por el `OSGi` contenedor.

pom.xml

El siguiente fragmento muestra las diferencias, en [formato de comparación de diferencias unificado](https://en.wikipedia.org/wiki/Diff#Unified_format)

```
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)- [pom.xml](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/7aed6b35b4c8dd3655296e1b10cf40c0dd1eaa61/pom.xml)

### Escritura del ReplicationPredicateEvaluator {#writing-the-replicationpredicateevaluator}

La variable `cq-search` el proyecto contiene el `AbstractPredicateEvaluator` clase abstracta. Esto se puede ampliar con algunos pasos para implementar su propio evaluador de predicados personalizado `(PredicateEvaluator`).

>[!NOTE]
>
>El siguiente procedimiento explica cómo crear una `Xpath` expresión para filtrar datos. Otra opción sería implementar la variable `includes` método que selecciona los datos en fila. Consulte la [Documentación de Java](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html#includes28comdaycqsearchpredicatejavaxjcrqueryrowcomdaycqsearchevalevaluationcontext29) para obtener más información.

1. Cree una nueva clase Java que se extienda `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. Ponga notas en la clase con un `@Component` como el siguiente

   src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

   El siguiente fragmento muestra las diferencias, en [formato de comparación de diferencias unificado](https://en.wikipedia.org/wiki/Diff#Unified_format)


```
@@ -19,8 +19,11 @@
  */
 package com.adobe.aem.docs.search;
+import org.apache.felix.scr.annotations.Component;
+import com.day.cq.search.eval.AbstractPredicateEvaluator;
+@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
 public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

  }
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)- [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/ec70fac35fbd0d132e00c6066a204804e9cbe70f/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)

>[!NOTE]
>
>La variable `factory`debe ser una cadena única que comience por `com.day.cq.search.eval.PredicateEvaluator/`y finalizando con el nombre de su `PredicateEvaluator`.

>[!NOTE]
>
>El nombre del `PredicateEvaluator` es el nombre del predicado, que se utiliza al crear consultas.

1. Omitir:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   En el método override se crea un `Xpath` expresión basada en la variable `Predicate` dado en el argumento .

### Ejemplo de un evaluador de predicados personalizado para metadatos de replicación {#example-of-a-custom-predicate-evalutor-for-replication-metadata}

La aplicación completa de esta `PredicateEvaluator` puede ser similar a la siguiente clase.

src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

```
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;

import org.slf4j.Logger;

import org.slf4j.LoggerFactory;

 
import com.day.cq.search.Predicate;

import com.day.cq.search.eval.AbstractPredicateEvaluator;

import com.day.cq.search.eval.EvaluationContext;

 
@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";

    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";

    static final String PN_LAST_REPLICATED = "cq:lastReplicated";

    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";

    static final String PREDICATE_SINCE = "since";

    static final String PREDICATE_SINCE_OP = " >= ";

    static final String PREDICATE_ACTION = "action";
 

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,

            EvaluationContext context) {

        log.debug("predicate {}", predicate);


        String date = predicate.get(PREDICATE_SINCE);

        String user = predicate.get(PREDICATE_BY);

        String action = predicate.get(PREDICATE_ACTION);


        StringBuilder sb = new StringBuilder();


        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);

            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);

            sb.append(PN_LAST_REPLICATED_BY);

            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);

            sb.append(PN_LAST_REPLICATED_ACTION);

            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator) - [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/blob/master/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)
