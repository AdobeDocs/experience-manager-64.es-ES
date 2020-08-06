---
title: Integración de la interfaz de usuario Crear correspondencia con su portal personalizado
seo-title: Integración de la interfaz de usuario Crear correspondencia con su portal personalizado
description: Aprenda a integrar la interfaz de usuario de creación de correspondencia con su portal personalizado
seo-description: Aprenda a integrar la interfaz de usuario de creación de correspondencia con su portal personalizado
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 3%

---


# Integración de la interfaz de usuario Crear correspondencia con su portal personalizado {#integrating-create-correspondence-ui-with-your-custom-portal}

## Información general {#overview}

Este artículo detalla cómo puede integrar la solución Crear correspondencia con su entorno.

## Invocación basada en URL {#url-based-invocation}

Una forma de llamar a la aplicación Crear correspondencia desde un portal personalizado es preparar la dirección URL con los siguientes parámetros de solicitud:

* el identificador de la plantilla de carta (con el parámetro cmLetterId) o el nombre de la plantilla Letter (con el parámetro cmLetterName)

* la dirección URL de los datos XML recuperados del origen de datos deseado (mediante el parámetro cmDataUrl).

Por ejemplo: el portal personalizado prepararía la dirección URL como\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, que puede ser el href de un vínculo en el portal.\
Si el portal tiene el nombre de plantilla Carta a mano, la dirección URL podría ser\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>La llamada de este modo no es segura, ya que los parámetros necesarios se pasan como una solicitud de GET, al exponer los mismos (claramente visibles) en la dirección URL.

>[!NOTE]
>
>Antes de llamar a la aplicación Crear correspondencia, guarde y cargue los datos para llamar a la interfaz de usuario Crear correspondencia en la dirección URL de datos determinada. Esto puede realizarse desde el propio portal personalizado o a través de otro proceso de back-end.

## Invocación basada en datos en línea {#inline-data-based-invocation}

Otra forma (y más segura) de llamar a la aplicación Crear correspondencia podría ser simplemente visitar la URL en `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, mientras se envían los parámetros y datos para llamar a la aplicación Crear correspondencia como una solicitud de POST (ocultándolos al usuario final). Esto también significa que ahora puede pasar los datos XML para la aplicación Crear correspondencia en línea (como parte de la misma solicitud, utilizando el parámetro cmData), lo que no era posible/ideal en el método anterior.

### Parámetros para especificar la letra {#parameters-for-specifying-letter}

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
   <td>Identificador de la instancia de carta.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Cadena</td> 
   <td><p>Identificador de la plantilla de letras. </p> <p>Si existen varias letras CM con el mismo nombre en un servidor, el uso del parámetro cmLetterName en la URL genera un error "Existen varias letras con el nombre". En ese caso, utilice el parámetro cmLetterId en la dirección URL en lugar de cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Cadena</td> 
   <td>El nombre de la plantilla Carta.</td> 
  </tr>
 </tbody>
</table>

El orden de los parámetros de la tabla especifica la preferencia de los parámetros utilizados para cargar la letra.

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
   <td>Uso de datos XML disponibles en la instancia de carta.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booleano</td> 
   <td>Para reutilizar los datos de prueba adjuntos en el diccionario de datos.</td> 
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
   <td>True para abrir la letra en el modo de previsualización<br /> </td> 
  </tr>
  <tr>
   <td>Aleatorio</td> 
   <td>Marca de hora</td> 
   <td>Para resolver los problemas de almacenamiento en caché del explorador.</td> 
  </tr>
 </tbody>
</table>

Si utiliza el protocolo http o cq para cmDataURL, la dirección URL de http/cq debe ser accesible de forma anónima.
