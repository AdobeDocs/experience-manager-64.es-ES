---
title: Preparación de recursos para su traducción
description: Cree carpetas raíz de idioma para prepararse para la traducción de recursos multilingües.
contentOwner: AG
feature: Projects,Translation
role: User,Admin
exl-id: cc6c4f9e-8e22-4622-8b24-230ae258351c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 9%

---

# Preparación de recursos para su traducción {#preparing-assets-for-translation}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Recursos multilingües significa recursos con binarios, metadatos y etiquetas en varios idiomas. Por lo general, los binarios, los metadatos y las etiquetas de los recursos existen en un idioma, y luego se traducen a otros idiomas para su uso en proyectos multilingües.

En Adobe Experience Manager Assets, los recursos multilingües se incluyen en las carpetas, donde cada carpeta contiene los recursos en un idioma diferente.

Cada carpeta de idioma se denomina copia de idioma. La carpeta raíz de una copia de idioma, conocida como raíz de idioma, identifica el idioma del contenido en la copia de idioma. Por ejemplo, */content/dam/it* es la raíz de idioma italiano para la copia en idioma italiano. Las copias de idioma deben utilizar un [raíz de idioma configurada correctamente](preparing-assets-for-translation.md#creating-a-language-root) para que el idioma correcto se dirija cuando se realicen traducciones de recursos de origen.

La copia de idioma para la que se agregaron recursos originalmente es el idioma principal. El idioma principal es la fuente que se traduce a otros idiomas.

La jerarquía de carpetas de ejemplo incluye varias raíces de idioma:

```java
/content
    /- dam
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Siga estos pasos para preparar los recursos para la traducción:

1. Cree la raíz de idioma de la principal del idioma. Por ejemplo, la raíz de idioma de la copia en inglés en la jerarquía de carpetas de ejemplo es `/content/dam/en`. Asegúrese de que la raíz del idioma esté configurada correctamente según la información de [Creación de una raíz de idioma](preparing-assets-for-translation.md#creating-a-language-root).

1. Añada recursos al idioma principal.
1. Cree la raíz de idioma de cada idioma de destino para el que necesite una copia de idioma.

## Creación de una raíz de idioma {#creating-a-language-root}

Para crear la raíz del idioma, cree una carpeta y utilice un código de idioma ISO como valor de la propiedad Name . Después de crear la raíz del idioma, puede crear una copia del idioma en cualquier nivel dentro de la raíz del idioma.

Por ejemplo, la página raíz de la copia en idioma italiano de la jerarquía de ejemplo tiene `it` como la propiedad Name. La propiedad Name se utiliza como nombre del nodo de recursos en el repositorio y, por lo tanto, determina la ruta de los recursos. (`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. En la consola de Assets, pulse o haga clic en **[!UICONTROL Crear]** y seleccione **[!UICONTROL Carpeta]** en el menú.

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. En el campo Nombre , escriba el código de país con el formato de `<language-code>`.

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. Haga clic o pulse **[!UICONTROL Crear]**. La raíz del idioma se crea en la consola Recursos.

## Visualización de raíces de idioma {#viewing-language-roots}

La IU táctil proporciona un panel Referencias que muestra una lista de las raíces de idioma que se han creado en [!DNL Experience Manager] Recursos.

1. En la consola Assets, seleccione el idioma principal para el que desea crear copias de idioma.
1. Toque o haga clic en el icono de navegación global y elija **[!UICONTROL Referencias]** para abrir el panel Referencia.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. En el panel Referencias, toque o haga clic en **[!UICONTROL Copias de idioma]**. El panel Textos en idiomas muestra las copias de idioma de los recursos.

   ![chlimage_1-123](assets/chlimage_1-123.png)
