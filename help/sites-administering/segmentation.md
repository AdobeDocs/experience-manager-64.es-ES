---
title: Configuración de la segmentación con ContextHub
seo-title: Configuring Segmentation with ContextHub
description: Obtenga información sobre cómo configurar la segmentación con ContextHub.
seo-description: Learn how to configure segmentation with Context Hub.
uuid: 196cfb18-317c-443d-b6f1-f559e4221baa
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 6cade87c-9ed5-47d7-9b39-c942268afdad
exl-id: 83e73a5d-c6fa-426a-8476-78769ae7a8c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1483'
ht-degree: 76%

---

# Configuración de la segmentación con ContextHub{#configuring-segmentation-with-contexthub}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!NOTE]
>
>En esta sección se describe la configuración de la segmentación al utilizar ContextHub. Si utiliza la funcionalidad Client Context, consulte la documentación relevante para [configuración de segmentación para Client Context](/help/sites-administering/campaign-segmentation.md).

La segmentación es una consideración clave al crear una campaña. Consulte [Administración de audiencias](/help/sites-authoring/managing-audiences.md) para obtener información sobre cómo funciona la segmentación y términos clave.

En función de la información que ya haya recopilado acerca de los visitantes del sitio y los objetivos que quiera lograr, deberá definir los segmentos y las estrategias necesarios para el contenido de destino.

Estos segmentos se utilizan para proporcionar a un visitante contenido dirigido específicamente. Este contenido se mantiene en la variable [Personalización](/help/sites-authoring/personalization.md) del sitio web. Las [Actividades](/help/sites-authoring/activitylib.md) definidas aquí se pueden incluir en cualquier página y definir para qué segmento de visitante se aplica el contenido especializado.

AEM permite personalizar fácilmente la experiencia de los usuarios. También le deja verificar los resultados de sus definiciones de segmento.

## Acceso a segmentos {#accessing-segments}

La variable [Audiencias](/help/sites-authoring/managing-audiences.md) se utiliza para administrar segmentos para ContextHub o Client Context, así como audiencias para su cuenta de Adobe Target. Esta documentación cubre la administración de segmentos para ContextHub. Para [Segmentos de ClientContext](/help/sites-administering/campaign-segmentation.md) y segmentos de Adobe Target, consulte la documentación pertinente.

Para acceder a sus segmentos, en la navegación global, seleccione **Navegación > Personalización > Audiencias**.

![chlimage_1-310](assets/chlimage_1-310.png)

## Editor de segmentos {#segment-editor}

El **Editor de segmentos** le permite modificar con facilidad un segmento. Para editar un segmento, seleccione un segmento en la [lista de segmentos](/help/sites-administering/segmentation.md#accessing-segments) y haga clic en el botón **Editar** botón.

![editor de segmentos](assets/segmenteditor.png)

Con el explorador de componentes, puede añadir contenedores **AND** y **OR** para definir la lógica del segmento. A continuación, agregue componentes adicionales para comparar propiedades y valores o secuencias de comandos de referencia y otros segmentos para definir los criterios de selección (consulte [Creación de un nuevo segmento](#creating-a-new-segment)) y el escenario exacto para seleccionar el segmento.

Cuando toda la instrucción se evalúa como verdadera, el segmento se ha resuelto. En caso de que se apliquen varios segmentos, el factor **Aumento** también se utiliza. Consulte [Creación de un nuevo segmento](#creating-a-new-segment)[ para obtener más información sobre el factor de ampliación.](/help/sites-administering/campaign-segmentation.md#boost-factor)

>[!CAUTION]
>
>El editor de segmentos no comprueba la existencia de referencias circulares. Por ejemplo, el segmento A hace referencia a otro segmento B, que a su vez hace referencia al segmento A. Debe asegurarse de que los segmentos no contengan ninguna referencia circular.

### Contenedores {#containers}

Los siguientes contenedores están disponibles de forma predeterminada y le permiten agrupar comparaciones y referencias para llevar a cabo una evaluación boolean. Se pueden arrastrar desde el explorador de componentes al editor. Consulte la siguiente sección, [Uso de contenedores AND y OR](/help/sites-administering/segmentation.md#using-and-and-or-containers), para obtener más información.

<table> 
 <tbody> 
  <tr> 
   <td>Contenedor AND<br /> </td> 
   <td>El operador boolean AND<br /> </td> 
  </tr> 
  <tr> 
   <td>Contenedor OR<br /> </td> 
   <td>El operador boolean OR</td> 
  </tr> 
 </tbody> 
</table>

### Comparaciones {#comparisons}

Las siguientes comparaciones de segmentos están disponibles y listas para usarse para evaluar las propiedades de los segmentos. Se pueden arrastrar desde el explorador de componentes al editor.

<table> 
 <tbody> 
  <tr> 
   <td>Propiedad-Valor<br /> </td> 
   <td>Compara una propiedad de un almacén con un valor definido<br /> </td> 
  </tr> 
  <tr> 
   <td>Propiedad-Propiedad</td> 
   <td>Compara una propiedad de un almacén con otra propiedad<br /> </td> 
  </tr> 
  <tr> 
   <td>Propiedad-Referencia de segmento</td> 
   <td>Compara una propiedad de un almacén con otro segmento al que se hace referencia<br /> </td> 
  </tr> 
  <tr> 
   <td>Propiedad-Referencia de script</td> 
   <td>Compara una propiedad de un almacén con los resultados de un script<br /> </td> 
  </tr> 
  <tr> 
   <td>Referencia de script-Referencia de script</td> 
   <td>Compara un segmento al que se hace referencia con los resultados de un script<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Al comparar valores, si no se establece el tipo de datos de la comparación (es decir, se configura para la detección automática), el motor de segmentación de ContextHub simplemente comparará los valores como lo haría JavaScript. No transmite valores a sus tipos esperados, lo que puede llevar a resultados engañosos. Por ejemplo:
>
>`null < 30 // will return true`
>
>Por lo tanto, cuando [cree segmentos](/help/sites-administering/segmentation.md#creating-a-new-segment), debe seleccionar un **tipo de datos** siempre que se conozcan los tipos de valores comparados. Por ejemplo:
>
>Al comparar la propiedad `profile/age`, ya sabe que el tipo comparado será un **número**, por lo que incluso si `profile/age` no está configurado, una comparación `profile/age` de menos de 30 devolverá **false**, como cabría esperar.

### Referencias {#references}

Las siguientes referencias están disponibles listas para usarse y para vincularse directamente a un script u otro segmento. Se pueden arrastrar desde el explorador de componentes al editor.

<table> 
 <tbody> 
  <tr> 
   <td>Referencia del segmento<br /> </td> 
   <td>Evaluación del segmento al que se hace referencia</td> 
  </tr> 
  <tr> 
   <td>Referencia de script</td> 
   <td>Evalúe el script al que se hace referencia. Consulte la siguiente sección, <a href="/help/sites-administering/segmentation.md#using-script-references">Uso de referencias de script</a>, para obtener más información.</td> 
  </tr> 
 </tbody> 
</table>

## Creación de un nuevo segmento {#creating-a-new-segment}

Para definir el nuevo segmento:

1. Después [acceso a los segmentos](/help/sites-administering/segmentation.md#accessing-segments), haga clic o pulse el botón Crear y seleccione **Crear segmento de ContextHub**.

   ![chlimage_1-311](assets/chlimage_1-311.png)

1. En el **Nuevo segmento de ContextHub**, introduzca un título para el segmento, así como un valor de ampliación si es necesario y, a continuación, pulse o haga clic en **Crear**.

   ![chlimage_1-312](assets/chlimage_1-312.png)

   Cada segmento tiene un parámetro de ampliación que se utiliza como factor de ponderación. Un número mayor indica que el segmento se seleccionará con preferencia sobre un segmento con un número menor en las instancias en las que varios segmentos son válidos.

   * Valor mínimo: `0`
   * Valor máximo: `1000000`

1. Arrastre una comparación o referencia al editor de segmentos que aparecerá en el contenedor AND predeterminado.
1. Toque o haga doble clic en la opción de configuración de la nueva referencia o segmento para editar los parámetros específicos. En este ejemplo, estamos probando personas en San José.

   ![screen_shot_2012-02-02at103135am](assets/screen_shot_2012-02-02at103135am.png)

   Establezca siempre un **Tipo de datos** si es posible, para garantizar que las comparaciones se evalúen correctamente. Consulte [Comparaciones](/help/sites-administering/segmentation.md#comparisons) para obtener más información.

1. Haga clic en **OK** para guardar la definición:
1. Agregue más componentes según sea necesario. Puede formular expresiones boolean utilizando los componentes de contenedor para las comparaciones AND y OR (consulte [Uso de los contenedores AND y OR](/help/sites-administering/segmentation.md#using-and-and-or-containers) más abajo). Con el editor de segmentos puede eliminar componentes que ya no se necesitan o arrastrarlos a nuevas posiciones dentro de la instrucción.

### Uso de contenedores AND y OR {#using-and-and-or-containers}

Con los componentes de contenedor AND y OR, puede construir segmentos complejos en AEM. Al hacer esto, es práctico tener en cuenta algunos puntos básicos:

* El nivel superior de la definición es siempre el contenedor AND que se crea inicialmente. Esto no se puede cambiar, pero no afecta al resto de la definición del segmento.
* Asegúrese de que tenga sentido anidar el contenedor. Los contenedores pueden verse como los corchetes de su expresión boolean.

El siguiente ejemplo se utiliza para seleccionar visitantes que se consideran en nuestro grupo de edad avanzada:

Hombre y entre 30 y 59 años

O

Mujeres y entre los 30 y los 59 años

Para empezar, coloque un componente contenedor OR dentro del contenedor AND predeterminado. Dentro del contenedor OR , agregue dos contenedores AND y dentro de ambos, puede agregar la propiedad o los componentes de referencia.

![screen_shot_2012-02-02at105145am](assets/screen_shot_2012-02-02at105145am.png)

### Uso de referencias de secuencia de comandos {#using-script-references}

Mediante el componente Referencia de secuencia de comandos, la evaluación de una propiedad de segmento se puede delegar a una secuencia de comandos externa. Una vez que la secuencia de comandos está configurada correctamente, puede utilizarse como cualquier otro componente de una condición de segmento.

#### Definición de una secuencia de comandos para referencia {#defining-a-script-to-reference}

1. Agregar archivo a `contexthub.segment-engine.scripts` clientlib.
1. Implemente una función que devuelva un valor. Por ejemplo:

   ```
   ContextHub.console.log(ContextHub.Shared.timestamp(), '[loading] contexthub.segment-engine.scripts - script.profile-info.js');
   
   (function() {
       'use strict';
   
       /**
        * Sample script returning profile information. Returns user info if data is available, false otherwise.
        *
        * @returns {Boolean}
        */
       var getProfileInfo = function() {
           /* let the SegmentEngine know when script should be re-run */
           this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
           this.dependOn(ContextHub.SegmentEngine.Property('profile/givenName'));
   
           /* variables */
           var name = ContextHub.get('profile/givenName');
           var age = ContextHub.get('profile/age');
   
           return name === 'Joe' && age === 123;
       };
   
       /* register function */
       ContextHub.SegmentEngine.ScriptManager.register('getProfileInfo', getProfileInfo);
   
   })();
   ```

1. Registre la secuencia de comandos con `ContextHub.SegmentEngine.ScriptManager.register`.

Si la secuencia de comandos depende de propiedades adicionales, la secuencia de comandos debería llamar a `this.dependOn()`. Por ejemplo, si la secuencia de comandos depende de `profile/age`:

```
this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
```

#### Referencia a una secuencia de comandos {#referencing-a-script}

1. Crear segmento de ContextHub.
1. Agregar el componente **Referencia de secuencia de comandos** en el lugar deseado del segmento.
1. Abra el cuadro de diálogo de edición del componente **Referencia de secuencia de comandos**. Si está [configurado correctamente](/help/sites-administering/segmentation.md#defining-a-script-to-reference), la secuencia de comandos debe estar disponible en la lista desplegable **Nombre de la secuencia de comandos**.

## Prueba de la aplicación de un segmento {#testing-the-application-of-a-segment}

Una vez definido el segmento, se pueden probar los resultados potenciales con la ayuda de la variable **[ContextHub](/help/sites-authoring/ch-previewing.md).**

1. Previsualización de una página
1. Haga clic en el icono de ContextHub para mostrar la barra de herramientas de ContextHub
1. Seleccione un perfil que coincida con el segmento que ha creado
1. ContextHub resolverá los segmentos aplicables para el personaje seleccionado

Por ejemplo, nuestra definición de segmento simple para identificar a los usuarios en nuestro grupo de edad avanzada es una definición de segmento simple basada en la edad y el sexo del usuario. Al cargar un perfil específico que coincida con esos criterios, se muestra si el segmento se ha resuelto correctamente:

![screen_shot_2012-02-02at105926am](assets/screen_shot_2012-02-02at105926am.png)

O si no se resuelve:

![screen_shot_2012-02-02at110019am](assets/screen_shot_2012-02-02at110019am.png)

>[!NOTE]
>
>Todos los rasgos se resuelven inmediatamente, aunque la mayoría solo cambia al volver a cargar la página.

Estas pruebas también se pueden realizar en páginas de contenido y en combinación con contenido de destino y **Actividades** y **Experiencias** relacionadas.

Si ha configurado una actividad y experiencia utilizando el ejemplo del segmento de grupo de edad superior anterior, puede probar fácilmente el segmento con la actividad . Para obtener más información sobre la configuración de una actividad, consulte la [documentación sobre la creación de contenido de destino](/help/sites-authoring/content-targeting-touch.md).

1. En el modo de edición de una página en la que ha configurado contenido de destino, puede ver que el contenido se orienta mediante un icono de flecha en el contenido.

   ![chlimage_1-313](assets/chlimage_1-313.png)

1. Cambie al modo de previsualización y, con el Context Hub, cambie a un perfil que no coincida con la segmentación configurada para la experiencia.

   ![chlimage_1-314](assets/chlimage_1-314.png)

1. Cambie a un perfil que no coincida con la segmentación configurada para la experiencia y compruebe que la experiencia cambia en consecuencia.

   ![chlimage_1-315](assets/chlimage_1-315.png)

## Uso del segmento {#using-your-segment}

Los segmentos se utilizan para dirigir el contenido real que ven las audiencias de destino específicas. Consulte [Administración de audiencias](/help/sites-authoring/managing-audiences.md) para obtener más información sobre audiencias y segmentos, y [Creación de contenido de destino](/help/sites-authoring/content-targeting-touch.md) acerca del uso de audiencias y segmentos para segmentar contenido.
