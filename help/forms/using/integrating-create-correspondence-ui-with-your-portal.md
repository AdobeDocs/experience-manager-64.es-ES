---
title: Integración de la IU Crear correspondencia con su portal personalizado
seo-title: Integrating Create Correspondence UI with your custom portal
description: Aprenda a integrar la interfaz de usuario de creación de correspondencia con su portal personalizado
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 3%

---

# Integración de la IU Crear correspondencia con su portal personalizado {#integrating-create-correspondence-ui-with-your-custom-portal}

## Información general {#overview}

Este artículo detalla cómo puede integrar la solución Crear correspondencia con su entorno.

## Invocación basada en URL {#url-based-invocation}

Una forma de llamar a la aplicación Crear correspondencia desde un portal personalizado es preparar la URL con los siguientes parámetros de solicitud:

* el identificador de la plantilla de carta (con el parámetro cmLetterId ) o el nombre de la plantilla Letter (con el parámetro cmLetterName )

* la dirección URL de los datos XML recuperados del origen de datos deseado (con el parámetro cmDataUrl ).

Por ejemplo, el portal personalizado prepararía la dirección URL como\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, que podría ser el href de un vínculo en el portal.\
Si el portal tiene el nombre de la plantilla Carta a mano, la URL podría ser\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>Llamar a de este modo no es seguro, ya que los parámetros necesarios se pasan como una solicitud de GET, al exponer lo mismo (claramente visible) en la dirección URL.

>[!NOTE]
>
>Antes de llamar a la aplicación Crear correspondencia, guarde y cargue los datos para llamar a la IU Crear correspondencia en la URL de datos determinada. Esto se puede hacer desde el propio portal personalizado o a través de otro proceso de back-end.

## Invocación basada en datos en línea {#inline-data-based-invocation}

Otra forma (y más segura) de llamar a la aplicación Crear correspondencia podría ser simplemente visitar la URL en `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, mientras se envían los parámetros y datos para llamar a la aplicación Crear correspondencia como una solicitud de POST (ocultándolos al usuario final). Esto también significa que ahora puede pasar los datos XML para la aplicación Crear correspondencia en línea (como parte de la misma solicitud, utilizando el parámetro cmData), que no era posible/ideal en el método anterior.

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
   <td>Identificador de la instancia de letra.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Cadena</td> 
   <td><p>Identificador de la plantilla de carta. </p> <p>Si existen varias letras CM con el mismo nombre en un servidor, el uso del parámetro cmLetterName en la URL genera el error "Hay varias letras con el nombre". En tal caso, utilice el parámetro cmLetterId en la dirección URL en lugar de cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Cadena</td> 
   <td>El nombre de la plantilla Carta.</td> 
  </tr>
 </tbody>
</table>

El orden de los parámetros de la tabla especifica la preferencia de los parámetros utilizados para cargar la carta.

### Parámetros para especificar el origen de datos XML {#parameters-for-specifying-the-xml-data-source}

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
   <td>Datos XML de un archivo de origen utilizando protocolos básicos como cq, ftp, http o file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Cadena</td> 
   <td>Uso de datos xml disponibles en la instancia de carta.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booleano</td> 
   <td>Para reutilizar los datos de prueba adjuntos en un diccionario de datos.</td> 
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
   <td>True para abrir la carta en el modo de vista previa<br /> </td> 
  </tr>
  <tr>
   <td>Aleatorio</td> 
   <td>Marca de tiempo</td> 
   <td>Para resolver los problemas de almacenamiento en caché del explorador.</td> 
  </tr>
 </tbody>
</table>

Si utiliza el protocolo http o cq para cmDataURL, la dirección URL de http/cq debe ser accesible de forma anónima.
