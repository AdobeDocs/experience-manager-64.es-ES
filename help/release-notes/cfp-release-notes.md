---
title: Notas de la versión del paquete de correcciones acumulativas de AEM 6.4
description: Notas de la versión específicas de los paquetes de correcciones acumulativas de Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: 1d5d2ef3840a40df7c3b223c7b5835e41553e9f1
workflow-type: tm+mt
source-wordcount: '4693'
ht-degree: 15%

---

# Notas de la versión del paquete de correcciones acumulativas de AEM 6.4 {#aem-cumulative-fix-pack-release-notes}

## Información de la versión {#release-information}

<!-- TBD: Update the SD URL. -->

| Productos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versión | 6.4.8.4 |
| Tipo | Paquete de correcciones acumulativas |
| Fecha | 25 de febrero de 2021 |
| Requisitos previos | [Paquete de servicio 8 de AEM 6.4 (6.4.8.0)](sp-release-notes.md) |
| Descargar URL | [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## Novedades de AEM 6.4.8.4 {#what-s-included-in-aem}

AEM paquete de correcciones acumulativas 6.4.8.4 es una actualización importante que incluye varias correcciones internas y de cliente desde la disponibilidad general de AEM 6.4 Service Pack 8 (6.4.8.0) en marzo de 2020.

AEM 6.4.8.4 es un paquete de correcciones acumulativas (CFP) que depende de AEM 6.4 Service Pack 8. Instale el CFP después de instalar AEM 6.4 Service Pack 8.

Las principales funciones y mejoras introducidas en [!DNL Adobe Experience Manager] 6.4.8.4 son:

* Capacidad para habilitar o deshabilitar el [!DNL Experience Manager Forms] el registro cambia al realizar una conversión PDFG.

* Autenticación basada en certificados X-509 para servicios web basados en SOAP en el modelo de datos de formulario.

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.24.

Para obtener información sobre CFP y otros tipos de versiones, consulte [AEM Actualización de las definiciones del vehículo de lanzamiento](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.4 proporciona correcciones para los siguientes problemas.

### Sites {#sites-6484}

* Después de instalar Experience Manager Service Pack 6.4.8.2, los usuarios no pueden editar los modelos de fragmento de contenido y experimentan el siguiente error:

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* Cuando un usuario hace clic en el botón de cierre de sesión, no se cierra la sesión del administrador de paquetes. (NPR-35161)
* Después de actualizar de Experience Manager 6.4.x a Experience Manager 6.4.8.3, los usuarios no pueden publicar una página mediante Administrar publicación. (CQ-4312511)
* Cuando mueve una página secundaria de modelo a la ubicación original, la configuración cq:liveSyncConfig no se elimina de una página secundaria de Live Copy. (NPR-35900)
* Cuando mueve un modelo que tiene Live Copies hacia adelante y hacia atrás, solo funciona el primer movimiento, entonces falla y no se muestra ningún mensaje de error. (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` causes `OutOfMemoryError` error porque la funcionalidad de etiquetado inteligente crea grandes `/oak:index/lucene` y `/oak:index/ntBaseLucene` índices (NPR-35650).
* Los usuarios no pueden proteger los recursos después de editarlos en [!DNL Adobe InDesign] y recibir error por falta de permisos (NPR-35340).
* Cuando se crea una nueva versión de un recurso existente después de resolver el conflicto de nombres, los metadatos del recurso original se sobrescriben (NPR-35939).
* Los grupos autogenerados en carpetas privadas no se mantienen ni se eliminan al eliminar la carpeta o al actualizar la carpeta con la variable [!UICONTROL Eliminar restricciones de carpetas privadas] conjunto de opciones (NPR-35625).

#### [!DNL Dynamic Media] {#dynamic-media}

* El error intermitente de ImageServer causa una respuesta 403 y el consecuente fallo de algunas funcionalidades de [!DNL Experience Manager]. (CQ-4308565)

### Integraciones {#integrations-6484}

* Cuando se abren las propiedades de una página después de actualizar al Experience Manager 6.4.8.3, los errores de JavaScript empiezan a aparecer en la consola (NPR-35649).

### Forms {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] lanza los paquetes de complementos una semana después de la fecha de lanzamiento programada del paquete de correcciones acumulativas de [!DNL Experience Manager].

**Administración de correspondencia**

* Cuando edita una carta, los módulos con condiciones tardan más en cargarse (NPR-35326).

* Al editar una carta, el contenido y los enlaces de datos no se muestran en la interfaz de usuario (CQ-4312905).

**Servicios de documento**

* No se pueden ensamblar los PDF después de la actualización [!DNL JAVA] a [!DNL JDK1.8.0_261] (NPR-35761, NPR-35848).

**Base JEE**

* Cuando edita una notificación de tarea en [!DNL Forms] flujo de trabajo, no puede guardarlo (CQ-4315055).

**Problemas corregidos en AEMForms-6.4.0-0027**

* (Solo JEE) Se han notificado vulnerabilidades de seguridad críticas (CVE-2021-44228 y CVE-2021-45046) para Apache Log4j2.

Para obtener información sobre las actualizaciones de seguridad, consulte [página boletines de seguridad del Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Revisiones y paquetes de funciones incluidos en los paquetes de correcciones acumulativas anteriores {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM paquete de correcciones acumulativas 6.4.8.3 es una actualización importante que incluye varias correcciones internas y de cliente desde la disponibilidad general de AEM 6.4 Service Pack 8 (6.4.8.0) en marzo de 2020.

AEM 6.4.8.3 es un paquete de correcciones acumulativas (CFP) que depende de AEM 6.4 Service Pack 8. Instale el CFP después de instalar AEM 6.4 Service Pack 8.

En AEM 6.4.8.3, el repositorio integrado (Apache Jackrabbit Oak) se actualiza a la versión 1.8.23.

Para obtener información sobre CFP y otros tipos de versiones, consulte [AEM Actualización de las definiciones del vehículo de lanzamiento](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3 proporciona correcciones para los siguientes problemas.

#### Sitios {#sites-6483}

* Al actualizar el texto de una variación de un fragmento de contenido, se actualiza el contenido del fragmento de contenido maestro en lugar de la variación (NPR-35080).

* Cuando se establece un valor numérico para la propiedad String type label de un componente, se elimina el componente y se utiliza la opción undo para recuperarlo, el tipo de propiedad label cambia automáticamente de String a Long (NPR-34738).

* Cuando se añade un componente Carga de archivo a varios campos, la ruta de la imagen se almacena en el nodo de componente en lugar del nodo de varios campos (NPR-34423).

* En el asistente Mover página , aunque no haya ningún destino seleccionado, el siguiente botón permanece habilitado (NPR-34460).

* Cuando el componente principal incluye la variable `cq:isContainer` , el componente heredado no incluye automáticamente la propiedad (CQ-4308409).

* Cuando se utiliza la minificación de CSS mediante `calc()` , los espacios en blanco alrededor de la función `+` se eliminan los signos (NPR-34991).

* Cuando se inicia una instancia de AEM, la variable `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` y `com.adobe.granite.maintenance.impl.TaskScheduler` los componentes no se muestran en `Active` (NPR-34952).

#### [!DNL Assets] {#assets-6483}

* Al crear una versión de un recurso existente, las actualizaciones de los metadatos del usuario no persisten si se aplica un perfil de metadatos a la carpeta (NPR-34833).
* Al usar [!DNL Adobe Asset Link] con [!DNL Adobe InDesign], los resultados de la búsqueda no contienen carpetas y colecciones, sino que solo contienen recursos (NPR-34700).
* Al arrastrar un recurso a una carpeta para moverlo, la interfaz de usuario también muestra la opción a [!UICONTROL Colocar en Lightbox] y [!UICONTROL Colocar una colección]. Incluso si se cancela la operación de traslado, la interfaz de usuario sigue mostrando las dos últimas opciones (NPR-34525).
* Cuando se abre la interfaz Administrar publicación, la opción de publicación no está disponible y, al seleccionar la opción Cancelar publicación, la página del ámbito está en blanco (CQ-4302509).

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* En la configuración de Ajustes preestablecidos de imagen, cuando la opción [!UICONTROL Habilitar disminución de resolución de crominancia del JPG] no está seleccionado en [!DNL Experience Manager], el cambio no se sincroniza con [!DNL Dynamic Media] (NPR-34284).
* En el [!UICONTROL Editor de ajustes preestablecidos de visor], al editar [!UICONTROL PanoramicImage/PanoramicImage_VR] preestablecido, en la variable `PanoramicView` el componente `PANORAMICVIEW_AUTOROTATE` la etiqueta del modificador no está disponible (CQ-4302043).
* Cancelación de la publicación de un vídeo desde [!DNL Experience Manager] no cancela la publicación del conjunto de vídeos adaptables en el Dynamic Media Classic configurado. (CQ-4304405).

#### Plataforma {#platform-6483}

* La variable `emitUseStrict` El indicador se agrega a la función de procesador Google Closure Compiler (GCC) `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. El indicador suprime la salida del `use strict` instrucción (NPR-34830).
* A `NullPointerException` se devuelve al iniciar tareas de mantenimiento diarias o semanales (NPR-34702).
* La variable [!DNL Apache Sling Health Check] está en desuso. En su lugar, utilice [Detector de patrones](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) para detectar infracciones de contenido (NPR-33929).

#### Integraciones {#integrations-6483}

* La variable [!UICONTROL Crear] aparece en el [!UICONTROL Audiencias] al pasar de una carpeta a la página [!UICONTROL Audiencias] (NPR-35152).

#### Interfaz de usuario {#ui-6483}

* La variable [!UICONTROL Filtros] panel de búsqueda en [!UICONTROL Omnisearch] la interfaz de usuario de también devuelve resultados de ubicaciones que no sean de donde se ejecuta la búsqueda (NPR-34877).
* Al cerrar el [!UICONTROL Filtros] panel activado [!UICONTROL Omnisearch] interfaz de usuario, el carril izquierdo no se restablece a [!UICONTROL Contenido] , lo que impide que se vuelva a abrir la [!UICONTROL Filtros] (NPR-34483).
* A `NullPointerException` al acceder a las propiedades de la página (NPR-34509).

#### Communities {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* Todos los casos de terminología no equitativa en el producto se sustituyen por equivalentes aceptados (NPR-34506).

#### Comercio {#commerce-6483}

* Cuando hay más de 15 productos en una colección, la colección solo muestra los 15 primeros productos (NPR-34494).

#### Forms {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] lanza los paquetes de complementos una semana después de la fecha de lanzamiento programada del paquete de correcciones acumulativas de [!DNL Experience Manager].

>[!NOTE]
>
>[!DNL Experience Manager] El paquete de correcciones acumulativas no incluye correcciones para [!DNL Experience Manager Forms]. Se entregan mediante una [!DNL Forms] paquete de complementos. Además, se lanza un instalador acumulativo que incluye correcciones para [!DNL Experience Manager Forms] en JEE. Para obtener más información, consulte [Instalación del paquete de complementos de AEM Forms](#install-aem-forms-add-on-package) y [Instalación del instalador de AEM Forms JEE](#install-aem-forms-jee-installer).

**Formularios adaptables**

* No se puede editar un formulario adaptable mediante la IU clásica después de aplicar la [!DNL Experience Manager] Paquete de correcciones acumulativas (NPR-35127).

* Los fragmentos tardan más en cargarse de forma adaptable debido a la invalidación de la caché (NPR-34655).

* Accesibilidad: La navegación con pestañas no funciona correctamente para los lectores de pantalla de forma adaptativa (NPR-34550).

**Administración de correspondencia**

* Al migrar los recursos desde ES3, estos incluyen dos condiciones predeterminadas no editables (NPR-34971).

**Base JEE**

* Migrar [!DNL AEM Forms] usuarios de Flash a HTML (CQ-4304075).

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM paquete de correcciones acumulativas 6.4.8.2 es una actualización importante que incluye varias correcciones internas y de cliente desde la disponibilidad general de AEM 6.4 Service Pack 8 (6.4.8.0) en marzo de 2020.

AEM 6.4.8.2 es un paquete de correcciones acumulativas (CFP) que depende de AEM 6.4 Service Pack 8. Instale el CFP después de instalar AEM 6.4 Service Pack 8.

En AEM 6.4.8.2, el repositorio integrado (Apache Jackrabbit Oak) se actualiza a la versión 1.8.22.

Para obtener información sobre CFP y otros tipos de versiones, consulte [AEM Actualización de las definiciones del vehículo de lanzamiento](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2 proporciona correcciones para los siguientes problemas.

#### Sitios {#sites-6482}

* Si la variable `RolloutConfigManagerFactoryImpl` no puede cargar una configuración de lanzamiento, no intenta cargar las configuraciones que faltan. Devuelve las configuraciones en caché (NPR-34091).
* En el componente principal de texto, después de utilizar la opción de edición del HTML de origen, la clase de `em` se elimina (NPR-34080).
* Al actualizar de Experience Manager 6.2 a Experience Manager 6.5, el componente Parsys de las plantillas estáticas no se muestra correctamente. La altura del componente Parsys se establece en 0 y los componentes que contiene no son visibles (NPR-34044).
* La información de la etiqueta no se muestra de los componentes permitidos dentro del Editor de plantillas (NPR-33908).

   ![Falta etiquetas en el contenedor de diseño](assets/33908_missing_labels.png)

* Los usuarios no pueden añadir ni editar componentes al parsys después del cuarto nivel de componentes anidados (NPR-33873).
* Si se cambia el contenido inicial de una plantilla editable y después se publica la plantilla, cualquier página nueva creada con esta plantilla mostrará la fecha de publicación de la plantilla aunque las páginas no se hayan publicado (NPR-33822).
* La variable `cq:acLinks` y `cq:acUUID` propiedades para [!DNL Adobe Campaign] en la copia se eliminan durante la operación de copiar y pegar (NPR-33793).
* En el [!UICONTROL Uso de Live] , solo se muestran 49 resultados. No muestra todo el uso del componente (NPR-33710).
* Una página web con `/` en la URL deja de responder durante la creación. Cuando se añade un componente durante la creación, el uso de la CPU aumenta y el explorador deja de responder (NPR-33625).
* En modo de edición en línea en [!DNL RTE], al arrastrar una imagen, no funciona para el componente Texto (NPR-33579).
* Es posible crear un componente en una página de modelo con el mismo nombre que el nombre de la página. Durante el despliegue, el nombre de este componente cambia por sufijo `_msm_moved`. Sin embargo, el componente se mueve al final del [!UICONTROL Sistema de párrafos] (NPR-33534).
* La promoción de Launch no publica páginas cuando [!UICONTROL incluir subpáginas] no está marcada en la primera raíz de contenido (NPR-33533).
* Redirigir a [!DNL Experience Manager] la página con anclaje no funciona en la instancia Autor como `PageRedirectServlets` coloca la cadena de consulta después de un fragmento de URL o un anclaje (NPR-34287).
* `PageRedirectServlet` anexa `.html` después de la asignación de Sling que provoca errores de vínculo (NPR-34271).
* Puede suspender el [!DNL Live Copy] de una página y la herencia se rompen como se ve en el modo Editor . Sin embargo, en las propiedades de página, el icono que representa la herencia indica incorrectamente que la herencia existe y no se rompe (NPR-34096).
* Problema con la visualización de los componentes permitidos en la página Editar plantilla (CQ-4297295).
* Después de actualizar Chrome y Firefox, los menús emergentes no funcionan como se espera. Al cargar las propiedades de la página, no muestra el panel cuando hay datos en él (CQ-4292995).
* Varias instancias de secuencias de comandos entre sitios en [!DNL Experience Manager Sites] componentes (NPR-33926).
* Las entradas del usuario no están correctamente codificadas para distintos componentes al enviar información al cliente (NPR-33696).
* Una dirección URL que termina con `childrenlist.html` muestra una página HTML en lugar de una respuesta 404. Estas direcciones URL son vulnerables a la ejecución de scripts en sitios múltiples (NPR-33441).

#### Assets {#assets-6482}

* La extracción de texto para los archivos PDF cargados no funciona y la búsqueda de texto completo de algunas palabras en un archivo PDF no consigue ese archivo PDF (NPR-34165).

   >[!NOTE]
   >Para que esta corrección funcione, reinicie la instancia de Adobe Experience Manager después de instalar el Service Pack 6.4.8.2.

* Las barras invertidas se añaden antes que los caracteres especiales en las sugerencias de búsqueda de recursos, que tienen caracteres especiales en su nombre (NPR-33833).

* Los filtros personalizados que se guardan como colecciones inteligentes no se aplican correctamente a los recursos, por lo que los resultados de la búsqueda no son precisos (NPR-33725).

* La línea de tiempo de un recurso dentro de una carpeta reordenada indica que el recurso se movió (NPR-33580).

* Cancelación de la publicación de recursos de forma masiva desde [!DNL Brand Portal] lleva a `Request-URI Too Long` error (NPR-34158).

* En la vista de columna, si el usuario selecciona [!UICONTROL Filtro] después de seleccionar un conjunto de recursos (se anula la selección de los recursos) y, a continuación, selecciona un conjunto diferente de recursos para mover, los recursos seleccionados anteriormente también se mueven a la nueva ubicación (NPR-34018).

* La barra de desplazamiento no está visible en la vista de lista, aunque haya muchos recursos para caber en la página (NPR-34156).

* La variable [!UICONTROL Administrar publicación] la página para los recursos está dañada y las opciones en ella no funcionan (CQ-4302509).

**Dynamic Media**

* La funcionalidad de recorte inteligente falla con un error cuando el perfil de imagen se agrega a una carpeta que tiene varias relaciones de aspecto (por ejemplo, 11) (NPR-34083).

* Cambios en los ajustes preestablecidos de imagen en [!UICONTROL Adobe Experience Manager] no sincronice con Dynamic Media Classic (NPR-34284, CQ-4299713).

* La variable [!UICONTROL PANORAMICVIEW_AUTOROTATE] falta la etiqueta modificadora en el [!UICONTROL Comportamiento] en [!UICONTROL Editor de ajustes preestablecidos de visor] (CQ-4302043).

#### Plataforma {#platform-6482}

* Los valores predeterminados de la variable **[!UICONTROL Tiempo de espera de conexión]** y **[!UICONTROL Tiempo de espera de socket]** no se han especificado los ajustes de configuración del Agente predeterminado (publicación) (NPR-33708).
* El programador de tareas de mantenimiento inicia y detiene las tareas de mantenimiento con demasiada frecuencia de la configurada (NPR-33520).
* No se pueden descargar registros con la herramienta Diagnóstico en una instancia de Experience Manager actualizada (NPR-34419).

#### Integraciones {#integrations-6482}

* El valor de `library_path` no se tiene en cuenta al generar [!DNL Adobe Launch] URL de biblioteca para bibliotecas migradas desde [!DNL Adobe Dynamic Tag Management]. Además, las bibliotecas migradas utilizan un prefijo diferente al [!DNL Adobe Launch] bibliotecas. (NPR-34238).
* Las propiedades heredadas de un servicio en la nube no persisten al actualizar las propiedades de página (NPR-33865).

#### Interfaz de usuario {#ui-6482}

* La visualización del recuento de recursos seleccionados en una página de búsqueda es incorrecta (NPR-33540).

#### Comunidades {#communities-6482}

* Los usuarios existentes de un grupo de comunidad agregados a través de Admin Console se eliminan de la lista de usuarios en cualquier modificación en la consola de grupo de la comunidad (NPR-34312).

#### Forms {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] El paquete de correcciones acumulativas no incluye correcciones para [!DNL Experience Manager Forms]. Se entregan mediante una [!DNL Forms] paquete de complementos. Además, se lanza un instalador acumulativo que incluye correcciones para [!DNL Experience Manager Forms] en JEE. Para obtener más información, consulte [Instalación del paquete de complementos de AEM Forms](#install-aem-forms-add-on-package) y [Instalación del instalador de AEM Forms JEE](#install-aem-forms-jee-installer).

**Formularios adaptables**

* Cuando falta un fragmento de formulario adaptable, el formulario adaptable no se puede procesar (NPR-34303).

* La descripción del contenido de ayuda de los campos de formulario adaptables muestra una etiqueta de HTML de párrafo (NPR-34117).

* Cuando se agrega un contenedor de Forms a una [!DNL Experience Manager Sites] , la página muestra el siguiente mensaje de error y no le permite añadir ningún componente nuevo (NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* Al seleccionar la variable **[!UICONTROL Revalidate en el servidor]** y cargar varios archivos adjuntos, el formulario adaptable no se puede enviar (NPR-33701).

* Al seleccionar la variable **[!UICONTROL Usar idioma de página]** y **[!UICONTROL El formulario abarca toda la anchura de la página]** opciones [!DNL Experience Manager Forms] componente en un [!DNL Experience Manager Sites] , la página no se traduce (NPR-33641).

* Al enviar un formulario adaptable habilitado para análisis incrustado en una [!DNL Experience Manager Sites] , analytics no funciona correctamente (NPR-31359).

* Se han eliminado dependencias en [!DNL Lodash] y [!DNL backbone] bibliotecas (NPR-33458).

* La variable **[!UICONTROL Enviar al extremo REST]** la acción de envío no funciona para un formulario adaptable (NPR-34513).

* Accesibilidad: Cuando se intenta enviar un formulario adaptable sin cargar un archivo adjunto para un campo obligatorio, el enfoque no se desplaza automáticamente al campo adjunto (NPR-34511).

* Las entradas de usuario no están correctamente codificadas para [!DNL Forms] al enviar información al cliente (NPR-33611).

**Flujo de trabajo**

* [!DNL Experience Manager] La operación de purga del flujo de trabajo falla y muestra el siguiente mensaje de error (NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* Al instalar [!DNL Experience Manager] 6.4.8.1. [!UICONTROL Para hacer] la lista de elementos no se muestra como vínculos. El texto de la variable [!UICONTROL Para hacer] los elementos incluyen etiquetas de HTML (NPR-34318).

**BackendIntegration**

* No se puede configurar un modelo de datos de formulario en un AWS alojado [!DNL Experience Manager Forms Linux] entorno (NPR-33617).

**Designer**

* When [!DNL Acrobat DC] está instalado en un [!DNL Experience Manager] El servidor de Forms, la variable **[!UICONTROL Distribuir formulario]** no está disponible en [!DNL Experience Manager Designer] versión 6.x (NPR-34325).

**Document Security**

* No se puede ejecutar la operación de firma con certificados basados en HSM en un archivo PDF después de instalar [!DNL Experience Manager] 6.4.8.0 (NPR-34309).

**Actualización**

* Al actualizar el [!DNL JBoss] versión 7.0.9 para [!DNL Experience Manager Forms] con seguridad de documentos en una [!DNL Linux] entorno, genera un error (CQ-4300546).

Para obtener información sobre las actualizaciones de seguridad, consulte [página boletines de seguridad del Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM paquete de correcciones acumulativas 6.4.8.1 es una actualización importante que incluye varias correcciones internas y de cliente desde la disponibilidad general de AEM 6.4 Service Pack 8 (6.4.8.0) en marzo de 2020.

El paquete de correcciones acumulativas 6.4.8.1 de AEM depende del paquete de servicio 8 de AEM 6.4. Por lo tanto, debe instalar el paquete AEM Cumulative Fix Pack 6.4.8.1 después de instalar AEM 6.4 Service Pack 8.

Algunos de los aspectos destacados de la AEM 6.4.8.1 son:

* No se permite el acceso anónimo al CRXDE Lite para mejorar la seguridad. En su lugar, se dirige a los usuarios a la pantalla de inicio de sesión. Consulte [desarrollo con CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).
* Se ha eliminado la integración de Package Share con Adobe Experience Manager.
* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.21.

Para obtener información sobre CFP y otros tipos de versiones, consulte [AEM Actualización de las definiciones del vehículo de lanzamiento](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1 proporciona correcciones a los siguientes problemas.

#### Sitios {#sites-6481}

* Los usuarios anónimos pueden acceder a las funciones CRX DE Lite (NPR-33522).
* Cuando el nombre de un componente local en una LiveCopy es idéntico al nombre de un componente en el modelo y el componente se despliega desde el modelo, el término _msm_move no se añade al nombre del componente local (NPR-33207).
* Los parámetros añadidos a la solicitud original no se incluyen en la URL de redireccionamiento (NPR-33174).
* Cuando la opción Coral.Select define emptyOption=true o contiene un elemento predeterminado con valor = &quot;&quot;, el archivo dropdownshowhide.js encuentra un error: Error de tipo no capturado: component.getValue no es una función (NPR-33163).
* Cuando un componente incluye otro componente como recurso data-sly, el marcador de posición del componente contenedor principal se reemplaza por el marcador de posición de los componentes internos (NPR-33119).
* Cuando se basa un fragmento de contenido en un esquema y contiene un área de texto obligatoria o un campo de ruta, el fragmento de contenido no se guarda (NPR-33007)
* Cuando crea un componente personalizado con el componente de fragmento de experiencia predeterminado y lo utiliza en páginas de AEM Sites, AEM muestra las referencias (uso) para el componente personalizado (NPR-32852).
* Cuando una página de AEM Sites forma parte de un conjunto de contenido grande con varias Live Copies, la vista previa del historial de versiones de la página no se carga (NPR-32772).
* Cuando promociona un lanzamiento, añade la mezcla &quot;cq:LiveRelationship&quot; a todos los componentes añadidos en el lanzamiento. Afecta a todos los lanzamientos independientemente de si se crea un lanzamiento con o sin seleccionar la opción — Heredar datos en directo de la página de origen — (NPR-32664).
* Cuando se inicia la paginación, el Selector de fragmentos de experiencia no carga todos los elementos (NPR-32605).
* No se puede crear un lanzamiento para una página de AEM Sites. La creación de un lanzamiento produce un error (NPR-32544).
* Administrar publicación no incluye los recursos a los que se hace referencia en el flujo de trabajo de solicitud de activación (NPR-32463).
* Pantalla de comprobación de estado de Dispatcher `Invalid cookie header` mensaje de advertencia en los archivos de registro (NPR-33630).
* La integración de Salesforce es vulnerable al SSRF (NPR-32671).
* XSS reflejado en PreferencesServlet (NPR-33439).

#### Recursos {#assets-6481}

* El recuento de recursos no cambia según el cambio de selección en la vista de lista (NPR-33285).

* El botón siguiente no está habilitado al seleccionar el nodo principal (donde la carpeta secundaria única está visible) y luego seleccionar la carpeta secundaria (NPR-33284).

* La interfaz de usuario táctil no se procesa (con error) para los usuarios que no tienen acceso de lectura en la raíz del repositorio, cuando el modo DMS7 o híbrido está habilitado (NPR-33175).

* Los caracteres GB18030 que aparecen en los nombres de carpetas y recursos cambian a blanco en los archivos zip descargados (NPR-33150).

* La carpeta adicional se crea al recortar inteligente un recurso que se encuentra dentro de una carpeta principal con punto `.` en su nombre (NPR-32755).

* La carga diferida no se activa y no se muestran más de 100 activos al seleccionar para revisar las tareas de la bandeja de entrada de notificaciones (NPR-32749).

* La página de enlace para compartir la colección está dañada debido al cambio en coral-info (NPR-32510).

* El procesamiento de recursos mientras la carga masiva se atasca (CQ-4293916).

* Vulnerabilidad del SSRF en el Experience Manager (NPR-33437).

#### Plataforma {#platform-6481}

* La variable [!DNL Sling] no se llama al filtro si `sling:match` la entrada de mapa se crea en `/etc/maps` (NPR-33308).
* Todos los agentes de vaciado se activan al desactivar una página (NPR-32941).
* Al usar la variable `ScriptProcessor` API para minimizar una biblioteca JavaScript, el archivo de registro muestra un mensaje de error indicando que el código JavaScript no es compatible con el modo estricto. La API no proporciona la opción de habilitar o deshabilitar el modo estricto. (NPR-32746).
* Cuando una consulta SQL se ejecuta durante más tiempo, por ejemplo 7 horas, AEM deja de responder (NPR-33043).

#### Interfaz de usuario {#ui-6481}

* Al buscar o examinar una ruta mediante un cuadro de diálogo de selección, el cuadro de diálogo de selección muestra todo el contenido del nodo JCR seleccionado en lugar de mostrar solo las imágenes (NPR-32712).

#### Proyectos de traducción {#tranlation-6481}

* A `NullPointerException` se ve en los registros de ejecución de un trabajo de traducción (NPR-32220).

#### Integraciones {#integrations-6481}

* Ejecución de scripts en sitios múltiples para JSON (NPR-32745).

#### Comunidades {#communities-6481}

* Los autores, después de crear un grupo nuevo, no se redirigen al grupo [!UICONTROL Grupo de la comunidad] sección [!DNL Internet Explorer] 11 (NPR-33202).
* Se produce un error al acceder a la variable [!UICONTROL Flujo de actividad] (NPR-33152).
* Edición de un [!DNL Communities] y cambiar la imagen en miniatura no actualiza la imagen en miniatura del grupo (NPR-32603).
* Al crear una versión de notificaciones y suscripciones de Contenido generado por el usuario (UGC), se almacena un ID incorrecto de la página de origen (CQ-4289703).
* Problema de scripts en sitios múltiples (NPR-33212).

#### Flujo de trabajo {#workflow-6481}

* Algunos componentes no aparecen en el cuadro de diálogo que aparece cuando un usuario completa un flujo de trabajo que incluye un [!UICONTROL Paso de participante del cuadro de diálogo] (NPR-32989).

* La variable [!UICONTROL Cronología] en el carril izquierdo tarda más tiempo en cargarse de lo esperado (NPR-32850).

#### Forms {#forms-6481}

>[!NOTE]
>
>AEM paquete de correcciones acumulativas no incluye correcciones para AEM Forms. Estas se entregan mediante un paquete independiente de complementos de Forms. Asimismo, se ha publicado un instalador acumulativo que incluye correcciones para AEM Forms en JEE. Para obtener más información, consulte [Instalación del paquete de complementos de AEM Forms](#install-aem-forms-add-on-package) y [Instalación del instalador de AEM Forms JEE](#install-aem-forms-jee-installer).

* Gestión de correspondencia: Cuando un usuario pega contenido desde un [!DNL Word] documento, el fragmento del documento de texto no conserva el formato (NPR-33213).
* Forms adaptable: Una nueva línea a una cadena en un diccionario de formularios adaptables agrega `&#xa;` caracteres del diccionario (NPR-33265).
* Forms adaptable: El usuario no puede guardar un formulario adaptable con más de un archivo adjunto (NPR-33214).
* Forms adaptable: `AddInstance` y `RemoveInstance` los métodos de la clase Instance Manager no agregan número dinámico de instancias para fragmentos de carga diferida en [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptable: Analytics habilitado en un formulario adaptable incrustado en un [!DNL Sites] La página no registra datos para los eventos Submit y Abandon (NPR-31359).
* Forms adaptable: Cuando un usuario pega el contenido desde un [!DNL Word] documento en un formulario adaptable y envíelo, el formulario adaptable enviado incluye caracteres Unicode. Además, la conversión de PDF a PDF/A falla debido a los caracteres Unicode (NPR-33348).
* Integración de back-end: Las solicitudes del modelo de datos de formulario fallan porque el token de actualización caduca debido a un estado inactivo incorrecto (NPR-33168).
* Servicios de documentos: El servicio Convertir PDF no puede convertir documentos PDF a PostScript debido a la falta de jars Gibson para [!DNL WebLogic] en el [!DNL Linux] server (NPR-33515, CQ-4292239).
* Servicios de documentos: Cuando un usuario convierte un archivo de texto en un PDF, los caracteres japoneses no se representan correctamente (NPR-33239).
* XSS almacenado con GuideSOMProviderServlet (NPR-32701).

## Instalar 6.4.8.4 {#install}

### Requisitos de configuración {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Para los clientes con Feature Packs instalados en AEM 6.4. Los Feature Packs opcionales proporcionados por Adobe dependen de la versión de la versión y de los service packs. Si tiene instalado algún paquete de funciones, póngase en contacto con el equipo de atención al cliente de AEM para validar la compatibilidad de esos paquetes de funciones con este paquete de correcciones acumulativas para AEM 6.4.

* AEM 6.4.8.4 requiere AEM 6.4.8.0. Visite [documentación de actualización](../sites-deploying/upgrade.md) para obtener instrucciones detalladas.
* En una implementación con MongoDB y varias instancias, instale AEM 6.4.8.4 en una de las instancias de creación mediante el Administrador de paquetes.
* Antes de instalar el paquete de correcciones acumulativas, asegúrese de tener una instantánea o una copia de seguridad nueva de su instancia de AEM.
* Reinicie la instancia antes de la instalación. Aunque solo es necesario cuando la instancia sigue en modo de actualización (y este es el caso cuando la instancia se actualizó desde una versión anterior), normalmente se recomienda si la instancia se ejecutó durante un período de tiempo más largo.

>[!NOTE]
>
>Adobe no recomienda quitar o desinstalar el paquete AEM 6.4.8.4.

### Instalación del paquete de correcciones acumulativas {#install-cumulative-fix-pack}

Siga estos pasos para instalar el paquete de correcciones acumulativas en una instancia de AEM 6.4.8.0 existente:

1. Haga clic en el vínculo [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) para descargar el paquete.

1. Abra [Administrador de paquetes](http://localhost:4502/crx/packmgr/index.jsp) y haga clic en **[!UICONTROL Cargar paquete]** para cargar el paquete.

1. Seleccione el nombre del paquete y haga clic en **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**El cuadro de diálogo en la IU del administrador de paquetes a veces se cierra de forma precipitada durante la instalación de 6.4.8.4**
>
>Por lo tanto, se recomienda esperar a que los registros de errores se estabilicen antes de acceder a la instancia. El usuario debe esperar a que se produzcan registros específicos relacionados con la desinstalación del paquete de actualización antes de asegurarse de que la instalación se realiza correctamente. Suele suceder en Safari, pero puede suceder de forma intermitente en cualquier navegador.

### Instalación automática {#auto-installation}

Existen dos formas de instalar automáticamente AEM 6.4.8.4 en una instancia en ejecución:

A. Coloque el paquete en .Carpeta */crx-quickstart/install* mientras se ejecuta el servidor. El paquete se instala automáticamente.

B. Utilice la variable [API HTTP del Administrador de paquetes](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - asegúrese de usar `cmd=install&recursive=true` - por lo que el paquete anidado está instalado.

>[!NOTE]
>
>AEM 6.4.8.4 no admite la instalación de Bootstrap.

### Validar la instalación {#validate-install}

1. La página de información del producto (*/system/console/productinfo*) debe mostrar la cadena de versión actualizada de Adobe Experience Manager, versión 6.4.8.4 en la opción de productos instalados.
1. Todos los paquetes OSGI tienen el valor ACTIVO o FRAGMENTO en la consola OSGI (utilice la consola web:/system/console/bundles).
1. El paquete OSGI org.apache.jackrabbit.oak-core está en la versión 1.8.17 o superior (utilice la consola web: /system/console/bundles).

Para determinar la plataforma certificada para ejecutarse con esta versión de AEM Sites y Assets, consulte [Requisitos técnicos](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Al instalar correctamente el paquete, aparece un mensaje informativo que indica que el paquete de contenido se ha instalado correctamente, como **&quot;Paquete de contenido AEM-6.4-Service-Pack-8 instalado correctamente&quot;.**

### Actualización de visores de Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4 contiene una nueva versión de visores de Dynamic Media (5.10.1) que permite comprobar si hay nombres duplicados en la página Ajustes preestablecidos de imagen. Se recomienda a los clientes de Dynamic Media que ejecuten el siguiente comando para que los ajustes preestablecidos de visor estén actualizados.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará los nuevos ajustes preestablecidos de visor en la ubicación /conf.

### Instalación del paquete de complementos para AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] lanza los paquetes de complementos una semana después de la fecha de lanzamiento programada del paquete de correcciones acumulativas de [!DNL Experience Manager].

>[!NOTE]
>
>Omita este paso si no utiliza AEM Forms. Las correcciones en AEM Forms se entregan mediante un paquete de complementos independiente.

1. Asegúrese de que ha instalado el AEM Cumulative Fix Pack.
1. Descargue el paquete de complementos de formularios correspondiente que aparece en [Versiones de AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) para su sistema operativo.
1. Instale el paquete de complementos de formularios como se describe en [Instalación de paquetes de complementos de formularios AEM](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Instalación del instalador de AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Omita este paso si no utiliza AEM Forms en JEE. Las correcciones en el instalador JEE de AEM Forms se entregan mediante un instalador independiente.

Para obtener información sobre la instalación del instalador acumulativo para AEM Forms JEE y la configuración posterior a la implementación, consulte [Instalador de parches JEE de AEM Forms](jee-patch-installer-64.md).

>[!NOTE]
>
>Después de instalar el instalador acumulativo para Experience Manager Forms en JEE, instale el último paquete de complementos de Forms, elimine el paquete de complementos de Forms de la `crx-repository\install` y reinicie el servidor.

### Uber Jar {#uber-jar}

El Uber Jar para AEM 6.4.8.4 está disponible en el [Repositorio de Maven Central](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

Para usar Uber Jar en un proyecto de Maven, consulte el artículo [Cómo usar Uber Jar](../sites-developing/ht-projects-maven.md) e incluya la siguiente dependencia en el elemento POM de su proyecto:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar y otros artefactos relacionados están disponibles en el Repositorio Central de Maven en lugar del repositorio Maven público de Adobe (repo.adobe.com). Se cambia el nombre del archivo UberJar principal a `uber-jar-<version>.jar`. Como resultado, no hay `classifier`, con `apis` como valor, para la variable `dependency` etiqueta.

## Funciones eliminadas u obsoletas {#removed-deprecated-features}

Esta sección enumera las funciones y capacidades que se han eliminado o dejado de utilizar en AEM 6.4.

| Área | Función | Reemplazo | Versión |
|---|---|---|---|
| Recursos | Administrar acción de etiqueta para subrecursos | Sin reemplazo | AEM 6.4.2.0 |
| Integración de Assets y Adobe Creative Cloud | [AEM para uso compartido de la carpeta Creative Cloud](https://docs.adobe.com/content/help/es-ES/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) se introdujo en AEM 6.2 como una forma de proporcionar a los usuarios creativos acceso a los recursos de AEM. Adobe Asset Link, la nueva capacidad de la aplicación Creative Cloud, proporciona experiencia de usuario mejorada y un acceso más eficaz a los recursos de AEM directamente desde Photoshop, InDesign e Illustrator. Adobe no realizará más mejoras en la funcionalidad de uso compartido de carpetas. Aunque la función está incluida en AEM, se recomienda a los clientes utilizar la sustitución. | Adobe Asset Link o aplicación de escritorio. Para obtener más información, consulte el artículo sobre la [integración de AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problemas conocidos {#known-issues}

* Si actualiza desde [!DNL Experience Manager] De 6.4 a [!DNL Experience Manager] 6.5, es posible que algunos paquetes no muestren su estado como `Active`. Instale la última [!DNL Experience Manager] 6.5 Service Pack para resolver el problema.

Para obtener información sobre los problemas conocidos de AEM 6.4.8.0 Service Pack, consulte [Notas de la versión de Service Pack de AEM 6.4.8.0](sp-release-notes.md).

## Paquetes de contenido y paquetes OSGi incluidos {#osgi-bundles-and-content-packages-included}

Los siguientes documentos de texto enumeran los paquetes OSGi y los paquetes de contenido incluidos en AEM 6.4.8.4.

Lista de paquetes OSGi incluidos en AEM 6.4.8.4

[Obtener archivo](assets/6.4.8.4_osgi_bundles.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.8.4

[Obtener archivo](assets/6.4.8.4_content_packages.txt)

## Recursos útiles {#helpful-resources}

* [Notas de la versión de AEM 6.4](../release-notes/release-notes.md)
* [Página de productos AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentación de AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=es)
* Suscripción a las [actualizaciones prioritarias de productos de Adobe](https://www.adobe.com/subscription/priority-product-update.html)

## Sitios restringidos {#restricted-sites-new}

Estos sitios solo están disponibles para los clientes. Si es un cliente y requiere acceso, póngase en contacto con su administrador de cuentas de Adobe.

* [Descarga de productos en licensing.adobe.com](https://licensing.adobe.com/)
* [Póngase en contacto con atención al cliente](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
