---
title: Vista previa de un formulario
seo-title: Previewing a form
description: Puede obtener una vista previa de los formularios antes de publicarlos o activarlos para asegurarse de que cumplen las expectativas. Las opciones de vista previa pueden variar según los tipos de formulario admitidos.
seo-description: You can preview your forms before publishing or activating to ensure it meets the expectations. Preview options may vary across the supported form types.
uuid: 9ec359ea-f518-441c-9c3d-e3c1ea07a532
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
feature: Adaptive Forms
exl-id: 130bdc9f-b19e-4b7d-a6ad-ef5097c9cf41
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 93%

---

# Vista previa de un formulario {#previewing-a-form}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

En AEM Forms, puede obtener una vista previa de los formularios y los documentos presentes en el repositorio. La vista previa permite saber exactamente qué aspecto tienen los formularios y cómo se comportan cuando se entregan a los usuarios finales.

Al obtener una vista previa de los formularios, estos se representan en la interfaz interactiva, y el usuario puede rellenarlos con datos. Al obtener una vista previa de los documentos, estos se representan en el modo no interactivo, y el usuario únicamente puede ver el documento. En el caso de los formularios, hay disponible una opción adicional de vista previa personalizada. Con esta opción, puede obtener una vista previa del formulario utilizando datos de un archivo XML. Los datos rellenan algunos o todos los campos del formulario que se está previsualizando.

La siguiente tabla muestra las opciones de vista previa disponibles para los distintos tipos de formularios admitidos:

<table> 
 <tbody>
  <tr>
   <td><strong>Tipo de recurso</strong><br /> </td> 
   <td><strong>Opciones de vista previa disponibles</strong><br /> </td> 
  </tr>
  <tr>
   <td>Documento</td> 
   <td>Vista previa del PDF</td> 
  </tr>
  <tr>
   <td>Formulario PDF</td> 
   <td>Vista previa del PDF y vista previa con datos<br /> </td> 
  </tr>
  <tr>
   <td>formulario adaptable</td> 
   <td>Vista previa del HTML y vista previa del HTML con datos</td> 
  </tr>
  <tr>
   <td>Plantilla de formulario</td> 
   <td>Vista previa del PDF, vista previa del PDF con datos, vista previa del HTML, vista previa del HTML con datos<br /> </td> 
  </tr>
 </tbody>
</table>

## Vista previa de un formulario {#previewing-a-form-1}

1. Seleccione el recurso que desea previsualizar y haga clic en Vista previa ![aem6forms_preview](assets/aem6forms_preview.png) en la barra de herramientas de acciones.

   >[!NOTE]
   >
   >Para seleccionar un recurso, cambie a la vista Lista en la vista Tarjeta predeterminada. Haga clic en ![aem6forms_viewlist](assets/aem6forms_viewlist.png) o ![aem6forms_viewcard](assets/aem6forms_viewcard.png) para cambiar de vista.

1. Al hacer clic en Vista previa, se muestran las posibles opciones de vista previa aplicables al tipo de recurso seleccionado. Haga clic en la opción que desee para representar el recurso seleccionado en una nueva pestaña.

   Las opciones son las siguientes:

   * Vista precia como HTML
   * Vista previa con datos
   * Vista previa como PDF (disponible para plantillas de formulario)

## Vista previa con datos {#preview-with-data}

Al seleccionar **Vista previa con datos**, puede ver el aspecto que tendrá el formulario una vez que se introduzcan datos reales en él. La opción Vista previa con datos permite cargar un XML con datos de usuario de ejemplo. Los datos de usuario de ejemplo se utilizan para rellenar el formulario de vista previa en el formato que elija.

1. Seleccione un recurso, haga clic en Vista previa ![aem6forms_preview](assets/aem6forms_preview.png) y seleccione **Vista previa con datos**.
1. En el cuadro de diálogo Vista previa de formulario, proporcione FormData como el archivo XML. Haga clic en Vista previa para representar el formulario con los datos combinados del XML.
