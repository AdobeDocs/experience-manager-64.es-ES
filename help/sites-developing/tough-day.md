---
title: Día duro
seo-title: Tough Day
description: La prueba de Día duro simula la carga diaria de unos 1000 autores en el peor de los casos, con todas las operaciones en curso al mismo tiempo.
seo-description: The Tough Day test simulates the daily load of around 1000 authors in a worst-case scenario with all the operations going on at the same time.
uuid: 7a13efe0-c455-4af0-ad7b-c39cb2479d74
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: f48fa5ba-749b-4d3d-a4dd-c802006c8f07
exl-id: 80442184-212a-424d-b320-5b301a54f974
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1931'
ht-degree: 2%

---

# Día duro{#tough-day}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Qué es el día duro 2 {#what-is-tough-day}

El Día difícil 2 es una aplicación que le permite probar los límites de su instancia de AEM. Se puede ejecutar de forma predeterminada con el grupo de prueba predeterminado o puede configurarse para adaptarlo a sus necesidades de prueba. Puede ver [esta grabación](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2017/aem-toughday2-stress-testing-benchmarking-tool.html) para una presentación de la aplicación.

## Cómo ejecutar el Día duro 2 {#how-to-run-tough-day}

Descargue la versión más reciente del Día duro 2 desde la [Repositorio de Adobes](https://repo1.maven.org/maven2/com/adobe/qe/toughday2/). Después de descargar la aplicación, puede ejecutarla de forma predeterminada proporcionando la variable `host` parámetro. En el ejemplo siguiente, la instancia de AEM se ejecuta localmente para que `localhost` se utiliza:

```xml
java -jar toughday2.jar --host=localhost
```

El grupo predeterminado que se ejecuta después de agregar los parámetros recibe el nombre `toughday`. Contiene los siguientes casos de uso:

* Cree páginas y Live Copies para ellas (incluidos los lanzamientos)
* Obtener página principal
* Ejecutar consultas en querybuilder
* Crear jerarquías de recursos
* Eliminar recursos

El grupo contiene un 15% de acciones de escritura y un 85% de acciones de lectura.

Para ejecutar las pruebas de grupo, el Día duro 2 instalará su paquete de contenido predeterminado. Esto se puede evitar estableciendo la variable `installsamplecontent` parámetro a `false`, pero recuerde que también debe cambiar las rutas predeterminadas para las pruebas que desea ejecutar. Si el jar se ejecuta sin parámetros, el Día duro 2 muestra la variable [información de ayuda](/help/sites-developing/tough-day.md#getting-help).

Como regla general, puede utilizar la aplicación siguiendo este patrón:

```xml
java -jar toughday2.jar [--help | --help_full | --help_tests | --help_publish]  [<global arguments> | <actions> | --runmode | --publishmode]
```

>[!NOTE]
>
>El Día 2 no tiene un paso de limpieza. Como resultado, se recomienda ejecutar el Día duro 2 en una instancia de ensayo clonada y no en la instancia de producción principal. La instancia de ensayo debe dejarse de lado después de las pruebas.

### Obtención de ayuda {#getting-help}

El Día difícil 2 ofrece una amplia gama de opciones de ayuda a las que se puede acceder desde la línea de comandos. Por ejemplo:

```xml
java -jar toughday2.jar --help_full
```

En la tabla siguiente, puede encontrar los parámetros de ayuda relevantes.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Parámetro</strong></td> 
   <td><strong>Descripción</strong></td> 
   <td><strong>Ejemplo</strong></td> 
  </tr> 
  <tr> 
   <td>--help</td> 
   <td>Imprime la información global, por ejemplo: las acciones disponibles, los grupos predefinidos, los modos de ejecución y los parámetros globales.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>—help_publish</td> 
   <td>Imprime todos los editores disponibles.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>—help_test</td> 
   <td>Imprime las clases de prueba y su descripción.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>—help_full</td> 
   <td>Imprime todo lo anterior, además de pruebas, editores y componentes de grupo.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> —help —runmode/publishmode type=&lt;mode&gt;</td> 
   <td>Muestra información sobre el modo especificado de ejecución o publicación.</td> 
   <td><p>java -jar toughday2.jar —help —runmode type=constantload</p> <p>java -jar toughday2.jar —help —publishmode type=ranges</p> </td> 
  </tr> 
  <tr> 
   <td>—help —suite=&lt;suitename&gt;</td> 
   <td>Enumera todas las pruebas de un grupo determinado y sus respectivas propiedades configurables.</td> 
   <td><br /> java -jar toughday2.jar —help —suite=get_testing</td> 
  </tr> 
  <tr> 
   <td> —help —tag=&lt;tag&gt;</td> 
   <td><br /> Enumera todos los elementos que tienen la etiqueta especificada.</td> 
   <td>java -jar toughday2.jar —help —tag=publish</td> 
  </tr> 
  <tr> 
   <td>—help &lt;testclass publisherclass=""&gt;</td> 
   <td><br /> Enumera todas las propiedades configurables para la prueba o el publicador dados.</td> 
   <td><p>java -jar toughday2.jar —help UploadPDFTest</p> <p>java -jar toughday2.jar —help CSVPublisher</p> </td> 
  </tr> 
 </tbody> 
</table>

### Parámetros globales {#global-parameters}

El Día difícil 2 ofrece parámetros globales que establecen o cambian el entorno para las pruebas. Estos incluyen el host de destino, el número de puerto, el protocolo utilizado, el usuario y la contraseña de la instancia y muchos más. Por ejemplo:

```xml
java -jar toughday2.jar --host=host --protocol=https --port=4502 --duration=30m --dryrun=true 
```

Puede encontrar los parámetros relevantes en la lista siguiente:

| **Parámetro** | **Descripción** | **Valor predeterminado** | **Valores posibles** |
|---|---|---|---|
| `--installsamplecontent=<Val>` | Instale o omita el paquete de contenido predeterminado del Día duro 2. | true | true o false |
| `--protocol=<Val>` | El protocolo utilizado para el host. | http | http o https |
| `--host=<Val>` | El nombre de host o la IP a la que se dirigirá. |  |  |
| `--port=<Val>` | Puerto del host. | 4502 |  |
| `--user=<Val>` | El nombre de usuario de la instancia. | administrador |  |
| `--password=<Val>` | Contraseña del usuario dado. | administrador |  |
| `--duration=<Val>` | Duración de las pruebas. Se puede expresar en (**s**)segundos, (**m**)minutos, (**h**)ours y (**d**). | 1d |  |
| `--timeout=<Val>` | El tiempo de ejecución de una prueba antes de que se interrumpa y se marque como fallida. Se expresa en segundos. | 180 |  |
| `--suite=<Val>` | El valor puede ser uno o una lista (separados por comas) de grupos de pruebas predefinidos. | toughday |  |
| `--configfile=<Val>` | El archivo de configuración yaml de destino. |  |  |
| `--contextpath=<Val>` | Ruta de contexto de la instancia. |  |  |
| `--loglevel=<Val>` | Nivel de registro para el motor del Día difícil 2. | INFORMACIÓN | TODOS, DEPURAR, INFORMACIÓN, ADVERTENCIA, ERROR, FATAL, DESACTIVADO |
| `--dryrun=<Val>` | Si es true, imprime la configuración resultante y no ejecuta ninguna prueba. | false | true o false |

## Personalización {#customizing}

La personalización se puede lograr de dos maneras: parámetros de línea de comandos o archivos de configuración de yaml. **Los archivos de configuración generalmente se utilizan para grupos personalizados grandes y anularán los parámetros predeterminados del Día duro 2. Los parámetros de la línea de comandos anulan tanto los archivos de configuración como los parámetros predeterminados.**

La única forma de guardar una configuración de prueba es copiarla en formato yaml. Para obtener más información, consulte esta [toughday.yaml](https://repo.adobe.com/nexus/service/local/repositories/releases/content/com/adobe/qe/toughday2/0.2.1/toughday2-0.2.1.yaml) y los ejemplos de configuración de yaml en las secciones siguientes.

### Adición de una nueva prueba {#adding-a-new-test}

Si no desea utilizar el valor predeterminado `toughday` puede agregar una prueba de su elección utilizando el `add` parámetro. Los ejemplos siguientes muestran cómo agregar la variable `CreateAssetTreeTest` pruebe utilizando parámetros de línea de comandos o un archivo de configuración de yaml.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest
```

Mediante el uso de un archivo de configuración de yaml:

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
```

### Adición de varias instancias de la misma prueba  {#adding-multiple-instances-of-the-same-test}

También puede agregar y ejecutar varias instancias de la misma prueba, pero cada instancia debe tener un nombre único. Los ejemplos siguientes muestran cómo se agregan dos instancias de la misma prueba, ya sea utilizando parámetros de línea de comandos o un archivo de configuración de yaml.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest name=FirstAssetTree --add CreateAssetTreeTest name=SecondAssetTree
```

Mediante el uso de un archivo de configuración de yaml:

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
    properties:
      name : FirstAssetTree
  - add : CreateAssetTreeTest
    properties:
      name : SecondAssetTree
```

### Cambio de las propiedades de prueba {#changing-the-test-properties}

Si necesita cambiar una o más de las propiedades de prueba, puede agregar esa propiedad a la línea de comandos o al archivo de configuración de yaml. Para ver todas las propiedades de prueba disponibles, agregue la variable `--help <TestClass/PublisherClass>` a la línea de comandos, por ejemplo:

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

Tenga en cuenta que los archivos de configuración de yaml sobrescribirán los parámetros predeterminados de Día difícil 2 y los parámetros de línea de comandos anularán tanto los archivos de configuración como los valores predeterminados.

Los ejemplos siguientes muestran cómo cambiar la variable `template` para la variable `CreatePageTreeTest` pruebe utilizando parámetros de línea de comandos o un archivo de configuración de yaml.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest template=/conf/toughday-templates/settings/wcm/templates/toughday-template
```

Mediante el uso de un archivo de configuración de yaml:

```xml
globals:
  host : localhost
tests:
  - add : CreatePageTreeTest
    properties:
      template : /conf/toughday-templates/settings/wcm/templates/toughday-template
```

### Uso de grupos de pruebas predefinidos {#working-with-predefined-test-suites}

Los ejemplos siguientes muestran cómo agregar una prueba a un grupo predefinido y cómo reconfigurar y excluir una prueba existente de un grupo predefinido.

Puede agregar una nueva prueba a un grupo predefinido utilizando la variable `add` y especificar el grupo predefinido de destino.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest
```

Mediante el uso de un archivo de configuración de yaml:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - add : CreatePageTreeTest
```

Las pruebas existentes en un grupo determinado también se pueden reconfigurar usando la variable `config`* *parámetro. Tenga en cuenta que también debe especificar el nombre del grupo y el nombre real de la prueba (no el nombre de la clase de prueba). Puede encontrar el nombre de la prueba en la `name` propiedad de la clase Test. Para obtener más información sobre cómo encontrar las propiedades de prueba, lea la [Cambio de las propiedades de prueba](/help/sites-developing/tough-day.md#changing-the-test-properties) para obtener más información.

En el ejemplo siguiente al título de recurso predeterminado para la variable `CreatePageTreeTest` (con nombre `UploadAsset`) se cambia a &quot;NewAsset&quot;.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --config UploadAsset title=NewAsset
```

Mediante el uso de un archivo de configuración de yaml:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - config : UploadAsset
    properties :
      title : NewAsset 
```

Además, también puede eliminar las pruebas de grupos predefinidos o editores de la configuración predeterminada mediante el uso de la variable `exclude` parámetro. Tenga en cuenta que también debe especificar el nombre del grupo y el nombre real de la prueba (no la prueba C) `lass` nombre). Puede encontrar el nombre de la prueba en la `name` propiedad de la clase test. En el ejemplo siguiente, la variable `CreatePageTreeTest` (con nombre `UploadAsset`) se elimina del grupo de informes de día difícil.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --exclude UploadAsset
```

Mediante el uso de un archivo de configuración de yaml:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - exclude : UploadAsset 
```

### Ejecutar modos {#run-modes}

El Día duro 2 puede ejecutarse en uno de los siguientes modos: **normal** y **carga constante**.

La variable **normal** el modo de ejecución tiene dos parámetros:

* `concurrency` : la concurrencia representa el número de subprocesos que el Día duro 2 creará para la ejecución de la prueba. En estos subprocesos, las pruebas se ejecutarán hasta que se haya agotado la duración o hasta que no haya más pruebas que ejecutar.

* `waittime` - el tiempo de espera entre dos ejecuciones de prueba consecutivas en el mismo subproceso. El valor debe expresarse en milisegundos.

El ejemplo siguiente muestra cómo añadir los parámetros utilizando la línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest --runmode=normal concurrency=20
```

o utilizando un archivo de configuración de yaml:

```xml
runmode:
  type : normal
  waittime : 300
  concurrency : 200
```

La variable **carga constante** el modo de ejecución difiere del modo de ejecución normal al generar un número constante de ejecuciones de prueba iniciadas, en lugar de un número constante de subprocesos. Puede configurar la carga utilizando el parámetro del modo de ejecución con el mismo nombre.

### Selección de prueba {#test-selection}

El proceso de selección de prueba es el mismo para ambos modos de ejecución y funciona de la siguiente manera: todas las pruebas tienen un `weight` , que determina la probabilidad de ejecución en un subproceso. Por ejemplo, si tenemos dos pruebas, una con un peso de 5 y otra con un peso de 10, es más probable que la segunda se ejecute dos veces más que la primera.

Además, las pruebas pueden tener un `count` , que limita el número de ejecuciones a un número determinado. Una vez pasado este número, no se producirán más ejecuciones de la prueba. Todas las instancias de prueba que ya se estén ejecutando finalizarán la ejecución según lo configurado. El siguiente ejemplo muestra cómo agregar estos parámetros en la línea de comandos o utilizando un archivo de configuración de yaml.

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest weight=5 --add CreatePageTreeTest weight=10 count=100 --runmode=normal concurrency=20 
```

o

```xml
- add : CreateAssetTreeTest
    properties :
      name : UploadAsset
      weight : 5
      base : 3
      foldertitle : IAmAFolder
      assettitle : IAmAnAsset
      count : 100
```

>[!NOTE]
>
>Debido a ejecuciones paralelas, el número real de ejecuciones de prueba no será exactamente la cantidad configurada en la variable `count` parámetro. Espere una desviación proporcional al número de subprocesos en ejecución (controlados por el `concurrency parameter`).

### Simulacro {#dry-run}

Una ejecución en seco analiza toda la entrada dada (parámetros de línea de comandos o archivos de configuración), combinándola con los valores predeterminados y, a continuación, genera los resultados. No ejecuta ninguna de las pruebas.

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## Salida {#output}

El Día difícil 2 genera métricas de prueba y registros. Para obtener más información, lea las secciones siguientes.

### Métricas de prueba {#test-metrics}

El Día difícil 2 actualmente informa de 9 métricas de prueba que puede evaluar. Métricas con la variable **&amp;ast;** solo se incluyen en los informes después de ejecutar correctamente:

| **Nombre** | **Descripción** |
|---|---|
| Marca de tiempo | Marca de tiempo de la última ejecución de prueba finalizada. |
| Aprobado | Número de ejecuciones correctas. |
| Error | Número de ejecuciones fallidas. |
| Min&amp;ast; | La duración más baja de la ejecución de la prueba. |
| Max&amp;ast; | Mayor duración de la ejecución de prueba. |
| Mediana y última; | Duración media calculada de todas las ejecuciones de prueba. |
| Average&amp;ast; | Duración media calculada de todas las ejecuciones de prueba. |
| StdDev&amp;ast; | La desviación estándar. |
| 90p&amp;ast; | Percentil 90. |
| 99p&amp;ast; | Percentil 99. |
| 99.9p&amp;ast; | Percentil 99,9. |
| Rendimiento real &amp;ast; | Número de ejecuciones dividido por el tiempo de ejecución transcurrido. |

Estas métricas se escriben con la ayuda de editores que pueden agregarse con la variable `add` (de forma similar a añadir pruebas). Actualmente, hay dos opciones:

* **CSVPublisher** : el resultado es un archivo CSV.
* **Editor de consola** : la salida se muestra en la consola.

De forma predeterminada, ambos editores están habilitados.

Además, existen dos modos en los que se generan los informes de las métricas:

* La variable **simple** modo de publicación : informa de los resultados desde el principio de la ejecución hasta el punto de la publicación.
* La variable **intervalos** modo de publicación : informa de los resultados en un intervalo de tiempo determinado. Puede establecer el lapso de tiempo con la variable **intervalo** parámetro de modo de publicación.

El siguiente ejemplo muestra cómo configurar la variable `intervals` en la línea de comandos o utilizando un archivo de configuración de yaml.

Mediante parámetros de línea de comandos:

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest --publishmode type=intervals interval=10s 
```

Mediante el uso de un archivo de configuración de yaml:

```xml
publishmode:
     type : intervals 
     interval : 10s 
     tests: 
        -add : CreatePageTreeTest
```

### Registro {#logging}

El Día difícil 2 crea una carpeta de registros en el mismo directorio donde ejecutó el Día duro 2. Esta carpeta contiene dos tipos de registros:

* **toughday.log**: contiene mensajes relacionados con el estado de la aplicación, información de depuración y mensajes globales.
* **toughday_&lt;testname>.log**: mensajes relacionados con la prueba especificada.

Los registros no se sobrescriben, las ejecuciones posteriores adjuntarán mensajes a los registros existentes. Los registros tienen varios niveles; para obtener más información, consulte la ` [loglevel parameter](/help/sites-developing/tough-day.md#global-parameters)`.
