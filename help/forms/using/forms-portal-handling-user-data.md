---
title: Portal de Forms | Gestión de datos de usuario
seo-title: Forms Portal | Handling user data
description: AEM Forms Portal proporciona componentes que puede utilizar para enumerar formularios adaptables, formularios HTML5 y otros recursos de Forms en la página de AEM Sites. Descubra cómo el portal de Forms almacena datos para formularios en borrador y enviados. Descubra más información sobre cómo acceder a los datos de los formularios borrador y enviados para los usuarios que iniciaron sesión y los anónimos en los almacenes de datos configurados y, si es necesario, elimínelos.
seo-description: AEM Forms portal provides components that you can use to list adaptive forms, HTML5 forms, and other Forms assets on AEM Sites page. Learn how Forms portal stores data for draft and submitted forms. Dig deeper on how to access draft and submitted forms data for logged-in and anonymous users in the configured data stores, and if required, delete it.
uuid: 2ac2b2a9-b603-489a-86b8-a78b697f130d
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 48f841b7-0e7f-4216-9ee8-fb6e843acaf0
role: Admin
exl-id: 05dbb6ee-09fd-44ee-bb8b-a3f3ebb32f5a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 82%

---

# Portal de Forms | Gestión de datos de usuario {#forms-portal-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Forms Portal proporciona componentes que puede utilizar para enumerar formularios adaptables, formularios HTML5 y otros recursos de Forms en la página de AEM Sites. Asimismo, puede configurarla para que muestre los borradores, los formularios adaptables enviados y los formularios HTML5 de un usuario que ha iniciado sesión. Para obtener más información sobre el portal de formularios, consulte [Introducción a la publicación de formularios en un portal](/help/forms/using/introduction-publishing-forms.md).

Cuando un usuario que ha iniciado sesión guarda un formulario adaptable como borrador o lo envía, se muestra en las pestañas Borradores y Envíos del portal de formularios. Los datos de los borradores o los formularios enviados se almacenan en el almacén de datos configurado para la implementación de AEM. Los borradores y los envíos de los usuarios anónimos no se muestran en la página del portal de formularios; sin embargo, los datos se almacenan en el almacén de datos configurado. Para obtener más información, consulte [Configuración de servicios de almacenamiento para borradores y envíos](/help/forms/using/configuring-draft-submission-storage.md).

## Almacenamiento de datos y datos de usuarios {#user-data-and-data-stores}

El portal de formularios almacena los datos de los borradores y los formularios enviados en los siguientes casos:

* La acción de envío configurada en el formulario adaptable es **Acción de envío del portal de formularios**.
* En el caso de las acciones de envío distintas de **Acción de envío del portal de formularios**, se habilita la opción **[!UICONTROL Almacenar datos en el portal de formularios]** en las propiedades de **Envío** del contenedor de formulario adaptable.

El portal de formularios almacena los siguientes datos sobre todos los borradores y los formularios enviados de los usuarios anónimos y los usuarios que han iniciado sesión:

* Los metadatos del formulario, como el nombre del formulario, la ruta, el ID de borrador o envío, la ruta de acceso de los archivos adjuntos y el ID de datos de usuario.
* Los archivos adjuntos del formulario como bytes de datos.
* Los datos del formulario como bytes de datos.

Según la persistencia del almacén de datos configurado, los datos de los borradores y los formulario enviados se almacenan en las siguientes ubicaciones.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Tipo de persistencia</strong></p> </td> 
   <td><p><strong>Almacén de datos</strong></p> </td> 
   <td><p><strong>Ubicación</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Predeterminado</p> </td> 
   <td><p>Repositorio de instancias de autor y publicación de AEM</p> </td> 
   <td><p><code>/content/forms/fp/</code></p> </td> 
  </tr> 
  <tr> 
   <td><p>Remoto</p> </td> 
   <td><p>Repositorio de instancias de AEM remotas y de autor de AEM</p> </td> 
   <td><p><code>/content/forms/fp/</code></p> </td> 
  </tr> 
  <tr> 
   <td><p>Base de datos</p> </td> 
   <td><p>Repositorio de instancias de autor y tablas de bases de datos de AEM</p> </td> 
   <td><code>data</code>, <code>metadata</code> y tablas de bases de datos <code>additionalmetadata</code></td> 
  </tr> 
 </tbody> 
</table>

## Acceder y eliminar datos de usuario {#access-and-delete-user-data}

Puede acceder a los datos de los borradores y los formularios enviados de los usuarios que han iniciado sesión y los usuarios anónimos desde los almacenes de datos configurados y, si es necesario, eliminarlos.

### Instancias de AEM {#aem-instances}

Todos los datos de los borradores y los formularios enviados de las instancias de AEM (de autor, publicación o remotas) de los usuarios que han iniciado sesión y los usuarios anónimos se almacenan en el nodo `/content/forms/fp/` del repositorio de AEM aplicable. Cada vez que un usuario anónimo o con la sesión iniciada guarda un borrador o envía un formulario, se genera un `draft ID` o `submission ID`, un `user data ID` y un `ID` aleatorio para cada archivo adjunto (si procede) que se asocian a su respectivo borrador o envío.

#### Acceder a los datos de usuario {#access-user-data}

Cuando un usuario que ha iniciado sesión guarda un borrador o envía un formulario, se crea un nodo secundario con su ID de usuario. Por ejemplo, los datos de los borradores y los envíos de Sarah Rose, cuyo ID de usuario es `srose`, se almacenan en el nodo `/content/forms/fp/srose/` del repositorio de AEM. En del nodo del ID de usuario, los datos se organizan en una estructura jerárquica.

La siguiente tabla explica cómo se almacenan los datos de todos los borradores de `srose` en el repositorio de AEM.

>[!NOTE]
>
>Una estructura idéntica a `drafts` se replica para los formularios enviados de `srose` en el nodo `/content/forms/fp/srose/submit/`.
>
>Todos los borradores y los envíos de los usuarios `anonymous` se almacenan en el nodo `/content/forms/fp/anonymous/`, el cual organiza los borradores y los envíos de todos los usuarios anónimos en los nodos `draft` y `submit`.

| Nodo | Descripción |
|---|---|
| `/content/forms/fp/srose/drafts` | Los datos de los nodos de contenedor de todos los borradores del usuario |
| `/content/forms/fp/srose/drafts/attachments/` | Organiza todos los archivos adjuntos del usuario en función del ID de borrador |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Contiene los archivos adjuntos del ID seleccionado en formato binario |
| `/content/forms/fp/srose/drafts/metadata/` | Organiza los metadatos de los formularios del usuario en función del ID de borrador |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Contiene los metadatos de los formularios del ID de borrador seleccionado |
| `/content/forms/fp/srose/drafts/data/` | Organiza los datos de los formularios del usuario en función del ID de datos de usuario |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Contiene los datos de formulario del ID de datos de usuario seleccionado en formato binario |

#### Eliminar los datos de usuario {#delete-user-data}

Para eliminar por completo los datos de usuario de los borradores y los envíos de un usuario que ha iniciado sesión de los sistemas de AEM, debe eliminar el nodo `user ID` de un usuario específico del nodo Autor. Debe eliminar manualmente los datos de todas las instancias de AEM aplicables.

Los datos de los borradores y los envíos de todos los usuarios anónimos se almacenan en los nodos comunes `drafts` y `submit` en `/content/forms/fp/anonymous`. No hay ningún método para encontrar datos para un usuario anónimo en particular a menos que se conozca alguna información identificable.En este caso, puede buscar la información que identifica al usuario anónimo en AEM repositorio y eliminar manualmente el nodo que lo contiene de todas las instancias de AEM aplicables para eliminar datos del sistema AEM. Sin embargo, si desea eliminar los datos de todos los usuarios anónimos, puede eliminar el nodo `anonymous` para eliminar los datos de los borradores y los envíos de todos los usuarios anónimos.

### Base de datos {#database}

Cuando AEM está configurado para almacenar datos en una base de datos, los datos de los borradores y los envíos del portal de formularios se almacenan en las siguientes tablas de bases de datos para los usuarios que han iniciado sesión y los usuarios anónimos:

* data
* metadatos
* metadatos adicionales

#### Acceder a los datos de usuario {#access-user-data-1}

Para acceder a los datos de los borradores y los envíos de los usuarios que han iniciado sesión y los usuarios anónimos en las tablas de bases de datos, ejecute el siguiente comando de base de datos. En la consulta, reemplace `logged-in user` por el ID de usuario a cuyos datos desea acceder, o por `anonymous` si se trata de un usuario anónimo.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Eliminar los datos de usuario {#delete-user-data-1}

Para eliminar los datos de los borradores y los envíos de un usuario que ha iniciado sesión desde las tablas de bases de datos, ejecute el siguiente comando de base de datos. En la consulta, reemplace `logged-in user` por el ID de usuario cuyos datos desea eliminar, o por `anonymous` si se trata de un usuario anónimo. Tenga en cuenta que para eliminar los datos de un usuarios anónimo en particular de la base de datos, debe localizarlos utilizando algún tipo de información identificable y eliminarlos de las tablas de bases de datos que contengan la información.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
