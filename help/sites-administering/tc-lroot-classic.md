---
title: Creación de una raíz de idioma mediante la IU clásica
seo-title: Creating a Language Root Using the Classic UI
description: Aprenda a crear una raíz de idioma mediante la IU clásica.
seo-description: Learn how to create a language root using the Classic UI.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
feature: Language Copy
exl-id: 316903a8-22cf-45e6-a9f3-ac1d75beddec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 3%

---

# Creación de una raíz de idioma mediante la IU clásica{#creating-a-language-root-using-the-classic-ui}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

El siguiente procedimiento utiliza la IU clásica para crear una raíz de idioma de un sitio. Para obtener más información, consulte [Creación de una raíz de idioma](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. En la consola Sitios web , en el árbol Sitios web , seleccione la página raíz del sitio. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Agregue una nueva página secundaria que represente la versión en idioma del sitio:

   1. Haga clic en Nuevo > Nueva página.
   1. En el cuadro de diálogo, especifique el Título y el Nombre. El nombre debe tener el formato de `<language-code>` o `<language-code>_<country-code>`, por ejemplo en, en_US, en_us, en_GB, en_gb.

      * El código de idioma admitido es un código de dos letras en minúsculas, tal como se define en la norma ISO-639-1
      * El código de país admitido es de dos letras, en minúsculas o mayúsculas, tal como se define en la norma ISO 3166
   1. Seleccione la Plantilla y haga clic en Crear.

   ![newpagefr](assets/newpagefr.png)

1. En la consola Sitios web , en el árbol Sitios web , seleccione la página raíz del sitio.
1. En el menú Herramientas, seleccione Copia de idioma.

   ![toolslanguageCopy](assets/toolslanguagecopy.png)

   El cuadro de diálogo Copia de idioma muestra una matriz de versiones de idiomas y páginas web disponibles. Una x en una columna de idioma significa que la página está disponible en ese idioma.

   ![languageecopydialog](assets/languagecopydialog.png)

1. Para copiar una página existente o un árbol de páginas en una versión de idioma, seleccione la celda de esa página en la columna idioma . Haga clic en la flecha y seleccione el tipo de copia que desea crear.

   En el siguiente ejemplo, la página de equipamiento/gafas de sol/irian se está copiando a la versión en francés.

   ![language ecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Tipo de copia de idioma | Descripción |
   |---|---|
   | auto | Utiliza el comportamiento de las páginas principales |
   | omitir | No crea una copia de esta página y de sus elementos secundarios |
   | `<language>+` (por ejemplo, Francés+) | Copia la página y todos sus elementos secundarios de ese idioma |
   | `<language>` (por ejemplo, francés) | Copia solo la página de ese idioma |

1. Haga clic en Aceptar para cerrar el cuadro de diálogo.
1. En el cuadro de diálogo siguiente, haga clic en Sí para confirmar la copia.
