---
title: Búsqueda de texto completo de GQL
description: Explore la función de búsqueda de texto completo de GQL en AEM Assets. Utilícelo para buscar recursos basados en metadatos específicos, como título, descripción y nombre del autor.
contentOwner: AG
feature: Buscar,Metadatos
role: User
exl-id: e819501c-4ac3-447f-944c-67adc42e8c61
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 2%

---

# Búsqueda de texto completo de GQL {#gql-full-text-search}

Explore la función de búsqueda de texto completo de GQL en AEM Assets. Utilícelo para buscar recursos basados en metadatos específicos, como título, descripción y nombre del autor.

La función de búsqueda de texto completo de GQL permite buscar recursos en función de metadatos específicos, como título, descripción, autor, etc.

Para buscar un recurso en función de sus metadatos, por ejemplo, title, especifique la palabra clave de metadatos seguida de su valor en el panel de búsqueda. La función de búsqueda de texto completo de GQL solo recuperará aquellos recursos cuyos metadatos coincidan exactamente con el valor correspondiente que haya introducido.

Por ejemplo, para buscar recursos que tengan el título &quot;Target&quot;, siga estos pasos:

## Búsqueda de recursos {#searching-assets}

1. En la barra de herramientas de la interfaz de usuario de Assets, toque o haga clic en el icono **[!UICONTROL Buscar]** para mostrar el cuadro Omnisearch.

   ![](assets/do-not-localize/chlimage_1.png)

1. Con el cursor en el cuadro Omnisearch, pulse Enter.
1. Toque o haga clic en el icono de navegación global para mostrar el panel **[!UICONTROL Filtros]**.
1. En el cuadro Omni Search, especifique el valor &quot;Target&quot;. Para limitar la búsqueda a una carpeta específica, toque o haga clic en el icono Examinar del panel Filtros y seleccione la carpeta. En este caso, la coincidencia solo se busca dentro de la carpeta y en las subcarpetas debajo de ella.

   >[!NOTE]
   >
   >También puede realizar búsquedas de texto completo en una carpeta. En este caso, debe especificar un término de búsqueda de texto completo que no esté vacío.

   ![gql_search](assets/gql_search.png)

1. Pulse **[!UICONTROL Enter]**. La interfaz de usuario de AEM Assets solo muestra los recursos cuyo título coincide exactamente con &quot;Target&quot;.

La función de búsqueda de texto completo de GQL permite buscar recursos en función de lo siguiente:

* Consulta compleja creada mediante la combinación a través de una operación Y, los valores especificados para varios campos de metadatos (propiedades)
* Varios valores para un único campo de metadatos
* Coincidencias de subcadena

La función de búsqueda de texto completo de GQL permite buscar recursos en función de las siguientes propiedades de metadatos. Los nombres de las propiedades (por ejemplo, autor, título, etc.) así como los valores distinguen entre mayúsculas y minúsculas.

>[!NOTE]
>
>La búsqueda de texto completo de GQL solo funciona para predicados de texto completo.

| Propiedad | Formato de búsqueda (valor de faceta) |
|---|---|
| [!UICONTROL Título] | title:John |
| [!UICONTROL Creador] | creador:John |
| [!UICONTROL Colaborador] | colaborador:John |
| [!UICONTROL Ubicación] | ubicación:India |
| [!UICONTROL Descripción] | description: &quot;Imagen de muestra&quot; |
| [!UICONTROL Herramienta Creador] | creatortool: &quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL Propietario del copyright] | copyright:&quot;Adobe Systems&quot; |
| [!UICONTROL Colaborador] | colaborador:John |
| [!UICONTROL Condiciones de uso] | usageterms:&quot;CopyRights Reserved&quot; |
| [!UICONTROL Creado] | creado:YYYY-MM-DDTHH:MM:SS.000+05:30...AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Fecha de caducidad] | caduca:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Tiempo de activación] | en tiempo:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Tiempo de inactividad] | offtime:YYYY-MM-DDTHH:MM:SS.000+05:30..AAAA-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL Intervalo de tiempo]  (caduca dateontime, offtime) | campo de faceta: límite inferior..Upperbound |
| [!UICONTROL Ruta] | /content/dam/&lt;nombre de carpeta> |
| [!UICONTROL Título del PDF] | pdftitle:&quot;Documento de Adobe&quot; |
| [!UICONTROL Asunto] | asunto: &quot;Formación&quot; |
| [!UICONTROL Etiquetas] | etiquetas: &quot;Ubicación Y Viaje&quot; |
| [!UICONTROL Tipo] | tipo: &quot;image\png&quot; |
| [!UICONTROL Anchura de la imagen] | ancho:límite inferior..Upperbound |
| [!UICONTROL Altura de la imagen] | height:lowerbound..Upperbound |
| [!UICONTROL Person] | person:John |

A continuación se muestran algunos ejemplos de formatos de búsqueda para consultas complejas:

* Para mostrar todos los recursos con varios campos de facetas (por ejemplo: title=John Doe y la herramienta de creación = Adobe Photoshop):

tiltle: herramienta de creación &quot;John Doe&quot; : Adobe&amp;ast;

* Para mostrar todos los recursos cuando el valor de facetas no es una sola palabra sino una frase (por ejemplo: title=Scott Reynolds)

title: &quot;Scott Reynolds&quot;

* Para mostrar recursos con varios valores de una sola propiedad (por ejemplo: title=Scott Reynolds o John Doe)

title: &quot;Scott Reynolds&quot; O &quot;John Doe&quot;

* Para mostrar recursos con valores de propiedad que empiecen por una cadena específica (por ejemplo: el título es Scott Reynolds)

title:&quot;Scott&quot;

* Para mostrar los recursos con valores de propiedad que terminan con una cadena específica (por ejemplo: el título es Scott Reynolds)

title:&quot;Reynolds&quot;

* Para mostrar recursos con un valor de propiedad que contenga una cadena específica (por ejemplo: title = Sala de reuniones de Basilea)

title: &quot;Reunión&quot;;

* Para mostrar los recursos que contienen una cadena concreta y tienen un valor de propiedad específico (por ejemplo: buscar Adobe de cadena en recursos con title=John Doe)

&amp;ast;Adobe&amp;ast; title:&quot;John Doe &quot;O título:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>La ruta de acceso, el límite, el tamaño y el orden de las propiedades no se pueden Oed con ninguna otra propiedad.
>
>La palabra clave de una propiedad generada por el usuario es su etiqueta de campo en el editor de propiedades en minúsculas, con espacios eliminados.


>[!NOTE]
>
>Si escribe una consulta JCR para buscar solo subrecursos, los recursos a los que se hace referencia coincidentes también se muestran junto con los subrecursos coincidentes.

La búsqueda de texto completo también admite operadores como -, ^, etc. Para buscar estas letras como literales de cadena, escriba la expresión de búsqueda entre comillas dobles. Por ejemplo, use &quot;Notebook - Beauty&quot; en lugar de Notebook - Beauty.

## Aumento de la búsqueda {#boosting-search}

Puede mejorar la relevancia de las palabras clave para recursos concretos para ayudar a impulsar las búsquedas basadas en palabras clave. En otras palabras, las imágenes para las que promociona palabras clave específicas aparecen en la parte superior de los resultados de búsqueda cuando realiza una búsqueda basada en estas palabras clave.

1. En la interfaz de usuario de Assets, abra la página de propiedades del recurso para el que desea promocionar una palabra clave.
1. Cambie a la pestaña **[!UICONTROL Avanzado]** y toque o haga clic en **[!UICONTROL Agregar]** en **[!UICONTROL Elevar para palabras clave de búsqueda]**.

   ![elevate_for_search](assets/elevate_for_search.png)

1. En el cuadro **[!UICONTROL Buscar promoción]**, especifique una palabra clave para la que desee impulsar la búsqueda de la imagen y, a continuación, toque o haga clic en **[!UICONTROL Agregar]**. Si es necesario, especifique varias palabras clave del mismo modo.

   ![add_search_word](assets/add_search_word.png)

1. Toque o haga clic en **[!UICONTROL Guardar y cerrar]**.
1. Busque la palabra clave mediante el cuadro Omnisearch . El recurso para el que promocionó esta palabra clave aparece entre los principales resultados de búsqueda.
