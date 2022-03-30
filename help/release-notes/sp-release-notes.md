---
title: Notas de la versión de Service Pack de AEM 6.4
seo-title: AEM 6.4 Service Pack Release Notes
description: Notas de la versión específicas de los Service Packs de Adobe Experience Manager 6.4.
seo-description: Release notes specific to Adobe Experience Manager 6.4 Service Packs.
uuid: 49a710a8-7cd5-47de-9a96-7af7f3c00dfc
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
discoiquuid: 93067308-e275-490f-8d78-ae79e046059c
exl-id: d0da9390-2167-47ee-82fd-8c81d8d68a3e
source-git-commit: 1537055fd88cbc3b01e4df7855a99f993f2052e4
workflow-type: tm+mt
source-wordcount: '21547'
ht-degree: 26%

---

# Notas de la versión de Service Pack de AEM 6.4 {#aem-service-pack-release-notes}

## Información de la versión {#release-information}

| Productos | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Versión | 6.4.8.0 |
| Tipo | Versión de Service Pack |
| Fecha | 5 de marzo de 2020 |
| Descargar URL | AEM 6.4.8.0 en [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/servicepack/aem-service-pkg-6.4.8.zip) |

## Novedades de AEM 6.4.8.0 {#what-s-included-in-aem}

AEM 6.4.8.0 es una actualización importante que incluye nuevas funciones, mejoras clave solicitadas por los clientes y rendimiento, estabilidad y mejoras de seguridad, publicada desde que se publicó de forma general AEM 6.4 en **Abril de 2018.**

También es acumulativo, lo que significa que 6.4.8.0 incluye todos los paquetes de servicio AEM 6.4 publicados antes de él.

Algunos aspectos destacados de esta versión del Service Pack son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.20.

* La funcionalidad de ajuste de palabras es compatible con los sitios web japoneses en WCM-RTE.

* Los sitios web japoneses admiten el procesamiento de salto de línea y salto de línea.

* Se agregó compatibilidad para utilizar el método BUNSETSU para romper las frases y líneas en japonés en las posiciones adecuadas.

* La interfaz de usuario de CCR para la gestión de correspondencia ahora admite valores decimales para la configuración regional en alemán.

* La integración del modelo de datos de formulario mediante el servicio web SOAP ahora admite grupos de opciones o atributos en elementos.

* AEM Assets ahora se configura con Brand Portal mediante [!DNL Adobe I/O].

* Se ha actualizado la versión de jQuery incluida en ContextHub a 3.2.1.

## Lista de cambios {#list-of-changes}

### Sites {#sites}

* Cuando una dirección URL de una página de AEM Sites contiene dos puntos o un símbolo de porcentaje, el explorador subyacente deja de responder y los ciclos de CPU muestran un pico (NPR-32368, NPR-31917).
* Cuando se abre una página de AEM Sites para editarla y se copia un componente, la acción de pegado sigue no disponible para algunos marcadores de posición (NPR-32328).
* El flujo de trabajo de solicitud de activación no incluye los recursos a los que se hace referencia (NPR-32304).
* Cuando se crea un modelo, si el número de registros es mayor de 80, solo se muestran los 80 primeros registros. Modelo muestra líneas en blanco para el resto de los registros (NPR-32058).
* Los usuarios pueden guardar un fragmento de contenido sin proporcionar información en los campos obligatorios (NPR-31988).
* La navegación automática no funciona para la ruta configurada en un componente de fragmento de experiencia principal (NPR-31921).
* Cuando se cambia el tipo de celda de una tabla en el Editor de texto enriquecido (RTE), se produce el siguiente error:
   `Error: No common ancestor found, cannot continue` (NPR-31916).
* Cuando el contenido se mueve dentro de la misma carpeta, la opción de mover página se desactiva (NPR-31841).
* Se agregó compatibilidad para dividir las frases en japonés mediante el método BUNSETSU y las líneas de salto en la posición adecuada (NPR-31836).
* Cuando edita un hipervínculo en el Editor de texto enriquecido (RTE), la ruta recién seleccionada no se guarda (NPR-31659).
* Cuando se elimina un componente multicampo y se deshace la eliminación, el componente se restaura, pero los datos no se restauran (NPR-31617).

### Assets {#assets}

* Se crea una carpeta sin nombre en Dynamic Media Classic al mover un recurso de una carpeta a otra en Experience Manager con la configuración de Dynamic Media Classic (NPR-32440).

* La página de detalles de los recursos de los archivos PDF no muestra botones de acción en el Experience Manager que se ejecuta en el modo Dynamic Media Scene7 (NPR-32316).

* Las representaciones de recursos y vídeo no se pueden eliminar (NPR-32213).

* El icono de calendario para la activación programada no se muestra en la columna Estado (en la IU clásica de la lista de recursos DAM) para los recursos cuya activación está programada para una fecha y hora posteriores (NPR-32198).

* La relación de los recursos se sobrescribe cuando los recursos están relacionados con más de un recurso que utiliza Otro (NPR-32196).

* El botón Guardar no importa el conjunto remoto cuando el usuario no ha realizado ningún cambio en el Editor de conjuntos en el cliente de Dynamic Media (NPR-32178).

* La ingesta de recursos de PSD causa un pico de CPU y una instancia de autor de Experience Manager no adaptable (NPR-32165).

* Excepción por falta de memoria observada cuando se carga un archivo ZIP grande en el DAM de Experience Manager (NPR-32155).

* Las direcciones URL del historial de versiones se muestran en el campo Referencias por de la página de propiedades de los recursos (NPR-31889).

* La cancelación de la publicación desde Brand Portal, en la página Administrar publicación, falla en las subcarpetas de una carpeta publicada (NPR-31835).

* Las codificaciones de vídeo de Dynamic Media no se cargan cuando la configuración de Scene7 Cloud se coloca en una carpeta privada `/conf` en lugar de `/conf/global` (NPR-31779).

* La imagen no se ve en la cronología después de agregar anotaciones, en el Experience Manager que se ejecuta en el modo de ejecución de Dynamic Media Scene7 (NPR-31754).

* El archivo ZIP descargado de DAM no se puede abrir con WinZip (NPR-31745).

### Integraciones {#integrations-6480}

* La variable **Empresa** y **Informes** Los menús desplegables del grupo se ocultan una vez **Fuente de informes** está seleccionada al configurar Adobe Analytics en Experience Manager cloud services (NPR-31729).

* Las propiedades de Adobe Campaign no se limpian cuando se realiza la copia de idioma de un boletín vinculado a un Adobe Campaign, mientras que la limpieza se produce cuando se copia o pega un boletín vinculado a un Adobe Campaign (NPR-32540).

* ReportSuitesServlet es vulnerable a SSRF (NPR-32161).

### Sling {#sling-6480}

* El sombreado no determinista de la observación de recursos no está funcionando (CQ-4286466).

### Proyectos {#projects-6480}

* El botón Crear no es visible para el usuario aunque este tenga permiso para crear un proyecto en la subcarpeta (NPR-31831).

* La funcionalidad para cambiar entre la vista de tarjeta, la vista de lista y la vista de calendario no funciona después de seleccionar la vista de calendario en Proyectos (NPR-31829).

### Traducción {#translation-6480}

* La creación de proyectos de traducción para varios idiomas genera el proyecto solo para algunos de los idiomas, y en el registro se observa un error (la resolución de recursos ya está cerrada) (NPR-32212).

### WCM-MSM {#wcm-msm-6480}

* Los problemas de permisos producen la visualización de errores al mover páginas dentro de un modelo (NPR-32610).

### WCM: editor de páginas {#wcm-page-editor-6480}

* El explorador deja de responder al intentar agregar un componente a una página con un formato de URL específico (NPR-32368, NPR-31917).

### WCM: IU de administrador {#wcm-admin-ui-6480}

* La gestión de publicación no incluye recursos a los que se hace referencia en el flujo de trabajo de solicitud de activación (NPR-32304).

### Communities {#communities}

* No se puede actualizar la imagen en miniatura del grupo para grupos (NPR-32603).

### Brand Portal {#brand-portal}

* Cancelar la publicación del esquema de metadatos en AEM Assets rellena un mensaje de error aunque el esquema se elimine en el servidor (CQ-4286871).

### Interfaz de usuario de base {#foundations-ui-6480}

* Se muestran caracteres no válidos en la dirección URL añadida a un componente Botón (NPR-32684).

### Forms {#forms}

>[!NOTE]
>
>Service Pack de AEM no incluye correcciones para AEM Forms. Estas se entregan mediante un paquete independiente de complementos de Forms. Asimismo, se ha publicado un instalador acumulativo que incluye correcciones para AEM Forms en JEE. Para obtener más información, consulte [Instalación del paquete de complementos de AEM Forms](#install-aem-forms-add-on-package) y [Instalación del instalador de AEM Forms JEE](#install-aem-forms-jee-installer).

* Designer: Si la opción de etiquetado está activada, el borde del subformulario desaparece en la salida del PDF generado (NPR-32546, NPR-32322).

* Designer: Si hay celdas combinadas en una tabla, la prueba de accesibilidad falla para el archivo PDF de salida convertido desde un formulario XDP mediante el servicio de salida (NPR-32079).

* Seguridad de documentos: Un archivo PDF protegido no se puede abrir sin conexión con la opción DisableGlobalOfflineSynchronizationData establecida en True (NPR-32080).

* Seguridad de documentos: Problemas al abrir un archivo de PDF protegido después de actualizar de ES4 a AEM 6.3 (NPR-32170).

* Servicios de documentos: Aparece un mensaje de error al intentar convertir un archivo PDF en un documento PDF/A mediante el método de conversión toPDFA (NPR-32663).

* Servicios de documentos: Se muestra una excepción al aplicar el servicio Extensiones de Reader en un archivo de PDF (NPR-32639).

* Servicios de documentos: Aparece un mensaje de error al ensamblar y convertir archivos XDP a archivos PDF (NPR-31821).

* Analytics no muestra los resultados adecuados al enviar o abandonar formularios en una página de Sites (NPR-31359).

### Revisiones y paquetes de funciones incluidos en instancias de Service Pack anteriores {#hotfixes-and-feature-packs-included-in-previous-service-packs}

#### AEM 6.4.7.0 {#experience-manager-6470}

AEM 6.4.7.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas desde la disponibilidad general de AEM 6.4 in **Abril de 2018.**

También es acumulativo, lo que significa que 6.4.7.0 incluye todos los paquetes de servicio AEM 6.4 que se lanzaron antes.

Algunos de los aspectos destacados de AEM 6.4.7.0 son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.17.
* Se ha agregado compatibilidad para establecer la versión de una página Sitios al eliminarla.
* Se ha añadido una nueva columna para la fecha de creación, que es ordenable, en **Lista DAM** ver y en los resultados de búsqueda de recursos en **Lista** vista (NPR-31311).
* Ordenación de recursos en función de **Nombre** se ha permitido en **Lista** vista.
* El tamaño del lote y el tiempo de espera del paso del flujo de trabajo para el reprocesamiento y la carga por lotes ahora se pueden configurar desde la interfaz de usuario de Dynamic Media.
* La variable `pdfBrochure` se ha establecido en false en la configuración de nube de Scene7 para guardar memoria en IPS.

##### Recursos {#assets-6470}

**Mejoras de producto**

* La versión de exportación del paquete de API `package com.day.cq.dam.handler.standard.msoffice` compatible con `dam-handler` el paquete se actualiza a 6.0.0 (CQ-4279059).
Si está utilizando el paquete `com.day.cq.dam.handler.standard.msoffice` en su implementación personalizada, se recomienda que compile su `dam-handler` paquete con el último frasco de uber.

* Se ha añadido una nueva columna para la fecha creada, que es ordenable, en la vista de lista de DAM y en los resultados de búsqueda de recursos en la vista de lista (NPR-31311).

* Se ha permitido la ordenación de recursos basada en la columna Nombre en la vista de lista (NPR-31299).

**Correcciones**

* Los metadatos de algunos documentos del PDF no se actualizan ni se guardan en el PDF al modificar su título (NPR-31575).

* Los recursos con el símbolo &quot;+&quot; en el nombre de archivo no se pueden eliminar (NPR-30588).

* Las propiedades de la carpeta DAM no muestran los usuarios o grupos añadidos (creados mediante la sincronización LDAP) en Grupos de usuarios cerrados (NPR-30555).

* Los caracteres especiales que aparecen en la línea Asunto de las plantillas de correo electrónico no se muestran correctamente (NPR-30547).

* Los nombres de los recursos se cambian a minúsculas al mover recursos de una carpeta a otra en AEM que se ejecuta en el modo de ejecución de Dynamic Media Scene7 (NPR-31631).

* Los nombres de los conjuntos de imágenes se cambian a minúsculas en Scene7, cuando se crea un conjunto de imágenes (o conjunto de medios) y se les asigna un nombre con la convención de nombres adecuada en DAM (NPR-31576).

* El flujo de trabajo de codificación de vídeo de Dynamic Media no puede generar miniaturas para el vídeo que se migra de Scene7 al modo de ejecución de Dynamic Media - Scene7 (NPR-31523).

* Se observa un error interno del servidor al usar el filtro para buscar conjuntos, en AEM que se ejecuta en Dynamic Media - Scene 7 runmode (NPR-31388).

* Se observa un error al editar un conjunto de imágenes remoto, para la imagen que reside en la carpeta con el mismo nombre que el nombre de empresa de Scene7 (NPR-31347).

* Los recursos que contienen referencias no se publican (DM) (NPR-31179).

* El valor de caducidad (tiempo de espera de caché del cliente) configurado para el modo híbrido de Dynamic Media no se replica en el entorno de entrega de Dynamic Media (NPR-31126).

* Las cargas desde AEM modo de ejecución de Dynamic Media - Scene7 a Scene7 tardan demasiado en completarse (NPR-30926).

* Después de crear una página con un componente Dynamic Media mientras se publica el mismo, desde la instancia de autor que se ejecuta en el modo de ejecución Dynamic Media - Scene7, se solicita al usuario que publique la configuración de dmscene7 (NPR-30880).

* El valor del parámetro &quot;asset&quot; en el código incrustado del visor permanece sin cambios después de cambiar los valores del campo &quot;Title after move&quot; y &quot;Name after move&quot; en Dynamic Media - Scene 7 (NPR-30745).

* La página de resultados de la búsqueda en la interfaz de usuario táctil (realizada a través de Omnisearch) se desplaza automáticamente hacia arriba y pierde la posición de desplazamiento del usuario (NPR-31306).

* Depuración de eventos DAM elimina los datos de evento más recientes (maxSavedActivities) y contiene los datos creados anteriormente (NPR-30870).

* El título del recurso y el cambio de nombre no persistieron después de mover la operación a una carpeta de destino que déclencheur el desplazamiento infinito al seleccionarlo (NPR-30647).

* Las colecciones se eliminan de la vista al aplicar cualquier filtro en AEM Assets al que se acceda desde Adobe Asset Link (CQ-4280534).

* El tamaño del lote y el tiempo de espera del paso del flujo de trabajo para el reprocesamiento y la carga por lotes no se pueden configurar desde la interfaz de usuario y es necesario configurarlos en CRXDE y el flujo de trabajo debe sincronizarse dos veces (CQ-4281254).

* El nombre de paso del flujo de trabajo para la carga por lotes y el paso de carga simple es el mismo en Scene7, lo que provoca confusión (CQ-4281176).

* El flujo de trabajo de reprocesamiento en Scene7 se atasca si falta un recurso en el nodo de metadatos (CQ-4281170).

* El paso Carga por lotes en el flujo de trabajo de reprocesamiento no funciona para la carpeta que tiene un recurso de vídeo (CQ-4280630).

* Las opciones de PDF enviadas a DM tienen extractKeywords establecido en true de forma predeterminada (CQ-4280101).

* Null Point Exception se observa al ejecutar el flujo de trabajo de reprocesamiento de Scene7 en una carpeta que contiene recursos que no son DM (CQ-4279555).

* El cambio de nombre de recursos en AEM no se sincroniza con la escena 7, cuando ya existe un recurso con un nombre duplicado en Scene 7 (CQ-4276763).

* El archivo zip enviado por correo electrónico para la descarga de recursos no se descomprime cuando un usuario con permisos de lectura intenta abrirlo (CQ-4277925).

* El flujo de trabajo de representación PPT no puede generar representaciones de los archivos PPT cargados, ya que AEM 6.4 no se puede actualizar a com.adobe.granite.poi versión 2.0.28 (CQ-4279059).

* Los archivos PDF no están indexados y el contenido dentro de no se puede buscar (CQ-4278916).

##### Sitios {#sites-6470}

* Cuando los lanzamientos se promocionan con páginas Promocionar solo modificadas y se realizan los lanzamientos Promocionar con páginas modificadas, solo las páginas modificadas parecen promocionarse. Además, cuando la lista que se va a promocionar es correcta, las páginas no modificadas se siguen mostrando en la parte inferior de la lista (NPR-31314).

* Cuando una página de AEM Sites se mueve a una ubicación diferente, sus propiedades no se actualizan según corresponda para reflejar su nueva ubicación (NPR-31265).

* Para un nuevo modelo, si el número de registros es superior a 40, solo se muestran los 40 primeros registros. Modelo muestra líneas en blanco para el resto de los registros (NPR-31182).

* Cuando el número de LiveCopies es grande, la descripción general de LiveCopy tarda mucho tiempo en procesar la vista previa (NPR-30945).

* Se ha agregado compatibilidad para establecer una versión de una página al eliminarla. Si el control de versiones está deshabilitado para la página eliminada, AEM Sites no puede restaurar esas páginas (NPR-30891).

* Cuando un usuario añade caracteres japoneses o coreanos en la propiedad description de un menú, el menú muestra caracteres distorsionados para texto en japonés y coreano (NPR-31331).

* Cuando un usuario se centra en los campos del carril izquierdo y utiliza un método abreviado de teclado para pegar contenido, pega el contenido del portapapeles del editor de páginas en lugar del contenido copiado de los campos del carril izquierdo (NPR-31169).

* Cuando un usuario edita un fragmento de contenido, se restaura la variación ya eliminada del fragmento de contenido (NPR-31178).

* La consulta de modelos de fragmento de contenido no es eficiente. Es muy lento si la instancia tiene muchas páginas y resulta en un error (NPR-30666).

* Al guardar el modelo de fragmento de contenido, la hora del campo de fecha y hora se establece en 00:00 (NPR-30540).

##### Integraciones {#integrations-6470}

* Al configurar Adobe Launch, se añade una barra diagonal (/) en la URL de la biblioteca (NPR-30700).

* El rendimiento de ContextHub se degrada tras la publicación (NPR-30884).

##### Sling {#sling-6470}

* Actualice la versión del paquete del proveedor de seguridad de la consola web a 1.2.4 para eliminar la dependencia de la api de inicio del panel de lanzamiento de webconsolesecurityprovider (NPR-30885).

##### Plataforma {#platform-6470}

* Las actualizaciones en la configuración del tamaño del búfer para el servicio HTTP basado en Jetty no se guardan (NPR-30925).

* QueryBuilder ahora es compatible con orderby fn:name() en consultas xpath (NPR-31322).

* Se ha actualizado la administración de eventos distribuidos de Sling a la versión 1.1.4, lo que mejora la calidad de los registros en un entorno agrupado (NPR-29256).

##### Interfaz de usuario de base {#foundation-6470}

* Si se desplaza hasta el final de la página de resultados con un gran número de resultados de búsqueda, el explorador se bloquea (NPR-31332).

* Al cambiar de la vista de tarjeta a la vista de lista en una página de resultados de búsqueda, hay un retraso antes de que la página se pueda desplazar (NPR-31280).

##### Oak {#oak-6470}

* Los archivos de MS Office con extensiones de archivo .docx y .xlsx que contienen imágenes JPEG no se pueden analizar con el analizador de Tika (NPR-31693).

##### Livefyre {#livefyre-6470}

* La integración de Livefyre con AEM actualización 6.4 proporciona Null Point Exception, cuando la integración se realiza utilizando el complemento DITA para recursos sintéticos. Sin embargo, la integración funciona cuando los componentes se añaden manualmente (FYR-11066).

##### Traducción {#translation-6470}

* La ruta al fragmento de experiencia de destino no se actualiza al promocionar una página de lanzamiento (NPR-30830).

##### Comunidades {#communities-6470}

* La funcionalidad de correo electrónico no funciona correctamente en algunos casos, incluso cuando la mensajería de correo electrónico está habilitada en la configuración de notificaciones, el sistema genera una excepción en NotificationsActivityStreamProvider (NPR-31521).
* No se pueden crear nuevos miembros, aparece una pantalla en blanco en la pantalla Crear miembro en AEM instancia de autor (NPR-30951).
* El usuario no puede publicar un comentario en un blog en Internet Explorer 11 (NPR-30927).
* El administrador de un grupo restringido no puede ver la tarjeta de grupo y no puede realizar ninguna operación de vínculo rápido (grupos de edición, publicación o eliminación) en AEM instancia de autor (NPR-30810).
* La información de grupos de miembros o grupos no está visible al crear un nuevo sitio en AEM instancia de autor (NPR-28840).

##### Forms {#forms-6470}

>[!NOTE]
>
>Service Pack de AEM no incluye correcciones para AEM Forms. Estas se entregan mediante un paquete independiente de complementos de Forms. Asimismo, se ha publicado un instalador acumulativo que incluye correcciones para AEM Forms en JEE. Para obtener más información, consulte [Instalación del paquete de complementos de AEM Forms](#install-aem-forms-add-on-package) y [Instalación del instalador de AEM Forms JEE](#install-aem-forms-jee-installer).

**Paquete de complemento de Forms**

**Formularios adaptables**

* Las cadenas contienen la clave de diccionario al localizar formularios adaptables (NPR-31109).

* Las casillas de verificación y las listas desplegables de Forms fallan en las comprobaciones de accesibilidad (NPR-31282).

**Formularios HTML5**

* Al generar la vista previa HTML5 de un formulario XDP, se muestra un parpadeo al agregar instancias de un subformulario (NPR-30907).

**Servicios de documentos para OSGi**

* Al ejecutar varios subprocesos simultáneos para ensamblar los formularios utilizando el método com.adobe.fd.assembler.service.AssemblerService.invoke() , se muestra un mensaje de error (NPR-31164).

* Los archivos temporales creados por el servicio Assembler no se eliminan automáticamente y requieren AEM reinicio (NPR-30846).

* La aplicación de derechos de ReaderExtension al PDF genera un mensaje de error (NPR-30930).

**Flujo de trabajo**

* El flujo de trabajo de OSGi falla debido a la utilización del 100% de la CPU (NPR-31234).

**Instalador JEE de Forms**

**Servicios de documento**

* El servicio Convertir PDF no convierte los documentos PDF a PostScript y muestra un mensaje de error (NPR-31267).

* La configuración del extremo SOAP se restablece después de aplicar un parche para corregir el fallo del HTML al PDF (NPR-31309).

**Servicio PDFG**

* No se puede cargar el archivo de configuración de Adobe PDF descargado mediante la IU de administración (NPR-31273).

#### AEM 6.4.6.0 {#experience-manager-6460}

AEM 6.4.6.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas desde la disponibilidad general de AEM 6.4 in **Abril de 2018.**

También es acumulativo, lo que significa que 6.4.6.0 incluye todos los paquetes de servicio AEM 6.4 que se lanzaron antes.

Algunos de los aspectos destacados de AEM 6.4.6.0 son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.15.
* Se ha agregado compatibilidad para rastrear estados de IU dinámicos en el seguimiento de eventos en la API de base.
* Se ha agregado compatibilidad de representación al componente principal de imagen.

**Assets**

* Vínculo de uso compartido de recursos de una carpeta con espacio y `&` en el nombre, se muestran tarjetas grises en blanco para algunos recursos. NPR-29934: revisión para CQ-4270187
* El flujo de trabajo de DAM se bloquea al crear recursos de MP4 para AEM. NPR-30031: revisión para CQ-4271352
* Problema de conectividad de etiquetas inteligentes de Adobe a través de Datapower. NPR-30026: revisión para CQ-4269457
* No se puede encontrar el PDF mediante OmniSearch. NPR-30046: revisión para GRANITE-26290
* Las rutas de recursos de las direcciones URL y los metadatos de las carpetas que genera la API de ACP no son URL codificadas.  GRANITE-26198: revisión para CQ-4271814
* La funcionalidad Crear tarea de revisión no funciona debido a una carga útil indefinida. NPR-30469: Revisión CQ-4274263
* La capacidad de cambiar la vista de la tarjeta a la vista de lista y viceversa desaparece después de realizar una OmniSearch en el selector de recursos. NPR-29852: revisión para CQ-4269369
* (IU táctil) Durante el asistente de administración de publicaciones, los recursos se añaden a la cola de replicación después de agregar las páginas, por lo que algunos de los recursos aparecen pasados unos segundos. NPR-29985: revisión para CQ-4270724
* Al ordenar la consulta de búsqueda por relevancia, se devuelven documentos de InDesign junto con plantillas de InDesign. Revisión para CQ-4273864
* Si el usuario tiene un id. de correo electrónico en mayúsculas, los usuarios no pueden registrar los recursos que ya se han extraído. Revisión para CQ-4276575
* Configuración de Cloud Services de Dynamic Media en `DMHybrid` da como resultado varios grupos de informes vacíos creados en Analytics sin ningún id de grupo de informes almacenado en AEM, lo que provoca la duplicación de grupos de informes. Revisión para CQ-4276855
* El cuadro de diálogo de advertencia no aparece al promocionar en la página &quot;Etiqueta administrada&quot;. Revisión para CQ-4252851
* Cuando se utiliza el carrusel para administrar etiquetas, el botón de navegación no funciona. Revisión para CQ-4275499
* La funcionalidad de los recursos de movimiento masivo está dañada, lo que provoca que no se muevan los recursos. Revisión para CQ-4272987

**Sites**

* `pageinfo.json` las solicitudes son extremadamente lentas y tardan demasiado en cargarse. NPR-29709: revisión para CQ-4269560
* `onTime` o `offTime` las propiedades de metadatos guardadas en los recursos no se recuperan si se reinicia el servidor AEM. NPR-30413: revisión para CQ-4272784
* Debido al comportamiento incorrecto de la clase ConfigPostProcessor , la suspensión de la página principal elimina el cq: Tipo de mezcla LiveRelationship de la página secundaria. NPR-30536, NPR-30510: revisión para CQ-4254113
* Ejecución de scripts en sitios múltiples (XSS) en el cuadro de diálogo Iniciar flujo de trabajo de la página de edición de Campaign. NPR-29747: revisión para CQ-4271067
* (IU clásica) La fase de bloqueo del flujo de trabajo desactiva la pestaña del flujo de trabajo hasta que se libera el bloqueo. NPR-30356: revisión para CQ-4237557
* (IE11) Al pegar contenido de HTML en un componente Editor de texto enriquecido con defaultPasteMode = texto sin formato, el HTML se pega con el formato, por lo que defaultPasteMode no tiene ningún efecto. NPR-30045: revisión para GRANITE-26094
* (IU clásica) Cuando se vuelve a cargar la página de administración del sitio, todos los elementos desplegables del menú &quot;Nuevo&quot; se desactivan. NPR-29980: revisión para CQ-4272044
* No se pueden agregar estilos al texto ni editar los estilos existentes creados en el contenido. NPR-29712: revisión para CQ-4266249
* (IU clásica) Recursos sin dc: el valor de título aparece sin título en el navegador de diálogo del campo de ruta. NPR-30166: Solicitud de backport para CQ-88858
* El cq: el listener no funciona con componentes anidados incluso después de añadir el componente parsys. NPR-30422: revisión para CQ-4274863
* Error de ContextHub durante la integración de AEM y Campaign. NPR-30625: revisión para CQ-4250790
* El valor del parámetro de solicitud resourceType se copia en el valor de un atributo de etiqueta HTML que se encapsula entre comillas dobles. NPR-29832: revisión para CQ-4255365
* Es necesario actualizar la página después de copiar y pegar los componentes de una página a otra. NPR-29982: revisión para CQ-4256019
* Publicar/Cancelar la publicación desde un alias de página no es compatible y debe eliminarse. NPR-30062: revisión para CQ-4271249
* Advertencia de ResourceResolver no cerrado en ExperienceFragmentsReplicationListener que provoca problemas de estabilidad a lo largo del tiempo, lo que obliga a reiniciar instancias de AEM. NPR-30416: revisión para CQ-4257521
* Al mover fragmentos de experiencias a los que se hace referencia en más de 150 páginas, no se modifica fragmentPath en las páginas donde se hace referencia a ellos. NPR-30556: revisión para CQ-4274900
* Error de análisis al abrir un fragmento de contenido que tiene caracteres &quot;dólar&quot; (`$`) y abra la llave (`{`) uno tras otro. Revisión para CQ-4270266
* VersionPreviewServlet genera errores en NullPointerException al intentar mostrar una versión de un fragmento de experiencia en la línea de tiempo. NPR-30074: revisión para CQ-4271881
* No se pueden bloquear los fragmentos de contenido a través de la función de protección. NPR-29923: revisión para CQ-4258785
* Error de verificación de firma en el controlador de autenticación SAML. NPR-30379: Solicitud de backport para GRANITE-26567

**Replicación**

* La sesión JCR/Resource Resolver se filtra durante la implementación de OAuth en cada replicación a MAC/Brand Portal. NPR-30000: revisión para Granite-26196

**Sling**

* El orden de los elementos secundarios afectados utilizando la superposición y el orden antes está causando IndexOutOfBoundException. NPR-30408: Revisión para Sling-8296 y Sling-7375
* InactiveBundlesHealthCheck está leyendo la configuración MissingPackagesHealthCheck una vez guardadas las configuraciones InactiveBundlesHealthCheck. NPR-30084: revisión para CQ-4272644

**Comercio**

* No se puede ejecutar el modelo de catálogo desde la consola Sitios . NPR-29829: revisión para CQ-4271461
* El recurso utilizado en el producto no muestra ninguna referencia al producto en la sección &quot;Referencias&quot; del recurso. La ruta del recurso no se actualiza si se mueve el recurso. NPR-30542: revisión para CQ-4270247

**Plataforma**

* El remitente de correo predeterminado de AEM no puede enviar correo a un servidor SMTP remoto a través de TLS v1.2. NPR-30476: revisión para GRANITE-26605

**Communities**

* Los grupos eliminados en el autor no están sincronizados con todos los editores. NPR-29987: revisión para CQ-4268738
* Los usuarios eliminados del campo Administradores de la comunidad no están sincronizados con el grupo Pertenencia. NPR-30389: revisión para CQ-4274339
* Los usuarios que forman parte del grupo de administradores no tienen vínculos rápidos para el grupo. NPR-30546: revisión para CQ-4275579
* Al actualizar cualquier grupo de la comunidad recién creado y existente, se sobrescribe la propiedad en jcr: y cambia su nombre al título de la primera página. NPR-30109: revisión para CQ-4273719
* La búsqueda rápida y a través de la ubicación y la dirección no funciona cuando la comunidad está configurada para trabajar con el proveedor de recursos de almacenamiento de bases de datos (DSRP). NPR-26737: revisión para CQ-4258493

**Traducción**

* La ejecución automática de la traducción no funciona. NPR-30499: revisión para CQ-4276288
* El usuario puede crear una copia de idioma en la ruta de contenido restringida a solo lectura. NPR-29937: revisión para CQ-4270708
* Problema de traducción: solo unos pocos componentes se traducen mediante traducción automática. NPR-30079: revisión para CQ-4273764

**Integración**

* El contenido personalizado no se muestra correctamente en la instancia de publicación hasta que no se reinicia la instancia. NPR-30421: revisión para CQ-4273706

**Proyectos**

* Los valores de dam:folderThumbnailPaths no se actualizan y muestran miniaturas antiguas incluso después de eliminar los recursos de la carpeta. NPR-30424: revisión para CQ-4273667

**Consolas de IU**

* Secuencias de comandos entre sitios (XSS) en propiedades de página Sitios en la ficha Miniaturas. NPR-30048: revisión para Granite-26200

**UI-Foundation**

* Se ha agregado compatibilidad para rastrear estados de IU dinámicos en el seguimiento de eventos en la API de base. NPR-30742, GRANITE-26322: Revisión para GRANITE-26036

**Forms**

>[!NOTE]
>
>Service Pack de AEM no incluye correcciones para AEM Forms. Estas se entregan mediante un paquete independiente de complementos de Forms. Asimismo, se ha publicado un instalador acumulativo que incluye correcciones para AEM Forms en JEE. Para obtener más información, consulte [Instalación del paquete de complementos de AEM Forms](#install-aem-forms-add-on-package) y [Instalación del instalador de AEM Forms JEE](#install-aem-forms-jee-installer).

**Paquete de complemento de Forms**

**Formularios adaptables**

* El archivo .css vacío tarda más tiempo en recuperarse del editor, lo que provoca problemas de rendimiento. NPR-30558: revisión para CQ-4274399
* Las Forms que se modifican después de la publicación no se publican de nuevo en el sitio. NPR-30411: revisión para CQ-4236566

**Forms: integración back-end**

* Se produce un error al crear el modelo de datos de formulario con el lenguaje de definición de servicio web (WSDL). NPR-30388: revisión para CQ-4272921

**Forms: administración de correspondencia**

* Los caracteres especiales como menor que (&lt;), bueno que (>) y el signo &amp; (&amp;) se codifican en la interfaz de usuario del agente. NPR-30410: revisión para CQ-4273887
* Cuando se activa un fragmento de texto que contiene valores de diccionario de datos, la interfaz de usuario del agente deja de responder. NPR-30098, NPR-30083: revisión para CQ-4272204
* La IU Crear correspondencia (IU de CCR) falla de forma intermitente con la variable de error (objeto Object). NPR-29983: revisión para CQ-4273874
* La recarga del borrador de la carta falla con una excepción cuando la descripción de los fragmentos de documento contiene caracteres especiales como menor que (&lt;), bueno que (>) y el signo (&amp;) en las propiedades. NPR-29930: revisión para CQ-4252762

**Formularios HTML5**

* Cuando se utiliza la opción de acceso al escritorio no visual en el modo Examinar para leer un formulario de HTML5, el navegador Chrome lee el elemento &quot;gráfico&quot; antes que cada gráfico vectorial escalable (SVG) en el diseño de formulario. NPR-30450: revisión para CQ-4274732

**Instalador JEE de Forms**

**Forms: base JEE**

* Al agregar o editar una conexión de servicio Web invocando servicios Web desde AEM formularios, Workbench genera un error: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30116: revisión para CQ-4273217

**Forms: servicios de documentos**

* Falta el error de etiqueta de PDF/A en la comprobación preliminar de Acrobat. NPR-30594: revisión para CQ-4276032
* Los enlaces de datos de un solo carácter en el PDF hacen que las extensiones del Reader fallen con el error &quot;java.lang.StringIndexOutOfBoundException: Índice de cadenas fuera de rango: 1&quot;. NPR-30128: revisión para CQ-4273878
* Cuando se hace una prueba de carga en el servicio HTML a PDF, se produce un error y se elimina la configuración del tipo de archivo del servidor de AEM Forms. NPR-30085: revisión para CQ-4272631
* Al acoplar un PDF con Adobe Acrobat 9.1 (XFA versión 3.0), no se mantiene el estado del formulario del PDF: Los elementos invisibles del formulario se devuelven a un estado visible. NPR-29978: revisión para CQ-4270888

**Forms: seguridad de documentos**

* El proceso de aplicación de una firma con marca de hora devuelve el error: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: error de invocación. NPR-30696, NPR-30537: revisión para CQ-4273778
* Configuration Manager no inserta cadenas japonesas para columnas de tabla localizadas. NPR-30496: revisión para CQ-4274868

**Servicio PDFG**

* Error de conexión al intentar convertir el documento de Word a PDF en Windows Server 2016. NPR-30597: revisión para CQ-4275652
* Se denegó el permiso de excepción al intentar usar el HTML para el servicio back-end de PDF a través de la biblioteca &quot;phantomjs&quot;. NPR-30456: revisión para CQ-4258077
* maxReuseCount para el servicio de HTML a PDF no se muestra con la Consola de administración de JBoss. NPR-30303, NPR-30135: revisión para CQ-4273763

#### AEM 6.4.5.0 {#experience-manager-6450}

AEM 6.4.5.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas desde la disponibilidad general de AEM 6.4 in **Abril de 2018.**

También es acumulativo, lo que significa que 6.4.5.0 incluye todos los paquetes de servicio AEM 6.4 que se lanzaron antes.

Algunos de los aspectos destacados de AEM 6.4.5.0 son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.13.
* Se ha agregado tiempo de espera de socket y tiempo de espera de conexión en los agentes de replicación de Brand Portal.
* Mejoras de Omnisearch : se ha aumentado el límite de paginación del resultado de búsqueda a 100 páginas.
* Desactivado `AssetDownloadServlet` Componente OSGi de forma predeterminada en AEM instancias de publicación. Para obtener más información, consulte [Descargar recursos de AEM](/help/assets/download-assets-from-aem.md).
* Se habilitó la compatibilidad con el administrador de varios sitios para los recursos. Para obtener más información, consulte [Reutilizar recursos con MSM para Assets](/help/assets/reuse-assets-using-msm.md).

**Recursos**

* Los recursos con un apóstrofo en el nombre de archivo no se sincronizan con Dynamic Media. NPR-29538: revisión para CQ-4270592
* Se ha actualizado la interfaz DAM DMGateway para que sea compatible con varias partes de S3. NPR-29740: revisión para CQ-4226303
* El cuadro de diálogo de descarga de recursos muestra un tamaño de archivo incorrecto al descargar representaciones para un vídeo en Dynamic Media. NPR-29642: revisión para CQ-4246202
* Los activos quedan inutilizables después de que el servicio Day CQ DAM Mime Type aplique texto para m3u8. NPR-29276: revisión para CQ-4264052
* El ajuste de referencia de recursos no guarda la sesión si alguno de los recursos movidos o renombrados forma parte de las colecciones de recursos de Sling. NPR-29143: Revisión para /CQ-4252605
* No se pueden rastrear ni encontrar recursos buscando en los valores de metadatos. NPR-29141: revisión para CQ-4260215
* Al utilizar el filtro de búsqueda para guardar una colección inteligente, la acción de clic en el panel no mantiene el enfoque. NPR-29000: revisión para CQ-4240323
* Mover una carpeta permite crear una carpeta con nombres en mayúsculas o en mayúsculas o en varias mayúsculas. NPR-28945: revisión para CQ-4265234
* Los resultados en blanco se muestran en Omnisearch si el nombre de la colección tiene espacio. NPR-29001: revisión para CQ-4236729
* Al cambiar el nombre de un archivo con algunos caracteres especiales no admitidos, como el símbolo &amp;, se crea una carpeta no válida. NPR-29196: revisión para CQ-4265037
* Archivo de extracción DAM para la funcionalidad de archivo zip no funciona. NPR-29187: revisión para CQ-4254421
* La importación de metadatos debe permitir la importación de metadatos sin registrar espacios de nombres. NPR-29425, NPR-28132: revisión para CQ-4269445
* Guardar los cambios de metadatos no funciona para los recursos cuyo nombre contiene un carácter de comillas. NPR-29395: revisión para CQ-4254305
* No se puede mover un recurso DAM si el nombre de archivo contiene un espacio en blanco. NPR-29270: revisión para CQ-4266403
* No se pueden descargar archivos ZIP comprimidos con el algoritmo Deflate64. NPR-29225: revisión para CQ-4253995
* Las miniaturas de los recursos se muestran lentamente al abrir una carpeta que contiene recursos con muchas versiones. NPR-29833: revisión para CQ-4271629
* No se puede introducir la colección resaltada si se pulsa la tecla Intro después de seleccionar la colección. NPR-29723: revisión para CQ-4261607
* Los scripts entre sitios (XSS) se atacan a través de la ventana de alerta restringida. NPR-29671: revisión para CQ-4270133
* No se pueden agregar relaciones a los recursos para los usuarios sin permisos de eliminación. NPR-29640: revisión para CQ-4269196
* Después de agregar el título del recurso en la página de propiedades, cuando el usuario intenta cerrar la página, AEM vuelve a abrir la página de propiedades. NPR-29628: revisión para CQ-4264929
* La creación de un gran número de relaciones en los recursos produce un error. NPR-28779: revisión para CQ-4250708
* La ingesta de recursos es lenta en el modo de ejecución de Scene7 Connect. NPR-28658: revisión para CQ-4263007
* Error TypeError no capturado: No se puede leer la propiedad &quot;split&quot; de undefined se muestra al intentar ver los resultados de la búsqueda. NPR-28803: revisión para CQ-4248371
* La replicación de AEM a Brand Portal se atasca durante largos períodos. NPR-28914: revisión para CQ-4254932
* Mover recursos en DAM no tiene como resultado un movimiento similar en Scene7. NPR-28957: revisión para CQ-4264974
* Las actualizaciones de metadatos no se pasan a IPS si el campo de metadatos se actualiza en AEM. NPR-28961: revisión para CQ-4255393
* VersioningTimelineEventProvider debe proporcionar la versión raíz junto con el comentario de la versión. Revisión para GRANITE-26063
* La inyección de datos lleva a la ejecución del código en el servidor. Revisión para CQ-4270246
* Se habilitó la compatibilidad con el administrador de varios sitios para los recursos. Revisión para CQ-4271453, CQ-4268621, CQ-4257491
* La interfaz de AEM debe mostrar una entrada adicional para la versión actual del recurso en el historial de línea de tiempo, mostrando así el último comentario de registro de Adobe Asset Link. Revisión para CQ-4262864
* El vídeo de ejemplo no se carga al crear o editar un MixedMediaSet. Revisión para CQ-4244889
* Si se desactivan los permisos para eliminar contenido en el lado del AEM, el usuario no podrá publicar en Brand Portal. Revisión para CQ-4270426
* Problemas relacionados con el límite de consultas con los informes de recursos después de la actualización a AEM 6.4.3. NPR-28588: Revisión para CQ-4262022, CQ-4260697
* La funcionalidad de descarga aprovecha AEM Assets mediante el servlet de descarga de recursos, lo que permite a los usuarios anónimos descargar todos los recursos. NPR-27315, revisión para CQ-4254732

**Sitios**

* El nombre de la etiqueta de queja JCR debe rellenarse automáticamente en función del título de la etiqueta. NPR-28990: revisión para CQ-4199411
* El botón Cancelar herencia no está visible en algunos de los campos agregados en las propiedades de página. NPR-29079: revisión para CQ-4265686
* La acción de vista previa de lanzamiento no debe intentar recrear la Live Copy ni mostrarla en la lista de páginas de lanzamiento. NPR-29151: revisión para CQ-4266213
* (Editor de plantillas) Regresión de directiva de estilo en el modo de estructura. NPR-28981: revisión para CQ-4264400
* Las Live Copies anidadas muestran entradas duplicadas durante el lanzamiento. NPR-29300: revisión para CQ-4268664
* La publicación de una Live Copy de una Live Copy que contiene un componente Importador de diseños falla y Error al recuperar referencias para la página seleccionada. NPR-28944: revisión para CQ-4265014
* Cuando se utiliza CoralUI con Multifield, se almacena el parámetro fileReferenceParameter en el nivel de componente en lugar de en el nivel de multicampo. NPR-29536: revisión para CQ-4266129
* La referencia de diseño no se replica en la publicación después de cancelar la herencia en el Importador de diseños. NPR-29648, NPR-29721: revisión para CQ-4269270, CQ-4271087
* El campo de ruta en el Editor de texto enriquecido se abre en la ruta raíz independientemente de la ruta especificada para la búsqueda. NPR-29483: revisión para CQ-4268997
* (IE11) Copiar y pegar el contenido del HTML en un componente RTE con defaultPasteMode = texto sin formato no pega el contenido como texto sin formato. NPR-29432, NPR-29171: Revisión para GRANITE-24941
* La corrección ortográfica del Editor de texto enriquecido ya no funciona en otros idiomas. NPR-29506: revisión para CQ-4264990
* Ejecución de scripts en sitios múltiples (XSS) en la página de Campaign. NPR-29614: revisión para CQ-4269322
* Minimizar el Editor de texto enriquecido desde la pantalla completa mientras se encuentra en el modo de edición de fuente provoca la pérdida del contenido. NPR-29574: revisión para CQ-4260584
* (IU clásica) La navegación a la última pestaña no siempre es posible cuando existe un gran número de etiquetas. NPR-29544: revisión para CQ-4264548
* (IU clásica) El menú de navegación del Admin Console desaparece y la página no se carga completamente. NPR-29571: revisión para CQ-4264585
* Se genera una alerta de error al añadir componentes a la página WCM cuando la minimización está habilitada en la instancia. NPR-29396: revisión para CQ-4266196
* Problema con la herencia de los nodos del sistema de estilos del elemento principal. NPR-29296: revisión para CQ-4266041
* La página restaurada con Deformación de tiempo debe hacer referencia a la imagen correcta en el momento de controlar las versiones.  NPR-29431: revisión para CQ-4262638
* Página en blanco con errores de JavaScript en el editor después de instalar la última versión de la instantánea 6.4.5. NPR-29475: revisión para CQ-4266196
* Al añadir un componente a un parsys, la propiedad de la lista de componentes del diseño no se respeta y se resuelve a un nombre de nodo de plantilla diferente con una estructura parsys similar. NPR-29509: revisión para CQ-4269044
* la zona cq:dropTargets cubre todo el componente en lugar del tamaño de la imagen, lo que dificulta el targeting con los componentes incrustados. NPR-29738: revisión para CQ-4268912
* El componente de imagen no llama al oyente &quot;después de editar&quot; una vez que se utiliza el editor in-situ de imágenes. Revisión NPR-29616 para CQ-4268065
* Problema al configurar la publicación social en Facebook. NPR-29212: revisión para CQ-4266630
* Cuando se promocionan los lanzamientos de las páginas modificadas, se tienen en cuenta las modificaciones en las ramas de lanzamiento y origen. NPR-29308: revisión para CQ-4266746
* La miniatura representada en el fragmento de contenido muestra una representación interna del calendario para los campos de fecha y hora. NPR-29531: revisión para CQ-4269362
* No se puede agregar de forma masiva una etiqueta a páginas con etiquetas diferentes existentes. NPR-28729: revisión para CQ-4262922
* El icono Activación programada no se muestra en el administrador del sitio. NPR-28725: revisión para CQ-4263917

**Replicación**

* Vulnerabilidad de la revelación de información confidencial en el componente Agente de replicación. NPR-29612, NPR-24951: Revisión para GRANITE-25070
* Los datos que proporcionó el usuario no se evitan en la salida del componente cq/replication/components/agent, lo que provoca una vulnerabilidad en la ejecución almacenada de scripts en sitios múltiples (XSS). Revisión para CQ-4266263

**Fragmentos de experiencias**

* No se pueden exportar fragmentos de experiencia para que sean objetivos cuando se utiliza una imagen inteligente. Revisión para CQ-4269606

**Social: informes**

* AEM informes de comunidad no se muestran en AEM instancia de autor. Revisión para CQ-4266294

**Plataforma**

* Ejecución de scripts en sitios múltiples (XSS) en el administrador de paquetes mientras se instala un paquete. NPR-29734, NPR-29713, NPR-29630: Revisión para GRANITE-26161, GRANITE-
* Varios scripts almacenados y reflejados entre sitios (XSS) en CRXDE Lite. NPR-29634: revisión para GRANITE-26049
* La funcionalidad de inicio de sesión para Uso compartido de paquetes utiliza una solicitud de GET en lugar de una solicitud de POST, lo que hace que la contraseña sea visible en la pestaña de red. NPR-29631: revisión para GRANITE-26048

**Felix**

* Secuencia de comandos entre sitios (XSS) observada en la consola del sistema. La página se carga y aparece cuando el ratón pasa por encima del campo de texto. NPR-29853, NPR-29633: Revisión para GRANITE-26188, GRANITE-26050

**Granite**

* La configuración del registrador de Apache Sling no filtra el script insertado.  NPR-29775: revisión para GRANITE-26051

**Comunidades**

* Los grupos eliminados en el autor deben eliminarse de las instancias de publicación. NPR-28933: revisión para CQ-4264645
* El secreto de la aplicación debe protegerse con un campo de contraseña, no mostrarse en texto sin formato para las herramientas de conexión social. NPR-29728: revisión para CQ-4270480
* Los visitantes y los miembros, sin privilegios de moderador, pueden ver las publicaciones pendientes o no aprobadas pegando la dirección URL. NPR-29726: revisión para CQ-4271124, CQ-4271441
* Se observa un tiempo de respuesta alto de hasta 40-50 segundos cuando el usuario inicia sesión en la comunidad. NPR-29678: revisión para CQ-4269444

**Traducción**

* Los usuarios sin acceso a funciones de traducción en la navegación no deben poder acceder a sus subpáginas. NPR-29644: revisión para CQ-4269979
* Los permisos de usuario no se mantienen como asistente permiten la creación de la copia de traducción en una ubicación de solo lectura. NPR-29375: revisión para CQ-4265877

**IU: bases**

* Se ha aumentado el límite de paginación del resultado de búsqueda a 100 páginas para la vista de tarjeta y a 200 para la vista de lista. NPR-29332: revisión para GRANITE-24644
* Debido a la carga lenta de etiquetas, no se muestra nada en la página de recopilación. NPR-29267: revisión para GRANITE-24902
* Si se cambia el límite de paginación a 100 en lugar de 40 déclencheur, la carga diferida extra se cargará sin solicitud de paginación. NPR-29246: revisión para GRANITE-25027
* AEM campo de contraseña de granito no se rellena después del cifrado. NPR-29245: revisión para GRANITE-24908

**Integración**

* Se muestra un mensaje de excepción al intentar editar y guardar la configuración de AEM launch. NPR-29086: revisión para CQ-4266153
* Error de conexión en las credenciales de BrightEdge.  NPR-29167: revisión para CQ-4265872
* Se debe eliminar la casilla de verificación heredada de que aparece en el nivel raíz en Configuraciones de Cloud Service. NPR-27856: revisión para CQ-4259676

**Sling**

* El tiempo de espera de conexión HTTP no se está leyendo desde las configuraciones. NPR-29264: revisión para SLING-7902
* La reescritura del instalador JCR hace que la configuración OSGi utilice un formato no válido y bloquee la reimplementación. NPR-29027: revisión para CQ-4264694

**Proyectos**

* Los usuarios no pueden completar el flujo de trabajo del proyecto. NPR-29621: revisión para CQ-4258791
* La lista Flujo de trabajo del proyecto muestra filas vacías más allá de 40 flujos de trabajo. NPR-28739: revisión para CQ-4264005
* Al seleccionar la opción Representación dinámica en Brand Portal, se descarga un archivo .zip vacío. NPR-29420: revisión para CQ-4268826
* La publicación de recursos de la carpeta de AEM Author /content/dam/mac en Brand Portal no funciona. NPR-29820: revisión para CQ-4271118
* La puntuación en el nombre causa problemas con el botón de publicación. NPR-29573: revisión para CQ-4269317
* No se puede crear la copia del idioma del recurso mediante el panel de referencia. Revisión para CQ-4269535

**Flujo de trabajo**

* La actualización de 6.4.2 a 6.4.4 rompe el campo del selector de calendario del participante en el cuadro de diálogo. NPR-29727: revisión para CQ-4270423

**WCM: IU de administración**

* Al abrir la pestaña permisos en la implementación de Coral2, no se muestran los botones. Revisión para CQ-4269419

**WCM: administrador de varios sitios (MSM)**

* La eliminación de un nodo secundario en Live Copy debe desasociar el elemento liveRelationship. Revisión para CQ-4270395
* La actualización a AEM 6.4.3 hace que el administrador de varios sitios tarde mucho en implementarse. Revisión para CQ-4271410

**Vulnerabilidad**

* El marco de protección CSRF no funciona con los formularios de base de AEM. NPR-28612: revisión para GRANITE-22231

**WCM: editor de páginas**

* Se ha reflejado el proceso de ejecución de scripts en sitios múltiples al utilizar un selector no válido. Revisión para CQ-4270397

**Forms**

Los aspectos destacados de los formularios de AEM 6.4.5.0 son:

**Paquete de complemento de Forms**

**Formularios adaptables**

* (IU táctil) La opción Iniciar flujo de trabajo no aparece en el cuadro de diálogo para su configuración. NPR-29521: revisión para CQ-4269050

**Forms: integración back-end**

* Se habilitó la compatibilidad con los servicios de federación de Active Directory (ADFS) v3.0 para la integración local de Microsoft Dynamics. NPR-30003, NPR-29484: revisión para CQ-4270586
* El servicio de precarga falla debido a un tiempo de respuesta prolongado del módulo de integración de datos de AEM Forms. NPR-28997: revisión para CQ-4265988
* El formato de la solicitud del servicio web SOAP no es correcto en AEM Forms. NPR-29013: revisión para CQ-4265443
* No se muestra ningún mensaje de error al probar el servicio SOAP, en caso de que el valor de fecha sea incorrecto. Revisión para CQ-4265445

**Forms - Comunicación interactiva y Forms - Gestión de correspondencia**

* La IU Crear correspondencia (IU de CCR) no gestiona un número flotante.  NPR-29210: revisión para CQ-4254201
* La información de objeto establecida en una variable no está visible en la IU Crear correspondencia (IU de CCR). NPR-29739: revisión para CQ-4250533
* No se puede copiar o pegar desde Omnisearch en letras. NPR-29808: revisión para CQ-4270783

**Formularios HTML5**

* Cuando se añade un espacio dentro del texto, el campo de texto no permite rellenarlo hasta el final. NPR-28844: revisión para CQ-4260239

**Instalador JEE de Forms**

**Forms: base JEE**

* El componente de servicio web de AEM Forms Workbench no puede invocar un servicio web, que requiere autenticación SSL bidireccional. NPR-29485: revisión para CQ-4246794
* El administrador de configuración JEE de AEM Forms no funciona con varias tarjetas NIC. NPR-29236: revisión para CQ-4268598
* AEM error de inicio procedente de GemFire: java.lang.IllegalStateException: Solo se puede establecer una conexión AdminDistributedSystem al mismo tiempo. NPR-29524: revisión para CQ-4266295
* NoClassDefFoundError debido a que la versión jar no coincide. NPR-28834: revisión para NPR-28834

**Forms: servicios de documentos**

* El archivo PDF/A no válido se notifica como PDF/A válido mediante la operación isPDFA. NPR-29076: revisión para CQ-4261541
* El PDF no puede convertir al PDF/A-1b si el campo Formulario no tiene diccionario de aspecto. NPR-29534: revisión para CQ-4269618
* La conversión de PDF/A del PDF producido con el servicio de salida no pasa la validación con Acrobat DC. NPR-29647: revisión para CQ-4270448
* El paquete POI de Apache falla con una excepción. NPR-27861, NPR-28048: revisión para CQ-4245898, CQ-4244778

**Forms: Designer**

* Se ha agregado compatibilidad con PDF/UA a los formularios XML Forms Architecture (XFA) generados con Designer y Output Service. NPR-23022

**Forms: flujo de trabajo**

* Los envíos del espacio de trabajo fallan con el carácter Umlaut. NPR-29087: revisión para CQ-4263172

**Paquetes de funciones incluidos**

**Recursos**

* Se habilitó la compatibilidad con el administrador de varios sitios para los recursos. Para obtener más información, consulte [Reutilizar recursos con MSM para Assets](/help/assets/reuse-assets-using-msm.md). NPR-26450: revisión para CQ-4259922

**Paquetes de contenido y paquetes OSGI incluidos**

Los siguientes documentos de texto enumeran los paquetes OSGI y los paquetes de contenido incluidos en el CFP.

Lista de paquetes OSGi incluidos en AEM 6.4.5.0

[Obtener archivo](assets/6.4.5.0_bundles.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.5.0

[Obtener archivo](assets/6.4.5.0_OSGI.txt)

#### AEM 6.4.4.0 {#experience-manager-6440}

AEM 6.4.4.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas desde la disponibilidad general de AEM 6.4 in **Abril de 2018.**

También es acumulativo, lo que significa que 6.4.4.0 incluye todos los paquetes de servicio AEM 6.4 que se lanzaron antes.

Algunos de los aspectos destacados de AEM 6.4.4.0 son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.11.
* Se ha agregado compatibilidad con la versión del servicio de almacenamiento en caché para evitar solicitudes HTTP de versión de servicio frecuentes.
* Se ha agregado compatibilidad para eliminar etiquetas automáticas.
* Se ha implementado el desplazamiento sin fin para el asistente de catálogo.
* Capacidad respaldada para restringir permisos según los sitios de la comunidad.
* Correcciones de rendimiento (almacenamiento en caché, ejecución asíncrona, lista de exclusión) para la comprobación de estado del contenido de Sling Granite.
* Se ha agregado el botón de selección de recursos al cuadro de diálogo de miniaturas de página.
* Se ha añadido una nueva propiedad para permitir el posicionamiento de la información sobre herramientas en los campos.
* Se ha mejorado la compatibilidad de ColorPicker dentro del campo Multifield.
* Se ha añadido una comprobación para ignorar los valores vacíos de los campos múltiples de entrada numérica en las clientlibs del fragmento de contenido.
* Se ha habilitado la compatibilidad con la API de texto del traductor de Microsoft v3.

**Recursos**

* Migración de la integración ACP y de existencias a AEM 6.4.4.0 NPR-27632
* Publicar posteriormente una carpeta de recursos vacía con subcarpetas hace que desaparezcan las subcarpetas. NPR-27558: revisión para CQ-4254701
* La adición de la propiedad String\[\] única sin espacio entre nombres provoca una reescritura XMP incompleta. NPR-26805: revisión para CQ-4254142
* Después de rasterizar el pdf de entrada, el resultado producido tiene imágenes faltantes. NPR-27929: revisión para CTG-4150481
* El Asistente para mover recursos muestra un recuento incorrecto de páginas de referencia para páginas publicadas. NPR-27833: revisión para CQ-4258014
* AssetPicker busca solo la primera etiqueta para filtrar el resultado cuando filtra con etiquetas. NPR-27778: revisión para CQ-4257705
* AEM controlador de PDF OOTB se atasca en el PDF de procesamiento con caracteres extranjeros. NPR-28778: revisión para CQ-4254234
* Cuando un archivo CSV tiene un valor que está separado por comas en una sola columna, AEM editor CSV no escapa a la coma y la trata como una columna separada. NPR-28801: revisión para CQ-4261694
* Problema con el Editor de esquemas de metadatos al utilizar el Explorador de rutas para seleccionar datos. NPR-28674: revisión para CQ-4263005
* Se procesan demasiados recursos en el servicio de contenido inteligente, lo que da como resultado una gran cantidad de tiempo para completar el proceso de etiquetado periódico. NPR-28640: revisión para CQ-4262661, CQ-4262644, CQ-4263234
* Las acciones de escritorio no funcionan para los resultados de Omnisearch desde `aem/start.html` página. NPR-27242: revisión para CQ-4248176
* La API de recursos no permite la carga de archivos > 2 GB, lo que provoca un error de carga. NPR-27629: revisión para Granite-23590
* Los metadatos no se guardan en el recurso descargado en el primer intento, en caso de que Dynamic Media esté habilitado en la instancia. NPR-28233: revisión para CQ-4260759
* La resolución del servicio no se cierra en la configuración del SiteCatalyst. NPR-28015: revisión para CQ-4259397
* Mover recursos en DAM no resulta en un movimiento similar en Scene7 (configuración p2p). NPR-28313: revisión para CQ-4261091

**Sitios**

* (IU clásica) En la lista de lanzamiento aparece una fracción de Live Copies. NPR-28598, NPR-28574: revisión para CQ-4263410
* LiveRelationshipManagerImpl lanza excepciones cuando cq:master está vacío o no es válido. NPR-28590: revisión para CQ-4263115
* El flujo de trabajo predeterminado &quot;Solicitud de eliminación&quot; no elimina las páginas correctamente. NPR-28668: revisión para CQ-4263195
* La interfaz de usuario de estado de relación no muestra los valores adecuados de año o marca de hora para los campos relacionados con el selector de fecha de coral. NPR-28666: revisión para CQ-4263661
* Ejecución de scripts en sitios múltiples (XSS) en SuggestionHandler para 6.4. NPR-28693: Revisión para CQ-4253821
* Mover la carpeta desde siteadmin termina sin memoria y hace que AEM no esté disponible. NPR-28346: revisión para CQ-4261398
* Las configuraciones de implementación de MSM LiveCopy se pierden después de la actualización. NPR-28311: revisión para CQ-4258705
* No se puede desplazar más allá de las 40 configuraciones de modelo. NPR-27640: revisión para CQ-4239166
* El uso de SynthResource como referencia genera una Null Pointer Exception y bloquea el movimiento de las páginas.  NPR-27576: revisión para CQ-4258262
* PushOnModify no funciona en la eliminación de instancias actualizadas de 6.1 a 6.4. NPR-28108: revisión para CQ-4259833
* (IU clásica) Falta el botón Cancelar herencia y el componente se puede editar en una página de Live Copy. NPR-28256: revisión para CQ-4260161
* OakState0001: Conflictos no resueltos en la implementación. NPR-27982: revisión para CQ-4259548
* Al copiar/pegar una estructura que contenga referencias de SynthResource, el proceso termina con un error 500. NPR-27709: revisión para CQ-4259179
* No se pueden finalizar los flujos de trabajo en ejecución cuando se activan las cargas útiles. NPR-27672: revisión para CQ-4258520
* El lanzamiento muestra rutas de lanzamiento duplicadas después de la actualización de 6.1 a 6.4. NPR-27845: Revisión para CQ-4259487
* Integre el modal del selector de recursos de dam en el componente de miniaturas de página. NPR-28131: revisión para CQ-108042
* (IU clásica) No se pueden abrir los cuadros de diálogo con el widget Etiquetas . NPR-28575: revisión para CQ-4262680
* La carga de archivos de varios campos no muestra la zona de colocación. NPR-28676: revisión para CQ-4263516
* Error “Valor del selector de recursión no válido” al migrar un componente de AEM 6.0 a AEM 6.2. NPR-28609: revisión para CQ-4241258
* El Editor de texto enriquecido en el cuadro de diálogo parpadea cuando la ventana emergente de un complemento es superior al área de texto, por lo tanto, bloquea cualquier creación posterior. NPR-27579: revisión para CQ-4257440
* (IU clásica) cq:action editannotate no funciona. NPR-28232: revisión para CQ-4257703
* La eliminación de etiquetas del panel de búsqueda de recursos del editor de páginas del filtro de etiquetas no actualiza la lista correctamente. NPR-27983: revisión para CQ-4245567
* Si los valores de los números de varios campos están vacíos, al hacer clic en Guardar se generará un mensaje de carga infinita sin que realmente se complete.  NPR-28400, NPR-28393: revisión para CQ-4244058, CQ-4244349
* Con permiso de lectura, los usuarios/grupos no pueden seleccionar un XF y no tienen opción de ver el XF y sus propiedades de página. NPR-28341: revisión para CQ-4260412
* Los datos JSON recibidos de Target tienen varios caracteres de escape que provocan que la página de la aplicación se rompa. NPR-28318: revisión para CQ-4252043
* No se puede editar ningún componente después de instalar AEM 6.4.3. NPR-28125: Revisión para CQ-4261216
* La eliminación de todas las etiquetas de un campo de etiqueta no persiste en un fragmento de contenido estructurado. NPR-28133: revisión para CQ-4247241
* Al editar las propiedades &quot;jcr:lastmodifiedby&quot; y &quot;jcr:lastmodified&quot; de un fragmento de contenido, los valores se actualizan sin que el usuario realice ningún cambio. NPR-27847: revisión para CQ-4257138
* Las versiones de los fragmentos de contenido comparan las mejoras de diferencias para AEM 6.4. NPR-27764
* Si no hay ninguna cq:allowedTemplates definida en /content/experience-fragments y allowedPaths se utiliza en la plantilla Experience Fragement, se produce un error cuando se mueve/copia Experience Fragement. NPR-27487: revisión para CQ-4257489
* El botón Crear aparece al actualizar para el nuevo usuario. NPR-27335: revisión para CQ-4255360
* Al intentar mover una página publicada, el recuento &quot;Páginas de referencia&quot; que aparece en la primera página del asistente &quot;Mover página&quot; es incorrecto. NPR-28111: revisión para CQ-4259663
* (IU táctil) El carril de referencias no muestra los vínculos entrantes. NPR-28529: revisión para CQ-4262306
* No se puede editar ningún componente y propiedades de página después de instalar AEM 6.4.3. NPR-27998: Revisión para CQ-4261216, CQ-4260441
* Migrar contexthub a jquery 3. NPR-28397: revisión para GRANITE-19902

**Comercio**

* No se puede seleccionar el catálogo si hay más de 20 catálogos en una carpeta. NPR-27649: revisión para CQ-4258119
* Los asistentes de comercio y las vistas de propiedades se rompen debido a la falta de header.referer . Revisión para CQ-4261122

**Campaign: Segmentación**

* com.day.cq.personalization.impl.TeaserResourceEventHandler entra en un bucle infinito y provoca actualizaciones en los nodos en instancias publicadas. Revisión para CQ-4263096

**Replicación**

* Error al crear contenido de replicación com.day.cq.replication.AccessDeniedException. NPR-28314: revisión para CQ-4261401
* Fuga de sesión cuando el ID del agente de usuario está establecido en admin en el agente de replicación. NPR-28220: revisión para CQ-4255517

**DAM: Creative Cloud**

* API HTTP de backport para encontrar imágenes similares dentro de AEM Assets. Revisión para CQ-4254091
* Mejorar la API ACP para permitir que los resultados de una consulta se limiten a los miembros de una colección. Revisión para CQ-4258708

**DAM: formatos**

* Una vez activada la exportación de metadatos, la página se redirige a una página 404. Revisión para CQ-4262447

**DAM: General**

* (Integración de Adobe Stock) El modo de error del servidor se muestra con un error de Oauth en el archivo error.log. Revisión para CQ-4260406
* La integración de Adobe Stock no funciona si 6.4.4 se aplica a 6.4.3. Revisión para CQ-4266009
* Falta el enlace al modelo CF incluso después de aplicar el parche SP3. Revisión para CQ-4259029

**Plataforma**

* (IU clásica) El botón de edición no está disponible en el componente Informe base después de actualizar a la versión 6.4.2. NPR-28560: Revisión para CQ-4262825
* Cuando se utiliza una consulta que combina property.operation=like y property.depth, termina en InvalidQueryException. NPR-28570: revisión para CQ-4262652
* Error interno del servidor cuando el nodo de idioma recién agregado se elimina del nodo de idioma superpuesto. NPR-28661: revisión para CQ-4239194
* Null Pointer Exception en stderr.log en el subproceso sling-oak-1 en inicios aleatorios. NPR-28665: revisión para CQ-4237845

**Felix**

* webconsole.plugins.memoryusage causa un bloqueo en la actualización. NPR-27895: revisión para GRANITE-20715

**Granite**

* La comprobación de estado de acceso al contenido de Sling realiza una validación excesiva y larga de /libs para la ruta de búsqueda de resolución de recursos personalizada. NPR-28113: revisión para GRANITE-23529

**Administración de fragmentos de contenido**

* Mejoras de uso y paridad de características con Recursos para fragmentos de contenido. Revisión para CQ-4253883

**Comunidades**

* Actualice el bootstrap vulnerable a las bibliotecas 3.4 y ckeditor a la 4.5.11. NPR-28490: Revisión para CQ-4257511
* La cancelación de los modos de edición no restaura el archivo adjunto eliminado. NPR-27902: revisión para CQ-4255150
* El componente en nombre del cuadro solo debe ser visible para los miembros privilegiados. NPR-27900: revisión para CQ-4251235
* Agregue rep:cache a Nodos ignorables en el Receptor de sincronización de usuarios de AEM Communities en las instancias de publicación. NPR-27842: revisión para CQ-4247234
* El cuadro de búsqueda muestra el carácter de escape en la interfaz de usuario. NPR-27838: revisión para CQ-4259757
* Se genera un error al buscar caracteres especiales como ( , +,? en la búsqueda rápida. NPR-28213: revisión para CQ-4260969
* Cree un grupo &quot;administradores específicos de la comunidad&quot; para que los usuarios puedan editar y crear el sitio de la comunidad correspondiente. NPR-27731
* Se ha agregado lógica para el evento de teclado para abrir vídeo. NPR-27726: revisión para CQ-4254026
* Se ha habilitado la navegación mediante el teclado para los componentes de habilitación de AEM Communities en la publicación. NPR-27728: revisión para CQ-4254028
* Se ha añadido una etiqueta aria para el botón de vista de lista y de tarjeta. NPR-27727: revisión para CQ-4254027
* Gestión de sesiones de resolución de recursos abiertos en Social- Communities. NPR-27721: revisión para CQ-4258714

**Traducción**

* Proporciona compatibilidad con la API de texto del traductor de Microsoft v3. NPR-28366: revisión para CQ-4249755
* jcr:language y cq:language no se actualizan automáticamente en el idioma traducido. NPR-28338: revisión para CQ-4256046
* Las referencias cíclicas provocan StackOverflowError al crear copia de idioma. NPR-27596: revisión para CQ-4255621
* En un proyecto de traducción en varios idiomas, al hacer clic en guardar y cerrar los resultados en páginas posteriores agregadas al proyecto, se crean nuevos proyectos en lugar de crear nuevos trabajos de traducción en un proyecto existente. NPR-28219, NPR-28236: revisión para CQ-4261276, CQ-4260731
* Cadena de error demasiado larga al añadir fragmento de contenido con datos masivos debido a la limitación en el número de caracteres permitidos. NPR-28722: revisión para CQ-4262362

**Social**

* El comentario publicado en la página siguiente se resalta con amarillo cada vez que se publica un comentario nuevo. Revisión para CQ-4261359
* No se pueden eliminar comentarios en el contenido generado por el usuario mediante API. NPR-28075: revisión para CQ-4261135
* AbstractNotificationOperationService causa ClassCastException. Revisión para CQ-4260456
* Elimine la referencia a la nube del Modelo de referencia de objetos de contenido compartido (SCORM) en el reproductor. Revisión para CQ-4260779

**IU: bases**

* La función &quot;Caché de salida del sistema de archivos&quot; integrada en el HTML Client Library Manager rompe la función &quot;debugClientLibs&quot; para scripts compilados como archivos LESS. NPR-27249: revisión para Granite-23313
* El número de recursos que se muestran cuando se activa el modo de depuración es siempre 1 y se producen muchos errores de JS en la consola del explorador.  NPR-27575: revisión para GRANITE-23750
* Guardar y cerrar en las propiedades de la página no vuelve a la página adecuada en AEM GUERRA con Tomcat. NPR-27566: revisión para GRANITE-23671

**Integración**

* `com.day.cq.personalization.impl.TeaserResourceEventHandler` entra en un bucle infinito y provoca actualizaciones en los nodos en instancias de publicación. NPR-28561: revisión para CQ-4263096
* Las acciones cq  :actions no se toman en consideración para un componente destinatario. NPR-27616: revisión para CQ-4257497
* La cancelación heredada de LiveCopy no funciona correctamente en contenedores de destino. NPR-28129: revisión para CQ-4259813
* (Configuraciones de Cloud Service) Se debe eliminar la casilla “heredada de” que aparece en el nivel raíz. NPR-27856: revisión para CQ-4259676

**Sling**

* Actualización de la API 1.3.8 de los modelos de Sling, Impl 1.4.10. NPR-27636: Revisión para GRANITE-23537

**OAK: Persistencia del segmento**

* SegmentBufferWriter no se descarga después de OnRC. NPR-27464

**Proyectos**

* El proyecto de traducción en varios idiomas no está creando trabajos en varios idiomas para los usuarios que no forman parte del grupo de administradores. NPR-28508: revisión para CQ-4262023
* ProjectTaskListServlet está filtrando un ResourceResolver cada vez que se llama a getTaskRenderers durante el inicio del servicio. NPR-27590: revisión para CQ-4258011
* Si un directorio tiene más subdirectorios que el tamaño de página y el orden es por fecha o tamaño, un error evita moverse más allá de la primera página. NPR-28867: revisión para CQ-4265039
* Correcciones de scripts en sitios múltiples (XSS) de backport en visores DAM. NPR-28106: revisión para CQ-4253215
* Los administradores del proyecto no pueden agregar páginas al proyecto de traducción porque el vínculo para agregar nuevas páginas al proyecto de traducción no está visible. Revisión para CQ-4266334

**Flujo de trabajo**

* Cuando se abre el cuadro de diálogo de elemento de trabajo completo en la notificación de flujo de trabajo que tiene un campo Etiqueta , al hacer clic en la marca cruzada se añade una propiedad Etiqueta . NPR-28304: revisión para CQ-4261321
* El botón Alternar selección de usuario del cuadro de diálogo Reasignar tarea no funciona. NPR-28963: revisión para CQ-4264206

**Forms**

Los aspectos destacados de los formularios de AEM 6.4.4.0 son:

* Se ha agregado compatibilidad para registrar API de seguridad de documentos para firmar y certificar como transacciones.

**Paquete de complemento de Forms**

**Integración de Adobe Sign**

* AEM 6.4 Forms Client SDK no contiene ningún paquete adobesign-recipient. NPR-27735: revisión para CQ-4259372

**Formularios adaptables**

* Cuando se crea un formulario adaptable Wan con una plantilla en blanco, los clientes no pueden crear paneles secundarios en el panel raíz del formulario. NPR-28758: revisión para CQ-4264157
* Cuando el valor del campo de año del componente de fecha es 9999, la secuencia de comandos de validación falla. NPR-28580: revisión para CQ-4262620
* Cuando se crea un formulario adaptable con una plantilla en blanco, los clientes no pueden crear paneles secundarios en el panel raíz del formulario. NPR-28758: revisión para CQ-4264157
* No se puede establecer el valor entre los campos de fragmentos cargados a medida de un formulario adaptable. NPR-27758: revisión para CQ-4259703
* El formulario adaptable no utiliza el Editor de texto enriquecido, pero carga sus bibliotecas.  NPR-27759: revisión para CQ-4259193
* El redireccionamiento a URL no funciona para formularios adaptables incorporados en una página de AEM Sites. NPR-27620: revisión para CQ-4239287
* No se puede establecer el valor entre los campos de fragmentos cargados a medida de un formulario adaptable. NPR-28320: revisión para CQ-4262345
* El formulario adaptable no utiliza el Editor de texto enriquecido, pero carga sus bibliotecas.  NPR-28001: revisión para CQ-4259703, CQ-4259193
* La firma manuscrita no funciona para la aplicación AEM Forms que se ejecuta en Apple iOS 12.1. NPR-28497: Revisión para CQ-4261765
* Enviar acción usando problemas de creación de &quot;Forms Workflow&quot; Classic en 6.4. Revisión para CQ-4252740
* Error al controlar la eliminación del almacenamiento de bloques y tmp. NPR-28806: revisión para CQ-4264441

**Forms: administración de correspondencia**

* La interfaz de usuario del agente no conserva el tamaño original de la imagen. NPR-28800: revisión para CQ-4259767
* Interfaz de usuario de CCR/agente: Las etiquetas de los campos Fecha cambiaron en la pestaña Datos . Revisión para CQ-4255499

**Forms: informes de transacciones**

* Se agregó compatibilidad para contar usando firmas digitales o certificando un documento como transacciones facturables. NPR-28495: revisión para CQ-4260236
* Se ha añadido la firma digital y la certificación a la API facturable. Revisión para CQ-4260236

**Administración de Forms**

Se ha agregado compatibilidad para reemplazar el uso de la biblioteca de cliente de controladores por guiones bajos en el asistente de revisión inicial de Forms Manager y el asistente de traslado de recursos. NPR-27643: revisión para CQ-4246536.
Un paquete permanece en estado de instalación después de instalar el paquete Forms Management en la rama release/640. La revisión para CQ-4265410 Forms enviada con archivos adjuntos no aparece en el flujo de trabajo con la acción de envío &quot;Invocar el flujo de trabajo de AEM Forms&quot; y habilitar el envío del portal activada . Revisión para CQ-4263110

**Forms: integración back-end**

* No se pueden realizar pruebas del preprocesador y el envío personalizado previo/posterior mediante Client SDK, revisión para CQ-4238469

**Instalador JEE de Forms**

**Forms: seguridad de documentos**

* Al utilizar el servicio updatepolicy, no se produce el error de objeto no se puede invertir. NPR-28751: revisión para CQ-4252287
* La compilación de la firma falla con la versión anterior de commons-pkg. Revisión para CQ-4265535

**Forms: base JEE**

* Cuando AEM Forms se integra en IBM WebSphere, se produce un error al crear un modelo de datos de formulario basado en SOAP. NPR-27923: revisión para CQ-4251134
* La herramienta SRT del Generador de PDF no detecta la versión instalada de Adobe Acrobat. NPR-27971

**Forms: Designer**

* Algunas imágenes JPEG de una plantilla XDP no se representan correctamente.  NPR-26702: revisión para LC-3917457

**Forms: flujo de trabajo**

* HTML5 Forms con proceso de envío predeterminado en an.lca no funciona en JBoss 7. NPR-28675: revisión para CQ-4243928
* No se pueden enviar PDF forms en HTML Workspace. NPR-28058: revisión para CQ-4260373
* Los datos del cliente se imprimen en los registros de información mediante el Forms Workflow de servicio Invocar FDM. Revisión para CQ-4260385

**Paquetes de funciones incluidos**

**Sitios**

* El control de versiones de los fragmentos de contenido compara las mejoras de diferencia para AEM 6.4. NPR-26760: FP para CQ-4248839
* Mejoras en la variación de los fragmentos de contenido para AEM 6.4. NPR-27866: FP para CQ-4248839
* Función habilitada en la configuración OSGI **Indicador de característica de retirada de flujo de trabajo AEM**. La acción de extracción debe finalizar la instancia del flujo de trabajo después de establecer el indicador . NPR-26451: revisión para CQ-4259090

**Plataforma**

* Extracción de faceta del generador de consultas mejorada aprovecha la API de Oak para 6.4. NPR-26674: FP para CQ-4230337

**Paquetes de contenido y paquetes OSGI incluidos**

Los siguientes documentos de texto enumeran los paquetes OSGI y los paquetes de contenido incluidos en el CFP.

Lista de paquetes OSGi incluidos en AEM 6.4.4.0

[Obtener archivo](assets/bundles_6_4_4_0.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.4.0

[Obtener archivo](assets/osgi_package_6_440.txt)

#### AEM 6.4.3.0 {#experience-manager-6430}

AEM 6.4.3.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas tras la disponibilidad general de AEM 6.4 en abril de 2018.

También es acumulativo, lo que significa que 6.4.3.0 incluye todos los paquetes de servicio AEM 6.4 que se lanzaron antes.

Algunos de los aspectos destacados de AEM 6.4.3.0 son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.9.
* Se ha agregado compatibilidad con la propiedad allowedPaths en las plantillas de formularios adaptables.
* Búsqueda mejorada basada en paneles para Recursos en AEM
* Correcciones de scripts en sitios múltiples (XSS) en la página Inicio de sesión.
* Se ha mejorado la instrumentación de la interfaz de usuario.
* Mejoras en la gestión de FormData.
* Se ha mejorado el manejo de la asignación de nombres de elementos dentro de un campo múltiple.
* Se ha mejorado el manejo de los elementos de marcador de posición (vista de tarjeta y vista de lista) durante la selección.
* Se ha añadido la autenticación IMS de Adobe y la compatibilidad con Admin Console para Managed Services.

**Recursos**

* El flujo de trabajo de DAM Update Asset no extrae referencias de archivos INDD si la opción ID Decouple está activada. NPR-26243; Revisión para CQ-4250933
* El mensaje de éxito no se muestra cuando se publican recursos con el Editor por lotes de recursos. NPR-26252; Revisión para CQ-4251688.
* Una vez visto un recurso desde un resultado de búsqueda, si hace clic en el botón Atrás del explorador, se generará un mensaje de error &quot;Solicitud incorrecta&quot; con un código de error 400. NPR 26578; Revisión para CQ-4253741
* Los metadatos de recursos muestran un error de espacio de nombres no válido después de instalar un Service Pack. NPR-22341; Quickfix para CQ-4237202
* La opción para reordenar carpetas y fragmentos de contenido en la vista de lista no se muestra para las carpetas aplicables. NPR-27153; Revisión para CQ-4255873
* Los usuarios no pueden agregar recursos a una nueva colección, ya que el resultado es un mensaje de error con una imagen rota en el cuadro de diálogo emergente de error. NPR-22431; Revisión para CQ-4237086
* La lista desplegable en cascada no es compatible con las listas desplegables dinámicas. NPR-27043; Revisión para CQ-4252564
* Si los usuarios establecen un valor no predeterminado para la &quot;carpeta raíz de la empresa&quot; en la configuración de nube de DMS7, el ajuste preestablecido de visor no funciona como se espera. NPR-26360; Revisión para CQ-4249505
* Los informes de recursos fallan en instancias con un gran número de activos. NPR-27278; Revisión para CQ-4256748
* Las subcarpetas no heredan el perfil de imagen SmartCrop de la carpeta principal. NPR-27197; Revisión para CQ-4256273
* Cuando se habilita la integración con Dynamic Media, se modifican algunas propiedades de metadatos de Assets. No se muestran los atributos de ancho, alto y ubicación. NPR-27203; Revisión para CQ-4256258
* Dynamic Media no utiliza el proxy configurado para algunos tipos de recursos. NPR-25211; Revisión para CQ-4244871
* La página Editor de metadatos contiene una excepción de puntero nulo para un parámetro de elemento no válido. NPR-26169; Revisión para CQ-4241368.
* Si una lista desplegable tiene una regla de opciones y una regla requerida aplicada, la regla requerida no se puede satisfacer en el editor de metadatos. NPR-27479; Revisión de CQ-4251428

**Sitios**

* Un usuario puede controlar las funciones del editor de texto enriquecido en el modo de pantalla completa en línea mediante políticas de contenido, pero no puede controlar las funciones del editor de texto enriquecido Editar cuadro de diálogo con políticas de contenido. NPR-26750: revisión para CQ-4241130
* El editor de texto enriquecido se vuelve inutilizable cuando se cambia de pantalla completa a diálogo flotante. La vista flotante contiene dos editores de texto enriquecido. NPR-25589: revisión para CQ-4206008
* Cuando se pulsa la tecla de retorno (tecla Intro) en un campo de texto, el editor de texto enriquecido cambia al modo de pantalla completa. NPR-26204: revisión para CQ-4245893
* El complemento Lista del editor de texto enriquecido está deshabilitado automáticamente y no permite modificaciones. NPR-26507: revisión para CQ-4239387
* Cuando se añade un carácter especial a la ventana del editor de texto enriquecido, la ventana se desplaza hacia arriba. NPR-26435: revisión para CQ-4249869
* Preguntas de almacenamiento en caché de ClientContext segment.js frente a preguntas que no están almacenadas en caché. NPR-26622: revisión para CQ-4253486
* Cuando se activa una regla secundaria de la instancia de autor a la instancia de publicación, la instancia de publicación deja de funcionar. NPR-26601: revisión para CQ-4253588
* Cuando el editor de texto enriquecido se combina con varios campos, se produce el error Uncaught TypeError: fieldAPI.getName is not a function at foundation.js. NPR-27146: revisión para CQ-4253155
* La integración de Salesforce no puede utilizar la configuración proxy. NPR-27244: revisión para CQ-4245300
* Cuando se programa una página para su activación mediante la opción Administrar publicación para una fecha posterior y se cambia a la vista de lista, falta el icono de calendario. NPR-26974: revisión para CQ-4239206
* Los usuarios no pueden editar permisos de grupos de usuarios cerrados en las propiedades de página. NPR-27138: Revisión para CQ-4256089 No se pueden editar las etiquetas a través del etiquetado. NPR-26957: revisión para CQ-4254858
* Cuando se mueve una etiqueta a la que se hace referencia desde un modelo de fragmento de contenido estructurado, las referencias existentes a la etiqueta dentro de un fragmento de contenido no se actualizan. Esto sucede en la pantalla de edición del modelo de fragmento de contenido. NPR-26776: revisión para CQ-4251805
* Cuando crea y promociona un lanzamiento con varias páginas, se crean varias versiones para cada página. NPR-26917: revisión para CQ-4254663
* AEM siteadmin no gestiona las rutas escritas en la barra de direcciones del explorador. NPR-26780: revisión para CQ-4254097
* Cuando una página se mueve a una nueva ubicación sin cambiarle el nombre, se pierde el historial de versiones de la página. NPR-26706: revisión para CQ-4254025
* Las direcciones URL en el editor de administración de fragmentos de experiencia no permiten superposiciones. NPR-26319: revisión para CQ-4252156
* Cuando se crea una página con una plantilla que contiene fragmento de experiencia vacío y se publica, la página no se abre y se produce un error DefaultSlingScript. NPR-26305: revisión para CQ-4252460
* Cuando se utiliza el uso de datos de forma remota con clases con un nombre idéntico, se produce un código no compatible. NPR-27282: revisión para Sling-7581
* Después de la instalación del SP de actualización, los sitios tienen una configuración de lanzamiento de modelo en blanco. NPR-27609: revisión para CQ-4257078

**DAM: Brand Portal**

* Los predicados de etiquetas no se publican cuando el formulario de esquema de metadatos se publica en Brand Portal. Revisión para CQ-4256218
* Cuando se publica una carpeta de tercer nivel de AEM a Brand Portal, sin publicar las carpetas principales, el nombre de la carpeta cambia. Revisión para CQ-4255423
* El predicado del explorador de rutas se publica de AEM Assets en Brand Portal según lo esperado. Sin embargo, la ruta publicada en BP permanece /content/dam, que debe actualizarse. Revisión para CQ-4256240

**DAM: Creative Cloud**

* Falta el icono &quot;Buscar recursos de Adobe&quot; en la navegación principal de AEM. Revisión para CQ-4254343

**DAM: Cliente DM**

* Después de ingerir vídeos en una carpeta asociada con el perfil de procesamiento de vídeo AVS, la ventana del explorador se actualiza una y otra vez. Revisión para CQ-4253563
* YouTube Publish falla al usar una etiqueta ad hoc que incluya caracteres en mayúsculas. Revisión para CQ-4252477
* Cuando se crea una anotación en un recurso como un PDF, la interfaz de usuario inicia un bucle infinito de actualización de la página. NPR-27052: revisión para CQ-4255396

**DAM - Servicios DM**

* Dynamic Media no utiliza el proxy configurado para algunos tipos de recursos. NPR-10727; Revisión para CQ-4244871

**Plataforma**

* Problemas de rendimiento con org.apache.sling.i18n. NPR-26812: revisión para SLING-7543
* No se pueden ver las propiedades del nodo cuando el XML de entrada tiene formato y está implementado. NPR-26198: revisión para CQ-4250448
* IndexOutOfBoundException en ResourceProviderTracker. NPR-26968: revisión para GRANITE-23310
* La consola JMX acumula numerosas sesiones de administración y se abre una nueva sesión cada 5 minutos. NPR-26958: revisión para CQ-4251090
* Después de actualizar de 6.2 a 6.4, el archivo de registro muestra la traza de la pila para la resolución de recursos sin cerrar com.adobe.granite.repository.hc.impl.content.sling.SlingContentHealthCheck. NPR-26176: revisión para Granite-21734
* Cuando se configura un agente de vaciado de Dispatcher listo para usar para actualizar alias, la operación falla con un StackOverflowError. NPR-26373: revisión para CQ-4242928
* La replicación utiliza un token OAuth caducado hasta que falla. NPR-25894
* Página restringida (página de grupo de usuarios cerrado) con sling: alias no redirige al usuario a la página de inicio de sesión. NPR-25715: Revisión para Granite=22263
* Al publicar etiquetas, no se muestra ninguna actividad en la interfaz de usuario. Revisión para CQ-4255961
* No se pueden editar las etiquetas en la IU clásica. Revisión para CQ-4258697
* Se ha actualizado org.apache.felix.http.bridge a la versión 4.0.4. NPR-27038: Backport para Granite - 23334
* Los registros de actividades del administrador de paquetes deben extraerse en un archivo de registro independiente. NPR-27323: revisión para Granite-14866
* El validador de paquetes no informa de las superposiciones en CFP. NPR-27119: revisión para GRANITE-22825

**Proyectos**

* La API ACP no gestiona correctamente la paginación solo con elementos secundarios de subdirectorio. NPR-27617: revisión para CQ-4258639

**OAK**

* No se puede iniciar sesión en el repositorio después de instalar AEM 6.4 Service Pack 2. NPR-27171: revisión para Granite-23317

**Replicación**

* El registro de auditoría permanece abierto con sesiones activas que siguen aumentando constantemente con ~750 cada día. NPR-27062: revisión para CQ-4241350

**Comunidades**

* Las publicaciones y las respuestas del foro se agregan al principio de la segunda página y, cuando se actualizan, la publicación se mueve a la ubicación correcta en la parte superior de la primera página. NPR-27342: revisión para CQ-4247338
* Los vínculos a todos los recursos colocan la ruta de contexto (/aempublish) después de desplazarse. NPR-26982: revisión para CQ-4254345
* Los grupos añadidos no están visibles en el menú desplegable Community Manager, Community Moderators y Privileged Member que hay en la edición de un sitio publicado. NPR-27190: revisión para CQ-4258574
* Solo se muestran 10 grupos en la página de recursos de habilitación aunque la paginación esté habilitada para la lista de grupos. NPR-26934: revisión para CQ-4252985
* La opción para habilitar/deshabilitar la búsqueda de anuncios programados en el componente de diario se proporciona en ConfigMgr y el trabajo SearchScheduledPosts está optimizado. NPR-26923: revisión para CQ-4250463
* La búsqueda por palabras clave en la dirección no funciona en la página de componentes del calendario cuando AEM comunidad está configurada para trabajar con DSRP. NPR-26737: revisión para CQ-4258493
* Se ha implementado un vínculo directo al comentario en lugar de la publicación principal en los detalles de un comentario, para obtener recursos de habilitación y interfaz de usuario de moderación. NPR-26704: revisión para CQ-4251381
* El contenido moderado mediante selección múltiple en la consola de moderación no aparece en el flujo de actividad. NPR-26695: revisión para CQ-4253244
* La búsqueda con nombre y apellidos en el campo Para de Mensajería de comunidades no devuelve el resultado esperado. NPR-26385: revisión para CQ-4248673
* Se ha observado un error al cargar un archivo adjunto que no sea una imagen (por ejemplo, .pdf) en el foro. NPR-27360: revisión para CQ-4257753
* Desanclar o cancelar la función de una publicación de foro no funciona si Author-Publish está configurado con MySQL DSRP. NPR-26125; Revisión para CQ-4251520
* Los componentes de colección (foros, blogs, calendario, ideación, control de calidad) ahora tienen una propiedad en el cuadro de diálogo de componentes para habilitar/deshabilitar &quot;Bloquear UGC en modo de edición de autor&quot;, de modo que se permita/deniegue la carga UGC en modo de edición WCM. NPR-26978: revisión para CQ-4248161
* La búsqueda de etiquetas no funciona para términos de búsqueda localizados. NPR-26171: revisión para CQ-4249926
* El botón Atrás omite una página en la búsqueda en el foro. NPR-26950: revisión para CQ-4254804
* AEM instancia que se ejecuta en el puerto Http predeterminado (80) no puede alcanzar el archivo imsmanifest.xml. NPR-27173: revisión para CQ-4252211
* Desmarcar comentario como respuesta para QnA no funciona si AEM Communities está configurado con DSRP. NPR-26247: revisión para CQ-4252232
* No se puede llamar al almacenamiento de Adobe: Error 414: URI de GET larga observada cuando los usuarios buscan /content/community-components/en/search.html y seleccionan el campo de autor como uno de los filtros para ese término de búsqueda. NPR-26643: revisión para CQ-4251303
* El valor desplegable de DataCenterURL en la configuración ASRP se cambia de Dallas a Virginia (para VA6). NPR-26936: revisión para CQ-4254434
* Los caracteres especiales en la búsqueda en el foro devuelven errores o no arrojan resultados. NPR-26930: revisión para CQ-4247744
* El número que se muestra para &quot;Número de resultados&quot; en la búsqueda en el foro utiliza un delimitador incorrecto para las configuraciones regionales de inglés y alemán. NPR-27050: revisión para CQ-4248939
* Las notificaciones no leídas no aumentan más allá de 21. NPR-26946, NPR-27480: revisión para CQ-4252829, CQ-4256939
* La paginación en la sección de comentarios de cualquier componente hace que los usuarios se desplacen hacia arriba para ver el contenido de la página al llegar a una página mediante la paginación. NPR-27032: revisión para CQ-4251228
* La carpeta del sitio de la comunidad no se puede hacer clic en la imagen en miniatura cuando se visualiza desde Admin Console en la instancia de autor de AEM. NPR-26986: revisión para CQ-4254036
* La opción &quot;marcar todo leído&quot; marca solo las 10 primeras notificaciones como leídas y otras permanecen sin leer hasta que se actualiza la página. NPR-27037: revisión para CQ-4254058
* La paginación no se activa para Ideación y la lista de temas (o respuestas) se hace más larga a menos que se vuelva a cargar. NPR-26193: revisión para CQ-4252104
* Las actividades de otros usuarios y el UGC eliminado son visibles al iniciar sesión con credenciales de moderador y al agregar &quot;#social-activities&quot; o &quot;#tabs-2&quot; al final de la URL del perfil del moderador. Revisión para CQ-4251355
* Todas las etiquetas asignadas no se pueden eliminar de un artículo de blog. NPR-26851: revisión para CQ-4253359
* Las relaciones con UGC no se eliminan al eliminar UGC. NPR-27630: revisión para CQ-4258706
* El vínculo para respuestas no funciona cuando se pulsa una fila en las respuestas del foro. NPR-27623: revisión para CQ-4256138
* El límite de suscripción de usuarios está establecido en 1000. NPR-27614: revisión para CQ-4254689
* La edición de un sitio y la edición de funciones en la configuración de funciones generan una excepción de puntero nulo. NPR-27377; Revisión para CQ-4255909

**Traducción**

* La vista previa de traducción no funciona con el contenido de muestra de we.retail. NPR-26727: revisión para CQ-4241179

**IU: bases**

* Se devuelve una NullPointerException al intentar descargar configuraciones después de actualizar a AEM 6.4. NPR-27310: Revisión para Granite-23573
* Backport proactivo para correcciones de granite.platform.login. NPR-26941
* Backport proactivo para granite.ui.content fixes. NPR-26294
* El componente de campo de número no valida números negativos en Internet Explorer 11. NPR-26701
* Backport proactivo para granite.ui.coralui3 correcciones. NPR-26662
* Backport proactivo para granite.ui.coralui3-eon correcciones. NPR-26666
* Backport proactivo para granite.ui.foundation.components correcciones. NPR-27313
* Backport proactivo para granite.ui.commons fixes. NPR-26753
* Backports de la interfaz de usuario de la base proactiva. NPR-26248

**Integración**

* Las modificaciones en AEM experiencias creadas mediante el motor de orientación no se publican. NPR-24869: revisión para CQ-4247832
* No se pueden crear varias actividades y experiencias si sus nombres incluyen caracteres japoneses. NPR-27271: revisión para CQ-4256857
* Actualice el extremo de la API de Launch. NPR-26790: revisión para CQ-4254380
* (Personalization) BrandsRetriever recorre todo el árbol. NPR-27060: revisión para CQ-4255790

**WCM: IU de administración**

* Se ha añadido la prueba HTTP para publicar/cancelar la publicación de una página con referencias y una prueba de IU para Live Copy. Revisión para CQ-4256894

**WCM: editor de páginas**

* La barra de herramientas Editar se desactiva para los componentes de la primera edición. Revisión para CQ-4253270

**Forms**

Los aspectos destacados de los formularios de AEM 6.4.3.0 son:

* Se ha habilitado la compatibilidad con una matriz/lista de objetos con sustitución de entidades dinámicas.
* Se ha habilitado la compatibilidad con FIPS para el flujo de trabajo ampliado de Reader en Firma digital, Extensiones de Reader, CryptoProvider y TrustStore.
* Se ha agregado compatibilidad con PDF/UA a los formularios XFA generados con Designer o Output Service.
* Se ha habilitado la compatibilidad con la propiedad allowedPaths en las plantillas de formularios adaptables.
* Se ha agregado compatibilidad con JBoss 7.1.4 para AEM Forms 6.4.

**Paquete de complemento de Forms**

**Integración de back-end**

* No se pueden rellenar las asignaciones del modelo de datos de formulario basadas en entidades dinámicas en la respuesta SOAP. NPR-26428: revisión para CQ-4250639
* El valor de _elementNamespace en los datos adicionales del modelo de datos de formulario, introducidos mediante la interfaz de usuario de prueba, no se refleja correctamente en la solicitud SOAP. Revisión para CQ-4255373
* Una restricción de propiedad que acepta valores NULL se inicializa con un valor predeterminado y no se puede sincronizar con FDM. Revisión para CQ-4253873
* El valor predeterminado de la propiedad que acepta valores NULL no está establecido en True para el origen de datos OData. Revisión para CQ-4253870

**Formularios adaptables**

* No se pueden cargar sitios y el editor de formularios. NPR-26977; Revisión para CQ-4249170
* Problemas al agregar un archivo adjunto a un formulario adaptable mediante el teclado. NPR-25913; Revisión para CQ-4249456

**Forms: comunicación interactiva**

* No se puede mover un panel que se haya agregado con la opción Agregar panel secundario en el árbol de contenido del canal web de comunicación interactiva y en formularios adaptables. Revisión para CQ-4253915
* Los nombres de las tablas se muestran en lugar del título de la asociación FDM en la sección Fuentes de datos del canal Imprimir. Revisión para CQ-4253669
* La función isUseXFABullets() no está deshabilitada en la clase PrintChannelRenderOptions y está disponible en el SDK del cliente. Revisión para CQ-4246583, CQ-4252700

**Administración de correspondencia**

* Javadocs para 6.4 no contiene com.adobe.dbforms.* paquete y las clases correspondientes. Revisión para CQ-4253200
* La interfaz de usuario de CCR muestra un valor no deseado predeterminado para el campo de fecha en caso de que no haya entrada del XML de datos de prueba. Revisión para CQ-4252041
* Si una carta contiene un módulo de lista, se pierde el espacio entre viñetas y texto al generar el PDF a partir de la carta. Revisión para CQ-4250588

**Administrador de Forms**

* Se ha habilitado la compatibilidad con la propiedad allowedPaths en las plantillas de formularios adaptables. NPR-26598: revisión para CQ-4255892

**Forms: flujo de trabajo**

* Si se incluyen llaves en el nombre de la tarea mientras se ejecuta el flujo de trabajo de Forms, se muestra una excepción en los registros. Revisión para CQ-4256626
* No se puede abrir una plantilla de búsqueda en el espacio de trabajo de AEM Forms. Revisión para CQ-4255651

**Mobile Forms**

* La notificación de salida no se muestra al salir del campo de fecha en AEM Forms representado como HTML en Internet Explorer o Chrome. NPR-26483: revisión para CQ-4239352
* Las fechas incluidas en el XML cuando comienza el procesamiento hacen que los formularios generen un error de validación cuando el usuario intenta abandonar el formulario. NPR-26787: revisión para CQ-4251211

**Instalador JEE de Forms**

**PDF Generator Service**

* No se puede mostrar la configuración de informes y cumplimiento de normas para el Generador de PDF. NPR-26715: revisión para CQ-4253384
* falta el archivo binario convertpdf en el paquete de complementos de AIX Forms, lo que provoca un error al invocar el servicio PDFA. Revisión para CQ-4257873
* El servicio de captura de papel se bloquea al procesar archivos TIFF. NPR-28079: revisión para CQ-4240649

**Servicios de documento**

* Agregue la conformidad con FIPS para el flujo de trabajo RE en Firma digital, Extensiones de Reader, CryptoProvider y TrustStore. NPR-27495: revisión para CQ-4257572
* La conversión falla al ejecutar el servicio AssemblerService.toPDFA en un bucle. NPR-26354: revisión para CQ-4248656
* No se puede validar la conformidad de los PDF correctamente según los estándares PDF/A-1b. NPR-26286: revisión para CQ-4227539
* Problemas de falta de memoria al actualizar AEM Forms de 6.1 SP2 CFP5 a CFP13. NPR-26285: revisión para CQ-4244379
* No se puede validar la conformidad de los PDF correctamente según los estándares de PDF/A. NPR-26272: revisión para CQ-4248823

**Forms: base JEE**

* Se ha agregado compatibilidad con JBoss 7.1.4 para AEM Forms 6.4. NPR-27331; Revisión para CQ-4255601

**Paquetes de funciones incluidos**

* Se ha habilitado la compatibilidad con una matriz/lista de objetos con sustitución de entidades dinámicas. NPR-26590: revisión para CQ-4254655

**Paquetes de contenido y paquetes OSGI incluidos**

Lista de paquetes OSGi incluidos en AEM 6.4.3.0

[Obtener archivo](assets/6.4.3.0_bundles.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.3.0

[Obtener archivo](assets/6.4.3.0_OSGI.txt)

#### AEM 6.4.2.0 {#experience-manager-6420}

AEM 6.4.2.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas desde la disponibilidad general de AEM 6.4 in **Abril de 2018.**
También es acumulativo, lo que significa que 6.4.2.0 incluye todos los paquetes de servicio AEM 6.4 que se lanzaron antes.

Algunos de los aspectos destacados de AEM 6.4.2.0 son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.7.
* Se ha agregado compatibilidad con las funciones 1.4 de la especificación del lenguaje de plantilla de HTML (HTL)
* Se ha agregado compatibilidad con MongoDB Enterprise 3.6.
* El Editor de páginas de sitios agrega compatibilidad con la edición y la composición en contexto con componentes del lado del cliente creados en React o Angular en combinación con <a href="../sites-developing/spa-walkthrough.md">AEM SDK de JS Editor SPA</a>.
* Mejoras en los fragmentos de contenido: se ha agregado la capacidad de realizar anotaciones en campos de texto y de comparar versiones en paralelo.
* Se ha añadido [integración con Adobe Stock](/help/assets/aem-assets-adobe-stock.md) para que los usuarios puedan buscar, previsualizar, guardar y conceder licencias sobre los recursos de Adobe Stock directamente desde AEM interfaz de usuario. Para obtener información más detallada, consulte [Uso de recursos de Adobe Stock con AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html).
* Se ha añadido compatibilidad con el metaesquema condicional dinámico y la capacidad de establecer un esquema de metadatos para carpetas de recursos.
* Se ha añadido una configuración en cada componente para habilitar/deshabilitar la funcionalidad de creación/actualización de miniaturas de carpetas.
* Mejoras en el Editor de imágenes en la creación de páginas.
* La corrección de regresión en Communities para el evento de puntuación no se gestiona correctamente en caso de que se elimine la respuesta seleccionada.
* Se ha revisado el límite máximo de resultados de búsqueda para solr a MAX_INT-10000.
* El trabajo de vaciado de transacción solo se inicia en la primera llamada a storeTransaction.
* El botón &quot;Seleccionar todo&quot; está ahora disponible en Vista de tarjeta y Vista de columna.
* Mejoras de accesibilidad en CoralUI.
* Se ha mejorado la administración de Coral.Keys.
* Se ha actualizado time.js a la versión 2.22.2
* Se ha actualizado jquery a la versión 1.12.1
* Se ha introducido el componente de estado del flujo de trabajo base.
* Se ha actualizado GCC a la versión más reciente.
* Mueva SAML a la nueva sincronización de IDP externa.

**Recursos**

* La generación de subconjuntos para el archivo pptx no contiene imágenes ni miniaturas. NPR-24286: revisión para CQ-4217986
* MigrarTodosRecursos : Agregue soporte para el procesamiento por lotes y mejore AEM método que agregue UUID a los activos antiguos. NPR-24861: revisión para CQ-4242863 y CQ-4247874
* Problema de rendimiento con la generación de miniaturas. NPR-24693: revisión para CQ-4246960
* (IU táctil) El componente &quot;predicado de opciones&quot; permanece en blanco cuando se añade a la página del editor de Asset Share. NPR-24643: revisión para CQ-4245295
* (Flujo de trabajo) Los recursos de etiquetas inteligentes no se procesan a través de la configuración del proxy. NPR-25840: revisión para CQ-4248202
* (Omnisearch) al eliminar el tipo de archivo:image de los criterios de búsqueda no se elimina el tipo de imagen. NPR-25232: revisión para CQ-4248280
* Cuando se intenta mover un archivo a una carpeta diferente, no se muestran las carpetas con apóstrofo en su nombre. NPR-25125: revisión para CQ-4248660
* El control deslizante en la página Subbasset no funciona correctamente cuando la preferencia de idioma definida es distinta del inglés. NPR-25274: revisión para CQ-4248489
* Problema con el archivo csv de exportación de metadatos al abrirlo en equipos con formato de número europeo. NPR-26009: revisión para CQ-4250677
* El botón Crear no está disponible en la selección de carpetas de recursos sin el permiso &quot;Eliminar&quot;. NPR-25788: revisión para CQ-4250140
* (Backport) Mejoras de accesibilidad: Duplicate-id: el valor del atributo id debe ser único, Etiqueta: Los elementos de formulario deben tener etiquetas y Nombre del vínculo: Los vínculos deben tener un texto discernible. NPR-24252: revisión para CQ-4250905, CQ-4250906, CQ-4250907
* La carga de un csv con campos separados por &quot;,&quot; falla para los países europeos. NPR-25549: revisión para CQ-4249931
* (Brand Portal) Los subconjuntos de un archivo pdf de varias páginas no se publican cuando se publica un recurso. NPR-25991: revisión para CQ-4245162
* Publicar funcionalidad posterior para AEM en la replicación de Brand Portal. NPR-25911: revisión para CQ-109139
* La publicación y cancelación de la publicación de la colección privada por usuarios no administradores resulta en un NPE. NPR-25906: revisión para CQ-4250594
* Deshabilite la publicación de fragmentos de contenido y esquemas de formularios en Brand Portal. NPR-24176, NPR-26004: revisión para CQ-4251592, CQ-4252026
* (Dynamic Media) Se han actualizado los visores de DM a la versión 5.10.1, que permite comprobar si hay nombres duplicados en la página Ajuste preestablecido de imagen. Consulte Actualización de visores de Dynamic Media (5.10.1). NPR-24403: revisión para CQ-4247554
* Error de JavaScript en la consola del explorador en la vista de columna al seleccionar un recurso o una carpeta. NPR-25939: revisión para CQ-4250228
* (Vista de columna) No se pueden identificar tareas, ya que el archivo de clave se muestra como una entrada en blanco en blanco. NPR-25903: revisión para CQ-4246307

**Sitios**

* La consulta de datasource.jsp en AEM 6.2 es diferente de AEM 6.4. NPR-24968: Revisión para CQ-4244235
* (IU clásica) No se pueden agregar etiquetas a las páginas. NPR-25255, NPR-25612: revisión para CQ-4249615
* HTML Template Language Specification 1.4 funciones compatibles con AEM 6.4.2.0 NPR-24585
* Herencia incorrecta en el componente local después de copiar una página de Live Copy. NPR-25920: revisión para CQ-4236737, CQ-4248957
* El tiempo de activación y desactivación se almacena en crx/de pero no obtiene lo mismo en la consola de la interfaz de usuario de las propiedades de la página. NPR-25154: revisión para CQ-4243431
* El sistema de estilos rompe los valores iniciales de las propiedades del cuadro de diálogo. NPR-25648: revisión para CQ-4250073
* Al definir una propiedad cq:tagName en un nodo cq:htmlTag , el nombre de la etiqueta no se tiene en cuenta si el componente se incluye mediante JSP. NPR-24154: revisión para CQ-4244120
* Para los componentes parsys anidados, siempre se aplica el primer diseño satisfactorio (con la ruta menos anidada) de varios componentes disponibles. Para obtener más información, consulte [Resolución de ruta de diseño](https://docs.adobe.com/content/help/es-ES/experience-manager-64/developing/platform/templates/page-templates-static.html). NPR-24973: revisión para CQ-4246276
* Al pegar texto en un componente RTE, se muestra un cuadro de diálogo emergente, pero no se representa correctamente. NPR-24895: revisión para CQ-4245901
* (RTE) Problemas de rendimiento con indicador de campo obligatorio. NPR-24894: revisión para CQ-4241895
* (Componente de página) Al añadir un componente a Parsys, se recorta de la derecha y se sale el ancho del marco del dispositivo. NPR-25536: revisión para CQ-4238224
* El editor de texto sin formato envía datos sin recortar y añade espacios adicionales. NPR-25312: revisión para CQ-4249006
* Al abrir el componente mediante el modo integrado, los complementos cargados anteriormente no son visibles por segunda vez. NPR-24610: revisión para CQ-4236850
* Al cargar un XF en la vista del editor copiando/pegando, la variación maestra no se carga automáticamente. NPR-24841: revisión para CQ-4248037
* Estructura de HTML incorrecta en siteadmin/damadmin rompe IE11. NPR-24686: revisión para CQ-4246363, CQ-4248402
* (Asistente para administrar publicación) El calendario de la fecha de activación en el paso Opciones no se abre después de que se hayan realizado algunas acciones en el paso Ámbito. NPR-25681: revisión para CQ-4250205
* La IU clásica no funciona para editar CUG ya que ha quedado obsoleta. NPR-25075: Revisión para 4241823
* Opción Crear no disponible para crear fragmentos de experiencia. NPR-26053: revisión para CQ-4249923
* La variación XF se activa dos veces más tarde, lo que genera ID duplicados para el mismo elemento. NPR-24179: revisión para CQ-4245093
* La tabla de base es vulnerable a la ejecución almacenada de scripts en sitios múltiples. NPR-25185: revisión para CQ-4240760
* Error &quot;Valor de selector de recursión no válido&quot; al migrar un componente de AEM 6.2.1.13 a AEM 6.4. NPR-24146

**WCM: editor de páginas**

* Varios parámetros apilados debido a consultas de larga duración (más de 6) hacen que AEM se ralentice. Revisión para CQ-4240247
* Error de JS al agregar cq:tagName vacío en el nodo cq:htmlTag . Revisión para CQ-4251852
* Actualice EditableActions en función de la reubicación columnClassNames. Revisión para CQ-4250781
* Exponga rutas de recursos y modelos utilizando una sola propiedad y atributo. Revisión para CQ-4251255
* Revertir los cambios de ruptura de la API export.json. Revisión para CQ-4251854
* (SPA editable) Candidato a la versión 1.0.0. Revisión para CQ-4251991
* La barra de herramientas Editar se desactiva para otros componentes al editar cualquier componente. Revisión para CQ-4253270

**Integración**

* Los campos Biblioteca y Descargar URL deben ser editables. NPR-24804: revisión para CQ-4246864
* Problema con varias configuraciones de DTM. NPR-24685: revisión para CQ-4247293
* Se ha agregado compatibilidad con la implementación asíncrona para bibliotecas de cliente alojadas. NPR-25716: revisión para CQ-4245745
* El componente dirigido con la oferta correspondiente que falta representa toda la página y, en lugar de un componente orientado vacío, se añade otra representación completa de la página. NPR-25273: revisión para CQ-4248003
* El motor de destino (mbox.js, at.js) no utiliza direcciones URL manipuladas y utiliza direcciones URL que contienen dos puntos, lo que puede provocar errores en determinadas implementaciones. NPR-25339: revisión para CQ-4237854
* (Launch)LibraryDownloadProcess almacena un valor de libraryUri incorrecto. NPR-25330: revisión para CQ-4250006

**Plataforma**

* Bucle de reindexación | NPE mientras realiza la Extracción de texto binario durante la actualización in situ de 6.3 a 6.4. Revisión para Granite - 21677
* Anulación transfronteriza de la ruta marcada interna /libs/cq/cloudserviceconfigs/templates/configpage/jcr:content: Problema al ejecutar el detector de patrones. NPR-25036: revisión para CQ-4248597
* Las entradas de registro no están escritas debido a NPE en LogEntryImpl. NPR-25627: revisión para Granite-22383
* La replicación del evento de eliminación no comprueba los derechos. NPR-25679: revisión para CQ-4241234
* Se ha agregado compatibilidad con STARTTLS en &quot;Day CQ Mail Service&quot;. NPR-25611: revisión para CQ-4249924
* Correcciones proactivas de backport para granite.platform.login para mejorar la accesibilidad. NPR-25176: Revisión para Granite 21746 y Granite-21309
* (AEM 6.4) Error al reconstruir el paquete y reinstalarlo. NPR-25173: revisión para CQ-4247939
* Se ha eliminado el aclHandling predeterminado MERGE_PRESERVE. NPR-24593: revisión para Granite-21889
* Content-Type no está propuesto y falta en la respuesta después de aplicar el ContentDispositionFilter dos veces. NPR-24175: revisión para Sling-7525
* El estado del Administrador de paquetes es incorrecto después de actualizar a AEM rama 6.4. NPR-24551: revisión para Granite-21750
* Instancia de AMS: análisis de registros de error. Revisión para CQ-4249567

**Seguridad**

* El reinicio de sesión de SAML redirige a la página de cierre de sesión utilizando IDP de Okta. NPR-25523: revisión para GRANITE-22364
* La autenticación IMS a través de las configuraciones del proveedor OAuth de IDP externo de OAK deshabilita el usuario creado en AEM. NPR-25301: revisión para Granite-22363

**MAC: Integración de Test&amp;Target**

* (Segmentación) Error de componente de texto durante la segmentación. Revisión para CQ-4233343

**Comunidades**

* (Biblioteca de archivos) La descarga de recursos con espacios en blanco de provoca problemas de formato. NPR-24260: revisión para CQ-4245159
* Correcciones de varios problemas de Adobe Social. NPR-24247: revisión para CQ-4245054, CQ-4245120, CQ-4245296
* El desplazamiento infinito de la consola de miembros y grupos falla en caso de que la publicación del autor se ejecute en diferentes rutas de contexto. NPR-24437: revisión para CQ-4246013
* La publicación no vuelve al estado sin responder ni siquiera cuando se elimina del estado respondido y la puntuación no disminuye. NPR-24419: revisión para CQ-4245797, CQ-4245932
* Los eventos agregados con la funcionalidad de calendario en las comunidades generan valores incorrectos. NPR-24883: revisión para CQ-4244056
* (Foro de comunidades) Problemas con clics en paginación y comportamiento de carga de página. NPR-24880: revisión para CQ-4246109
* (Chrome) Las conversiones de zona horaria fallan en los eventos de comunidades. NPR-24881: revisión para CQ-4247115
* No se puede procesar el objeto incrustado en el correo electrónico. NPR-24999: revisión para CQ-4248022
* La secuencia de automoderación debe ejecutarse en la actualización de UGC además de la creación de UGC. NPR-25892: revisión para CQ-4251399
* Capacidad de respuesta del diálogo modal en los Grupos. NPR-25623: revisión para CQ-4248805
* Se produce una excepción solar en la eliminación de contenido. NPR-25869: revisión para CQ-4248908
* Los vínculos paginados a subprocesos con muchos anuncios no funcionan en las notificaciones. NPR-25678: revisión para CQ-4243038
* Los valores de tiempo en los resultados de búsqueda muestran la hora del servidor en lugar de la zona horaria del cliente. NPR-25594: revisión para CQ-4248986
* (Comentarios del foro) El botón Atrás del explorador no funciona según lo esperado. NPR-25205: revisión para CQ-4248573
* (Resultados de la búsqueda) El botón Atrás del explorador no funciona según lo esperado. NPR-25214: revisión para CQ-4248574
* Se devuelve nulo cuando se superpone el componente community groupmemberlist. NPR-25228: revisión para CQ-4248523
* (Calendario de comunidades) ClassCastException se genera al guardar el evento con la nueva imagen de portada. NPR-25167: revisión para CQ-4248662
* (Comunidades) Mensajes que se truncan. NPR-25326
* (AEM Publish) El recurso de puntuación falla con la ruta de contexto y muestra la pantalla en blanco. NPR-26155: revisión para CQ-4251942
* (MSRP) El calendario recién creado se guarda parcialmente arrojando NPE en el registro de errores. NPR-26071: revisión para CQ-4250531
* La paginación Foro/Tema solo se actualiza cuando se actualiza la página. NPR-26070, NPR-25965: revisión para CQ-4249509
* (Foro de preguntas y respuestas) No se puede navegar a la página anterior al abrir un vínculo directo a un comentario. NPR-26069: revisión para CQ-4251699
* La carga de imágenes en el grupo Crear no funciona en móviles. NPR-26172: revisión para CQ-4251703
* (Mensajería) Al utilizar DSRP, el nombre del receptor de mensajes siempre se muestra como &quot;Desconocido&quot;. NPR-26056: revisión para CQ-4251397
* La etiqueta de estado de finalización de recursos de Puntuación de habilitación aparece vacía en la interfaz de usuario. NPR-26034: revisión para CQ-4249994
* Al crear un nuevo grupo de comunidad, se crea un grupo de comunidad duplicado en un clúster mongoMK activo/activo. NPR-26032: revisión para CQ-4245884
* (Autor) El asistente para la creación de grupos tarda demasiado en cargar o crear un grupo dentro del asistente. NPR-26031: revisión para CQ-4244966
* Parsys desaparece al añadir una instrucción include en el script hbs. NPR-25908: revisión para CQ-4250489
* Al habilitar “Permitir privilegiados”, los miembros privilegiados solo pueden componer para usuarios que son miembros de la comunidad. NPR-25877: revisión para CQ-4248450
* Vínculos profundos bloqueados para su activación. NPR-25966: revisión para CQ-4251478
* La paginación del foro no se actualiza dinámicamente al eliminar las respuestas. NPR-25970: revisión para CQ-4248975, CQ-4252843
* El desplazamiento automático y el resaltado no funcionan en los eventos de calendario y de biblioteca de archivos en caso de comentarios anidados. NPR-25958: revisión para CQ-4251471
* (DSRP) El rendimiento de los vínculos directos/profundos se degradan con grandes cantidades de contenido generado por el usuario. NPR-25957: revisión para CQ-4251470
* No se pueden modificar las propiedades de Permitir miembros privilegiados y miembros privilegiados. NPR-26014: revisión para CQ-4244592
* Marcar todo como leído restablece los contadores de notificaciones para todas las páginas de la comunidad. NPR-25931: revisión para CQ-4248612
* Edite las TI que fallan para DSRP. NPR-25929: revisión para CQ-4251382
* Las TI de correo electrónico fallan debido a NPE al crear plantillas de correo electrónico. NPR-26039: revisión para CQ-4250962
* Problemas de los subprocesos del foro al incrustar imágenes con muy alta resolución. NPR-26037: revisión para CQ-4244453, CQ-4253099
* El tiempo muestra los conmutadores cuando la zona horaria del servidor difiere de la del usuario. NPR-26036: revisión para CQ-4248751
* Si se adjunta un archivo dos veces con el mismo nombre a una publicación de foro, se producirá un error en el servidor. NPR-24172: revisión para CQ-4244367
* Correcciones de rendimiento de backport: paginación de grupos en creación y publicación, búsqueda de grupos en autor, Evitar la serialización de respuestas para diario, calendario e ideación, y carga diferida para obtener la membresía de grupos (invitar/desinvitar) para cada grupo mientras se ve la página de listado de grupos. NPR-24538: revisión para CQ-4246515
* Los recursos de habilitación no están visibles en el autor. Revisión para CQ-4252618
* Las notificaciones no se generan para subprocesos de un usuario desconocido. Revisión para CQ-4245132
* La búsqueda de grupos no aparece en el carril izquierdo. Revisión para CQ-4252621
* (Autor) La paginación no funciona para la Consola de grupos. Revisión para CQ-4242786
* Actualización de la interfaz de usuario de jQuery. Revisión para CQ-4248894
* Actualice a la última versión de SCORM 2017.1. NPR-25675: revisión para CQ-4240671
* Los campos &quot;Componer en nombre&quot; son visibles para los usuarios que no son de la comunidad. NPR-25331: revisión para CQ-4247858
* La publicación sigue estando visible en la interfaz de usuario incluso después de la eliminación y da error en la consola. NPR-26290: revisión para CQ-4252803
* (Configuración del sitio) No se pueden guardar los cambios realizados en las funciones. NPR-26274: revisión para CQ-4252187
* (Vulnerabilidad de seguridad) Adquisición de cuenta debido a una mala configuración del token web de JSON. NPR-26458: revisión para CQ-4253314
* La paginación no se restablece al eliminar las respuestas. NPR-26326: revisión para CQ-4252997
* La imagen adjunta no se muestra en Borradores durante la edición. Revisión para CQ-4253360
* La página no se actualiza al adjuntar datos adjuntos en la base de datos relacional (DSRP). Revisión para CQ-4253084
* Los grupos no funcionan dentro del recurso del sitio de habilitación. Revisión para CQ-4252975
* Los requisitos previos de las rutas de aprendizaje no se mantienen en la habilitación. Revisión para CQ-4252948

**Flujo de trabajo**

* La interfaz de usuario del iniciador del flujo de trabajo no muestra las configuraciones del iniciador 41 anteriores y déclencheur un error de javascript en la consola. NPR-25028: revisión para CQ-4247604
* La edición de un flujo de trabajo heredado sin editar su iniciador hace que se creen varios flujos de trabajo en cualquier flujo de trabajo que contenga el paso Activar página/recurso . NPR-25870: revisión para CQ-4250896
* Vínculo incorrecto en la carga útil del flujo de trabajo si la página tiene un nodo de metadatos. NPR-25916: revisión para CQ-4250733

**Traducción**

* Se ha corregido que al importar un proyecto traducido se realizan dos solicitudes de POST concurrentes, lo que provoca errores. NPR-24889: revisión para CQ-4247638
* Se ha corregido que, al crear un proyecto de traducción para varios idiomas, todas las páginas del mismo idioma se añadían al mismo trabajo. NPR-25091: revisión para CQ-4246112
* Se ha corregido que, en algunos casos, el trabajo de traducción solo enumeraba las 40 páginas principales. NPR-25974: revisión para CQ-4248661
* El componente DataPicker (Coral2) no cambia el año. NPR-24466: revisión para Granite-21893

**IU: bases**

* Backports de la interfaz de usuario de la base proactiva. NPR-24344, NPR-24345, NPR-25176, NPR-25095, NPR-24332, NPR-25653, NPR-25932, NPR-259 35, NPR-25976
* (Importador de diseños) La importación de una página no importa js,css. NPR-25203: revisión para Granite-22236
* Backports de la interfaz de usuario de la base proactiva para mejorar la estabilidad del producto. NPR-24334

**MAC: Integración de Test&amp;Target**

* La segunda página de PersonalizationWizard ( lanzada por &quot;Start Targeting&quot; ) está en blanco y genera errores en la consola. Revisión para CQ-4253277

**Fragmentos de experiencias**

* Integración de fragmentos de experiencias combinados/Target con AEM 6.4.2.0. Revisión para CQ-4248653

**Administración de fragmentos de contenido**

* Anotaciones de fragmentos de contenido y comparación paralela de versiones de fragmentos de contenido. Revisión para CQ-4247148

**DAM: General**

* El filtro &quot;Protegido por&quot; no funciona correctamente en la búsqueda. Revisión para CQ-4247070
* Al realizar el flujo de trabajo de actualización de recursos, la copia del idioma del recurso y su miniatura se quedan en blanco. Revisión para CQ-4250641
* Duplicate-id: el valor del atributo id debe ser único. Revisión para CQ-4250905
* Etiqueta: Los elementos de formulario deben tener etiquetas. Revisión para CQ-4250906
* Nombre del vínculo: Los vínculos deben tener un texto discernible. Revisión para CQ-4250907
* Migración de plantillas de metadatos de carpeta de puerto JMX y ServiceUserMapping. Revisión para CQ-4252947
* Las pruebas de WebdriverIO no se ejecutan en la rama de versión 640 de CQ/dam. Revisión para CQ-4252749
* Los vínculos a recursos movidos no se vuelven a factorizar si se publica el vínculo. Revisión para CQ-4245756

**DAM: visualizadores**

* Error intermitente al cargar vídeo con nuevos visores 5.10.1. Revisión para CQ-4250562

**DAM-Brand Portal**

* La cancelación de la publicación de una colección de Brand Portal está fallando con un error. Revisión para CQ-4245990
* No se pueden cancelar la publicación de ajustes preestablecidos de imagen desde Brand Portal. Revisión para CQ-4246140
* Los subconjuntos de un archivo pdf de varias páginas no se publican cuando se publica un recurso. Revisión para CQ-4245162

**DAM - DMClient**

* Al publicar un recurso de vídeo en YouTube, las etiquetas que resultan en YouTube incluyen la ruta completa de la etiqueta. Revisión para CQ-4245549
* (Actualizaciones de exclusión y inclusión) Problema con el redireccionamiento de CSS del visor. Revisión para CQ-4247854
* No se puede crear o editar el ajuste preestablecido de visualizador como no miembro del grupo &quot;administradores&quot;. Revisión para CQ-4247618
* (6.4.1.0) Al agregar varios vídeos en parsys, el reproductor de vídeo se rompe. Revisión para CQ-4248517
* Cambiar el nombre y mover recursos dentro de un conjunto de imágenes hace que la edición sea imposible. Revisión para CQ-4248434
* La publicación de vídeos grandes en YouTube genera mensajes de tiempo de espera. Revisión para CQ-4237831
* (Vista de lista) La interfaz de usuario del Selector/Selector de recursos cambia a gris y está deshabilitada para el usuario. Revisión para CQ-4237817
* (Zoom vertical) Css no se carga con un error 404. Revisión para CQ-4236508
* Al intentar descargar un recurso con un carácter de porcentaje (%) en el nombre del recurso, se crea un archivo vacío. Revisión para CQ-4250558
* (Vista de tarjeta) No se muestra ningún indicador de procesamiento al utilizar Copiar y Pegar en un recurso de vídeo. Revisión para CQ-4249037
* (Actualice de 6.3.2 a 6.4) Los ajustes preestablecidos de imagen de preactualización se muestran como &quot;No publicado&quot; en la página Representaciones, pero no generan botones de URL cuando se seleccionan. Revisión para CQ-4240406
* Mejoras en la deuda técnica/menores. Revisión para CQ-4240648
* El Selector de recursos (o Selector de recursos) no muestra todos los recursos de las carpetas disponibles. Revisión para CQ-4218414
* El ajuste preestablecido de imagen sin altura muestra imágenes con un tamaño incorrecto. Revisión para CQ-4246546
* (Recursos de varias páginas) La interfaz de usuario rompe al hacer clic en las anotaciones. Revisión para CQ-4251434
* Al actualizar de la versión 6.3 a la 6.4 y posteriores al ajuste preestablecido de Analytics, se crea un nuevo grupo de informes y un ajuste preestablecido de Analytics, con lo que se pierden los datos de informes más antiguos del usuario. Revisión para CQ-4244529
* (Asistente para administrar publicación) La lista de recursos parece estar vacía al intentar publicar o cancelar la publicación. Revisión para CQ-4251881
* Al elegir Visualizadores después de ver el conjunto de miembros, los vídeos AVS no se reproducen correctamente. Revisión para CQ-4205308
* Los ajustes preestablecidos de procesamiento de vídeo de preactualización no pueden tener un nuevo ajuste preestablecido de codificación de vídeo añadido ni editar los ajustes preestablecidos de codificación existentes. Revisión para CQ-4240407
* Los ajustes preestablecidos de imagen no se aplican a las representaciones dinámicas descargadas. Revisión para CQ-4249862
* El botón Seleccionar todo no funciona correctamente en la página de listado de ajustes preestablecidos de visor. Revisión para CQ-4252462
* Perfiles de vídeo: El botón Seleccionar todo no funciona. Revisión para CQ-4253076, CQ-4251447
* Paso de validación de SP2 - paso de humo. Revisión para CQ-4251639

**DAM: DMServices**

* No se pudieron generar las representaciones de Dynamic Media para el archivo EPS. Revisión para CQ-4243688

**Granite**

* El error en el paquete SymbolicName conduce a un paquete duplicado. Revisión para Granite-22155
* Puede que CUGConfiguration no recoja CugExclude. Revisión para Granite-21109
* Al reiniciar el Adobe Granite Workflow Core, se vuelven a ejecutar los pasos del flujo de trabajo desde el medio, creando flujos de trabajo innecesarios. NPR-25057: revisión para Granite-22218
* JcrResourceBundle no admite correctamente varios nombres base. NPR-25245: revisión para Granite-22317
* Al instalar paquetes de contenido, las ACL se agrupan por entidad de seguridad, por lo tanto, se rompe el modelo de permisos. NPR-24583: revisión para Granite-21591
* Actualice Jetty a la versión 9.4.11 para corregir vulnerabilidades. NPR-25030: revisión para Granite-22120

**Forms**

Los aspectos destacados de los formularios de AEM 6.4.2.0 son:

* Se ha añadido una nueva propiedad para que las colas se actualicen sin actualizar el explorador.
* Se ha agregado la capacidad de que el usuario utilice el mismo archivo WSDL para varios servicios.
* Se ha eliminado el patrón de marca de tiempo no admitido de la lista desplegable del selector de fecha.
* Se ha agregado compatibilidad para la subyección de xfaf y pdf en OSGI.
* Se agregó compatibilidad para usar la variable [capacidad de informes de transacciones](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) en implementaciones locales.
* Se ha agregado código para no mostrar la variable secundaria en el editor de reglas de condición.

**Paquete de complemento de Forms**

**Informes de transacciones**

* Actualice la configuración de Informes de transacciones con la importancia de la replicación inversa configurada en un servidor de publicación. NPR-26050: revisión para CQ-4246650
* Inicialización retrasada del trabajo de vaciado periódico. NPR-25968: revisión para CQ-4245024
* El registro de transacciones falla con la excepción de puntero nulo. Revisión para CQ-4247302

**Forms: flujo de trabajo**

* (Espacio de trabajo HTMLEspacio de trabajo HTML) Cuando un usuario reclama una tarea, el recuento de colas se actualiza para ese usuario en particular, pero no para otros usuarios, a menos que se actualice la página. Este problema se ha corregido con una nueva propiedad de . Para configurar esta nueva propiedad en la instancia de AEM, consulte su Configuración . NPR-24536: revisión para CQ-4233665
* No se puede cargar un formulario grande en la aplicación AEM Forms en la versión 6.4. NPR-24463: Revisión para CQ-4245091
* Problema en la aplicación de Mobile Workspace al intentar ver la tarea compartida. NPR-25177: revisión para CQ-4248733
* Comportamiento de validación incoherente entre la web y APK. NPR-25670: revisión para CQ-4248178
* Cuando se realiza una llamada a un servicio web, un formulario HTML5 se abre dentro del cliente, falla y se devuelve un mensaje de error. NPR-26048: revisión para CQ-4244716
* Problema al llamar al servicio en la aplicación de Windows 6.3 de AEM formularios. NPR-26468: Revisión para CQ-4252341

**Mobile Forms**

* (Conjunto de formularios) Problema de validación de campos SSN y Mobile al obtener una vista previa. NPR-24458: revisión para CQ-4244983
* Los datos no se muestran con el prefijo de campos multilínea en la vista previa del HTML. NPR-24549: revisión para CQ-4244212
* Los datos se pierden cuando la secuencia de comandos se evalúa en un campo multilínea. NPR-25333, revisión para CQ-4249610

**Forms: comunicación interactiva y gestión de correspondencia**

* La sincronización falla en IC con plantilla básica y plantilla de impresión IC de referencia. NPR-24912
* (CCR) Los validadores no funcionan para campos/variables. Revisión para CQ-4245047
* El icono de objeto del modelo de datos desaparece de forma intermitente en la barra de herramientas Editar texto. Revisión para CQ-4245122
* Los registros de excepciones aparecen en IC copiado si se elimina el IC original. Revisión para CQ-4249378
* En la representación de letras, la condición no se evalúa como verdadera aunque los datos sean correctos. Revisión para CQ-4245944
* Los componentes generados automáticamente no se resaltan al seleccionarlos en el árbol de contenido. Revisión para CQ-4246178
* Problemas al abrir el editor de plantillas de canal web. Revisión para CQ-4248182
* No se puede cambiar el orden de los recursos añadidos, ya que las flechas arriba/abajo siguen deshabilitadas. Revisión para CQ-4252042
* No se pueden actualizar las propiedades del módulo Condición. Revisión para CQ-4247909
* Cuando el usuario reorganiza un objeto en el canal web, es necesario mejorar el usuario del cuadro de diálogo &quot;Cancelar herencia&quot;. Revisión para CQ-4241076
* Los datos de la carta correspondientes a los enlaces definidos en XDP no se rellenan usando la dirección URL de la carta directa. Revisión para CQ-4245833
* (Problema de almacenamiento en caché) La sincronización de canales web no refleja los cambios realizados en los fragmentos de diseño, el fragmento de texto del canal de impresión. Revisión para CQ-4251460
* No se pueden actualizar el fragmento de diseño y las propiedades DD. Revisión para CQ-4247830
* (CCR) La recarga del borrador está fallando debido al análisis de XML. Revisión para CQ-4250950
* (Editor IC) El botón &quot;Editar fragmento&quot; debería ser más visible. Revisión para CQ-4244694
* (XDP) Se muestra una pantalla en blanco al agregar un fragmento de presentación en el nuevo subformulario creado. Revisión para CQ-4248810
* Error de prueba DocumentFragment-master-DeployWithServerSideTests. Revisión para CQ-4245496
* Variable de módulo de texto Instancia duplicada en el módulo Condición. Revisión para CQ-4252128
* La dirección URL de vista previa del PDF no muestra los informes de transacciones al publicar. Revisión para CQ-4246158
* Problemas relacionados con la sincronización de IC con el canal de impresión y la sincronización con el canal web. Revisión para CQ-4251505
* Limpieza del código EXM: Elimine LocalFunctionMapper. Revisión para CQ-4243265
* Para corregir el tipo de recurso TableHeader del componente de tabla webChannel de IC. Revisión para CQ-4251821
* (Editor de CI) Problemas de uso. Revisión para CQ-4241081
* El subformulario Canal de impresión no muestra la funcionalidad de inserción. Revisión para CQ-4252994
* La sincronización Conservar cambios falla después de eliminar el nodo FDM o el marcador de posición Variable. Revisión para CQ-4253178
* (Editor de plantillas) La plantilla básica muestra las áreas de colocación de encabezado/pie de página adicionales y los parpadeos de pantalla al abrir el canal web. Revisión para CQ-4253323
* Los componentes generados automáticamente no se resaltan al seleccionarlos del árbol de contenido. Revisión para CQ-4246178

**Servicios de documento**

* (Servicio de formulario) OSGI no es compatible con XFAF. NPR-25181, revisión para CQ-4251313
* Los caracteres en el encabezado del fichero de PDF ensamblado están llegando a ser confusos. NPR-25113: revisión para CQ-4244682

**Formularios adaptables**

* Enviar acción como enviar correo lanza una excepción con los campos CC/BC en blanco. NPR-25019: revisión para CQ-4243039
* No se puede usar el componente Formulario de AEM OOTB debido a una consulta ineficiente. NPR-25065: revisión para CQ-4247256
* Elimine sling:orderBefore de los nodos de diálogo guideImageChoiceComponent. Revisión para CQ-4245013
* (Selector de fecha) El patrón de edición no admite dos tipos de patrones de marca de hora. Revisión para CQ-4237982
* Envíe Acción utilizando problemas de creación de &quot;Forms Workflow&quot; Classic. Revisión para CQ-4236981
* (Canal Web) El gráfico IC debe heredar la propiedad colspan del gráfico AF. Revisión para CQ-4252143

**Integración de back-end**

* (Solicitudes SOAP) Los decimales grandes (más de 6 dígitos) se representan en notación exponencial, lo que provoca un error de validación. NPR-25283: revisión para CQ-4248100
* Validación incorrecta de parámetros opcionales definidos en tipos complejos. NPR-25070: revisión para CQ-4247107
* Se ha agregado la capacidad de que el usuario utilice el mismo archivo WSDL para varios servicios. NPR-24604, revisión para CQ-4247756
* FDM ajusta el orden de los parámetros en sus llamadas SOAP. NPR-25069, revisión para CQ-4247180
* FDM combina entidades (en Lista/Matriz) en una solicitud SOAP. NPR-25284: revisión para CQ-4248375

**Instalador JEE de Forms**

**Servicio PDFG**

* La función crear/modificar de la configuración de seguridad no funciona. NPR-24769: revisión para CQ-4246927
* Optimize PDF desincrustando selectivamente fuentes mediante una sola llamada API. NPR-23287

**Servicios de documento**

* El servicio de salida no proporciona las etiquetas correctas para el Reader de accesibilidad. NPR-24438, NPR-24439, NPR-24440, NPR-24441: Revisión para CQ-4243849, CQ-4243845, CQ-4243852, CQ-4243853

**Document Security**

* Problema con la creación de directivas mediante Document Security. NPR-25586, NPR-25547: revisión para CQ-4247086

**Forms: base JEE**

* Procesos que se ejecutan como Cuenta de contexto del sistema de forma intermitente. NPR-25289, NPR-25313: revisión para CQ-4249331
* AEM Forms JEE se ve afectado por la alerta de seguridad de enlace de datos de Apache Struts y Jackson. NPR-25628: revisión para CQ-4242891
* El proceso del punto de inicio del correo electrónico no funciona. NPR-25253: revisión para CQ-4248518

**Paquetes de funciones incluidos**

**Recursos**

* Se ha añadido [integración con Adobe Stock](/help/assets/aem-assets-adobe-stock.md) para que los usuarios puedan buscar, previsualizar, guardar y conceder licencias sobre los recursos de Adobe Stock directamente desde AEM interfaz de usuario. Para obtener información más detallada, consulte [Uso de recursos de Adobe Stock con AEM recursos](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/creative-workflows/adobe-stock.html). NPR-15779: revisión para CQ-30857
* Se ha agregado compatibilidad con el metaesquema condicional dinámico. Para obtener más información, consulte [Metadatos en cascada](/help/assets/cascading-metadata.md). NPR-25189: revisión para CQ-4237413
* Se habilitó la opción &quot;Descarga de recursos&quot; en los fragmentos de contenido. Para obtener más información, consulte [Informes de recursos](/help/assets/asset-reports.md). NPR-25186: revisión para CQ-4237410
* Posibilidad de establecer un esquema de metadatos para carpetas de recursos. Para obtener más información, consulte [Esquema de metadatos de carpeta](/help/assets/folder-metadata-schema.md) y consulte su [Configuración](#configuration-settings-required-for-npr) después AEM la instalación de 6.4.2.0. NPR-21268: revisión para CQ-4221574

**Sitios**

* Permita editar un fragmento de contenido sin permisos de eliminación. Para obtener más información, consulte [Personalizar y ampliar fragmentos de contenido](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-delete.html). NPR-25793: revisión para CQ-4248750
* Se ha agregado la capacidad de anotar fragmentos de contenido. Para obtener más información, consulte [Variaciones: creación de fragmentos](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-variations.html#annotating-a-content-fragment). NPR-25188: revisión para CQ-4235336
* Versiones: Comparar fragmentos de contenido en paralelo. Para obtener más información, consulte [Administración de fragmentos de contenido](https://docs.adobe.com/content/help/en/experience-manager-64/assets/fragments/content-fragments-managing.html#comparing-fragment-versions). NPR-25187: revisión para CQ-4237412
* Mejoras del Editor de imágenes con respecto a AEM 6.4.2.0. Para obtener más información, consulte [Editor de imágenes](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24467

**Paquetes de contenido y paquetes OSGI incluidos**

Lista de paquetes OSGi incluidos en AEM 6.4.2.0

[Obtener archivo](assets/6.4.2.0_bundle-list.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.2.0

[Obtener archivo](assets/6_4_2_0content-package-list.txt)

#### AEM 6.4.1.0 {#experience-manager-6410}

AEM 6.4.1.0 es una actualización importante que incluye correcciones y mejoras clave para el cliente, de rendimiento, estabilidad y seguridad publicadas tras la disponibilidad general de AEM 6.4 en abril de 2018.

AEM 6.4.1.0 se puede instalar en la AEM 6.4 GA. Algunos de los aspectos destacados del Service Pack son:

* El repositorio integrado (Apache Jackrabbit Oak) se ha actualizado a la versión 1.8.3.
* Se han introducido etiquetas inteligentes mejoradas.
* Correcciones en Selector de diseño, Selector de etiquetas (cambie la VM de origen y la VM de destino a auto).
* Se añadió la compatibilidad de typeHint para guardar valores como cadena.
* Se ha agregado compatibilidad con SMTP sobre TLS en el servicio de correo.
* Corrección de la administración de proxy para el reenviador HTTP en DMS7.
* Actualice a /etc/clientlibs/social/thirdparty/handlebars/source/handlebars.js versión 1.3.
* Correcciones en paquetes DMHybrid Opt-OUT y Opt-IN.
* Correcciones en Recorte inteligente.
* Se han migrado los valores de configuración de OOTB a la nueva ubicación ( de /etc a /conf).
* Se han agregado perfiles de color a la configuración del cliente en los servidores de envío.
* Migración de la configuración del servidor de imágenes desde /etc —&amp;gt; /conf.
* Se ha agregado el fragmento de contenido de origen para la traducción.
* Se agregó compatibilidad con ARIA para Print y PrintDialog.
* Se ha agregado compatibilidad con ARIA de validación de correo electrónico.
* Backport proactivo para correcciones de platform.clientlibs.
* Prevención de la ejecución automática de scripts cuando no hay entrada en el dataType explícito (resuelve CVE-2015-9251).

**Recursos**

* El valor desplegable en cascada se muestra en blanco al volver a abrir la página de propiedades de recursos. NPR-23042: revisión para CQ-4238761
* Los vínculos compartidos en la página de mylinkshare y los vínculos a la página no están disponibles para el usuario no administrador NPR-23044: Revisión para CQ-4239004
* Para evitar una excepción de puntero nulo en el flujo de trabajo de actualización de recursos DAM en 6.4.0. NPR-24134: Revisión para CQ-4244972
* La página WCM publicada muestra iconos de marcador de posición para puntos interactivos, faltan archivos CSS con el error 403 para los visores OOTB. NPR-23041: revisión para CQ-4233716
* (Vista detallada) La función de navegación siguiente/posterior deja una superposición DIV en el área de vista previa de representación dinámica que bloquea el acceso al visor. NPR-23043: revisión para CQ-4238499
* La representación de la imagen CMYK tiene una saturación incorrecta. NPR-23048: revisión para CQ-4235470
* XMP extracción de metadatos por Scene7ListInfoProvider consume muchos recursos. NPR-23754
* (dam-delivery) El reenviador HTTP no respeta la configuración del proxy HTTP. NPR-24002: revisión para CQ-4244140

**Sitios**

* Cuando cambiamos el nombre de la página al moverla, el movimiento de la página se realiza correctamente, pero el cambio de nombre de la funcionalidad no funciona. NPR-22923: revisión para CQ-4235907
* Error al publicar una página de Live Copy que apunta a una página de importador en Adobe Campaign. NPR-23053: revisión para CQ-4237164
* Mover/Cambiar nombre en la IU clásica falla con el error &quot;Se ha producido un error al mover la página&quot; y no se ha cambiado el nombre. NPR-23051: revisión para CQ-4235907
* Al cambiar el contenido de la vista Columna a la vista de lista, se muestra una página en blanco y se déclencheur una excepción de puntero nulo para las páginas con OffTime establecido y OnTime en blanco. NPR-22968, NPR-23052: revisión para CQ-4238940

**Comercio**

* Corregir la prueba de Hobbes principales erróneas (Módulo CQ/Commerce). Revisión para CQ-4253494

**Vulnerabilidad**

* La integración de Salesforce es vulnerable a la falsificación de solicitudes del lado del servidor (SSRF). NPR-24289: revisión para CQ-4245277
* Falsificación de solicitudes del lado del servidor (SSRF) y Secuencias de comandos entre sitios (XSS) en ReportingServicesProxyServlet. NPR-24657: revisión para CQ-4246880
* Secuencia de comandos entre sitios (XSS): Se refleja en el catálogo de creación de comercio wizard.html/content. NPR-24642: revisión para CQ-4237017
* Ejecución de scripts en sitios múltiples (XSS) en vínculos de proyectos de la interfaz de usuario de administración. NPR-23272: revisión para CQ-4241795

**WCM: componentes base**

* Al abrir el selector Diseño , se produce una excepción de puntero nulo. NPR-23047: revisión para CQ-4238736

**Interfaz de usuario**

* (Coral3 Datepicker) Agregue soporte para typeHint para guardar valores como &quot;String&quot;. NPR-23398: revisión para Granite-21194
* La traducción de internacionalización no funciona en el nivel de idioma. NPR-22967, NPR-23046: Revisión para Granite-21111
* Backport proactivo para granite.ui.commons fixes. NPR-23537
* Backport proactivo para granite.ui.content fixes. NPR-23535
* Backport proactivo para granite.ui.coralui correcciones. NPR-23538
* No se pueden quitar varios usuarios del grupo a la vez. NPR-23846
* (OMEGA) Informe &quot;Función&quot; solo en inglés. NPR-23989: revisión para Granite-21231
* (Importador de diseños) La importación de una página no importa el js, css. NPR-25203: revisión para Granite-22236

**Integración**

* ResourceResolver no cerrado en com.day.cq.analytics.sitecatalyst. NPR-22340: revisión para CQ-4236515
* TargetContentImpl hace que AEM seo lenta durante consultas de larga duración. NPR-22359: revisión para CQ-4236907
* El motor de destino (mbox.js, at.js) no utiliza direcciones URL manipuladas y utiliza direcciones URL que contienen dos puntos, lo que puede provocar errores en determinadas implementaciones. NPR-22434: revisión para CQ-4237854
* En el modo de Target, los autores pueden modificar un componente heredado del modelo sin cancelar la herencia. NPR-22865: revisión para CQ-4237907
* (Personalization) Los iconos se deforman al cambiar a la vista de tarjeta. NPR-23373, NPR-23374: revisión para CQ-4240018, CQ-4240019
* (Personalization) La consola de audiencias no muestra los tipos nt:folder . NPR-23375: revisión para CQ-4242293
* Cuando un componente está dirigido a una instancia de publicación, aparece un parpadeo que muestra la experiencia predeterminada antes de la experiencia de destino. NPR-23415: revisión para CQ-4242038
* (Consola de Adobe IMS) La configuración del servicio OSGi AccessTokenProvider vuelve a aparecer después de la eliminación. NPR-23520: revisión para CQ-4208250
* La replicación de referencia de configuración falla con la estructura de carpetas intermedias. NPR-23485: revisión para CQ-4242751
* (Personalization) clientlib bloqueada por el servlet proxy. NPR-23521: revisión para CQ-4240995
* (Consola de Adobe IMS) Las soluciones de nube registradas no se recogen en el asistente de configuración. NPR-23977: revisión para CQ-4244549
* Bucle infinito al cargar contenido de destino en páginas sin extensión de HTML. NPR-23522: revisión para CQ-4223600
* La activación falla en una página con referencias de configuración heredadas de Dynamic Tag Management. NPR-23485: revisión para CQ-4242751

**Plataforma**

* (IU clásica) (IU táctil) El selector de etiquetas no se muestra y genera una excepción al intentar buscar etiquetas mediante un predicado de etiquetas en el esquema de búsqueda de recursos. NPR-23049: revisión para CQ-4239371
* (IU clásica) Los componentes que utilizan xtype=tags devuelven null y no se pueden seleccionar de la lista de etiquetas eth. NPR-23050: revisión para CQ-4239937
* (Marcas) El cuadro de diálogo de inclusión menciona Adobe Marketing Cloud en lugar de Adobe Experience Cloud. NPR-23210: revisión para CQ-4237799
* La opción Filtro AEM hace que sea lenta después de actualizar de 6.3 a 6.4. NPR-23260: Revisión para CQ-4239847 (para comprobar)
* Backport proactivo para correcciones de granite.omnisearch.core. NPR-23536
* Backport proactivo para correcciones de platform.clientlibs. NPR-23569
* Se dañó la herencia de configuración del Cloud Service al editar otras propiedades de página. NPR-23216: revisión para CQ-4239782
* Se habilitó la compatibilidad con STARTTLS en el servicio de correo de Day CQ. NPR-23941: revisión para CQ-4240397

**Proyectos**

* (Fragmento de contenido) La copia de idioma para los recursos incrustados no se crea mientras el recurso en inglés se añade a la traducción. Revisión para CQ-4243477
* El menú desplegable msft config muestra la configuración de /libs(6.4 configuraciones) en lugar de /etc(6.3 configuraciones) en el modo heredado. Revisión para CQ-4243475
* Promocionar y eliminar automáticamente los lanzamientos de traducción en proyectos de traducción. Revisión para CQ-4243474
* El fragmento de contenido dentro de los sitios no se traduce. Revisión para CQ-4243482, CQ-4243483, CQ-4245687
* Error del servidor al abrir el filtro de búsqueda de trabajos de traducción. Revisión para CQ-4236813
* El menú desplegable de la configuración de Credential está en blanco incluso después de que tif esté presente en /conf/we-retail. Revisión para CQ-4236315
* Abrir KPI de proyecto: degradación del rendimiento a medida que se crean más proyectos. NPR-23840: revisión para CQ-4238392
* El Iniciador de flujos de trabajo no puede aceptar el valor TypeHint de String. NPR-23863: revisión para CQ-4238356

**Comunidades**

* Vulnerabilidades de seguridad en la versión 1.0 de Handlebars. NPR-23636: revisión para CQ-4243055
* La activación masiva de mensajes marcados no funciona. NPR-23867: revisión para CQ-4243962
* El valor predeterminado no se muestra en el botón de ordenación del componente de foro. NPR-23882: revisión para CQ-4243375
* Problemas con el envío de mensajes de sitios de la comunidad a grupos. NPR-23935

**Flujo de trabajo**

* El Servicio de notificación por correo electrónico del flujo de trabajo de CQ diario desencadena un mensaje de correo electrónico por nodo Mongo para las notificaciones WorkflowCompleted y WorkflowAborted. NPR-22515: revisión para CQ-4238172
* La ejecución del flujo de trabajo de recursos de actualización de DAM genera una NullPointerException. NPR-23010: revisión para Granite-21096
* El paso del proceso de flujo de trabajo no muestra secuencias de comandos de /etc/workflow/scripts. NPR-23263: revisión para Granite-20775
* El paso Participante dinámico del flujo de trabajo no muestra scripts de /apps/workflow/scripts. NPR-23464: revisión para Granite-21276
* No se puede editar ningún flujo de trabajo después de editarlo una vez. NPR-23742: revisión para CQ-4238526
* (IU clásica) Al editar los iniciadores del flujo de trabajo, las condiciones desaparecen, lo que provoca que los flujos de trabajo se inicien sin condiciones. NPR-23835: revisión para CQ-4239153
* Bandeja de entrada del proyecto: al cambiar a la vista de calendario se muestra el contenido de la bandeja de entrada principal. NPR-23947: revisión para CQ-4241236
* Debe exponer los detalles de carga útil en el paquete para que el componente HTL pueda mostrar el valor en la vista de lista. NPR-23948: revisión para CQ-4240953
* No se pueden almacenar los datos del cuadro de diálogo en el paso Participante del cuadro de diálogo. NPR-23965: revisión para CQ-4234123
* (IU táctil) Al guardar un modelo de flujo de trabajo, el botón &quot;Sincronizar&quot; cambia a &quot;Sincronizado&quot;, lo que provoca errores ortográficos. Revisión para CQ-4244843
* Bandeja de entrada del proyecto: al cambiar a la vista de calendario se muestra el contenido de la bandeja de entrada principal. Revisión para CQ-4244436
* No se pueden seleccionar los cuadros de diálogo en el paso Participante en el cuadro de diálogo. Revisión para CQ-4244532
* Backport proactivo para correcciones de granite.omnisearch.core. NPR-23536
* Problema en la aplicación Mobile Workspace 6.4 con la tarea compartida. NPR-26383

**WCM: traducción**

* (Panel de referencia) Los trabajos de traducción no se ejecutan durante la creación del proyecto. Revisión para CQ-4245327

**WCM: administrador de varios sitios (MSM)**

* (MSM) Mejora del rendimiento del lanzamiento. Revisión para CQ-4231488
* (MSM) Brecha de tiempo en la escucha de eventos entre el evento que se está produciendo y la gestión de eventos. Revisión para CQ-4227766

**Pantallas**

* La página de pantalla falla con un error debido a la falta de dependencias para screens-core-pkg:1.4.42. Revisión para CQ-4245918

**Proyectos: traducción**

* (Fragmento de contenido) La copia de idioma para los recursos incrustados no se crea mientras el recurso en inglés se añade a la traducción. Revisión para CQ-4243477
* El menú desplegable msft config muestra la configuración de /libs(6.4 configs)en lugar de /etc(6.3 configs) en el modo heredado. Revisión para CQ-4243475
* Promocionar y eliminar automáticamente los lanzamientos de traducción en proyectos de traducción. Revisión para CQ-4243474
* El fragmento de contenido dentro de los sitios no se traduce. Revisión para CQ-4243482, CQ-4243483, CQ-4245687
* Error del servidor al abrir el filtro de búsqueda de trabajos de traducción. Revisión para CQ-4236813
* El menú desplegable de la configuración de Credential está en blanco incluso después de que tif esté presente en /conf/we-retail. Revisión para CQ-4236315

**Administración de fragmentos de contenido**

* Al eliminar un componente, se rellenan los registros con trazas de pila. Revisión para CQ-4242315

**DAM: General**

* Al cerrar la vista de detalles de un recurso, se devuelve a una página de resultados de búsqueda incorrecta. Revisión para CQ-4240960
* (Camera Raw) Falta la opción de ajuste de imagen. Revisión para CQ-4246121
* IndexOutOfBoundException: Informe de modificación de los recursos de OOTB. Revisión para CQ-4239744
* Elimine la puntuación de confianza del csv del informe. Revisión para CQ-4241491
* Envío de correo electrónico compartido de vínculos roto para remitente no &quot;administrador&quot;. Revisión para CQ-4240357
* Corrección de errores de TI. Revisión para CQ-4249891

**DAM: Brand Portal**

* Las propiedades de los recursos solo listan 3 propiedades en la primera ficha, por lo que todas las pestañas parecen vacías. Revisión para CQ-4242503
* Los predicados de tipo de archivo y tamaño de archivo no están disponibles en el formulario de búsqueda publicado. Revisión para CQ-4242026
* La búsqueda en el predicado de directorios debe filtrarse hacia fuera o no mostrarse en los filtros de búsqueda. Revisión para CQ-4241386
* La búsqueda predeterminada de debe existir después de cancelar la publicación. Revisión para CQ-4241383, CQ-4241113
* El gesto Publicar en Brand Portal no funciona para los ajustes preestablecidos de imagen. Revisión para CQ-4241074
* Publicar en Brand Portal no funciona para colecciones. Revisión para CQ-4241122, CQ-4246558

**DAM: Cliente DM**

* Al actualizar a la versión 6.4, se eliminan los perfiles de codificación de vídeo creados anteriormente. Revisión para CQ-4244067
* El atributo Texto alternativo se desglosa en el componente Dynamic Media. Revisión para CQ-4244081
* (DMS7) La edición de conjuntos remotos en AEM no se sobrescribe en Scene7. Revisión para CQ-4243430
* Verificación de la versión 6.4 de SP1 basada en DM Hybrid. Revisión para CQ-4244623
* (DMS7-UA) Al hacer clic en el botón Incrustar de un recurso de vídeo publicado, no parece que ocurra nada. Se espera que el cuadro de diálogo Incrustar se muestre con el código del HTML. Revisión para CQ-4245237
* (MDL híbrido) Copiar URL para los activos de vídeo publicados o los conjuntos de medios mixtos obtiene &quot;`[object Object]`&quot; en el cuadro de diálogo URL. Revisión para CQ-4245236, CQ-4245451
* (DMHybrid) La página Vista de detalles del vídeo no contiene la vista previa del recurso de vídeo y envía un mensaje de error a la consola. Revisión para CQ-4244320
* Codificación automática S7 del contenido de we.retail. Revisión para CQ-4242253
* Los ajustes preestablecidos de procesamiento de vídeo de preactualización no pueden tener un nuevo ajuste preestablecido de codificación de vídeo añadido ni editar los ajustes preestablecidos de codificación existentes. Revisión para CQ-4240407
* Los ajustes preestablecidos de imagen de preactualización se muestran como No publicado en la página Representaciones y no arroja una URL. Revisión para CQ-4240406
* (CSS) Se muestran los recursos, pero los visualizadores utilizados son predeterminados y no los visualizadores OOTB. Revisión para CQ-4239839
* Se ha deshabilitado la ejecución manual del paso de limpieza y se han utilizado clases de coral privadas. Revisión para CQ-4239729
* El visor de imágenes genera un error y no muestra el recorte inteligente correcto. Revisión para CQ-4237564
* El ajuste preestablecido heredado en /etc parece estar roto y no se migra a la ubicación en /conf después de guardar. Revisión para CQ-4237416
* Regresión en OOB VideoViewer 5.8.x : el visor amplía el iframe a la derecha, por lo que se rompe el diseño de la página. Revisión para CQ-4235465
* (DMS7) La URL de representación de recorte inteligente y los botones Incrustar están activos para las imágenes que no se han publicado. Revisión para CQ-4233696
* (DMHybrid) Restaure la función de recorte/rotación anterior. Revisión para CQ-4239489
* Al previsualizar un vídeo en la vista de tarjeta, el botón de reproducción no se pone en pausa. Revisión para CQ-4238592
* Al realizar una actualización de Opt-In, la configuración de YouTube no se mueve ni copia de su antigua ubicación a la nueva ubicación. Revisión para CQ-4238590
* DropDos perfiles de procesamiento de vídeo AVS de OOTB se enumeran en Propiedades de carpeta y solo uno contiene codificaciones definidas. Revisión para CQ-4238096
* (DMS7) Recorte inteligente: Vista de detalles: El botón URL se denomina botón Copiar para las representaciones. Revisión para CQ-4237804
* La página de listado de ajustes preestablecidos de visor permanece en blanco incluso después de ejecutar los comandos curl. Revisión para CQ-4243246
* Se ha deshabilitado la ejecución manual del paso de limpieza y el uso de clases de coral privadas. Revisión para CQ-4239729
* La página Detalles del informe de vídeo no muestra recursos de vídeo. Revisión para CQ-4246208

**DAM: DMServices**

* Configuración de nube (DMS7): No se puede sincronizar contenido nuevo con Scene7 después de actualizar a SP1. Revisión para CQ-4244437
* (DMHybrid) Los perfiles de color y la configuración del catálogo no se registran en una llamada debug_info=catalog. Revisión para CQ-4242346
* Añadir perfiles de color a la configuración del cliente en los servidores de envío. Revisión para CQ-4241818, CQ-4241819
* (DMHybrid) Después de 6.3 &amp;gt; actualización 6.4, la configuración del catálogo se mueve al nodo incorrecto. Revisión para CQ-4239974, CQ-4239975
* (DMHybrid) pushviewerpresets script no crea los nodos necesarios para modificar la configuración del catálogo. Revisión para CQ-4240076
* Al utilizar la selección desplegable &quot;Formato&quot; y seleccionar los formatos PNG o JPG, el archivo descargado se muestra como saturado y más oscuro que el recurso original. Revisión para CQ-4240073
* (DMS7) Elimine la asignación de tipo MIME: image_x-eps. Revisión para CQ-4240394
* (DMS7) Los parámetros de carga para el fondo de knockout no pasan ipsApiService.log y, por lo tanto, no funcionan. Revisión para CQ-4240686
* Al actualizar los perfiles de procesamiento de imágenes creados en una instancia de 6.3 a 6.4, se rompe la propiedad &quot;Crop-type&quot;. Revisión para CQ-4237739
* (Dynamic Media) La carga regular de recursos fuera de la carpeta de recorte inteligente falla. Revisión para CQ-4237670
* Ajuste el código de reserva de perfil para el nombre de perfil &quot;Codificación de vídeo adaptable&quot; a &quot;Codificación de vídeo adaptable&quot;. Revisión para CQ-4237666
* Los datos EmbedXMP siempre se definen como “activos” para el proceso de generación de Ptiff. Revisión para CQ-4234498
* La representación de la imagen CMYK tiene una saturación incorrecta. Revisión para CQ-4235470
* La configuración del servidor de imágenes no se replica en la entrega mientras los registros de replicación los marcan como correctos. Revisión para CQ-4239480, CQ-4239046
* (DMS7) No se pueden crear conjuntos utilizando referencias antiguas/nuevas a la Configuración de nube. Revisión para CQ-4238078
* El paso del flujo de trabajo de Scene7 solo lee Scene7 en el nombre y la descripción, pero no aclara el paso del flujo de trabajo en el flujo de trabajo de actualización de DAM. Revisión para CQ-4237865

**DAM: Etiquetas inteligentes**

* Presentado [Etiquetas inteligentes mejoradas](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951

**Forms**

Las correcciones de AEM Forms se entregan mediante paquetes de complementos y otros instaladores de parches que se proporcionan con la versión. Para obtener más información, consulte Versiones de AEM Forms.

Los aspectos destacados de AEM Forms son:

* Presentación de AEM Forms [capacidad de informes de transacciones](https://docs.adobe.com/content/help/en/experience-manager-64/forms/transaction-reports/transaction-reports-overview.html) para rastrear y mantener el recuento de transacciones como formularios enviados, documentos procesados y documentos procesados en su implementación de AEM Forms. Proporciona perspectivas sobre el uso de productos y ayuda a los usuarios empresariales a comprender los volúmenes de procesamiento digital.
* Se ha habilitado la compatibilidad con el PDF/UA en los formularios XML.
* Se ha añadido allowProxy = true para Clientlib **aemfd.ccm.channel.contentpage**
* Se ha actualizado el código para que la búsqueda de título avanzada se realice tal cual contiene en lugar de ser igual a .
* Actualice a la nueva versión del administrador de paquetes de nodos (NPM) en el equipo de integración continua.

**Paquete de complemento de Forms**

**Integración de back-end**

* Se genera un error al proporcionar null como valor a un campo opcional. NPR-24397
* La invocación de WSDL da error cuando el elemento tiene un área de nombres diferente del global. NPR-24281
* (WSDL FDM) Obteniendo DermisException: Datos de lista exceptuados en el caso de matriz de tipo de propiedad. NPR-24265
* (WSDL FDM) Obteniendo DermisException: java.lang.Exception: createSOAPParam: Parámetros no válidos. NPR-24264
* (SDK de cliente de FDM) No se puede realizar la prueba del preprocesador o posterior y la acción de envío personalizada. Revisión para CQ-4238469
* Correcciones para problemas de Javadoc en Dermis. Revisión para CQ-4244250
* Se mejoró la entrada en el lenguaje de descripción de servicios web (WSDL). Revisión para CQ-4244133
* La prueba de autenticación básica para WSDL produce un error diferente para la misma configuración en AEM 6.3 y AEM 6.4. Revisión para CQ-4244132
* Solicitud para incluir ValueUtil en client-sdk y javadocs. Revisión para CQ-4242803
* (Configuración de nube FDM) No se puede configurar la autenticación basada en SOAP desde la configuración de nube. Revisión para CQ-4238462
* Dermis - Añade paquetes que faltan en Javadocs. Revisión para CQ-4242815
* WSDLInvokerParams se incluirá en el sdk del cliente del complemento de Forms. NPR-23381: revisión para CQ-4240233

**Formularios adaptables**

* La representación del documento (IC) debe registrarse como una transacción mediante el servicio de registro de transacciones. Revisión para CQ-4245333
* Al ejecutar UAT5, falta una entrada en el pdf generado en la fase de verificación. Revisión para CQ-4243184
* Caso de prueba para una copia profunda de guideContext. Revisión para CQ-4242924
* Falta el campo de tipo de prueba al ejecutar el UAT3 en el servidor actualizado más reciente. Revisión para CQ-4243120
* En el servidor actualizado, al formulario enviado le faltan los valores de estado, provincia, región y país que estaban presentes en el servidor anterior a la actualización. Revisión para CQ-4241444
* (Editor de expresiones) Error al navegar a la etapa de verificación durante el envío del formulario. Revisión para CQ-4241384
* Faltan valores en la fase de verificación del servidor actualizado y anterior a la actualización del formulario enviado. Revisión para CQ-4241896
* El botón Salir y guardar en la parte inferior de la página no funciona. Revisión para CQ-4240112
* Falta el número de contacto en la configuración actualizada. Revisión para CQ-4239870
* En `ACTION TAKEN` en la pestaña Tipo de disputa , &quot;Documentos adicionales para apoyar mi reclamación&quot; tiene un campo adicional Tipo de prueba guardado &quot;en él. Revisión para CQ-4239873
* Error &quot;Error en getDataAPI&quot; encontrado en la fase verifyPdf. Revisión para CQ-4239865
* Errores en los registros de migración para la instancia de autor y publicación. Revisión para CQ-4239365
* Errores en los registros de migración para la instancia de autor y publicación. Revisión para CQ-4239635
* Error de deserialización como &quot;Deserialización no permitida para la clase sun.util.calendar.ZoneInfo&quot; en registros de error después del envío de un formulario adaptable. Revisión para CQ-4240419
* El campo de estado no se rellena en la representación de formularios de Mobile. Revisión para CQ-4240597
* Elimine el uso de referencia de los componentes de las plantillas de la lista de anti-patrones. Revisión para CQ-4239217
* HTML5 Numeric Box establecida como Float o Decimal ofrece diferentes resultados de validación en distintos navegadores. NPR-23528: revisión para CQ-4244097
* (Carga de imagen) La imagen no se muestra en la vista previa del DOR. Revisión para CQ-4243178
* El servidor JEE genera un error al intentar enviar el formulario adaptable con &quot;PDF de correo electrónico&quot; e &quot;Incluir archivos adjuntos&quot;. Revisión para CQ-4239894
* El gráfico no se traza durante la ejecución utilizando la tabla o el panel. Revisión para CQ-4240010
* El envío del formulario adaptable no funciona y no hay cambios en el recuento de transacciones debido a un error en el envío. Revisión para CQ-4246125
* (Opción de imagen) El documento de las opciones de registro no está visible. Revisión para CQ-4236976
* La interfaz de usuario del editor de plantillas no es estable. Revisión para CQ-4241497
* Los AF no se muestran mediante la ficha activos del panel lateral, mientras que se muestra mediante la opción Examinar AEM cuadro de diálogo de propiedades de componentes de formulario. Revisión para CQ-4236751
* El ID de flujo de trabajo generado para la conversión de formularios debe estar disponible en el formulario adaptable generado. Revisión para CQ-4240014
* No se puede seleccionar la plantilla para crear una página en los sitios en Actualización directa: Livecycle al servidor 6.4. Revisión para CQ-4241300

**Servicio del ensamblador**

* Registro de transacciones en Assembler Services. Revisión para CQ-4245018, CQ-4245017, CQ-4245016.
* La transacción no se notifica cuando la conversión de PDF/A se realiza mediante DDX. Revisión para CQ-4246039

**Administrador de Forms**

* Lista de botones CREATE de FM para ordenarlos alfabéticamente. Revisión para CQ-4242307

**Portal de formularios**

* Los borradores guardados en el servidor de preactualización no se abren correctamente en el servidor actualizado. Revisión para CQ-4243303
* Actualización de la versión a 7.1 para adobe-formsmanager-core-module. Revisión para CQ-4245753
* Los borradores guardados en el servidor de preactualización no se abren correctamente en el servidor actualizado. Revisión para CQ-4243303
* Los escenarios de archivos adjuntos se rompen al reemplazar, agregar o quitar archivos adjuntos en la nueva instancia/misma instancia del borrador. Revisión para CQ-4243165
* El recuento de borradores recuperados de consultar la base de datos es superior al recuento de borradores presentes en el portal. Revisión para CQ-4241489
* Forms enviado en el servidor de actualización previa no está presente en el servidor actualizado. Revisión para CQ-4241490
* El formulario que se muestra en la interfaz de usuario en la pestaña de envíos está en estado No enviado a pesar de que el mensaje de envío se ha realizado correctamente. Revisión para CQ-4241487
* El guideContext debe formarse copiando en profundidad los campos, ya que guideContext contiene customPropertyMap que es un objeto. Revisión para CQ-4240126
* Error al intentar guardar un formulario. Revisión para CQ-4240763
* La entrada para formularios guardados y enviados se rellena en crx/de a pesar de que tenemos la configuración de base de datos proporcionada en Borrador del portal de Forms y configuración de envío. Revisión para CQ-4240726
* (Buscar y listar) El valor fijo del título de búsqueda avanzada debería funcionar como contiene en lugar de como igual. Revisión para CQ-4245499

**Mobile Forms**

* El campo de fecha se superpone en Mobile Forms. Revisión para CQ-4242256
* El envío de formularios para Mobile Forms debe registrarse como una transacción mediante el servicio de registro de transacciones. Revisión para CQ-4246166
* El envío de formularios en Forms set debe registrarse como una transacción mediante el Servicio de registro de transacciones. Revisión para CQ-4246165

**Aplicación de AEM Forms**

* (Aplicación de Windows) No se puede procesar el formulario. Revisión para CQ-4238005

**OSGI de flujo de trabajo**

* Registro de transacciones en Tarea de asignación de flujo de trabajo. Revisión para CQ-4244440
* (Paso FDM) No se pueden utilizar valores de metadatos de flujo de trabajo cuando se inserta un paso Asignar tarea entre el paso de proceso y el paso fdm. Revisión para CQ-4241472
* La delegación de la tarea de asignación no funciona en la integración de Forms en los flujos de trabajo OSGI. NPR-23709: revisión para CQ-4243700
* (Editor del modelo de flujo de trabajo) Algunos modelos de flujo de trabajo no se pueden editar mediante el editor del modelo WF de la IU clásica. Revisión para CQ-4241151

**Documento multicanal**

* El campo Fecha de la plantilla se superpone con el subformulario en la creación IC. Revisión para CQ-4240110
* No se debe permitir que el encabezado se elimine o se mueva hacia arriba y hacia abajo en la creación de canales web IC. Revisión para CQ-4243358
* (Editor de CI) Las filas predeterminadas se establecerán en 1 para los componentes de tabla. Revisión para CQ-4244848
* Área de destino para permanecer visible incluso después de arrastrar el contenido y soltarlo sobre él. Revisión para CQ-4244534
* El canal web no reconoce el espacio de pestañas en los fragmentos de documento de texto. Revisión para CQ-4244481
* (Canal de impresión) La representación del documento (IC) debe registrarse como una transacción mediante el servicio de registro de transacciones. Revisión para CQ-4245335
* (Canal web) La representación del documento (IC) debe registrarse como una transacción mediante el servicio de registro de transacciones. Revisión para CQ-4245334
* La búsqueda de contenedores de documentos o el árbol del modelo de datos deben estar unificados a la búsqueda de filtros de recursos. Revisión para CQ-4242305
* (Fragmento de documento) La propiedad de sangría aplica sangría al texto según la cantidad de unidades que no se pueden comprender. Revisión para CQ-4241082, CQ-4240643
* (Editor IC) El icono Editar fragmento en el mosaico del fragmento de documento que aparece en la ficha Recursos no es muy fácil de descubrir y entender. Revisión para CQ-4241047
* Permita el acceso anónimo a la biblioteca de cliente de IC Anonymous inaccesible. Revisión para CQ-4245588
* (Canal web) Los datos no se resuelven en ninguna de las tablas de la vista previa web y se muestran como en blanco. Revisión para CQ-4244476
* Los encabezados de tabla se muestran como variables en el canal web en la generación automática. Revisión para CQ-4244242
* (Editor IC) El contenido de un fragmento de documento utilizado en un IC debe cambiarse de tamaño automáticamente para ajustarse a la anchura del área de destino. Revisión para CQ-4244094
* El nombre del canal que se muestra en la parte superior central debe ser coherente para el título IC de WEB/PRINT. Revisión para CQ-4242498
* El panel de objetos de datos del editor de texto solo debe incluir entidades de nivel superior, revisión para CQ-4244121
* El nombre predeterminado no se asigna al agregar un componente nuevo en el editor. Revisión para CQ-4244691
* Añadir la configuración de Colspan en todos los componentes del canal web. Revisión para CQ-4244946
* La propiedad Ancho de tabla del fragmento de diseño no se restablece y respeta en el canal de impresión Carta o Comunicación del cliente. Revisión para CQ-4241574

**Administración de correspondencia**

* Subtítulos eliminados de la plantilla de letras después de editar un recurso de texto que contiene marcadores de posición. NPR-24196
* El archivo XDP, cuando se carga y utiliza como diseño para plantillas de letras, no puede previsualizar ni editar las plantillas. NPR-24143: revisión para CQ-4244407
* La selección de asignación está seleccionada de forma predeterminada en el fragmento de lista. Revisión para CQ-4240097
* Editor de condiciones : la evaluación de varios resultados debe estar habilitada de forma predeterminada. Revisión para CQ-4240096
* La imagen que se elimina de la lista sigue mostrando la imagen en la vista previa. Revisión para CQ-4239909
* El conjunto de reglas del módulo de condiciones se establece como &#39;Predeterminado&#39; para todos los módulos. Revisión para CQ-4239878
* La creación del diccionario de datos falla con el error &quot;Excepción de JCR desconocida&quot;. Revisión para CQ-4244122
* Lagunas en JavaDocs de contenido 6.3. Revisión para CQ-4213586

**Instalador JEE de Forms**

**Núcleo**

* (HTML Workspace) Falta información de seguimiento para las aplicaciones con el símbolo entre paréntesis en el nombre. NPR-23402

**Servicio PDFG**

* Registro de transacciones en los servicios PDFG. Revisión para CQ-4244951, CQ-4244586
* Reducir los PDF al desincrustar selectivamente las fuentes a través de una sola llamada API. NPR-23287
* Problema de actualización de las configuraciones de PDFG en AEM actualización. Revisión para CQ-4241176
* Registro de transacciones en PDFUtility Service. Revisión para CQ-4245014

**Administración de procesos**

* (Espacio de trabajo HTML) Los puntos de inicio del proceso no se ordenan en orden alfanumérico. Revisión para CQ-4239629
* (espacio de trabajo del HTML) Prepare la llamada de datos que aparece dos veces cuando el borrador se abre la primera vez. Revisión para CQ-4243280
* (HTML Workspace) El proceso de preparación de datos se activa al cerrar un formulario. Revisión para CQ-4239456
* El espacio de trabajo se bloquea cuando se atraviesa entre dos tareas. Revisión para CQ-4237125

**Workbench**

* El proceso Administrar perfil de acción Preparar datos falla cuando la configuración predeterminada del proceso de procesamiento está establecida en HTML. Revisión para CQ-4244292

**Forms Designer**

* Agregue compatibilidad con PDF/UA a los formularios XML generados mediante Designer y el servicio de salida. NPR-23022
* Los hipervínculos en línea definidos en Designer no se etiquetan ni tienen texto alternativo cuando se guardan como PDF desde Designer. NPR-23023

**Paquetes de funciones incluidos**

**Recursos**

* Se ha agregado la capacidad de Etiquetas inteligentes mejoradas. Para obtener más información, consulte [Etiquetas inteligentes mejoradas](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/enhanced-smart-tags.html). NPR-21951: revisión para CQ-4234883
* Se han introducido las referencias de AEM Assets en InDesign. Para obtener más información, consulte [Referencias de AEM Assets en InDesign](/help/assets/managing-linked-subassets.md). NPR-23386

**Sitios**

* (Creación de páginas) Mejoras en el Editor de imágenes. Para obtener más información, consulte [Editor de imágenes](https://docs.adobe.com/content/help/en/experience-manager-64/developing/components/image-editor.html). NPR-24267: revisión para CQ-4245502

**Paquetes de contenido y paquetes OSGI incluidos**

Los siguientes documentos de texto enumeran los paquetes OSGI y los paquetes de contenido incluidos en el CFP.

Lista de paquetes OSGi incluidos en AEM 6.4.1.0

[Obtener archivo](assets/6_4_1_0_bundle-list.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.1.0

[Obtener archivo](assets/6_4_1_0_content-package-list.txt)

### Instalar 6.4.8.0 {#install}

#### Requisitos de configuración {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Para los clientes con Feature Packs instalados en AEM 6.4. Los Feature Packs opcionales proporcionados por Adobe dependen de la versión de la versión y del Service Pack. Si tiene instalado algún paquete de funciones, póngase en contacto con el equipo de atención al cliente de AEM para validar la compatibilidad de esos paquetes de funciones con este paquete de servicios para AEM 6.4.

* AEM 6.4.8.0 requiere AEM 6.4. Para obtener más información, consulte [documentación de actualización](../sites-deploying/upgrade.md).
* La descarga del Service Pack está disponible en [Portal de distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/es/aem.html) para descargar.
* En una implementación con MongoDB y varias instancias, instale AEM 6.4.8.0 en una de las instancias de creación mediante el Administrador de paquetes.
* Antes de instalar el paquete de servicio, asegúrese de disponer de una instantánea o una copia de seguridad nueva de su instancia de AEM.
* Reinicie la instancia antes de la instalación. Aunque solo es necesario cuando la instancia sigue en modo de actualización (y este es el caso cuando la instancia se actualizó desde una versión anterior), normalmente se recomienda si la instancia se ejecutó durante un período de tiempo más largo.

>[!NOTE]
>
>Adobe no recomienda quitar o desinstalar el paquete AEM 6.4.8.0.

### Instalación del Service Pack mediante el Administrador de paquetes {#install-the-service-pack-via-package-share}

Siga estos pasos para instalar el paquete de servicio en una instancia de AEM 6.4 existente:

1. Descargue el paquete desde Distribución de software.

1. En AEM, inicie sesión en el Administrador de paquetes y añada el paquete AEM 6.4.8.0 descargado. Seleccione el paquete cargado y haga clic en **[!UICONTROL Instalar]**.

>[!NOTE]
>
>**El cuadro de diálogo en la IU del administrador de paquetes a veces se cierra de forma precipitada durante la instalación de 6.4.8.0**
>
>Por lo tanto, se recomienda esperar a que los registros de errores se estabilicen antes de acceder a la instancia. El usuario debe esperar a que se produzcan registros específicos relacionados con la desinstalación del paquete de actualización antes de asegurarse de que las instalaciones se realicen correctamente. Suele suceder en Safari, pero puede suceder de forma intermitente en cualquier navegador.

### Instalación automática {#auto-installation}

Existen dos formas de instalar automáticamente AEM 6.4.8.0 en una instancia en ejecución:

A. Coloque el paquete en .Carpeta */crx-quickstart/install* mientras se ejecuta el servidor. El paquete se instala automáticamente.

B. Utilice la variable [API HTTP del Administrador de paquetes](/help/sites-administering/package-manager.md) - asegúrese de usar `cmd=install&recursive=true` - por lo que el paquete anidado está instalado.

>[!NOTE]
>
>AEM 6.4.8.0 no admite la instalación de Bootstrap.

### Validar la instalación {#validate-install}

1. La página Información del producto (*/system/console/ productinfo *) debería mostrar la cadena de versión actualizada &quot;Adobe Experience Manager, versión 6.4.8.0&quot; en Productos instalados.
1. Todos los paquetes OSGI tienen el valor ACTIVO o FRAGMENTO en la consola OSGI (utilice la consola web:/system/console/bundles).
1. El paquete OSGI org.apache.jackrabbit.oak-core está en la versión 1.8.17 o superior (utilice la consola web: /system/console/bundles).

Para determinar la plataforma certificada para ejecutarse con esta versión de AEM Sites y Assets, consulte [Requisitos técnicos](../sites-deploying/technical-requirements.md).

>[!NOTE]
>Al instalar correctamente el paquete, aparece un >mensaje informativo indicando que el contenido >paquete se ha instalado correctamente, como **&quot;Paquete de contenido AEM-6.4-Service-Pack-7 instalado correctamente&quot;.**

### Actualización de visores de Dynamic Media (5.10.1) {#update-dynamic-media-viewers}

<p id="Dynamic">AEM 6.4.8.0 contiene una nueva versión de visores de Dynamic Media (5.10.1) que permite comprobar si hay nombres duplicados en la página Ajuste preestablecido de imagen. Se recomienda a los clientes de Dynamic Media que ejecuten el siguiente comando para que los ajustes preestablecidos de visor estén actualizados.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

que copiará los nuevos ajustes preestablecidos de visor en la ubicación /conf.

### Instalación del paquete de complementos para AEM Forms {#install-aem-forms-add-on-package}

#### Instalación de complementos para AEM Forms {#installaemformsaddon}

>[!NOTE]
>
>Omita este paso si no utiliza AEM Forms. Las correcciones en AEM Forms se entregan mediante un paquete de complementos independiente.

>[!NOTE]
>
>AEM 6.4.8.0 incluye una nueva versión del [paquete de compatibilidad de AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). Si utiliza una versión anterior del paquete de compatibilidad de AEM Forms y actualiza a AEM 6.4.8.0, instale la versión más reciente del paquete de compatibilidad de AEM Forms después de la instalación del paquete de complementos de Forms.

1. Asegúrese de que ha instalado el Service Pack de AEM.
1. Descargue el paquete de complementos de formularios correspondiente que aparece en [Versiones de AEM Forms](https://helpx.adobe.com/es/aem-forms/kb/aem-forms-releases.html) para su sistema operativo.
1. Instale el paquete de complementos de formularios como se describe en [Instalación de paquetes de complementos de formularios AEM](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Instalación del instalador de AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Omita este paso si no utiliza AEM Forms en JEE. Las correcciones en el instalador JEE de AEM Forms se entregan mediante un instalador independiente.

Para obtener información sobre la instalación del instalador acumulativo para AEM Forms JEE y la configuración posterior a la implementación, consulte [Instalador de parches JEE de AEM Forms 0015](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0015.html).

#### Ajustes de configuración necesarios para NPR-21268 {#configuration-settings-required-for-npr}

Si utiliza la IU clásica (antigua) y ha creado plantillas de metadatos con ella, siga los pasos para ejecutar el script JMX para preservarlos:

1. Vaya a /system/console/jmx.
1. Haga clic en &quot;Migrar plantillas de metadatos&quot;.
1. Haga clic en &quot;migrarMetadataTemplatesAtPath&quot; y proporcione la ruta de la carpeta en la que desea que se mantengan las plantillas de metadatos.

#### Ajustes de configuración necesarios para NPR-24536 {#configuration-settings-required-for-npr-1}

El recuento de la Cola compartida no se actualiza de forma predeterminada para otros usuarios cuando un usuario solicita una tarea. Para ello, hemos introducido una nueva propiedad. Siga los pasos a continuación para configurar esta propiedad en la instancia de AEM:

1. Vaya a la IU de Administración -> Services -> Workspace -> Global administration.
1. Exporte la configuración Global.
1. En el archivo XML descargado, añada la etiqueta &lt;client_taskspollinginterval>10&lt;/client_taskspollinginterval> En este caso, 10 es el valor de ejemplo en segundos. Puede modificarlo en consecuencia.
1. Guarde el archivo.
1. Vuelva a la IU de Administración -> Services -> Workspace -> Global administration.
1. Importe el archivo xml en la sección Importar configuración global.
1. Ahora puede cerrar la sesión del sistema y volver a iniciarla.
1. Recuento de inicios de cola compartidos que se actualizan para otros usuarios del espacio de trabajo.
1. Para desactivar la encuesta, cambie el valor a 0 y vuelva a importar el archivo XML.

### Uber Jar {#uber-jar}

El Uber Jar para AEM 6.4.8.0 está disponible en el [Repositorio de Maven público de Adobe](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8/).

Para usar Uber Jar en un proyecto de Maven, consulte el artículo [Cómo usar Uber Jar](../sites-developing/ht-projects-maven.md) e incluya la siguiente dependencia en el elemento POM de su proyecto:

```shell
<dependency>
      <code>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

### Funciones eliminadas u obsoletas {#removed-deprecated-features}

Esta sección enumera las funciones y capacidades que se han eliminado o dejado de utilizar en AEM 6.4.

| Área | Función | Reemplazo | Versión |
|---|---|---|---|
| Recursos | Administrar acción de etiqueta para subrecursos | Sin reemplazo | AEM 6.4.2.0 |
| Integración de Assets y Adobe Creative Cloud | [AEM para uso compartido de la carpeta Creative Cloud](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) se introdujo en AEM 6.2 como una forma de proporcionar a los usuarios creativos acceso a los recursos de AEM. Adobe Asset Link, la nueva capacidad de la aplicación Creative Cloud, proporciona experiencia de usuario mejorada y un acceso más eficaz a los recursos de AEM directamente desde Photoshop, InDesign e Illustrator. Adobe no realizará más mejoras en la funcionalidad de uso compartido de carpetas. Aunque la función está incluida en AEM, se recomienda a los clientes utilizar la sustitución. | Adobe Asset Link o aplicación de escritorio. Para obtener más información, consulte el artículo sobre la [integración de AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

### Problemas conocidos {#known-issues}

* Durante la instalación pueden aparecer los siguientes errores y advertencias:

   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Tiempo de espera de que el cambio de registro se complete sin registrar.
   * `com.adobe.granite.maintenance.impl.TaskScheduler` no se encontraron ventanas de mantenimiento en granite/operations/maintenance
   * `com.adobe.cq.com.adobe.cq.ui.commons bundle com.adobe.cq.com.adobe.cq.ui.commons:1.2.28 (204)[com.adobe.cq.ui.wcm.commons.internal.servlets.rte.RTEFilterServletFactory(573)]`: El método unbindModif ha generado una excepción (java.lang.IllegalStateException: Servicio ya no registrado).
Estos errores no requieren ninguna acción, ya que no afectan a la instancia de AEM.

### Problemas resueltos {#resolved-issues}

**AEM 6.4.4.0**

* No se observa ningún error de recurso al importar/exportar metadatos. CQ-4253263
* No se puede editar ningún componente de imagen y propiedades de página después de aplicar 6.4.3.0 sobre 6.4.2.0. CQ-4260316 y CQ-4260441 Para solucionar este problema:
   * Vaya al Administrador de paquetes
   * Vuelva a instalar el paquete &quot;cq-ui-wcm-admin-content-1.0.1004.zip&quot;
   * Recompilar todos los JSP `(http://<AEM HOST>:<AEM PORT/system/console/slingjsp)` O Reinicie la instancia.

### Paquetes de contenido y paquetes OSGi incluidos {#osgi-bundles-and-content-packages-included}

Los siguientes documentos de texto enumeran los paquetes OSGi y los paquetes de contenido incluidos en AEM 6.4.8.0.

Lista de paquetes OSGi incluidos en AEM 6.4.8.0

[Obtener archivo](assets/6.4.8.0_osgi_bundles.txt)

Lista de paquetes de contenido incluidos en AEM 6.4.8.0

[Obtener archivo](assets/6.4.8.0_content_packages.txt)

### Recursos útiles {#helpful-resources}

* [Notas de la versión de AEM 6.4](../release-notes/release-notes.md)
* [Página de productos AEM](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentación de AEM 6.4](https://experienceleague.adobe.com/docs/experience-manager-64.html?lang=es)
* Suscripción a las [actualizaciones prioritarias de productos de Adobe](https://www.adobe.com/subscription/priority-product-update.html)

### Sitios restringidos {#restricted-sites-new}

Estos sitios solo están disponibles para los clientes. Si es un cliente y requiere acceso, póngase en contacto con su administrador de cuentas de Adobe.

* [Descarga de productos en licensing.adobe.com](https://licensing.adobe.com/).
* Actualizaciones, parches y paquetes de productos para obtener funcionalidad adicional en [Distribución de software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* [Asistencia al cliente mediante Admin Console](https://adminconsole.adobe.com/). Para obtener más información, consulte [Nueva experiencia de asistencia al cliente de Adobe](https://docs.adobe.com/content/help/en/customer-one/using/home.html).
