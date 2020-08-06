---
title: Creación de una raíz de idioma con la IU clásica
seo-title: Creación de una raíz de idioma con la IU clásica
description: Aprenda a crear una raíz de idioma mediante la IU clásica.
seo-description: Aprenda a crear una raíz de idioma mediante la IU clásica.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---


# Creación de una raíz de idioma con la IU clásica{#creating-a-language-root-using-the-classic-ui}

El siguiente procedimiento utiliza la IU clásica para crear una raíz de idioma de un sitio. Para obtener más información, consulte [Creación de una raíz](/help/sites-administering/tc-prep.md#creating-a-language-root)de idioma.

1. En la consola Sitios web, en el árbol Sitios web, seleccione la página raíz del sitio. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Añada una nueva página secundaria que represente la versión de idioma del sitio:

   1. Haga clic en Nuevo > Nueva página.
   1. En el cuadro de diálogo, especifique el Título y el Nombre. El nombre debe tener el formato `<language-code>` o, `<language-code>_<country-code>`por ejemplo, en, en_US, en_us, en_GB, en_gb.

      * El código de idioma admitido es el código de dos letras en minúscula definido por ISO-639-1
      * El código de país admitido es el código de dos letras en minúsculas o en mayúsculas, tal como se define en la norma ISO 3166
   1. Seleccione la plantilla y haga clic en Crear.

   ![newpagefr](assets/newpagefr.png)

1. En la consola Sitios web, en el árbol Sitios web, seleccione la página raíz del sitio.
1. En el menú Herramientas, seleccione Copiar idioma.

   ![toolslanguage ecopy](assets/toolslanguagecopy.png)

   El cuadro de diálogo Copiar idioma muestra una matriz de las versiones de idioma y las páginas web disponibles. Una x en una columna de idioma significa que la página está disponible en ese idioma.

   ![languageEopydialog](assets/languagecopydialog.png)

1. Para copiar una página o un árbol de páginas existentes en una versión de idioma, seleccione la celda de esa página en la columna de idioma. Haga clic en la flecha y seleccione el tipo de copia que desea crear.

   En el siguiente ejemplo, la página de equipamiento/gafas de sol/iria se copia a la versión en francés.

   ![language ecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Tipo de copia del idioma | Descripción |
   |---|---|
   | auto | Utiliza el comportamiento de las páginas principales |
   | ignore | No crea una copia de esta página y de sus elementos secundarios |
   | `<language>+` (p. ej. francés+) | Copia la página y todos sus elementos secundarios de ese idioma |
   | `<language>` (por ejemplo, francés) | Copia solo la página de ese idioma |

1. Haga clic en Aceptar para cerrar el cuadro de diálogo.
1. En el cuadro de diálogo siguiente, haga clic en Sí para confirmar la copia.

