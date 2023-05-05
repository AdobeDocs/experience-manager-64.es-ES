---
title: Usar el guardado automático en la aplicación de AEM Forms
seo-title: Using autosave in AEM Forms app
description: Aprenda a utilizar la función de guardado automático en la aplicación de AEM Forms para evitar la pérdida de datos.
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 91%

---

# Usar el guardado automático en la aplicación de AEM Forms {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cuando un usuario introduce datos en la aplicación de Adobe Experience Manager Forms, la función de guardado automático los guarda a intervalos regulares. La función de guardado automático de la aplicación de AEM Forms ayuda a evitar la pérdida de datos si la aplicación se cierra accidentalmente.

La aplicación se puede cerrar accidentalmente en los siguientes casos:

* Si el dispositivo se apaga debido a una batería baja
* Si el usuario cierra la aplicación
* Si se produce un bloqueo inesperado

Puede especificar los intervalos tras los cuales la aplicación guardará los datos introducidos.

>[!NOTE]
>
>Seleccione la frecuencia de guardado automático de forma correcta. Las operaciones frecuentes de guardado automático pueden tener un impacto notable en el rendimiento del dispositivo.

Siga estos pasos para utilizar la función de guardado automático en la aplicación de AEM Forms:

1. Inicie sesión en la aplicación y navegue hasta **[!UICONTROL Configuración > General]**.
1. En la pantalla General, utilice la opción **[!UICONTROL Frecuencia de guardado automático]** para seleccionar los intervalos a los que desea que la aplicación guarde los datos introducidos.
   [ ![Configuración de la frecuencia de guardado automático](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. Cuando reinicie la aplicación e inicie sesión con el mismo usuario, se le pedirá que restaure la tarea con el cuadro de diálogo Recuperar tarea no guardada. Haga clic en **[!UICONTROL Aceptar]** en el cuadro de diálogo Recuperar tarea no guardada para reanudar el trabajo con la tarea guardada. Puede hacer clic en **[!UICONTROL Cancelar]** para eliminar los datos guardados correspondientes al último guardado automático activado y comenzar a trabajar con una tarea nueva.

   Al hacer clic en **[!UICONTROL Aceptar]**, la tarea se restaurará con los datos correspondientes a la última función de guardado automático activada antes de que la aplicación se bloqueara. Incluye los datos del formulario y todos los archivos adjuntos asociados a la tarea.
   [ ![Recuperar una tarea ](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** Un formulario de trabajo en curso **B.** Aplicación cerrada a la fuerza **C.** Aplicación reiniciada con el cuadro de diálogo Recuperar tarea no guardada **D.** Formulario restaurado con datos originales
