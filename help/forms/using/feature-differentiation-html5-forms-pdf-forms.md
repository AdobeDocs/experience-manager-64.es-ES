---
title: 'Diferenciación de funciones entre formularios HTML5 y PDF '
seo-title: 'Diferenciación de funciones entre formularios HTML5 y PDF '
description: Función admitida en formularios HTML5 y formularios PDF
seo-description: Función admitida en formularios HTML5 y formularios PDF
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
translation-type: tm+mt
source-git-commit: 49b7cff2c1583ee1eb929434f27c1989558e197f

---


# Diferenciación de funciones entre formularios HTML5 y PDF {#feature-differentiation-between-html-forms-and-pdf-forms}

La siguiente tabla especifica la compatibilidad con funciones de los formularios HTML5 y los formularios PDF:

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
   <td>Admitido</td> 
  </tr>
  <tr>
   <td>Campo de firma<br /> </td> 
   <td><strong>Las firmas</strong> digitales no son compatibles, pero se agrega un nuevo campo de firma <strong>de</strong> garabatos para las firmas en papel como las firmas. Puede garabatear su firma en el formulario mediante el campo Firma <strong>de</strong> garabatos. La firma se guarda en el formulario como una imagen. Puede guardar la información de geolocalización en el campo Firma <strong>de</strong> garabatear.</td> 
   <td>Campo de firma disponible para firmas <strong>digitales</strong>.</td> 
  </tr>
  <tr>
   <td>Combinación de datos</td> 
   <td>Admitido</td> 
   <td>Admitido</td> 
  </tr>
  <tr>
   <td>Imágenes</td> 
   <td>El esquema de URI de datos se utiliza para mostrar imágenes. Todas las versiones modernas de los navegadores admiten este esquema, pero hay diferencias en la gama de formatos de imagen que admite cada navegador.<br /> </td> 
   <td>Se admiten los formatos .gif, .png, .jpeg, .bmp y .tiff.</td> 
  </tr>
  <tr>
   <td>Paginación<br /> </td> 
   <td><p>Un formulario HTML5 se divide en paneles y cuadros para que tenga un aspecto similar al de los formularios PDF. El tamaño de la página se calcula de forma dinámica. Si se elimina o se marca como oculto todo el contenido de una página en un formulario HTML5, la página en blanco se oculta y no se muestra un espacio vacío (espacio en blanco) entre las páginas situadas encima y debajo de la página en blanco.</p> <p>Si la combinación de datos o las secuencias de comandos agregan contenido a una página, la longitud de la página se expande para dar cabida al contenido recién agregado. No se agregan páginas nuevas al formulario para dar cabida al contenido recién agregado. </p> <p><strong></strong> Nota: Cuando se elimina o se marca como oculta todo el contenido de una página en un formulario HTML5, la página en blanco (espacio en blanco) permanece visible entre la primera y la segunda página, pero no entre otras páginas.</p> </td> 
   <td>La paginación en PDF depende del contenido de datos combinado o del contenido del usuario, y el recuento de páginas aumenta o reduce en función de ello.</td> 
  </tr>
  <tr>
   <td>Encabezados/pies de página </td> 
   <td>Compatible. <br /> <br /> Como los formularios móviles HTML5 no admiten saltos de página, los encabezados y pies de página solo aparecen una vez. Sin embargo, puede configurarlas en la presentación para que aparezcan en varios lugares de la vista previa de formularios móviles.<br /> </td> 
   <td>Compatible.</td> 
  </tr>
  <tr>
   <td>Widgets personalizados</td> 
   <td>Se pueden personalizar utilidades para mejorar la experiencia del usuario en dispositivos móviles.<br /> </td> 
   <td>Todas las utilidades están bloqueadas y no se puede conectar ninguna utilidad personalizada.<br /> </td> 
  </tr>
  <tr>
   <td>API de script XFA</td> 
   <td>Admite las construcciones de secuencias de comandos XFA más utilizadas. Para obtener más información sobre las construcciones admitidas, consulte Compatibilidad con <a href="/help/forms/using/scripting-support.md">secuencias de comandos</a>.</td> 
   <td>Admite todas las construcciones de secuencias de comandos XFA.</td> 
  </tr>
  <tr>
   <td>API de secuencias de comandos de Acrobat </td> 
   <td>Los formularios HTML5 admiten las API más utilizadas. Para obtener más información, consulte Compatibilidad con <a href="/help/forms/using/scripting-support.md">secuencias de comandos</a>.</td> 
   <td>Si el archivo PDF se abre en Acrobat o Reader, también admite todas las API de secuencias de comandos que proporciona Acrobat.</td> 
  </tr>
  <tr>
   <td>Compatibilidad con idiomas de derecha a izquierda </td> 
   <td>Admitido</td> 
   <td>Admitido</td> 
  </tr>
 </tbody>
</table>

Siga las prácticas recomendadas para habilitar una plantilla de formulario para representaciones HTML5 y asegurarse de que el comportamiento y el aspecto de los formularios HTML5 y del PDF basado en XFA son coherentes. Para obtener una lista detallada de prácticas recomendadas, consulte [Prácticas recomendadas para diseñar un formulario HTML5.](/help/forms/using/best-practices-for-html5-forms.md)

**[Comuníquese con la asistencia técnica](https://www.adobe.com/account/sign-in.supportportal.html)**
