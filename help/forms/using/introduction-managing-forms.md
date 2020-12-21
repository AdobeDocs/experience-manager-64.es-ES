---
title: Introducción a la administración de formularios
seo-title: Introducción a la administración de formularios
description: AEM Forms proporciona herramientas para administrar Forms adaptable y recursos relacionados. Este artículo le presenta las funciones clave de administración de formularios y los elementos de la interfaz de usuario.
seo-description: AEM Forms proporciona herramientas para administrar Forms adaptable y recursos relacionados. Este artículo le presenta las funciones clave de administración de formularios y los elementos de la interfaz de usuario.
uuid: 8a9fe83a-e9dc-410e-9bae-eca936c6eb8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager, introduction
discoiquuid: 6f9cb26a-ac7f-4218-827f-9d4d55b859b4
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '1605'
ht-degree: 0%

---


# Introducción a la administración de formularios {#introduction-to-managing-forms}

AEM Forms proporciona una interfaz de usuario simplificada pero potente para crear y administrar formularios, documentos, temáticas, letras, fragmentos de documento, diccionarios de datos y recursos relacionados. Ayuda a administrar el ciclo de vida completo de formularios, documentos y recursos relacionados, desde el escritorio de un desarrollador hasta la oferta\
en un servidor de portal para usuarios finales. Puede utilizar la interfaz de usuario de AEM Forms para:

* Acceso a los componentes de AEM Forms
* Acceso a las configuraciones de AEM Forms

>[!NOTE]
>
>Para obtener información detallada sobre otras herramientas y opciones de AEM, consulte [Uso del Entorno de creación](/help/sites-authoring/home.md).

## Acceso a los componentes de AEM Forms {#access-aem-forms-components}

Junto con las opciones para crear formularios, documentos y recursos relacionados, AEM proporciona opciones para crear sitios, recursos, administrar una instancia de AEM, etc. Puede hacer clic en el logotipo del Experience Manager ![adobeexperience emanager](assets/adobeexperiencemanager.png) para navegar a todas las herramientas disponibles. Junto con los vínculos a las consolas de otros componentes, también contiene vínculos para AEM Forms . Para navegar a AEM Forms, haga clic en el **logotipo del Experience Manager** ![adobeexperience emanager](assets/adobeexperiencemanager.png) > **navegación** ![brújula](assets/compass.png) > **Forms**. Se muestran los vínculos de las siguientes consolas:

* Formularios y documentos
* Temas
* Cartas
* Fragmentos de documento
* Diccionarios de datos

![aem-forms-console](assets/aem-forms-console.png)

### Formularios y documentos  {#forms-documents}

Forms &amp; Documentos proporciona opciones para crear una comunicación interactiva, un formulario adaptable, un fragmento de formulario adaptable y un conjunto de formularios. Solo para AEM Forms en JEE, Forms &amp; Documentos ofrece una opción para importar archivos desde el almacenamiento local y sincronizar recursos de AEM Forms con Workbench.

El botón Crear es el punto de partida del proceso de creación o carga de recursos de AEM Forms. Proporciona opciones para crear:

* **Comunicación** interactiva: Una comunicación interactiva es una correspondencia digital, una declaración o un documento basados en HTML personalizada, interactiva y compatible con el dispositivo. Las comunicaciones interactivas son de naturaleza interactiva y cambian el diseño y el diseño automáticamente en función del dispositivo y la configuración del usuario. Para obtener información detallada, consulte [Información general sobre comunicaciones interactivas](/help/forms/using/interactive-communications-overview.md).

* **Formulario adaptable:** Un formulario adaptable es un formulario interactivo y interactivo. Puede crear un formulario adaptable para adaptarse dinámicamente a las entradas del usuario agregando o eliminando secciones de formulario basadas en la respuesta del usuario, el dispositivo o el entorno de trabajo. El artículo [Introducción a la creación de formularios adaptables](/help/forms/using/introduction-forms-authoring.md) proporciona información detallada sobre los formularios adaptables.

* **Fragmento de formulario adaptable:** aunque cada formulario está diseñado para un propósito específico, hay algunos segmentos comunes en la mayoría de los formularios, como proporcionar detalles personales como nombre y dirección, detalles de familia, detalles de ingresos, etc. Puede crear un recurso individual para estas secciones. Estos segmentos reutilizables independientes se denominan fragmentos de formulario adaptables. Para obtener información detallada, consulte el artículo [fragmentos de formulario adaptables](/help/forms/using/adaptive-form-fragments.md).

* **Conjunto de formularios:** Un conjunto de formularios es una colección de formularios HTML5 agrupados y presentados como un único conjunto de formularios para los usuarios finales. Cuando los usuarios finales inicio rellenar un conjunto de formularios, estos se pasan sin problemas de un formulario a otro. Al final, un usuario puede enviar todos los formularios, como una sola entidad, con un solo clic. Para obtener información detallada, consulte [Conjunto de formularios en AEM Forms](/help/forms/using/formset-in-aem-forms.md).

* **Carpeta:la interfaz de usuario de** AEM Forms utiliza carpetas para organizar los recursos. Admite dos tipos de carpetas:

   * **Carpeta general:** estas carpetas se utilizan para recursos creados en la interfaz de usuario de AEM Forms. Estas carpetas no tienen una estructura de carpetas estricta. Puede cambiar el nombre, crear subcarpetas y almacenar formularios adaptables, comunicaciones interactivas, fragmentos de formulario adaptables, plantillas de formulario (XDP), PDF forms, Documentos y recursos relacionados en estas carpetas.
   * **Forms Workflow:las carpetas de flujo de trabajo de** Forms se crean cuando se migran los procesos de Workbench (archivos de LiveCycle) y se sincronizan con la interfaz de usuario de AEM Forms. No se permite cambiar el nombre, crear una subcarpeta, crear una comunicación interactiva, un fragmento de formulario adaptable o una comunicación interactiva. Tampoco se le permite eliminar una carpeta de versión ni crear y cargar un formulario adaptable, un fragmento de formulario adaptable o una comunicación interactiva en paralelo a la carpeta de la versión.

![carpetas](assets/folders.png)

**A.** Carpeta general  **B.** Forms Workflow

El panel Forms y Documento también ofrece opciones para:

* **Importar archivos desde almacenamiento local:** puede importar PDF forms y Documentos, plantillas de formulario (formularios XFA) y otros recursos (imagen y esquema XML para XSD). Para obtener instrucciones paso a paso, consulte [Importación y exportación de recursos a AEM Forms](/help/forms/using/import-export-forms-templates.md).

* **Sincronizar recursos de AEM Forms con Workbench:** Puede utilizar la opción Archivos de Workbench para sincronizar recursos entre la interfaz de usuario de AEM Forms y Workbench. Garantiza que todos los recursos estén disponibles en la interfaz de usuario de AEM Forms y en la selección de recursos del repositorio crx de Workbench.

### Temas  {#themes}

Un tema contiene detalles de estilo para componentes y paneles. Las temáticas tienen una identidad independiente. Por lo tanto, puede reutilizar un tema en varios formularios adaptables. Puede especificar estilos para un componente o modificar las propiedades CSS de los distintos componentes utilizados en los formularios. Los estilos incluyen propiedades como colores de fondo, colores de estado, transparencia y tamaño. Puede guardar las personalizaciones en un tema y colocarlas en componentes del formulario como un ajuste preestablecido. Al agregar el tema al formulario, el estilo especificado se refleja en los componentes correspondientes del formulario. Con AEM 6.2 Forms, puede crear temáticas y aplicarlas a sus formularios.

Para obtener información sobre cómo crear y utilizar temáticas, consulte [Temáticas en AEM Forms](/help/forms/using/themes.md).

### Cartas  {#letters}

Una carta de formularios AEM es una correspondencia segura, personalizada e interactiva. Puede utilizar AEM Forms para reunir rápidamente letras (también conocidas como correspondencias) de contenido preaprobado y de creación personalizada en un proceso optimizado.

Para obtener información sobre cómo crear y utilizar letras, consulte [Crear carta](/help/forms/using/create-letter.md).

### Fragmentos de documento {#document-fragments}

Los fragmentos de documento son partes reutilizables o componentes de una correspondencia que permite componer letras. Los fragmentos de documento son de tipo texto, lista, condición y fragmento de diseño. Para obtener información sobre la creación y el uso de fragmentos de documento, consulte [creación de fragmentos de documento](/help/forms/using/document-fragments.md).

### Diccionarios de datos {#data-dictionaries}

Normalmente, los usuarios empresariales no necesitan conocer las representaciones de metadatos como XSD (esquema XML) y clases Java. Sin embargo, generalmente requieren acceso a estas estructuras y atributos de datos para generar soluciones. AEM Forms utiliza el diccionario de datos que permite a los usuarios comerciales utilizar información de fuentes de datos back-end sin conocer detalles técnicos sobre sus modelos de datos subyacentes.

Para obtener información sobre la creación y el uso de diccionarios de datos, consulte el artículo sobre creación de [diccionario de datos](/help/forms/using/data-dictionary.md)

## Acceso a las configuraciones de AEM Forms {#accessing-aem-forms-configurations}

AEM panel de herramientas contiene herramientas para varios componentes. Para navegar a las herramientas específicas de AEM Forms, haga clic en el **logotipo del Experience Manager** ![adobeexperience emanager](assets/adobeexperiencemanager.png) > **herramientas** ![martillo](assets/hammer.png) > **Forms**. Se muestran las herramientas para realizar las siguientes funciones:

* **Configurar carpeta vigilada:** un administrador puede configurar una carpeta de red, conocida como carpeta vigilada, de modo que cuando un usuario coloque un archivo (como un archivo PDF) en la carpeta vigilada, se inicie una operación preconfigurada y se manipule el archivo.  <!-- Fix broken link For detailed information, see Create and Configure a watched folder. -->

* **Configurar el servicio sin conexión de la aplicación de Forms:** el servicio sin conexión de la aplicación de AEM Forms almacena en caché las rutas o direcciones URL de los recursos utilizados en un formulario. El almacenamiento en caché de rutas o direcciones URL de los recursos utilizados en un formulario mejora el rendimiento del servidor. Para configurar el componente sin conexión del lado del servidor de la aplicación de AEM Forms, consulte [Trabajo en modo sin conexión](/help/forms/using/work-offline-mode.md).

![aem-forms-tools](assets/aem-forms-tools.png)

* **Configurar generador de PDF:** un administrador puede configurar la configuración de AEM Forms PDF Generator, agregar cuentas de usuario e importar o exportar la configuración al generador de PDF.
* **Publicar recursos de gestión de correspondencia:** AEM Forms permite publicar todas las letras, fragmentos de Documento y diccionarios de datos y dependencias relacionadas de una instancia de autor a la vez. Los recursos publicados incluyen todos los recursos de Correspondence Management y las dependencias relacionadas. Para obtener información detallada, consulte [Publicación y cancelación de la publicación de formularios y documentos](/help/forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **Exportar recursos de gestión de correspondencia:** puede descargar todos los recursos de gestión de correspondencia y las dependencias relacionadas como un paquete desde una instancia de formularios AEM. Para ver los pasos detallados, consulte [Importación y exportación de recursos a AEM Forms](/help/forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Elementos comunes de la interfaz de usuario {#commonelements}

* **Carril izquierdo:** puede hacer clic en el icono del carril izquierdo  ![](assets/railleftpng.png) carrilRailleftpngpara mostrar las capacidades de Línea de tiempo y Referencias de AEM Forms.

   * **Línea de tiempo:** puede agregar y vista comentarios en un recurso que se pueda revisar en la línea de tiempo. Para obtener instrucciones detalladas, consulte [Creación y administración de revisiones para recursos en formularios](/help/forms/using/create-reviews-forms.md).
   * **Referencias:** un recurso de AEM Forms se puede utilizar en varios recursos de AEM Forms. Por ejemplo, un fragmento de documento se puede utilizar en varias letras. Referencias es una lista de recursos (otros formularios o recursos) en los que se utiliza el recurso seleccionado y también la lista de otros recursos que utiliza el recurso seleccionado.

* **Rutas de exploración:** Una ruta de exploración representa el título de la consola o carpeta actual. Puede hacer clic en la opción Ruta de exploración para navegar entre el nivel de carpetas que están en una jerarquía superior.
* **Conmutador de vistas:** puede hacer clic en el  ![](assets/viewlist.png) visor del icono del conmutador de Vistas o en la  ![](assets/viewcard.png) tarjeta de vista para cambiar rápidamente entre la lista y la vista de tarjetas. Para obtener más información sobre los componentes comunes de la interfaz de usuario, consulte [Uso del Entorno de creación](/help/sites-authoring/basic-handling.md).
* **Búsqueda:** La opción de búsqueda  ![](assets/search.png) permite buscar rápidamente y saltar al contenido y las herramientas que necesita. Escriba el nombre del contenido o la capacidad del producto y seleccione entre las sugerencias; por ejemplo, escriba &quot;Documentos&quot; para buscar rápidamente y navegar a la consola de Forms y Documentos o Fragmentos de Documento. Para obtener más información sobre la búsqueda, consulte el artículo AEM 6.2 [search](/help/sites-authoring/search.md)
* **Barra de herramientas** Acciones: Al seleccionar un recurso, la barra de herramientas de acciones aparece encima de la lista de recursos. Contiene todas las herramientas de administración del recurso seleccionado. Puede situar el cursor sobre un icono de herramienta para vista de la información sobre herramientas que describe su funcionalidad

>[!NOTE]
>
>Cuando un usuario realiza una búsqueda en cualquier consola de Forms y Documentos, el carril sólo contiene **Filtros y opciones**. Puede utilizar Filtros y opciones para realizar búsquedas avanzadas.

* **Barra de herramientas** Acciones: Al seleccionar un recurso, la barra de herramientas de acciones aparece encima de la lista de recursos. Contiene todas las herramientas de administración del recurso seleccionado. Puede situar el cursor sobre un icono de herramienta para vista de la información sobre herramientas que describe su funcionalidad

![Barra de herramientas de acciones para un formulario adaptable](assets/action-tool-bar.png)