---
title: Envío asincrónico de formularios adaptables
seo-title: Asynchronous submission of adaptive forms
description: Aprenda a configurar el envío asincrónico en formularios adaptables.
seo-description: Learn to configure asynchronous submission for adaptive forms.
uuid: 3b8aeac8-cb38-4a2b-8375-556b2736d58b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 6e4e3af5-4260-4f38-9b29-0818e92bc182
feature: Adaptive Forms
exl-id: 1ca492e9-9832-4e5d-8020-2690ac4f5505
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 87%

---

# Envío asincrónico de formularios adaptables {#asynchronous-submission-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Tradicionalmente, los formularios web se configuran para enviarse sincrónicamente. Cuando los usuarios envían un formulario, se les redirige a una página de reconocimiento o, en caso de error en el envío, a una página de error. Sin embargo, las experiencias web modernas, como las aplicaciones de una sola página, están ganando popularidad en los casos en los que la página web permanece estática mientras la interacción cliente-servidor se produce en segundo plano. Ahora puede proporcionar esta experiencia con formularios adaptables mediante la configuración del envío asincrónico. En este caso, un formulario adaptable se comporta como una aplicación de una sola página, ya que el formulario no se vuelve a cargar o su URL no cambia cuando los datos del formulario enviados se validan en el servidor.

Siga leyendo para obtener más información sobre el envío asincrónico en formularios adaptables.

## Configuración del envío asincrónico {#configure}

Para configurar el envío asincrónico en un formulario adaptable haga lo siguiente:

1. En el modo Autor del formulario adaptable, seleccione el objeto Contenedor de formularios y pulse ![cmppr1](assets/cmppr1.png) para abrir sus propiedades.
1. En la sección de propiedades de **[!UICONTROL Envío]**, habilite **[!UICONTROL Usar envío asincrónico]**.
1. En la sección **[!UICONTROL Al enviar]**, seleccione una de las siguientes opciones para realizarla cuando se envíe correctamente del formulario.

   * **[!UICONTROL Redirigir a URL]**: redirige a la URL o página especificada después de enviar el formulario. Puede especificar una URL o examinar y elegir la ruta a una página en el campo **[!UICONTROL URL/ruta de redireccionamiento]**.
   * **[!UICONTROL Mostrar mensaje]**: muestra un mensaje sobre el envío del formulario. Puede escribir un mensaje en el campo de texto debajo de la opción Mostrar mensaje. El campo de texto admite el formato de texto enriquecido.

1. Pulse ![check-button1](assets/check-button1.png) para guardar las propiedades.

## Funcionamiento del envío asincrónico {#how-asynchronous-submission-works}

AEM Forms proporciona controladores de éxito y de error predeterminados para los envíos de formularios. Los controladores son funciones del lado del cliente que se ejecutan en función de la respuesta del servidor. Cuando se envía un formulario, los datos se transmiten al servidor para su validación, lo que devuelve una respuesta al cliente con información sobre el evento de éxito o error del envío. La información se pasa en forma de parámetros al controlador correspondiente para ejecutar la función.

Además, los autores y desarrolladores de formularios pueden escribir reglas a nivel de formulario para invalidar los controladores predeterminados. Para obtener más información, consulte [Invalidar los controladores predeterminados mediante reglas](#custom).

Primero vamos a revisar la respuesta del servidor para los eventos de éxito y de error.

### Respuesta del servidor para el evento de éxito del envío {#server-response-for-submission-success-event}

La estructura de la respuesta del servidor para el evento de éxito del envío es la siguiente:

```
{
  contentType : "<xmlschema or jsonschema>", 
  data : "<dataXML or dataJson>" , 
  thankYouOption : <page/message>, 
  thankYouContent : "<thank you page url/thank you message>"
}
```

La respuesta del servidor en caso de que el envío del formulario se realice correctamente incluye:

* el tipo de formato de datos del formulario: XML o JSON;
* los datos del formulario en formato XML o JSON;
* la opción seleccionada para redireccionar a una página o mostrar un mensaje como se ha configurado en el formulario;
* la URL de la página o contenido del mensaje, según la configuración del formulario.

El controlador de éxito lee la respuesta del servidor y, en consecuencia, redirige a la URL de la página configurada o muestra un mensaje.

### Respuesta del servidor para el evento de error del envío {#server-response-for-submission-error-event}

La estructura de la respuesta del servidor para el evento de error del envío es la siguiente:

```
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

La respuesta del servidor en caso de que se produzca un error durante el envío del formulario incluye:

* el motivo del error, el error de CAPTCHA o la validación del lado del servidor;
* la lista de objetos de error, que incluye la expresión SOM del campo en el que se ha producido un error al efectuar la validación y el mensaje de error correspondiente.

El controlador de error lee la respuesta del servidor y, en consecuencia, muestra el mensaje de error en el formulario.

## Invalidar los controladores predeterminados mediante reglas {#custom}

Los desarrolladores y autores de formularios pueden escribir reglas a nivel de formulario en el editor de código para invalidar los controladores predeterminados. La respuesta del servidor para eventos de éxito y error se expone a nivel de formulario, al cual los desarrolladores pueden acceder usando `$event.data` en las reglas.

Realice los siguientes pasos para escribir reglas en el editor de código para controlar los eventos de éxito y error.

1. Abra el formulario adaptable en el modo Autor, seleccione cualquier objeto de formulario y pulse ![edit-rules1](assets/edit-rules1.png) para abrir el editor de reglas.
1. Seleccione **[!UICONTROL Formulario]** en el árbol Objetos de formulario y pulse **[!UICONTROL Crear]**.
1. Seleccione **[!UICONTROL Editor de código]** de la lista desplegable de modo de selección.
1. En el editor de código, pulse **[!UICONTROL Editar código]**. Pulse **[!UICONTROL Editar]** en el cuadro de diálogo de confirmación.
1. Elija **[!UICONTROL Envío correcto]** o **[!UICONTROL Error en el envío]** de la lista desplegable **[!UICONTROL Evento]**.
1. Escriba una regla para el evento seleccionado y pulse **[!UICONTROL Listo]** para guardar la regla.
