---
title: Guardar formularios como plantillas
seo-title: Save forms as templates
description: Aprenda a crear plantillas a partir de formularios con datos que se requieren repetidamente.
seo-description: Learn how to create templates from forms with data required repeatedly.
uuid: 090c6271-4061-4adc-a063-9df4953b47ce
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e0df2f85-664a-47b3-a8c5-e986b975d421
exl-id: 355c4810-6e45-41cb-9b60-73225bd53526
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 92%

---

# Guardar formularios como plantillas {#save-forms-as-templates}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

A veces, cuando los usuarios rellenan un formulario, las entradas de algunos campos son las mismas. Para estas instancias, puede rellenar los campos que requieran valores idénticos en cada caso y guardar el formulario o borrador como plantilla. Cada vez que cree una instancia de plantilla, los campos especificados ya se rellenarán con los valores especificados en la plantilla. Le ahorra tiempo y esfuerzo para rellenar el formulario.

Realice los siguientes pasos para crear una plantilla:

1. Abra un formulario y seleccione o rellene los campos que tengan valores casi idénticos cada vez que lo utilice. Puede incluir un archivo adjunto con la plantilla que suele agregar al rellenar el formulario.
1. Pulse el icono **Guardar como plantilla** ![save_as_template](assets/save_as_template.png). Aparecerá un cuadro de diálogo para especificar el nombre de la plantilla.
1. Especifique el nombre de la plantilla y pulse **Guardar**. La plantilla aparecerá en la carpeta de plantillas.

   Si existe una plantilla con el mismo nombre, aparecerá un cuadro de diálogo para confirmar que se sobrescribe la plantilla existente. Para reemplazar la plantilla existente por una nueva, pulse **Continuar** o para guardar la plantilla con un nombre diferente, pulse **Cancelar**.

Ahora, puede abrir la plantilla guardada. Cada vez que se abre una plantilla, se crea un formulario o una tarea nuevos y el formulario muestra los datos guardados y las opciones. Con las plantillas, puede editar los datos precargados, agregar un archivo adjunto, guardar como borrador, enviar la tarea o crear otra plantilla que lo utilice. Las plantillas son específicas de los dispositivos móviles y no se sincronizan con el servidor de Adobe Experience Manager Forms.

También puede eliminar una plantilla si ya no es necesaria. Para eliminar una plantilla, navegue hasta la carpeta de plantillas, pulse los puntos suspensivos y, a continuación, pulse **Eliminar plantilla**.

>[!NOTE]
>
>Una plantilla está disponible de forma local y no se sincroniza con el servidor. Al borrar los datos locales de la aplicación, se eliminará la plantilla.
