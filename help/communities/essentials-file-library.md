---
title: Elementos esenciales de la biblioteca de archivos
seo-title: File Library Essentials
description: Uso de la función de biblioteca de archivos
seo-description: Working with the file library feature
uuid: 0630f13e-97b4-4f93-9dce-07f559287c29
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 9019b967-fff8-4dda-bc5a-fd4a3e14a4ef
exl-id: 0e9d508e-d7dc-478a-99c0-c6885bcdcb81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# Elementos esenciales de la biblioteca de archivos {#file-library-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con la función de biblioteca de archivos.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/filelibrary/components/hbs/filelibrary</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.filelibrary</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/filelibrary.hbs<br /> /libs/social/filelibrary/components/hbs/folder/folder.hbs<br /> /libs/social/filelibrary/components/hbs/folder/item.hbs<br /> /libs/social/filelibrary/components/hbs/document/document.hbs<br /> /libs/social/filelibrary/components/hbs/document/item.hbs<br /> </td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/filelibrary/components/hbs/filelibrary/clientlibs/filelibrary.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="file-library.md">Función de la biblioteca de archivos</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

## Elementos esenciales para el servidor {#essentials-for-server-side}

* [API de biblioteca de archivos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/api/package-summary.html)

* [Puntos finales de la biblioteca de archivos](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/filelibrary/client/endpoints/package-summary.html)

* [Personalizaciones del lado del servidor](server-customize.md)

### Función Biblioteca del archivo {#file-library-function}

Una estructura de sitio de la comunidad que incluye el [Función Biblioteca de archivos](functions.md#file-library-function), incluye un `file library` componente.

### Acceso a los comentarios anunciados para bibliotecas de archivos (UGC) {#accessing-comments-posted-for-file-libraries-ugc}

UGC debe moderarse utilizando uno de los métodos estándar de moderación.\
Consulte [Moderación del contenido generado por el usuario](moderate-ugc.md).

A partir del AEM 6.1 Comunidades, se utilizará un [tienda común](working-with-srp.md) para UGC incluye acceso programático a UGC independientemente de la opción de almacenamiento elegida (como ASRP, MSRP o JSRP).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

Consulte:

* [Información general del proveedor de recursos de almacenamiento](srp.md) : introducción y descripción general del uso del repositorio
* [Elementos esenciales de SRP y UGC](srp-and-ugc.md) - Métodos y ejemplos de utilidad SRP
* [Acceso a UGC con SRP](accessing-ugc-with-srp.md) - Directrices de codificación
* [Refactorización de SocialUtils](socialutils.md) : asignación de métodos de utilidad obsoletos a métodos de utilidad SRP actuales
