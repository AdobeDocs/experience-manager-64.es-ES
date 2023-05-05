---
title: Texto de marcador de posición en AEM Forms
seo-title: Placeholder text in AEM Forms
description: El texto de marcador de posición está diseñado para ayudar al usuario con la introducción de datos cuando el control no tiene valor. Puede ser un valor de muestra o una breve descripción del formato esperado.
seo-description: Placeholder text is intended to aid the user with data entry when the control has no value. It could be a sample value or a brief description of the expected format.
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: Adaptive Forms
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 88%

---

# Texto de marcador de posición en AEM Forms {#placeholder-text-in-aem-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El texto de marcador de posición representa una palabra o una frase corta. Está diseñado para ayudar al usuario a introducir los datos cuando el control no tiene valor. Un texto de marcador de posición puede ser un valor de muestra o una breve descripción del formato esperado. El texto de marcador de posición se muestra antes de que el usuario introduzca un valor, y se quita cuando el usuario introduce o selecciona un valor.

>[!NOTE]
>
>Si se especifica, el texto del marcador de posición debe tener un valor que no contenga caracteres de nueva línea.

![Componente de fecha con y sin texto de marcador de posición](assets/dat-picker-place-holder-text.png)

**A.** Componente de fecha con texto de marcador de posición **B.** Componente de fecha sin texto de marcador de posición

AEM Forms admite texto de marcador de posición en los campos Cuadro de contraseña, Selector de fecha, Cuadro numérico y Cuadro de texto.\
Los textos de los marcadores de posición no son compatibles con el widget de fecha HTML5 nativo. Para especificar un texto de marcador de posición:

1. Haga clic con el botón derecho en un componente que admita texto de marcador de posición y haga clic en **Editar**. Aparecerá el cuadro de diálogo Editar componente.

1. Abra la pestaña **Título y texto**.
1. Especifique una palabra o una frase corta en el **Cuadro de texto de marcador de posición**. Haga clic en **Aceptar**.

>[!NOTE]
>
>El texto del marcador de posición no es compatible con Microsoft Internet Explorer 9.
