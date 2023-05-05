---
title: Elementos esenciales de contenido destacado
seo-title: Featured Content Essentials
description: Trabajo con contenido de funciones
seo-description: Working with feature content
uuid: b376828a-1431-4d16-ad6b-b23a3ea62a75
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 781625f1-39a0-4e34-948c-d4eab35dd5c1
exl-id: 4805db0f-18d2-4bbc-a4d6-eaafa7a4c152
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%

---

# Elementos esenciales de contenido destacado {#featured-content-essentials}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página proporciona la información esencial para trabajar con contenido destacado.

A diferencia de fijar una publicación en la parte superior de un foro, esta función permite que el contenido se resalte en cualquier parte dentro del sitio de la comunidad.

## Elementos esenciales para el cliente {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/commons/components/hbs/featuredcontent</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusible</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td> <i>predeterminada</i></td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/commons/components/hbs/featuredcontent/featuredcontent.hbs<br /> /libs/social/commons/components/hbs/featuredtopic/featuredtopic.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/commons/components/hbs/featuredcontent/clientlibs/featuredcontent.css</td> 
  </tr>
  <tr>
   <td><strong> propiedades</strong></td> 
   <td>Consulte <a href="featured.md">Contenido destacado</a></td> 
  </tr>
 </tbody>
</table>

* [Personalizaciones del lado del cliente](client-customize.md)

### Función Biblioteca del archivo {#file-library-function}

Una estructura de sitio de la comunidad que incluye el [Función Contenido destacado](functions.md#featured-content-function), incluye un `featured content` componente.
