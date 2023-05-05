---
title: Personalizar el seguimiento de eventos de formulario
seo-title: Customizing form event tracking
description: Si un usuario pasa más de 60 segundos en un campo, se activará un evento de visita de campo y los detalles del campo se enviarán a Adobe SiteCatalyst.
seo-description: If a user spends more than 60 seconds on a field, a fieldvisit event is triggered and the details of the field are sent to Adobe SiteCatalyst.
uuid: 2f790085-2f1a-45be-9a69-6100c76dcae0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 60d67c6b-5994-42ef-b159-ed6edf5cf9d4
exl-id: e07adddb-e904-4a80-9b1c-8028b12c0e37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 87%

---

# Personalizar el seguimiento de eventos de formulario {#customizing-form-event-tracking}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

De serie, los siguientes eventos se rastrean en un formulario adaptable habilitado para análisis:

<table> 
 <tbody> 
  <tr> 
   <th>Evento</th> 
   <th>Variables disponibles</th> 
  </tr> 
  <tr> 
   <td>procesar</td> 
   <td>formName, formTitle, formInstance, source</td> 
  </tr> 
  <tr> 
   <td>abandon</td> 
   <td>formName, formTitle, formInstance, panelName, panelTitle</td> 
  </tr> 
  <tr> 
   <td>save</td> 
   <td>formName, formTitle, formInstance, panelName, source</td> 
  </tr> 
  <tr> 
   <td>submit</td> 
   <td>formName, formTitle, formInstance, source</td> 
  </tr> 
  <tr> 
   <td>error</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td> 
  </tr> 
  <tr> 
   <td>help</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td> 
  </tr> 
  <tr> 
   <td>fieldVisit</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle<br /> </td> 
  </tr> 
  <tr> 
   <td>panelVisit</td> 
   <td>formName, formTitle, panelName, panelTitle</td> 
  </tr> 
 </tbody> 
</table>

## Personalizar el tiempo de espera del evento de visita de campo {#customizing-the-field-visit-event-timeout}

En la configuración predeterminada de AEM Forms, si un usuario emplea más de 60 segundos en un campo, `fieldvisit` se activará y los detalles del campo se enviarán a Adobe Analytics. Puede personalizar la línea de base de seguimiento de tiempo del campo en Configuración de AEM Forms Analytics en la consola de configuración de AEM (/system/console/configMgr) para aumentar o reducir el límite de tiempo de espera.

## Personalizar los eventos de seguimiento {#customizing-the-tracking-events}

Puede modificar la función `trackEvent` disponible en el archivo `/libs/afanalytics/js/custom.js` para personalizar el seguimiento de eventos. Cuando un evento que se rastrea está en un formulario adaptable, se llama a la función `trackEvent`. La función `trackEvent` acepta dos parámetros: `eventName` y `variableValueMap`.

Puede evaluar el valor de *eventName *y *variableValueMap* argumentos para cambiar el comportamiento de seguimiento de eventos. Por ejemplo, puede elegir enviar la información al servidor de análisis después de que se produzca un determinado número de eventos de error. También puede elegir realizar cualquiera de las siguientes personalizaciones:

* Puede establecer un umbral de tiempo antes de enviar el evento.
* Puede mantener un estado para decidir la acción, por ejemplo, *fieldVisit* inserta un evento ficticio basado en la marca de tiempo del último evento.
* Puede usar la función `pushEvent` para enviar el evento al servidor de Analytics *.*

* Puede optar por no insertar el evento en el servidor de Analytics.

### Muestra {#sample}

En el siguiente ejemplo, establezca el estado de la variable *error* evento de cada *fieldName *se mantiene el atributo*. *El evento se envía al servidor de análisis solo si se vuelve a producir un error.

```
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## Personalizar el evento panelvisit {#customizing-the-panelvisit-event}

En la configuración predeterminada de AEM Forms, después de cada 60 segundos, se comprobará si la ventana que contiene el formulario adaptable está activa. Si la ventana está activa, se activará un evento `panelVisit` en Adobe Analytics. Ayuda a comprobar que el documento o el formulario están activos y a calcular el tiempo empleado en el formulario o documento correspondiente.

>[!NOTE]
>
>El nombre del evento que se utiliza para realizar una actividad y calcular el tiempo empleado es “panelVisit”. Este evento es diferente del de visita del panel enumerado en la tabla anterior.

Puede modificar la función scheduleHeartBeatCheck disponible en el archivo `/libs/afanalytics/js/custom.js` para cambiar o detener este evento enviado a Adobe Analytics a intervalos regulares.
