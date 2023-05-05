---
title: Integrar la interfaz de usuario de Crear correspondencia con su portal personalizado
seo-title: Integrating Create Correspondence UI with your custom portal
description: Aprenda a integrar la interfaz de usuario de Crear correspondencia con su portal personalizado
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 70%

---

# Integrar la interfaz de usuario de Crear correspondencia con su portal personalizado {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

Este artículo explica cómo puede integrar la solución Crear correspondencia con su entorno.

## Invocación basada en URL {#url-based-invocation}

Una forma de llamar a la aplicación Crear correspondencia desde un portal personalizado es preparar la URL con los siguientes parámetros de solicitud:

* el identificador de la plantilla de carta (con el parámetro cmLetterId ) o el nombre de la plantilla Letter (con el parámetro cmLetterName )

* la dirección URL de los datos XML recuperados de la fuente de datos deseada (con el parámetro cmDataUrl)

Por ejemplo, el portal personalizado prepararía la dirección URL como\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, la cual podría ser el href de un vínculo del portal.\
Si el portal tiene el nombre de la plantilla Carta a mano, la URL podría ser\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>Realizar la llamada de esta forma no es seguro, ya que los parámetros necesarios se pasan como una petición GET, exponiendo lo mismo (claramente visible) en la URL.

>[!NOTE]
>
>Antes de llamar a la aplicación Crear correspondencia, guarde y cargue los datos para llamar a la interfaz de usuario de Crear correspondencia en la URL de datos determinada. Puede hacerlo desde el propio portal personalizado o a través de otro proceso de back-end.

## Invocación basada en datos en línea {#inline-data-based-invocation}

Otra forma (y más segura) de llamar a la aplicación Crear correspondencia podría ser simplemente visitar la URL en `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, mientras se envían los parámetros y datos para llamar a la aplicación Crear correspondencia como una solicitud de POST (ocultándolos al usuario final). Eso significa también que ahora puede pasar los datos XML para la aplicación Crear correspondencia en línea (como parte de la misma solicitud, utilizando el parámetro cmData), lo que no era posible ni lo ideal en el caso del método anterior.

### Parámetros para especificar una carta {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>Nombre</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Cadena</td> 
   <td>El identificador de la instancia de carta.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Cadena</td> 
   <td><p>Identificador de la plantilla de carta. </p> <p>Si existen varias letras CM con el mismo nombre en un servidor, el uso del parámetro cmLetterName en la URL genera el error "Hay varias letras con el nombre". En tal caso, utilice el parámetro cmLetterId en la dirección URL en lugar de cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Cadena</td> 
   <td>El nombre de la plantilla de carta.</td> 
  </tr>
 </tbody>
</table>

El orden de los parámetros de la tabla especifica la preferencia de los parámetros utilizados para cargar la carta.

### Parámetros para especificar la fuente de datos XML {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>Nombre</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>Los datos XML de un archivo de fuente utilizando protocolos básicos como cq, ftp, http o file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Cadena</td> 
   <td>El uso de los datos XML disponibles en la instancia de carta.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booleano</td> 
   <td>Permite reutilizar los datos de prueba adjuntos en un diccionario de datos.</td> 
  </tr>
 </tbody>
</table>

El orden de los parámetros de la tabla especifica la preferencia de los parámetros utilizados para cargar los datos XML.

### Otros parámetros {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>Nombre</strong></td> 
   <td><strong>Tipo</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Booleano</td> 
   <td>True para abrir la carta en el modo de vista previa.<br /> </td> 
  </tr>
  <tr>
   <td>Aleatorio</td> 
   <td>Marca de tiempo</td> 
   <td>Para resolver los problemas de almacenamiento en caché del explorador.</td> 
  </tr>
 </tbody>
</table>

Si utiliza el protocolo http o cq para cmDataURL, la URL de http/cq debe ser accesible de forma anónima.
