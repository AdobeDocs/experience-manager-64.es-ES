---
title: Prueba de la IU
seo-title: Prueba de la IU
description: AEM proporciona un marco para automatizar las pruebas de la IU AEM
seo-description: AEM proporciona un marco para automatizar las pruebas de la IU AEM
uuid: b0280a70-643e-4455-82ea-fa7a90823b53
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: components, testing
discoiquuid: bc0130c3-826e-47dd-b18b-85e1a7bb9936
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 1%

---


# Prueba de la IU{#testing-your-ui}

AEM proporciona un marco para automatizar las pruebas de la IU AEM. Con el marco, las pruebas de interfaz de usuario se escriben y ejecutan directamente en un navegador web. La estructura proporciona la API de ajavascript para crear pruebas.

El marco de AEM prueba utiliza Hobbes.js, una biblioteca de pruebas escrita en JavaScript. El marco Hobbes.js fue desarrollado para probar AEM como parte del proceso de desarrollo. El módulo ya está disponible para uso público para probar las aplicaciones AEM.

>[!NOTE]
>
>Consulte la [documentación](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/test-api/index.html) de Hobbes.js para obtener más información sobre la API.

## Estructura de las pruebas {#structure-of-tests}

Al utilizar pruebas automatizadas dentro de AEM, es importante comprender los siguientes términos:

|  |  |
|---|---|
| Acción | Una **acción** es una actividad específica de una página web, como hacer clic en un vínculo o en un botón. |
| Caso de prueba | Un caso **de** prueba es una situación específica que puede estar formada por una o más **acciones**. |
| Test Suite | Un grupo **de pruebas** es un grupo de casos **de** prueba relacionados que juntos prueban un caso de uso específico. |

## Ejecución de pruebas {#executing-tests}

### Visualización de grupos de pruebas {#viewing-test-suites}

Abra la consola de pruebas para ver los grupos de pruebas registrados. El panel Pruebas contiene una lista de los grupos de pruebas y sus casos de prueba.

Vaya a la consola Herramientas a través de Navegación **global -> Herramientas > Operaciones -> Pruebas**.

![chlimage_1-26](assets/chlimage_1-26.png)

Al abrir la consola, los grupos de pruebas se muestran a la izquierda junto con una opción para ejecutarlos de forma secuencial. El espacio a la derecha que se muestra con un fondo de cuadros es un marcador de posición para mostrar el contenido de la página a medida que se ejecutan las pruebas.

![chlimage_1-27](assets/chlimage_1-27.png)

### Ejecución de un único grupo de pruebas {#running-a-single-test-suite}

Los grupos de pruebas se pueden ejecutar de forma individual. Al ejecutar un grupo de pruebas, la página cambia a medida que se ejecutan los casos de prueba y sus acciones y los resultados aparecen una vez finalizada la prueba. Los iconos indican los resultados.

Un icono de marca de verificación indica una prueba pasada:

![](do-not-localize/chlimage_1-5.png)

El icono &quot;X&quot; indica que la prueba ha fallado:

![](do-not-localize/chlimage_1-6.png)

Para ejecutar un grupo de pruebas:

1. En el panel Pruebas, toque o haga clic en el nombre del caso de prueba que desee ejecutar para expandir los detalles de las acciones.

   ![chlimage_1-28](assets/chlimage_1-28.png)

1. Toque o haga clic en el botón **Ejecutar prueba** .

   ![](do-not-localize/chlimage_1-7.png)

1. El marcador de posición se reemplaza por el contenido de la página a medida que se ejecuta la prueba.

   ![chlimage_1-21](assets/chlimage_1-29.png)

1. Revise los resultados del caso de prueba tocando o haciendo clic en la descripción para abrir el panel **Resultado** . Al tocar o hacer clic en el nombre del caso de prueba en el panel **Resultado** se muestran todos los detalles.

   ![chlimage_1-30](assets/chlimage_1-30.png)

### Ejecución de varias pruebas {#running-multiple-tests}

Los grupos de pruebas se ejecutan secuencialmente en el orden en que aparecen en la consola. Puede explorar en profundidad una prueba para ver los resultados detallados.

![chlimage_1-31](assets/chlimage_1-31.png)

1. En el panel Pruebas, toque o haga clic en el botón **Ejecutar todas las pruebas** o en el botón **Ejecutar pruebas** debajo del título del grupo de pruebas que desee ejecutar.

   ![](do-not-localize/chlimage_1-8.png)

1. Para vista de los resultados de cada caso de prueba, toque o haga clic en el título del caso de prueba. Al tocar o hacer clic en el nombre de la prueba en el panel **Resultado** se muestran todos los detalles.

   ![chlimage_1-32](assets/chlimage_1-32.png)

## Creación y uso de un grupo de pruebas sencillo {#creating-and-using-a-simple-test-suite}

El siguiente procedimiento le guía a través de la creación y ejecución de un grupo de pruebas con contenido [](/help/sites-developing/we-retail.md)We.Retail, pero puede modificar fácilmente la prueba para utilizar una página web diferente.

Para obtener más información sobre la creación de sus propios grupos de pruebas, consulte la documentación [de la API de](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/test-api/index.html)Hobbes.js.

1. Abra CRXDE Lite. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Haga clic con el botón secundario en la `/etc/clientlibs` carpeta y, a continuación, haga clic en **Crear > Crear carpeta**. Escriba `myTests` el nombre y haga clic en **Aceptar**.
1. Haga clic con el botón secundario en la `/etc/clientlibs/myTests` carpeta y haga clic en **Crear > Crear nodo**. Utilice los siguientes valores de propiedad y haga clic en **Aceptar**:

   * Nombre: `myFirstTest`
   * Tipo: `cq:ClientLibraryFolder`

1. Añada las siguientes propiedades al nodo myFirstTest:

   | Nombre | Tipo | Value |
   |---|---|---|
   | `categories` | `String[]` | `granite.testing.hobbes.tests` |
   | `dependencies` | `String[]` | `granite.testing.hobbes.testrunner` |

   >[!NOTE]
   >
   >**Solo AEM Forms**
   >
   >Para probar los formularios adaptables, agregue los siguientes valores a las categorías y dependencias. Por ejemplo:
   >
   >**categorías**: `granite.testing.hobbes.tests, granite.testing.hobbes.af.commons`
   >
   >**dependencias**: `granite.testing.hobbes.testrunner, granite.testing.hobbes.af`

1. Haga clic en **Guardar todo**.
1. Haga clic con el botón secundario en el `myFirstTest` nodo y haga clic en **Crear > Crear archivo**. Name the file `js.txt` and click **OK**.
1. En el `js.txt` archivo, escriba el siguiente texto:

   ```
   #base=.
   myTestSuite.js
   ```

1. Haga clic en **Guardar todo** y, a continuación, cierre el `js.txt` archivo.
1. Haga clic con el botón secundario en el `myFirstTest` nodo y haga clic en **Crear > Crear archivo**. Name the file `myTestSuite.js` and click **OK**.
1. Copie el siguiente código en el `myTestSuite.js` archivo y, a continuación, guarde el archivo:

   ```
   new hobs.TestSuite("Experience Content Test Suite", {path:"/etc/clientlibs/myTests/myFirstTest/myTestSuite.js"})
      .addTestCase(new hobs.TestCase("Navigate to Experience Content")
         .navigateTo("/content/we-retail/us/en/experience/arctic-surfing-in-lofoten.html")
      )
      .addTestCase(new hobs.TestCase("Hover Over Topnav")
         .mouseover("li.visible-xs")
      )
      .addTestCase(new hobs.TestCase("Click Topnav Link")
         .click("li.active a")
   );
   ```

1. Vaya a la consola **Pruebas** para probar el grupo de pruebas.

