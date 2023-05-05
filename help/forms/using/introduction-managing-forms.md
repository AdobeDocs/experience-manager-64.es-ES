---
title: Introducción a la administración de formularios
seo-title: Introduction to managing forms
description: AEM Forms proporciona herramientas para administrar los formularios adaptables y los recursos relacionados. Este artículo presenta las principales funciones y elementos de la interfaz de usuario de Forms Management.
seo-description: AEM Forms provides tools to manage Adaptive Forms and related assets. This article introduces you to the key forms management capabilities and user interface elements.
uuid: 8a9fe83a-e9dc-410e-9bae-eca936c6eb8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager, introduction
discoiquuid: 6f9cb26a-ac7f-4218-827f-9d4d55b859b4
exl-id: 08686ad6-85cc-4de5-86d8-05d55acec418
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 70%

---

# Introducción a la administración de formularios {#introduction-to-managing-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Forms proporciona una interfaz de usuario simplificada pero potente para crear y administrar formularios, documentos, temas, cartas, fragmentos de documento, diccionarios de datos y recursos relacionados. Ayuda a administrar el ciclo de vida completo de formularios, documentos y recursos relacionados, desde el escritorio de un desarrollador hasta la oferta\
en un servidor de portal para usuarios finales. Puede utilizar la interfaz de usuario de AEM Forms para:

* Acceso a los componentes de AEM Forms
* Acceso a las configuraciones de AEM Forms

>[!NOTE]
>
>Para obtener información detallada sobre otras herramientas y opciones de AEM, consulte [Uso del entorno de creación](/help/sites-authoring/home.md).

## Acceso a los componentes de AEM Forms {#access-aem-forms-components}

Junto con las opciones para crear formularios, documentos y recursos relacionados, AEM proporciona opciones para crear sitios, recursos, administrar una instancia de AEM, etc. Puede hacer clic en el logotipo ![adobe_experience_manager](assets/adobeexperiencemanager.png) de Experience Manager para desplazarse a todas las herramientas disponibles. Junto con vínculos a las consolas de otros componentes, también contiene vínculos para AEM Forms . Para ir a AEM Forms, haga clic en el botón **Logotipo del Experience Manager** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **navegación** ![brújula](assets/compass.png) > **Forms**. Se muestran los vínculos de las siguientes consolas:

* Formularios y documentos
* Temas
* Cartas
* Fragmentos de documento
* Diccionarios de datos

![aem-forms-console](assets/aem-forms-console.png)

### Formularios y documentos  {#forms-documents}

Formularios y documentos proporciona opciones para crear una comunicación interactiva, un formulario adaptable, un fragmento de formulario adaptable y un conjunto de formularios. Solo para AEM Forms en JEE, Forms &amp; Documents proporciona una opción para importar archivos del almacenamiento local y sincronizar recursos de AEM Forms con Workbench.

El botón crear es el punto de partida del proceso de creación o carga de recursos de AEM Forms. Proporciona opciones para crear:

* Una **comunicación interactiva**: una comunicación interactiva es una correspondencia, un extracto o un documento digital personalizado, interactivo y compatible con el dispositivo, basado en HTML. Las comunicaciones interactivas son interactivas en su naturaleza y cambian su diseño automáticamente según el dispositivo y la configuración del usuario. Para obtener información detallada, consulte [Información general sobre comunicaciones interactivas](/help/forms/using/interactive-communications-overview.md).

* Un **formulario adaptable:** un formulario adaptable es un formulario atractivo e interactivo. Puede crear un formulario adaptable para adaptarse de forma dinámica a las entradas del usuario añadiendo o eliminando secciones de formulario basadas en la respuesta del usuario, el dispositivo o el entorno de trabajo. El artículo [Introducción a la creación de formularios adaptables](/help/forms/using/introduction-forms-authoring.md) proporciona información detallada sobre los formularios adaptables.

* Un **fragmento de formulario adaptable**: aunque cada formulario está diseñado para un propósito específico, la mayoría de ellos contienen algunos segmentos comunes, por ejemplo, para proporcionar datos personales como el nombre y la dirección, datos familiares, datos de ingresos, etc. Puede crear un recurso individual para estas secciones. Estos segmentos reutilizables e independientes se denominan fragmentos de formulario adaptable. Para obtener información detallada, consulte el artículo [fragmentos de formulario adaptables](/help/forms/using/adaptive-form-fragments.md).

* Un **conjunto de formularios:** un conjunto de formularios es una colección de formularios HTML5 agrupados que se presentan como un único conjunto de formularios a los usuarios finales. Cuando los usuarios finales empiezan a rellenar un conjunto de formularios, pueden desplazarse sin problemas de un formulario a otro. Al final, un usuario puede enviar todos los formularios como una sola entidad con un solo clic. Para obtener información detallada, consulte [Conjunto de formularios en AEM Forms](/help/forms/using/formset-in-aem-forms.md).

* **Carpeta:** La interfaz de usuario de AEM Forms utiliza carpetas para organizar los recursos. Admite dos tipos de carpetas:

   * **Carpeta general:** Estas carpetas se utilizan para los recursos creados en la interfaz de usuario de AEM Forms. Este tipo de carpetas no tiene una estructura de carpetas estricta. Puede cambiar el nombre de las carpetas, crear subcarpetas y utilizarlas para almacenar formularios adaptables, comunicaciones interactivas, fragmentos de formulario adaptable, plantillas de formulario (XDP), formularios PDF, documentos y recursos relacionados.
   * **carpeta del Forms Workflow:** Las carpetas de flujo de trabajo de Forms se crean cuando los procesos de Workbench (archivos de LiveCycle) se migran y sincronizan con la interfaz de usuario de AEM Forms. No se puede cambiar el nombre de estas carpetas, ni crear subcarpetas, comunicaciones interactivas o fragmentos de formulario adaptable en ellas. Tampoco se permite eliminar una carpeta de versiones, crear y cargar un formulario adaptable, un fragmento de formulario adaptable o una comunicación interactiva en paralelo a la carpeta de versiones.

![carpetas](assets/folders.png)

**A.** Carpeta general **B.** carpeta de Forms Workflow

El panel Formularios y documentos también proporciona opciones para lo siguiente:

* **Importar archivos desde el almacenamiento local:** puede importar formularios y documentos PDF, plantillas de formulario (formularios XFA) y otros recursos (imagen y esquema XML para XSD). Para obtener instrucciones paso a paso, consulte [Importación y exportación de recursos a AEM Forms](/help/forms/using/import-export-forms-templates.md).

* **Sincronizar recursos de AEM Forms con Workbench:** puede utilizar la opción Archivos de Workbench para sincronizar recursos entre la interfaz de usuario de AEM Forms y Workbench. Garantiza que todos los recursos estén disponibles en la interfaz de usuario de AEM Forms y en la selección de recursos del repositorio crx de Workbench.

### Temas  {#themes}

Un tema contiene los detalles del estilo de los componentes y los paneles. Los temas tienen una identidad independiente. Eso significa que puede reutilizar un tema en varios formularios adaptables. Puede especificar estilos para un componente o modificar las propiedades CSS de varios componentes utilizados en los formularios. Los estilos contienen propiedades como los colores de fondo, los colores de estado, la transparencia y el tamaño. Puede guardar las personalizaciones en un tema y portarlas en componentes del formulario como ajustes preestablecidos. Al agregar el tema al formulario, el estilo especificado se refleja en los componentes correspondientes de ese formulario. Con AEM 6.2 Forms, puede crear temas y aplicarlos a sus formularios.

Para obtener información sobre cómo crear y usar los temas, consulte [Temas de AEM Forms](/help/forms/using/themes.md).

### Cartas  {#letters}

Una carta de AEM forms es una correspondencia segura, personalizada e interactiva. Puede utilizar AEM Forms para ensamblar rápidamente letras (también conocidas como correspondencias) de contenido preaprobado y creado de forma personalizada en un proceso optimizado.

Para obtener información sobre la creación y el uso de las cartas, consulte [Crear carta](/help/forms/using/create-letter.md).

### Fragmentos de documento {#document-fragments}

Los fragmentos de documento son elementos reutilizables o componentes de una correspondencia que se utilizan para componer cartas. Los fragmentos del documento son de tipo texto, lista, condición y fragmento de diseño. Para obtener información sobre la creación y el uso de fragmentos de documento, consulte [Creación de fragmentos de documento](/help/forms/using/document-fragments.md).

### Diccionarios de datos {#data-dictionaries}

Normalmente, los usuarios empresariales no necesitan conocer las representaciones de metadatos, como las clases XSD (esquema XML) y Java. Sin embargo, por lo general, requieren acceso a estas estructuras y atributos de datos para crear soluciones. AEM Forms utiliza el diccionario de datos para permitir que los usuarios empresariales utilicen información de fuentes de datos back-end sin conocer detalles técnicos sobre sus modelos de datos subyacentes.

Para obtener información sobre cómo crear y usar diccionarios de datos, consulte el artículo Creación del [diccionario de datos](/help/forms/using/data-dictionary.md).

## Acceso a las configuraciones de AEM Forms {#accessing-aem-forms-configurations}

El panel Herramientas AEM contiene herramientas para varios componentes. Para ir a las herramientas específicas de AEM Forms, haga clic en el botón **Logotipo del Experience Manager** ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > **herramientas** ![martillo](assets/hammer.png) > **Forms**. Se muestran herramientas para realizar las siguientes funciones:

* **Configurar carpeta inspeccionada:** un administrador puede configurar una carpeta de red, conocida como carpeta inspeccionada, de forma que cuando un usuario coloque un archivo (por ejemplo, un archivo PDF) en dicha carpeta, se inicie una operación preconfigurada y se manipule el archivo. <!-- Fix broken link For detailed information, see Create and Configure a watched folder. -->

* **Configurar el servicio sin conexión de la aplicación Forms:** El servicio sin conexión de aplicaciones de AEM Forms almacena en caché las rutas o direcciones URL de los recursos utilizados en un formulario. El almacenamiento en caché de rutas o direcciones URL de los recursos utilizados en un formulario mejora el rendimiento del lado del servidor. Para configurar el componente sin conexión del lado del servidor de la aplicación de AEM Forms, consulte [Trabajar en modo sin conexión](/help/forms/using/work-offline-mode.md).

![aem-forms-tools](assets/aem-forms-tools.png)

* **Configure el Generador de PDF:** Un administrador puede configurar el Generador de PDF de AEM Forms, agregar cuentas de usuario e importar o exportar la configuración al Generador de PDF.
* **Publicar recursos de gestión de correspondencia:** AEM Forms permite publicar todas las letras, fragmentos de documento, diccionarios de datos y dependencias relacionadas de una instancia de autor a la vez. Los recursos publicados incluyen todos los recursos de Administración de correspondencia y las dependencias relacionadas. Para obtener información detallada, consulte [Publicación y cancelación de la publicación de formularios y documentos](/help/forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **Exportar activos de gestión de correspondencia:** Puede descargar todos los recursos de Gestión de correspondencia y las dependencias relacionadas como un paquete desde una instancia de formularios AEM. Para ver los pasos detallados, consulte [Importación y exportación de recursos a AEM Forms](/help/forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Elementos comunes de la interfaz de usuario {#commonelements}

* **Carril izquierdo:** Puede hacer clic en el icono del carril izquierdo ![ferrovileftpng](assets/railleftpng.png) para mostrar las funciones de Línea de tiempo y Referencias de AEM Forms.

   * **Cronología:** puede agregar y ver los comentarios de un recurso que esté disponible para su revisión en la cronología. Para obtener instrucciones detalladas, consulte [Creación y administración de revisiones para recursos de formularios](/help/forms/using/create-reviews-forms.md).
   * **Referencias:** Un recurso de AEM Forms se puede usar en varios recursos de AEM Forms. Por ejemplo, un fragmento de documento se puede utilizar en varias cartas. Referencias es una lista de los recursos (otros formularios o recursos) en los que se utiliza el recurso seleccionado, y también la lista de otros recursos que utiliza ese recurso.

* **Rutas de exploración:** una ruta de exploración representa el título de la consola o carpeta actual. Puede hacer clic en la opción Ruta de exploración para desplazarse por el nivel de las carpetas superiores de la jerarquía.
* **Cambiar vista:** puede hacer clic en los iconos del conmutador de vista ![Ver vista](assets/viewlist.png) o ![Ver tarjeta](assets/viewcard.png) para cambiar rápidamente entre la vista de lista y la vista de tarjeta. Para obtener más información sobre los componentes comunes de la interfaz de usuario, consulte [Uso del entorno de creación](/help/sites-authoring/basic-handling.md).
* **Buscar:** La opción Búsqueda ![Búsqueda](assets/search.png) permite buscar y saltar rápidamente al contenido y las herramientas que necesita. Escriba el nombre del contenido o la capacidad del producto y selecciónelo entre las sugerencias; por ejemplo, escriba &quot;Documentos&quot; para buscar rápidamente y desplazarse hasta Formularios y documentos o la consola Fragmentos de documento. Para obtener más información sobre la búsqueda, consulte el artículo [Búsqueda](/help/sites-authoring/search.md) de AEM 6.2.
* **Barra de herramientas Acciones**: al seleccionar un recurso, aparece la barra de herramientas Acciones encima de la lista de recursos. Contiene todas las herramientas de administración del recurso seleccionado. Puede situar el ratón sobre un icono de herramienta para ver la información sobre herramientas que describe su funcionalidad

>[!NOTE]
>
>Cuando un usuario realiza una búsqueda en cualquier consola de Formularios y documentos, el carril contiene únicamente **Filtros y opciones**. Puede usar Filtros y opciones para realizar búsquedas avanzadas.

* **Barra de herramientas Acciones**: al seleccionar un recurso, aparece la barra de herramientas Acciones encima de la lista de recursos. Contiene todas las herramientas de administración del recurso seleccionado. Puede situar el ratón sobre un icono de herramienta para ver la información sobre herramientas que describe su funcionalidad

![Barra de herramientas Acciones en un formulario adaptable](assets/action-tool-bar.png)
