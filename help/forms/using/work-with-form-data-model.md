---
title: Trabajo con el modelo de datos de formulario
seo-title: Trabajo con el modelo de datos de formulario
description: La integración de datos proporciona un editor de modelos de datos de formulario para configurar y trabajar con modelos de datos de formulario.
seo-description: La integración de datos proporciona un editor de modelos de datos de formulario para configurar y trabajar con modelos de datos de formulario.
uuid: cd123d42-f7cf-489d-8182-f3a01a2a4799
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: 2ee45ac0-bc15-403a-93fc-c8592afb967d
feature: Form Data Model
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '3153'
ht-degree: 0%

---


# Trabajo con el modelo de datos de formulario {#work-with-form-data-model}

La integración de datos proporciona un editor de modelos de datos de formulario para configurar y trabajar con modelos de datos de formulario.

![](do-not-localize/data-integeration.png)

El editor del modelo de datos de formulario proporciona una interfaz de usuario intuitiva y herramientas para editar y configurar un modelo de datos de formulario. Con el editor, se pueden agregar y configurar objetos, propiedades y servicios del modelo de datos desde orígenes de datos asociados en el modelo de datos de formulario. Además, permite crear objetos y propiedades de modelos de datos sin orígenes de datos y enlazarlos posteriormente con objetos y propiedades de modelos de datos respectivos. También puede generar y editar datos de ejemplo para propiedades de objetos del modelo de datos que puede utilizar para rellenar previamente formularios adaptables y comunicaciones interactivas al obtener una vista previa. Puede probar los objetos y servicios del modelo de datos configurados en un modelo de datos de formulario para asegurarse de que está correctamente integrado con los orígenes de datos.

Si es nuevo en la integración de datos de Forms y no ha configurado un origen de datos o creado un modelo de datos de formulario, consulte los temas siguientes:

* [Integración de datos de AEM Forms](/help/forms/using/data-integration.md)
* [Configuración de fuentes de datos](/help/forms/using/configure-data-sources.md)
* [Crear modelo de datos de formulario](/help/forms/using/create-form-data-models.md)

Continúe leyendo para obtener más información sobre las diversas tareas y configuraciones que puede realizar con el editor del modelo de datos de formulario.

>[!NOTE]
>
>Debe ser miembro de los grupos **fdm-author** y **forms-user** para poder crear y trabajar con el modelo de datos de formulario. Póngase en contacto con el administrador de AEM para convertirse en miembro de los grupos.

## Agregar objetos y servicios del modelo de datos {#add-data-model-objects-and-services}

Si ha creado un modelo de datos de formulario con orígenes de datos, puede utilizar el editor del modelo de datos de formulario para agregar objetos y servicios del modelo de datos, configurar sus propiedades, crear asociaciones entre objetos del modelo de datos y probar el modelo y los servicios de datos de formulario.

Puede agregar objetos y servicios del modelo de datos desde orígenes de datos disponibles en el modelo de datos de formulario. Cuando los objetos del modelo de datos añadidos aparecen en la ficha Modelo, los servicios añadidos aparecen en la pestaña Servicios.

Para agregar objetos y servicios del modelo de datos:

1. Inicie sesión en la instancia de autor de AEM, vaya a **[!UICONTROL Forms > Integraciones de datos]** y abra el modelo de datos de formulario en el que desea agregar objetos del modelo de datos.
1. En el panel Fuentes de datos , expanda las fuentes de datos para ver los objetos y servicios disponibles del modelo de datos.
1. Seleccione los objetos y servicios del modelo de datos que desea agregar al modelo de datos de formulario y pulse **[!UICONTROL Agregar seleccionado]**.

   ![objetos seleccionados](assets/selected-objects.png)

   La ficha Modelo muestra una representación gráfica de todos los objetos del modelo de datos y sus propiedades agregadas al modelo de datos del formulario. Cada objeto del modelo de datos se representa mediante un cuadro en el modelo de datos del formulario.

   ![model-tab](assets/model-tab.png)

   >[!NOTE]
   >
   >Puede mantener y arrastrar cuadros de objetos del modelo de datos alrededor para organizarlos en el área de contenido. Todos los objetos del modelo de datos agregados al modelo de datos de formulario aparecen atenuados en el panel Fuentes de datos.

   La ficha Servicios enumera los servicios añadidos.

   ![services-tab](assets/services-tab.png)

   >[!NOTE]
   >
   >Además de los objetos y servicios del modelo de datos, el documento de metadatos del servicio OData incluye propiedades de navegación que definen la asociación entre dos objetos del modelo de datos. Para obtener más información, consulte [Trabajo con propiedades de navegación de los servicios OData](#work-with-navigation-properties-of-odata-services).

1. Toque **[!UICONTROL Guardar]** para guardar el objeto del modelo de formulario.

   >[!NOTE]
   >
   >Puede invocar los servicios que configuró en la ficha Servicios de un modelo de datos de formulario mediante las reglas de formulario adaptables. Los servicios configurados están disponibles en la acción Invocar servicios del editor de reglas Para obtener más información sobre el uso de estos servicios en las reglas de formularios adaptables, consulte Invocar servicios y establecer el valor de las reglas en el [editor de reglas](/help/forms/using/rule-editor.md).

## Crear objetos del modelo de datos y propiedades secundarias {#create-data-model-objects-and-child-properties}

### Crear objetos del modelo de datos {#create-data-model-objects}

Aunque puede agregar objetos de modelo de datos desde orígenes de datos configurados, también puede crear objetos o entidades de modelo de datos sin orígenes de datos. Resulta útil, especialmente si no se han configurado orígenes de datos en el modelo de datos de formulario.

Para crear un objeto de modelo de datos sin orígenes de datos:

1. Inicie sesión en la instancia de autor de AEM, vaya a **[!UICONTROL Forms > Integraciones de datos]** y abra el modelo de datos de formulario en el que desea crear una entidad u objeto del modelo de datos.
1. Pulse **[!UICONTROL Crear entidad]**.
1. En el cuadro de diálogo Crear modelo de datos, especifique un nombre para el objeto del modelo de datos y pulse **[!UICONTROL Agregar]**. Se agrega un objeto de modelo de datos al modelo de datos del formulario. Tenga en cuenta que el objeto del modelo de datos recién agregado no está enlazado a un origen de datos y no tiene propiedades como se muestra en la siguiente imagen.

   ![new-entity](assets/new-entity.png)

A continuación, puede agregar propiedades secundarias en objetos del modelo de datos no enlazados.

### Agregar propiedades secundarias {#child-properties}

El editor del modelo de datos de formulario permite crear propiedades secundarias en un objeto del modelo de datos. La propiedad cuando se crea no está enlazada a ninguna propiedad de un origen de datos. Posteriormente, puede enlazar la propiedad secundaria con otra propiedad del objeto del modelo de datos que la contiene.

Para crear una propiedad secundaria:

1. En un modelo de datos de formulario, seleccione un objeto de modelo de datos y pulse **[!UICONTROL Crear propiedad secundaria]**.
1. En el cuadro de diálogo **[!UICONTROL Crear propiedad secundaria]**, especifique un nombre y un tipo de datos para la propiedad en los campos **[!UICONTROL Nombre]** y **[!UICONTROL Tipo]**, respectivamente. Si lo desea, puede especificar un título y una descripción para la propiedad.
1. Habilitar Calculado si la propiedad es una propiedad calculada. El valor de una propiedad calculada se evalúa en función de una regla o una expresión. Para obtener más información, consulte [Editar propiedades](#edit-properties).
1. Si el objeto del modelo de datos está enlazado a un origen de datos, la propiedad secundaria añadida se enlazará automáticamente a la propiedad del objeto del modelo de datos principal con el mismo nombre y tipo de datos.

   Para enlazar manualmente una propiedad secundaria con una propiedad de objeto del modelo de datos, pulse el icono Examinar situado junto al campo **[!UICONTROL Enlace de referencia]**. El cuadro de diálogo **[!UICONTROL Seleccionar objeto]** enumera todas las propiedades del objeto del modelo de datos principal. Seleccione una propiedad con la que enlazar y pulse el icono de visto. Tenga en cuenta que solo puede seleccionar una propiedad del mismo tipo de datos que la propiedad secundaria.

1. Pulse **[!UICONTROL Listo]** para guardar la propiedad secundaria y pulse **[!UICONTROL Guardar]** para guardar el modelo de datos del formulario. La propiedad secundaria se agrega ahora al objeto del modelo de datos.

Después de crear objetos y propiedades del modelo de datos, puede seguir creando formularios adaptables y comunicaciones interactivas basadas en el modelo de datos del formulario. Posteriormente, cuando haya orígenes de datos disponibles y configurados, puede enlazar el modelo de datos de formulario con orígenes de datos. El enlace se actualizará automáticamente en los formularios adaptables y comunicaciones interactivas asociados. Para obtener más información sobre la creación de formularios adaptables y comunicaciones interactivas mediante el modelo de datos de formulario, consulte [Uso del modelo de datos de formulario](/help/forms/using/using-form-data-model.md).

### Enlace de objetos y propiedades del modelo de datos {#bind-data-model-objects-and-properties}

Cuando los orígenes de datos que desea integrar con el modelo de datos de formulario están disponibles, puede agregarlos al modelo de datos de formulario tal como se describe en [Actualizar orígenes de datos](/help/forms/using/create-form-data-models.md#update). A continuación, haga lo siguiente para enlazar los objetos y propiedades del modelo de datos independiente:

1. En el modelo de datos de formulario, seleccione el origen de datos independiente que desea enlazar con un origen de datos.
1. Pulse **[!UICONTROL Editar propiedades]**.
1. En el panel **[!UICONTROL Editar propiedades]**, pulse el icono Examinar situado junto al campo **[!UICONTROL Enlace]**. Se abre el cuadro de diálogo **[!UICONTROL Seleccionar objeto]** que enumera los orígenes de datos agregados en el modelo de datos del formulario.

   ![select-object](assets/select-object.png)

1. Expanda el árbol de fuentes de datos y seleccione un objeto de modelo de datos para enlazar con el icono de marca de verificación y tocarlo.
1. Pulse **[!UICONTROL Listo]** para guardar las propiedades y, a continuación, pulse **[!UICONTROL Guardar]** para guardar el modelo de datos del formulario. El objeto del modelo de datos ahora está enlazado con un origen de datos. Observe que el objeto del modelo de datos ya no está marcado como Unbound.

   ![bound-model-object](assets/bound-model-object.png)

## Configurar servicios {#configure-services}

Para leer y escribir datos para un objeto de modelo de datos, haga lo siguiente para configurar los servicios de lectura y escritura:

1. Seleccione la casilla de verificación situada en la parte superior de un objeto del modelo de datos para seleccionarlo y pulse **[!UICONTROL Editar propiedades]**.

   ![edit-properties](assets/edit-properties.png)

   Editar propiedades para configurar los servicios de lectura y escritura de un objeto de modelo de datos

   Se abre el cuadro de diálogo Editar propiedades.

   ![edit-properties-2](assets/edit-properties-2.png)

   Cuadro de diálogo Editar propiedades

   >[!NOTE]
   >
   >Además de los objetos y servicios del modelo de datos, el documento de metadatos del servicio OData incluye propiedades de navegación que definen la asociación entre dos objetos del modelo de datos. Cuando se agrega un origen de datos del servicio OData a un Modelo de datos de formulario, hay un servicio disponible en el Modelo de datos de formulario para todas las propiedades de navegación de un objeto del modelo de datos. Puede utilizar este servicio para leer las propiedades de navegación del objeto del modelo de datos correspondiente.
   >
   >Para obtener más información sobre el uso del servicio, consulte [Trabajo con propiedades de navegación de los servicios OData](#work-with-navigation-properties-of-odata-services).

1. Cambie **[!UICONTROL Top Level Object]** para especificar si el objeto del modelo de datos es un objeto de modelo de nivel superior.

   Los objetos del modelo de datos configurados en un modelo de datos de formulario están disponibles para su uso en la ficha Objetos del modelo de datos del explorador de contenido de un formulario adaptable basado en el modelo de datos del formulario. Cuando se agrega asociación entre dos objetos del modelo de datos, el objeto del modelo de datos con el que se asocia se anida en el objeto del modelo de datos que se asocia en la ficha Objetos del modelo de datos. Si el modelo de datos anidado es un objeto de nivel superior, también aparecerá por separado en la ficha Objetos del modelo de datos. Por lo tanto, verá dos entradas de la misma, una dentro y otra fuera de la jerarquía anidada, lo que podría confundir a los autores del formulario. Para que el objeto del modelo de datos asociado aparezca solo en la jerarquía anidada, desactive la propiedad Objeto de nivel superior.

1. Seleccione Read and Write services para los objetos del modelo de datos seleccionado. Aparecen los argumentos de los servicios.

   ![read-write-services](assets/read-write-services.png)

   Servicios de lectura y escritura configurados para la fuente de datos de los empleados

1. Pulse ![aem_6_3_edit](assets/aem_6_3_edit.png) para que el argumento del servicio de lectura se enlace a un atributo de perfil de usuario, a un atributo de solicitud o a un valor literal y especifique el valor de enlace. Vincula el argumento service al atributo de enlace o valor literal especificado, que se pasa al servicio como argumento para recuperar detalles asociados con el valor especificado de la fuente de datos.

   En este ejemplo, el argumento `id` tomará el valor del atributo `empid` del perfil de usuario y lo pasará como argumento al servicio de lectura. Leerá y devolverá valores de propiedades asociadas del objeto del modelo de datos `employee` para el `empid` especificado. Por lo tanto, si especifica 00250 en el campo `empid` del formulario, el servicio de lectura leerá los detalles del empleado con 00250 id de empleado.

   Además, puede hacer que un argumento sea obligatorio u opcional.

   ![editar-argumento](assets/edit-argument.png)

   Enlace del argumento id al atributo empid de AEM perfil de usuario

1. Pulse **[!UICONTROL Listo]** para guardar el argumento, **[!UICONTROL Listo]** para guardar las propiedades y, a continuación, **[!UICONTROL Guardar]** para guardar el modelo de datos del formulario.

## Agregar asociaciones {#add-associations}

Normalmente, hay asociaciones creadas entre objetos del modelo de datos en un origen de datos. La asociación puede ser de uno a uno o de uno a varios. Por ejemplo, puede haber varios dependientes asociados a un empleado. Se denomina asociación &quot;uno a varios&quot; y `1:n` la representa en la línea que conecta los objetos del modelo de datos asociados. Sin embargo, si una asociación devuelve un nombre de empleado único para un ID de empleado determinado, se denomina asociación uno a uno.

Cuando se agregan objetos del modelo de datos asociados en un origen de datos a un modelo de datos de formulario, sus asociaciones se retienen y se muestran como conectadas mediante líneas de flecha. Puede agregar asociaciones entre objetos del modelo de datos en distintos orígenes de datos en un modelo de datos de formulario.

>[!NOTE]
>
>Las asociaciones predefinidas en un origen de datos JDBC no se conservan en el modelo de datos de formulario. Debe crearlos manualmente.

Para añadir una asociación:

1. Seleccione la casilla de verificación situada en la parte superior de un objeto de modelo de datos para seleccionarlo y pulse **[!UICONTROL Agregar asociación]**. Se abre el cuadro de diálogo Agregar asociación .

   ![añadir-asociación](assets/add-association.png)

   >[!NOTE]
   >
   >Además de los objetos y servicios del modelo de datos, el documento de metadatos del servicio OData incluye propiedades de navegación que definen la asociación entre dos objetos del modelo de datos. Puede utilizar estas propiedades de navegación cuando agregue asociaciones en el Modelo de datos de formulario. Para obtener más información, consulte [Trabajo con propiedades de navegación de los servicios OData](#work-with-navigation-properties-of-odata-services).

   Se abre el cuadro de diálogo Agregar asociación .

   ![add-associate-2](assets/add-association-2.png)

   Cuadro de diálogo Agregar asociación

1. En el panel Agregar asociación :

   * Especifique un título para la asociación.
   * Seleccione el tipo de asociación: de uno a uno o de uno a muchos.
   * Seleccione el objeto del modelo de datos que desea asociar.
   * Seleccione el servicio de lectura para leer los datos del objeto de modelo seleccionado. Aparece el argumento de servicio de lectura. Edite para cambiar el argumento, si es necesario, y enlácelo a la propiedad del objeto del modelo de datos que desea asociar.

   En el siguiente ejemplo, el argumento predeterminado para el servicio de lectura del objeto del modelo de datos Dependent es `dependentid`.

   ![add-union-example](assets/add-association-example.png)

   El argumento predeterminado para el servicio de lectura de dependientes es dependiente

   Sin embargo, el argumento debe ser una propiedad común entre el objeto del modelo de datos asociado, que en este ejemplo es `Employeeid`. Por lo tanto, el argumento `Employeeid` debe enlazarse a la propiedad `id` del objeto del modelo de datos Empleado para obtener los detalles de dependientes asociados del objeto del modelo de datos Dependent.

   ![add-associate-example-2](assets/add-association-example-2.png)

   Argumento y enlace actualizados

   Toque **[!UICONTROL Listo]** para guardar el argumento.

1. Pulse **[!UICONTROL Listo]** para guardar la asociación y, a continuación, **[!UICONTROL Guardar]** para guardar el modelo de datos del formulario.
1. Repita los pasos para crear más asociaciones según sea necesario.

>[!NOTE]
>
>La asociación añadida aparece en el cuadro de objetos del modelo de datos con el título especificado y una línea que conecta los objetos del modelo de datos asociados.
>
>Para editar una asociación, seleccione la casilla de verificación correspondiente y pulse **[!UICONTROL Editar asociación]**.

![add-associate](assets/added-association.png)

## Editar propiedades {#properties}

Puede editar las propiedades de los objetos del modelo de datos, sus propiedades y los servicios que se agreguen en el modelo de datos de formulario.

Para editar propiedades:

1. Active la casilla de verificación situada junto a un objeto de modelo de datos, una propiedad o un servicio del modelo de datos de formulario.
1. Pulse **[!UICONTROL Editar propiedades]**. Se abrirá el panel **[!UICONTROL Editar propiedades]** del objeto, propiedad o servicio del modelo seleccionado.

   * **Objeto** del modelo de datos: Especifique los servicios de lectura y escritura y edite los argumentos.
   * **Propiedad**: Especifique el tipo, subtipo y formato de la propiedad. También puede especificar si la propiedad seleccionada es la clave principal del objeto del modelo de datos.
   * **Servicio**: Especifique el objeto del modelo de entrada, el tipo de salida y los argumentos del servicio. Para un servicio Get, puede especificar si se espera que devuelva una matriz.

   ![edit-properties-service](assets/edit-properties-service.png)

   Cuadro de diálogo Editar propiedades para obtener un servicio

1. Pulse **[!UICONTROL Listo]** para guardar las propiedades y, a continuación, **[!UICONTROL Guardar]** para guardar el modelo de datos del formulario.

### Crear propiedades calculadas {#computed}

Una propiedad calculada es aquella cuyo valor se calcula en función de una regla o una expresión. Con una regla, puede establecer el valor de una propiedad calculada en una cadena literal, un número, el resultado de una expresión matemática o el valor de otra propiedad en el modelo de datos del formulario.

Por ejemplo, puede crear una propiedad calculada **FullName** cuyo valor sea el resultado de la concatenación de las propiedades **FirstName** y **LastName** existentes. Para ello:

1. Cree una nueva propiedad con el nombre `FullName` cuyo tipo de datos sea String.
1. Habilite **[!UICONTROL Computed]** y pulse **[!UICONTROL Done]** para crear la propiedad.

   ![computado](assets/computed.png)

   Se crea la propiedad calculada FullName. Fíjese en el icono que aparece junto a la propiedad para mostrar una propiedad calculada.

   ![computed-prop](assets/computed-prop.png)

1. Seleccione la propiedad FullName y pulse **[!UICONTROL Editar regla]**. Se abre una ventana del editor de reglas.
1. En la ventana del editor de reglas, pulse **[!UICONTROL Crear]**. Se abre una ventana de regla **[!UICONTROL Set Value]**.

   En la lista desplegable Seleccionar opción , seleccione **[!UICONTROL Expresión matemática]**. Otras opciones disponibles son **[!UICONTROL Form Data Model Object]** y **[!UICONTROL String]**.

1. En la expresión matemática, seleccione **[!UICONTROL FirstName]** y **[!UICONTROL LastName]** en el primer y el segundo objeto, respectivamente. Seleccione **[!UICONTROL plus]** como operador.

   Pulse **[!UICONTROL Listo]** y, a continuación, pulse **[!UICONTROL Cerrar]** para cerrar la ventana del editor de reglas. La regla tiene un aspecto similar al siguiente.

   ![regla](assets/rule.png)

1. En el modelo de datos de formulario, pulse **[!UICONTROL Guardar]**. La propiedad calculada está configurada.

## Trabajar con propiedades de navegación de los servicios de OData {#work-with-navigation-properties-of-odata-services}

En los servicios OData, las propiedades de navegación se utilizan para definir asociaciones entre dos objetos del modelo de datos. Estas propiedades se definen en un tipo de entidad o un tipo complejo. Por ejemplo, en el siguiente extracto del archivo de metadatos de los servicios de ejemplo de OData de ejemplo [TripPin](https://www.odata.org/blog/trippin-new-odata-v4-sample-service/), la entidad persona contiene tres propiedades de navegación: Amigos, BestFriend y Viajes.

Para obtener más información sobre las propiedades de navegación, consulte [Documentación de OData](https://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part3-csdl/odata-v4.0-errata03-os-part3-csdl-complete.html#_Toc453752536).

```xml
<edmx:Edmx xmlns:edmx="https://docs.oasis-open.org/odata/ns/edmx" Version="4.0">
<script/>
<edmx:DataServices>
<Schema xmlns="https://docs.oasis-open.org/odata/ns/edm" Namespace="Microsoft.OData.Service.Sample.TrippinInMemory.Models">
<EntityType Name="Person">
<Key>
<PropertyRef Name="UserName"/>
</Key>
<Property Name="UserName" Type="Edm.String" Nullable="false"/>
<Property Name="FirstName" Type="Edm.String" Nullable="false"/>
<Property Name="LastName" Type="Edm.String"/>
<Property Name="MiddleName" Type="Edm.String"/>
<Property Name="Gender" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.PersonGender" Nullable="false"/>
<Property Name="Age" Type="Edm.Int64"/>
<Property Name="Emails" Type="Collection(Edm.String)"/>
<Property Name="AddressInfo" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location)"/>
<Property Name="HomeAddress" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Location"/>
<Property Name="FavoriteFeature" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature" Nullable="false"/>
<Property Name="Features" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Feature)" Nullable="false"/>
<NavigationProperty Name="Friends" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person)"/>
<NavigationProperty Name="BestFriend" Type="Microsoft.OData.Service.Sample.TrippinInMemory.Models.Person"/>
<NavigationProperty Name="Trips" Type="Collection(Microsoft.OData.Service.Sample.TrippinInMemory.Models.Trip)"/>
</EntityType>
```

Al configurar un servicio OData en un Modelo de datos de formulario, todas las propiedades de navegación de un contenedor de entidades están disponibles a través de un servicio del Modelo de datos de formulario. En este ejemplo del servicio de OData TripPin, las tres propiedades de navegación del contenedor de entidad `Person` se pueden leer utilizando un servicio `GET LINK` en el Modelo de datos de formulario.

A continuación, se resalta el servicio `GET LINK of Person /People` en el Modelo de datos de formulario, que es un servicio combinado para las tres propiedades de navegación en la entidad `Person` del servicio OData de TripPin.

![nav-prop-service](assets/nav-prop-service.png)

Una vez que agregue el servicio `GET LINK` a la ficha Servicios del Modelo de datos de formulario, puede editar las propiedades para elegir el objeto del modelo de salida y la propiedad de navegación que se utilizará en el servicio. Por ejemplo, el siguiente servicio `GET LINK of Person /People` del siguiente ejemplo utiliza Trip como objeto del modelo de salida y la propiedad de navegación como Trips.

![edit-prop-nav-prop](assets/edit-prop-nav-prop.png)

>[!NOTE]
>
>Los valores disponibles en el campo **[!UICONTROL Default Value]** del argumento **NavigationPropertyName** dependen del estado de la matriz **[!UICONTROL Return?]** botón de alternancia. Cuando está activada, muestra las propiedades de navegación del tipo Collection.

En este ejemplo, también puede elegir el objeto del modelo de salida como argumento de propiedad de persona y navegación como Amigos o BestFriend (en función de si la matriz **[!UICONTROL Return?]** está activada o desactivada).

![edit-prop-nav-prop2](assets/edit-prop-nav-prop2.png)

Del mismo modo, puede elegir un servicio `GET LINK` y configurar sus propiedades de navegación al agregar asociaciones en el Modelo de datos de formulario. Sin embargo, para poder seleccionar una propiedad de navegación, asegúrese de que el **[!UICONTROL Enlace al campo]** esté configurado como **[!UICONTROL Literal]**.

![add-associate-nav-prop](assets/add-association-nav-prop.png)

## Generar y editar datos de ejemplo {#sample}

El editor del modelo de datos de formulario permite generar datos de ejemplo para todas las propiedades de objetos del modelo de datos, incluidas las propiedades calculadas, en un modelo de datos de formulario. Es un conjunto de valores aleatorios que cumplen con el tipo de datos configurado para cada propiedad. También puede editar y guardar datos, que se conservan incluso si se regeneran los datos de ejemplo.

Para generar y editar datos de ejemplo, haga lo siguiente:

1. Abra un modelo de datos de formulario y pulse **[!UICONTROL Editar datos de ejemplo]**. Genera y muestra los datos de ejemplo en la ventana Editar datos de ejemplo .

   ![sample-data](assets/sample-data.png)

1. En la ventana **[!UICONTROL Editar datos de ejemplo]** , edite los datos según sea necesario y pulse **[!UICONTROL Guardar]**.

A continuación, puede utilizar los datos de ejemplo para rellenar previamente y probar comunicaciones interactivas basadas en el modelo de datos de formulario. Para obtener más información, consulte [Uso del modelo de datos de formulario](/help/forms/using/using-form-data-model.md).

## Probar los objetos y servicios del modelo de datos {#test-data-model-objects-and-services}

El modelo de datos de formulario está configurado, pero antes de ponerlo en uso, es posible que desee comprobar si los objetos y servicios configurados del modelo de datos funcionan según lo esperado. Para probar los objetos y servicios del modelo de datos:

1. Seleccione un objeto de modelo de datos o un servicio en el modelo de datos de formulario y pulse **[!UICONTROL Test Model Object]** o **[!UICONTROL Test Service]**, respectivamente.

   Se abre la ventana Modelo de datos de formulario de prueba.

   ![test-data-model](assets/test-data-model.png)

1. En la ventana Probar modelo de datos de formulario, seleccione el objeto o servicio del modelo de datos que desea probar en el panel Entrada.

1. Especifique un valor de argumento en el código de prueba y pulse **[!UICONTROL Prueba]**. Una prueba correcta devuelve el resultado en el panel Salida.

   ![test-data-model-2](assets/test-data-model-2.png)

Del mismo modo, se pueden probar otros objetos y servicios del modelo de datos de formulario.

## Pasos siguientes {#next-steps}

Tiene un modelo de datos de formulario de trabajo que ya está listo para su uso en formularios adaptables y flujos de trabajo de comunicaciones interactivos. Para obtener más información, consulte [Uso del modelo de datos de formulario](/help/forms/using/using-form-data-model.md).
