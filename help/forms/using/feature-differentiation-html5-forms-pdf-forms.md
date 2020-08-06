---
title: 'Diferenciación de funciones entre formularios HTML5 y PDF forms '
seo-title: 'Diferenciación de funciones entre formularios HTML5 y PDF forms '
description: Función admitida en formularios y PDF forms HTML5
seo-description: Función admitida en formularios y PDF forms HTML5
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 3%

---


# Diferenciación de funciones entre formularios HTML5 y PDF forms {#feature-differentiation-between-html-forms-and-pdf-forms}

La siguiente tabla especifica la compatibilidad con funciones para formularios y PDF forms HTML5:

<table> 
 <tbody>
  <tr>
   <th>Función</th> 
   <th>Formularios HTML5</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>Códigos de barras<br /> </td> 
   <td>No disponible en el nivel de interfaz de usuario. </td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Campo de firma<br /> </td> 
   <td><strong>Las firmas</strong> digitales no son compatibles, pero se agrega un nuevo campo de firma <strong>de</strong> garabatos para las firmas en papel como las firmas. Puede garabatear su firma en el formulario mediante el campo Firma <strong>de</strong> garabatos. La firma se guarda en el formulario como una imagen. Puede guardar la información de geolocalización en el campo Firma <strong>de</strong> garabatos.</td> 
   <td>Campo de firma disponible para firmas <strong>digitales</strong>.</td> 
  </tr>
  <tr>
   <td>Combinación de datos</td> 
   <td>Compatible</td> 
   <td>Compatible</td> 
  </tr>
  <tr>
   <td>Imágenes</td> 
   <td>El esquema de URI de datos se utiliza para mostrar imágenes. Todas las versiones modernas de los navegadores admiten este esquema, pero hay diferencias en la gama de formatos de imagen que admite cada navegador.<br /> </td> 
   <td>Se admiten los formatos .gif, .png, .jpeg, .bmp y .tiff.</td> 
  </tr>
  <tr>
   <td>Paginación<br /> </td> 
   <td><p>Un formulario HTML5 se divide en paneles y cuadros para que tenga un aspecto similar al de los PDF forms. El tamaño de la página se calcula de forma dinámica. Si se elimina o se marca como oculto todo el contenido de una página en un formulario HTML5, la página en blanco se oculta y no se muestra un espacio vacío (espacio en blanco) entre las páginas situadas encima y debajo de la página en blanco.</p> <p>Si la combinación de datos o las secuencias de comandos agregan contenido a una página, la longitud de la página se expande para dar cabida al contenido recién agregado. No se agregan páginas nuevas al formulario para dar cabida al contenido recién agregado. </p> <p><strong>Nota:</strong> Cuando se elimina o se marca como oculta todo el contenido de una página en un formulario HTML5, la página en blanco (espacio en blanco) permanece visible entre la primera y la segunda página, pero no entre otras páginas.</p> </td> 
   <td>La paginación en PDF depende del contenido de datos combinado o del contenido del usuario, y el recuento de páginas aumenta o reduce en función de ello.</td> 
  </tr>
  <tr>
   <td>Encabezados/pies de página </td> 
   <td>Compatible. <br /> <br /> Como los formularios móviles HTML5 no admiten saltos de página, los encabezados y pies de página solo aparecen una vez. Sin embargo, puede configurarlas en la presentación para que aparezcan en varios lugares de la previsualización de formularios móviles.<br /> </td> 
   <td>Compatible.</td> 
  </tr>
  <tr>
   <td>Widgets personalizados</td> 
   <td>Se pueden personalizar utilidades para mejorar la experiencia del usuario en dispositivos móviles.<br /> </td> 
   <td>Todas las utilidades están bloqueadas y no se puede conectar ninguna utilidad personalizada.<br /> </td> 
  </tr>
  <tr>
   <td>API de script XFA</td> 
   <td>Admite las construcciones de secuencias de comandos XFA más utilizadas. Para obtener más información sobre la lista de construcciones admitidas, consulte Compatibilidad con <a href="/help/forms/using/scripting-support.md">secuencias de comandos</a>.</td> 
   <td>Admite todas las construcciones de secuencias de comandos XFA.</td> 
  </tr>
  <tr>
   <td>API de Acrobat Script </td> 
   <td>Los formularios HTML5 admiten las API más utilizadas. Para obtener más información, consulte Compatibilidad con <a href="/help/forms/using/scripting-support.md">secuencias de comandos</a>.</td> 
   <td>Si el archivo PDF se abre dentro de Acrobat o Reader, también admite todas las API de script que proporciona Acrobat.</td> 
  </tr>
  <tr>
   <td>Compatibilidad con idiomas de derecha a izquierda </td> 
   <td>Compatible</td> 
   <td>Compatible</td> 
  </tr>
 </tbody>
</table>

Siga las prácticas recomendadas para habilitar una plantilla de formulario para representaciones HTML5 y asegurarse de que el comportamiento y el aspecto de los formularios HTML5 y del PDF basado en XFA son coherentes. Para obtener una lista detallada de las prácticas recomendadas, consulte [Prácticas recomendadas para diseñar un formulario HTML5.](/help/forms/using/best-practices-for-html5-forms.md)

