---
title: Componentes de Adobe Campaign
seo-title: Adobe Campaign Components
description: Cuando integre con Adobe Campaign, tendrá componentes disponibles para cuando trabaje con boletines informativos y formularios.
seo-description: When you integrate with Adobe Campaign, you have components available for when working with newsletters and with forms.
uuid: 5c75c216-dc28-4d3b-b6f7-3c4726143c8b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 560b62b7-6bff-4cc4-baf9-c6573daa61ef
exl-id: 66fc7691-1c93-4714-b75f-ae03512261e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2490'
ht-degree: 7%

---

# Componentes de Adobe Campaign{#adobe-campaign-components}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cuando integre con Adobe Campaign, tendrá componentes disponibles para cuando trabaje con boletines informativos y formularios. Ambas se describen en este documento.

## Componentes del boletín de Adobe Campaign {#adobe-campaign-newsletter-components}

Todos los componentes de Campaign siguen las prácticas recomendadas descritas en [Prácticas recomendadas para plantillas de correo electrónico](/help/sites-administering/best-practices-for-email-templates.md) y se basan en el lenguaje de marcado de Adobe [HTL](https://helpx.adobe.com/es/experience-manager/htl/using/overview.html).

Cuando abra un boletín o correo electrónico configurado para integrarse con Adobe Campaign, debería ver los siguientes componentes en la sección **Newsletter de Adobe Campaign** sección:

* Encabezado (Campaign)
* Imagen (Campaign)
* Vínculo (campaña)
* Plantilla de imagen de Scene7 (Campaign)
* Referencia de destino (Campaign)
* Texto e imagen (Campaign)
* Texto y personalización (Campaign)

En la siguiente sección se describe estos componentes.

![chlimage_1-112](assets/chlimage_1-112.png)

### Encabezado (Campaign) {#heading-campaign}

El componente Encabezado puede:

* Muestre el nombre de la página actual; para ello, deje la variable **Título** campo en blanco.
* Mostrar un texto especificado en la **Título** campo .

Edite el **Encabezado (Campaign)** directamente. Dejar vacío para utilizar el título de página.

![chlimage_1-113](assets/chlimage_1-113.png)

Puede configurar lo siguiente:

* **Título**
Si desea utilizar un nombre que no sea el título de la página, introdúzcalo aquí.

* **Nivel de encabezado (1, 2, 3, 4)**
Nivel de encabezado basado en los tamaños de encabezamiento del HTML 1-4.

En el siguiente ejemplo se muestra el componente Encabezado (Campaign) que se está visualizando.

![chlimage_1-114](assets/chlimage_1-114.png)

### Imagen (Campaign) {#image-campaign}

El componente de imagen (campaña) muestra una imagen y un texto de acompañamiento en función de los parámetros especificados.

Puede cargar una imagen y, a continuación, editarla y manipularla (por ejemplo, recortar, rotar y añadir un vínculo/título/texto).

Puede cargar una imagen y, a continuación, editarla y manipularla (por ejemplo, recortar, rotar y añadir un vínculo/título/texto). Puede arrastrar y soltar una imagen desde el [Buscador de contenido](/help/sites-authoring/author-environment-tools.md#thecontentfinderclassicui) directamente en el componente o en su cuadro de diálogo Editar. También puede hacer doble clic en el área central del cuadro de diálogo Editar para explorar el sistema de archivos local y cargar una imagen. Las dos pestañas del cuadro de diálogo Editar también controlan todas las definiciones y manipulaciones de la imagen:

![chlimage_1-115](assets/chlimage_1-115.png)

Cuando se carga una imagen, se puede configurar lo siguiente:

* **Mapa**
Para asignar una imagen, seleccione Asignar. Puede especificar cómo desea crear el mapa de imagen (rectángulo, polígono, etc.) y hacia dónde debe apuntar el área.

* **Recortar**
Seleccione Recortar para recortar una imagen. Utilice el ratón para recortar la imagen.

* **Rotar**
Para girar una imagen, seleccione Rotar. Utilícelo repetidamente hasta que la imagen gire de la manera que desee.

* **Borrar**
Elimine la imagen actual.

* Barra de zoom (solo clásica)

   Para acercar y alejar la imagen, utilice la barra de deslizamiento situada debajo de la imagen (encima de los botones Aceptar y Cancelar)

* **Título**

   Título de la imagen.

* **Texto alternativo**

   Texto alternativo para usar al crear contenido accesible.

* **Vincular a**

   Cree un vínculo a los recursos u otras páginas dentro del sitio web.

* **Descripción**

   Descripción de la imagen.

* **Tamaño**

   Define la altura y la anchura de la imagen.

>[!NOTE]
>
>Debe introducir la información en el **Texto alternativo** en el campo **Avanzadas** o la imagen no se puede guardar y verá el siguiente mensaje de error:
>
>`Validation failed. Verify the values of the marked fields.`

En el siguiente ejemplo se muestra el componente Imagen (Campaign) que se está visualizando.

![chlimage_1-116](assets/chlimage_1-116.png)

### Vínculo (campaña) {#link-campaign}

El componente Vínculo (Campaign) le permite añadir un vínculo al boletín informativo. Este componente solo está disponible en la interfaz de usuario clásica, aunque se puede añadir uno en la interfaz de usuario táctil y abrirlo en modo de compatibilidad.

![chlimage_1-117](assets/chlimage_1-117.png)

Puede configurar lo siguiente en la sección **Mostrar**, **Información de URL** o **Avanzadas** pestañas:

* **Rótulo de vínculo**
Pie de ilustración del vínculo. Este es el texto que ven los usuarios.

* **Información del objeto Link**
Agrega información adicional sobre cómo utilizar el vínculo.

* **LinkType**
En la lista desplegable, seleccione entre 
**Dirección URL personalizada** y **Documento adaptable**. Este campo es obligatorio. Si selecciona URL personalizada, puede proporcionar la URL del vínculo. Si selecciona Documento adaptable, puede proporcionar la ruta del documento.

* **Parámetro de URL adicional**
Añada cualquier parámetro de URL adicional. Haga clic en Agregar elemento para agregar varios elementos.

>[!NOTE]
>
>Debe introducir la información en el **Tipo de vínculo** en el campo **Información de URL** o el componente no se puede guardar y verá el siguiente mensaje de error:
>
>`Validation failed. Verify the values of the marked fields.`

En el siguiente ejemplo se muestra el componente Vínculo (Campaign) que se está visualizando.

![chlimage_1-118](assets/chlimage_1-118.png)

### Referencia de destino (Campaign) {#targeted-reference-campaign}

El componente Referencia de destino (Campaign) permite crear una referencia a un párrafo de destino.

En este componente, vaya al párrafo de destino para seleccionarlo.

Haga clic en el menú desplegable para desplazarse hasta el párrafo al que desea hacer referencia. Cuando termine, haga clic en **OK**.

### Texto e imagen (Campaign) {#text-image-campaign}

El componente Texto e imagen (Campaign) añade un bloque de texto y una imagen.

![chlimage_1-119](assets/chlimage_1-119.png)

Al igual que con los componentes Texto y personalización (Campaign) e Imagen (Campaign) , puede configurar:

* **Texto**
Escriba texto. Utilice la barra de herramientas para modificar el formato, crear listas y añadir vínculos.

* **Imagen**
Arrastre una imagen desde el buscador de contenido o haga clic para buscar una imagen. Recorte o gire según sea necesario.

* **Propiedades de imagen** (**Propiedades de imagen avanzadas**)

   Permite especificar lo siguiente:

   * **Título**

      Título del bloque; se mostrará pasando el ratón.

   * **Texto alternativo**

      Texto alternativo que se mostrará si la imagen no se puede mostrar.

   * **Vincular a**

      Cree un vínculo a los recursos u otras páginas dentro del sitio web.

   * **Descripción**

      Descripción de la imagen.

   * **Tamaño**

      Define la altura y la anchura de la imagen.

>[!NOTE]
>
>La variable **Texto alternativo** en el campo **Avanzadas** es obligatorio o el componente no se puede guardar y verá el siguiente mensaje de error:
>
>`Validation failed. Verify the values of the marked fields.`

En el siguiente ejemplo se muestra el componente Texto e imagen (Campaign) que se está visualizando.

![chlimage_1-120](assets/chlimage_1-120.png)

### Texto y personalización (Campaign) {#text-personalization-campaign}

El componente Texto y personalización (Campaign) permite introducir un bloque de texto utilizando un editor WYSIWYG, con la funcionalidad proporcionada por el [Editor de texto enriquecido](/help/sites-authoring/rich-text-editor.md). Además, este componente permite utilizar campos de contexto y bloques de personalización disponibles en Adobe Campaign; también consulte [Inserción de personalización](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#inserting-personalization).

La selección de iconos permite dar formato al texto, incluyendo características de fuente, alineación, vínculos, listas y sangría.

Agregue texto como lo haría normalmente en el editor de texto enriquecido. Para añadir la personalización, seleccione la lista desplegable Adobe Campaign y seleccione los campos que desee.

![chlimage_1-121](assets/chlimage_1-121.png)

Puede añadir los campos de texto y contexto o los bloques de personalización para crear el contenido. A continuación, seleccione Client Context para probar los datos en los perfiles de personalidad. Después de seleccionar una persona, los campos de personalización se sustituyen automáticamente por datos del perfil seleccionado.

>[!NOTE]
>
>Solo los campos definidos en la variable **nms:seedMember** se tienen en cuenta el esquema o una de sus extensiones. Los atributos de las tablas vinculadas a **nms:seedMember** no están disponibles.

## Componentes de formulario de Adobe Campaign {#adobe-campaign-form-components}

Los componentes de Adobe Campaign se utilizan para crear un formulario que los usuarios rellenen para suscribirse a un boletín, cancelar la suscripción a un boletín o actualizar sus perfiles de usuario.

Cada campo de componente se puede vincular a un campo de base de datos de Adobe Campaign. Los campos disponibles difieren según el tipo de datos que contienen, tal como se describe en la sección [Componentes y tipo de datos](#components-and-data-type). Si amplía el esquema de destinatarios en Adobe Campaign, los nuevos campos estarán disponibles en los componentes cuyos tipos de datos coincidan.

Cuando abra un formulario configurado para integrarse con Adobe Campaign, verá los siguientes componentes en la variable **Adobe Campaign** sección:

* Casilla (Campaign)
* Campo de fecha (Campaign) y Campo de fecha/HTML5 (Campaign)
* Clave principal cifrada (Campaign)
* Visualización de error (Campaign)
* Clave de reconciliación oculta (Campaign)
* Campo numérico (Campaign)
* Campo de opción (Campaign)
* Lista de comprobación de suscripciones (Sightly)
* Campo de texto (Campaign)

En esta sección se describe cada componente en detalle.

### Componentes y tipo de datos {#components-and-data-type}

En la tabla siguiente se describen los componentes disponibles para mostrar y modificar los datos de perfil de Adobe Campaign. Cada componente se puede asignar a un campo de perfil de Adobe Campaign para mostrar su valor y actualizar el campo cuando se envíe el formulario. Los distintos componentes solo pueden coincidir con campos de un tipo de datos adecuado.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Componente</strong></p> </td> 
   <td><p><strong>Tipo de datos del campo Adobe Campaign</strong></p> </td> 
   <td><p><strong>Campo de ejemplo</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Casilla (Campaign)</p> </td> 
   <td><p>booleano</p> </td> 
   <td><p>Ya no se puede contactar (por ningún canal)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo de fecha (Campaign)</p> <p>Campo de fecha/HTML 5 (Campaign)</p> </td> 
   <td><p>fecha</p> </td> 
   <td><p>Fecha de nacimiento</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo numérico (Campaign)</p> </td> 
   <td><p>numérico (byte, corto, largo, doble)</p> </td> 
   <td><p>Edad</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo de opción (Campaign)</p> </td> 
   <td><p>byte con valores asociados</p> </td> 
   <td><p>Sexo</p> </td> 
  </tr> 
  <tr> 
   <td><p>Campo de texto (Campaign)</p> </td> 
   <td><p>cadena</p> </td> 
   <td><p>Correo electrónico</p> </td> 
  </tr> 
 </tbody> 
</table>

### Configuración común a la mayoría de componentes {#settings-common-to-most-components}

Los componentes de Adobe Campaign tienen configuraciones comunes en todos los componentes (excepto los componentes Clave principal cifrada y Clave de reconciliación oculta).

En la mayoría de los componentes, puede configurar lo siguiente:

#### Título y texto {#title-and-text}

* **Título**

   Si desea utilizar un nombre que no sea el nombre del elemento, introdúzcalo aquí.

* **Ocultar título**

   Seleccione esta casilla de verificación si no desea que el título sea visible.

* **Descripción**

   Añada una descripción al campo para proporcionar más información para los usuarios.

* **Mostrar sólo valor**

   Solo muestra el valor, si hay uno

#### Adobe Campaign {#adobe-campaign}

Puede configurar lo siguiente:

* **Asignación**

   Seleccione un campo de personalización de Adobe Campaign, si corresponde.

* **Clave de reconciliación**

   Seleccione esta casilla de verificación si este campo forma parte de la clave de reconciliación.

#### Restricciones {#constraints}

* **Requerido**

   Seleccione esta casilla de verificación para que este componente sea necesario; es decir, los usuarios deben introducir un valor.

* **Mensaje obligatorio**

   De forma opcional, añada un mensaje que indique que el campo es obligatorio.

#### Estilo {#styling}

* **CSS**

   Introduzca las clases CSS que desee utilizar para este componente.

### Casilla (Campaign) {#checkbox-campaign}

El componente Casilla (Campaign) permite al usuario modificar los campos de perfil de Adobe Campaign que son de tipo booleano de datos. Por ejemplo, puede tener un componente Casilla (Campaign) que permita al destinatario especificar que no desea que se le contacte a través de ningún canal.

Puede [configuración común a la mayoría de componentes de Adobe Campaign](#settings-common-to-most-components) en el componente Casilla (Campaign).

En el siguiente ejemplo se muestra el componente Casilla (Campaign) que se está visualizando.

![chlimage_1-122](assets/chlimage_1-122.png)

### Campo de fecha (Campaign) y Campo de fecha/HTML 5 (Campaign) {#date-field-campaign-and-date-field-html-campaign}

Utilice el campo date para permitir que los destinatarios alcancen una fecha; por ejemplo, puede que desee que los destinatarios especifiquen sus fechas de nacimiento. El formato de fecha coincide con el formato utilizado en la instancia de Adobe Campaign.

Además de [configuración común a la mayoría de componentes de Adobe Campaign](#settings-common-to-most-components), puede configurar lo siguiente:

* **Restricciones - Restricción** lista desplegable

   Puede seleccionar - **Ninguna** o **Fecha** : para añadir la restricción de una fecha o sin ninguna restricción. Si selecciona fecha, la respuesta que los usuarios escriban en el campo debe tener un formato de fecha.

* **Mensaje de restricción**

   Además, puede añadir un mensaje de restricción para que los usuarios sepan cómo dar formato a sus respuestas.

* **Estilo - Anchura**

   Ajuste la anchura del campo tocando o haciendo clic en el **+** y **-** o escribir un número.

En el siguiente ejemplo se muestra el componente Campo de fecha (Campaign) con el ancho ajustado que se está visualizando.

![chlimage_1-123](assets/chlimage_1-123.png)

### Clave principal cifrada (Campaign) {#encrypted-primary-key-campaign}

Este componente define el nombre del parámetro de URL que contendrá el identificador de un perfil de Adobe Campaign (**Identificador de recurso principal** o **Clave principal cifrada** en Adobe Campaign Standard y 6.1, respectivamente).

Cada formulario que muestra y modifica los datos de perfil de Adobe Campaign **must** incluir un componente Clave principal cifrada.

Puede configurar lo siguiente en el componente Clave principal cifrada (Campaign):

* **Título y texto: Nombre del elemento**

   El valor predeterminado es encryptionPK. Solo es necesario cambiar el nombre del elemento cuando esté en conflicto con el nombre de otro elemento del formulario. Dos campos de formulario no pueden tener el mismo nombre de elemento.

* **Adobe Campaign: parámetro de URL**

   Añada el parámetro URL para la EPK. Por ejemplo, puede utilizar el valor **epk**.

En el siguiente ejemplo se muestra el componente Clave principal cifrada (Campaign) que se está visualizando.

![chlimage_1-124](assets/chlimage_1-124.png)

### Visualización de error (Campaign) {#error-display-campaign}

Este componente permite mostrar errores de back-end. La gestión de errores del formulario debe configurarse como Reenviar para que el componente funcione correctamente.

En el siguiente ejemplo se muestra el componente Visualización de error (Campaign) que se está visualizando.

![chlimage_1-125](assets/chlimage_1-125.png)

### Clave de reconciliación oculta (Campaign) {#hidden-reconciliation-key-campaign}

El componente Clave de reconciliación oculta (Campaign) le permite añadir campos ocultos como parte de la clave de reconciliación a un formulario.

Puede configurar lo siguiente en el componente Clave de reconciliación oculta (Campaign):

* **Título y texto: Nombre del elemento**

   Toma el valor predeterminado reconcilKey. Solo es necesario cambiar el nombre del elemento cuando esté en conflicto con el nombre de otro elemento del formulario. Dos campos de formulario no pueden tener el mismo nombre de elemento.
* **Adobe Campaign: asignación**
Asigne a un campo de personalización de Adobe Campaign.

En el siguiente ejemplo se muestra el componente Clave de reconciliación oculta (Campaign) que se está visualizando.

![chlimage_1-126](assets/chlimage_1-126.png)

### Campo numérico (Campaign) {#numeric-field-campaign}

Utilice el campo numérico para permitir que los destinatarios introduzcan números, por ejemplo su edad.

Además de [configuración común a la mayoría de componentes de Adobe Campaign](#settings-common-to-most-components), puede configurar lo siguiente:

* **Restricciones - Restricción** lista desplegable

   Puede seleccionar - **Ninguna** o **Numérico** - para añadir la restricción de un número o de ninguna restricción. Si selecciona un número, la respuesta que los usuarios escriban en el campo debe ser numérica.

* **Mensaje de restricción**

   Además, puede añadir un mensaje de restricción para que los usuarios sepan cómo dar formato a sus respuestas.
* **Estilo - Anchura**
Ajuste la anchura del campo tocando o haciendo clic en el 
**+** y **-** o escribir un número.

En el siguiente ejemplo se muestra un componente Campo numérico (Campaign) con el ancho configurado que se está visualizando.

![chlimage_1-127](assets/chlimage_1-127.png)

### Campo de opción (Campaign) {#option-field-campaign}

Esta lista desplegable permite seleccionar una opción; por ejemplo, el sexo o el estado de un destinatario.

Puede [configuración común a la mayoría de componentes de Adobe Campaign](#settings-common-to-most-components) en el componente Campo de opciones (Campaign). Para rellenar la lista desplegable, seleccione el campo correspondiente en los campos de personalización de Adobe Campaign tocando o haciendo clic en el símbolo de Adobe Campaign y navegando hasta el campo .

En el siguiente ejemplo se muestra el componente Campo de opciones (Campaign) que se está visualizando.

![chlimage_1-128](assets/chlimage_1-128.png)

### Lista de comprobación de suscripciones (Sightly) {#subscriptions-checklist-campaign}

Utilice la variable **Lista de comprobación de suscripciones (Campaign)** para modificar las suscripciones asociadas a un perfil de Adobe Campaign.

Cuando se agrega a un formulario, este componente muestra todas las suscripciones disponibles como casillas de verificación y permite al usuario seleccionar las suscripciones que desee. Cuando los usuarios envían el formulario, este componente suscribe al usuario o cancela su suscripción de los servicios seleccionados según el tipo de acción del formulario (**Adobe Campaign: Suscripción a servicios** o **Adobe Campaign: Cancelar suscripción a los servicios**).

>[!NOTE]
>
>El componente no comprueba a qué servicios se ha suscrito o dado de baja el usuario.

Puede [configuración común a la mayoría de componentes de Adobe Campaign](#settings-common-to-most-components) en el componente Lista de comprobación de suscripciones (Campaign) . (No hay configuraciones de Adobe Campaign disponibles para este componente).

En el siguiente ejemplo se muestra el componente Lista de comprobación de suscripciones (Campaign) que se está visualizando.

![chlimage_1-129](assets/chlimage_1-129.png)

### Campo de texto (Campaign) {#text-field-campaign}

El componente Campo de texto (Campaign) que permite introducir datos de tipo cadena, como nombre, apellidos, dirección, dirección de correo electrónico, etc.

Además de [configuración común a la mayoría de componentes de Adobe Campaign](#settings-common-to-most-components), puede configurar lo siguiente:

* **Restricciones - Restricción** lista desplegable

   Puede seleccionar - **Ninguno, Correo electrónico,** o **Nombre (sin diéresis)** : para añadir la restricción de una dirección de correo electrónico, un nombre o ninguna restricción. Si selecciona el correo electrónico, la respuesta que los usuarios escriban en el campo debe ser una dirección de correo electrónico. Si selecciona un nombre, debe ser un nombre (no se permiten diéresis).

* **Mensaje de restricción**

   Además, puede añadir un mensaje de restricción para que los usuarios sepan cómo dar formato a sus respuestas.

* **Estilo - Anchura**

   Ajuste la anchura del campo tocando o haciendo clic en el **+** y **-** o escribir un número.

En el siguiente ejemplo se muestra el componente Campo de texto (Campaign) que se está visualizando.

![chlimage_1-130](assets/chlimage_1-130.png)
