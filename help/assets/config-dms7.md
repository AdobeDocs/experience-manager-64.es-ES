---
title: 'Configuración de Dynamic Media: modo Scene7'
seo-title: 'Configuración de Dynamic Media: modo Scene7'
description: 'Información sobre cómo configurar Dynamic Media: modo Scene7.'
seo-description: 'Información sobre cómo configurar Dynamic Media: modo Scene7.'
uuid: 81cc208b-e95d-4a01-9817-2b6d50cfe8b8
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: cd3adbac-9868-4838-9d8a-37dde8973df4
translation-type: tm+mt
source-git-commit: df92346ca23161b8eaff293a6b9f2c8b7c72e2ec
workflow-type: tm+mt
source-wordcount: '5571'
ht-degree: 4%

---


# Configuración de Dynamic Media: modo Scene7 {#configuring-dynamic-media-scene-mode}

Si utiliza la configuración de Adobe Experience Manager para distintos entornos, como uno para desarrollo, uno para ensayo y otro para producción en directo, deberá configurar Cloud Services de Dynamic Media para cada uno de esos entornos.

## Diagrama de arquitectura de Dynamic Media: modo Scene7 {#architecture-diagram-of-dynamic-media-scene-mode}

El diagrama de arquitectura siguiente describe el funcionamiento del modo Dynamic Media - Scene7.

Con la nueva arquitectura, AEM es responsable de los recursos principales y de las sincronizaciones con Dynamic Media para el procesamiento y la publicación de recursos:

1. Cuando el recurso principal se carga en AEM, se replica en Dynamic Media. En ese momento, Dynamic Media gestiona todo el procesamiento de recursos y la generación de representaciones, como la codificación de vídeo y las variantes dinámicas de una imagen.
1. Una vez generadas las representaciones, AEM acceder a las representaciones de Dynamic Media remotas y realizar su previsualización de forma segura (no se devuelve ningún binario a la instancia de AEM).
1. Una vez que el contenido está listo para publicarse y aprobarse, activa el servicio Dynamic Media para insertar el contenido en los servidores envío y almacenar el contenido en caché en la CDN.

![chlimage_1](assets/chlimage_1.png)

## Activación de Dynamic Media en el modo Scene7 {#enabling-dynamic-media-in-scene-mode}

[Dynamic Media está desactivado de forma predeterminada. ](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) Para aprovechar las funciones de Dynamic Media, debe activarlas.

>[!NOTE]
>
>Medios dinámicos: el modo Scene7 es solo para la instancia de AEM Author. Como tal, debe configurar `runmode=dynamicmedia_scene7`la instancia de AEM Author, no la de AEM Publish.

Para habilitar Dynamic Media, debe iniciar AEM usando el `dynamicmedia_scene7` runmode desde la línea de comandos escribiendo lo siguiente en una ventana de terminal (el puerto de ejemplo utilizado es 4502):

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## (Opcional) Migración de ajustes preestablecidos y configuraciones de Dynamic Media de 6.3 a 6.4 Cero tiempo de inactividad {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Si está actualizando AEM Dynamic Media de 6.3 a 6.4 (que ahora incluye la capacidad de cero implementaciones de tiempo de inactividad), debe ejecutar el siguiente comando curl para migrar todos los ajustes preestablecidos y configuraciones de `/etc` a `/conf` CRXDE Lite.

>[!NOTE]
>
>Si ejecuta la instancia de AEM en modo de compatibilidad (es decir, tiene la compatibilidad empaquetada instalada), no es necesario ejecutar estos comandos.

Para migrar los ajustes preestablecidos y configuraciones personalizados de `/etc` a `/conf`, ejecute el siguiente comando de curl de Linux:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Para todas las actualizaciones, ya sea con o sin el paquete de compatibilidad, puede copiar los ajustes preestablecidos de visor integrados ejecutando el siguiente comando:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## (Opcional) Instalación del paquete de funciones 18912 para la migración masiva de recursos {#installing-feature-pack}

El paquete de funciones 18912 le permite ingestar recursos de forma masiva mediante FTP o migrar recursos desde el modo Dynamic Media (híbrido) o Dynamic Media Classic a Dynamic Media (Scene7) en el modo AEM. Está disponible en Adobe Professional Services.

Consulte [Instalación del paquete de funciones 18912 para obtener más información sobre la migración](bulk-ingest-migrate.md) masiva de recursos.

## Configuring Dynamic Media Cloud Services {#configuring-dynamic-media-cloud-services}

Cambie la contraseña antes de configurar los Cloud Services de Dynamic Media. Después de recibir el correo electrónico de aprovisionamiento con las credenciales de Dynamic Media, debe [iniciar sesión](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) en Dynamic Media Classic para cambiar la contraseña. La contraseña que se proporciona en el correo electrónico de aprovisionamiento es generada por el sistema y está pensada para ser una contraseña temporal solamente. Es importante que actualice la contraseña para que el Cloud Service de Dynamic Media esté configurado con las credenciales correctas.

>[!NOTE]
>
>De forma predeterminada, la ruta de configuración para Cloud Services es `/content/dam`. El modo Dynamic Media - Scene7 no admite ninguna otra ruta de configuración.

Para configurar Cloud Services de Dynamic Media:

1. En AEM, toque el logotipo de AEM para acceder a la consola de navegación global y toque el icono Herramientas y, a continuación, **[!UICONTROL Cloud Services > Configuración]** de Dynamic Media.
1. En la página Explorador de configuración de Dynamic Media, en el panel izquierdo, toque **[!UICONTROL global]** y **[!UICONTROL Crear]**. No toque ni seleccione el icono de carpeta a la izquierda de [!UICONTROL global].
1. En la página [!UICONTROL Crear configuración] de Dynamic Media, escriba un título, la dirección de correo electrónico de la cuenta de Dynamic Media y la contraseña y, a continuación, seleccione su región. Se proporcionan por Adobe en el correo electrónico de aprovisionamiento. Póngase en contacto con el servicio de soporte técnico si no recibió esto.

   Tap **[!UICONTROL Connect to Dynamic Media]**.

   >[!NOTE]
   >
   >Después de recibir el correo electrónico de aprovisionamiento con las credenciales de Dynamic Media, [inicie sesión](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) en Dynamic Media Classic para cambiar la contraseña. La contraseña que se proporciona en el correo electrónico de aprovisionamiento es generada por el sistema y está pensada para ser una contraseña temporal solamente. Es importante que actualice la contraseña para que el servicio de nube de Dynamic Media esté configurado con las credenciales correctas.

1. Si la conexión es correcta, también puede establecer lo siguiente:

   * **[!UICONTROL Compañía]** : el nombre de la cuenta de Dynamic Media. Es posible que tenga varias cuentas de Dynamic Media para distintas submarcas, divisiones o entornos de ensayo y producción.
   * **[!UICONTROL Ruta de carpeta raíz de la empresa]**
   * **[!UICONTROL Publicación de recursos]** : la opción **[!UICONTROL Inmediatamente]** significa que, cuando se cargan recursos, el sistema los ingesta y proporciona la URL o incrustación al instante. No es necesaria la intervención del usuario para publicar recursos. La opción **[!UICONTROL Tras la Activación]** significa que primero debe publicar explícitamente el recurso antes de proporcionar un vínculo URL/Incrustar.
   * **[!UICONTROL Servidor]** de Previsualización segura: permite especificar la ruta de URL al servidor de previsualización de representaciones seguras. Es decir, una vez generadas las representaciones, AEM acceder a las representaciones de Dynamic Media remotas y realizar su previsualización de forma segura (no se devuelven los binarios a la instancia de AEM).

      A menos que tenga una disposición especial para utilizar el servidor de su propia compañía o un servidor especial, Adobe recomienda que utilice la configuración predeterminada.
   >[!NOTE]
   >
   >No se admite el control de versiones en DMS7. Además, la activación retrasada solo se aplica si **[!UICONTROL Publicar recursos]** en la página Editar configuración de Dynamic Media está configurada en **[!UICONTROL Al activarse]** y, a continuación, solo hasta la primera vez que se activa el recurso.
   >
   >Una vez activado un recurso, cualquier actualización se publica inmediatamente en directo en el Envío S7.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. Toque **[!UICONTROL Guardar]**.
1. Para realizar una previsualización segura del contenido de Dynamic Media antes de publicarlo, deberá &quot;lista de permitidos&quot; de la instancia de creación de AEM para conectarse a Dynamic Media:

   * Inicie sesión en su cuenta de Dynamic Media Classic: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html). Adobe proporcionó las credenciales y el inicio de sesión en el momento del aprovisionamiento. Si no dispone de esta información, póngase en contacto con el servicio de asistencia técnica.
   * En la barra de navegación situada cerca de la parte superior derecha de la página, toque **[!UICONTROL Ajustes > Ajustes de aplicación > Ajustes de publicación > Servidor]** de imágenes.
   * En la lista desplegable Contexto de publicación de la página Servidor de imágenes, seleccione **[!UICONTROL Probar servicio]** de imágenes.
   * Para el filtro de direcciones de cliente, toque **[!UICONTROL Añadir]**.
   * Seleccione la casilla de verificación para habilitar (activar) la dirección y, a continuación, introduzca la dirección IP de la instancia de AEM Author (no de Dispatcher IP).
   * Toque **[!UICONTROL Guardar]**.

Ha finalizado con la configuración básica; está listo para usar Dynamic Media: modo Scene7.

Si desea personalizar aún más la configuración, puede completar de forma opcional cualquiera de las tareas en [(Opcional) Configuración avanzada en el modo](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode)Dynamic Media - Scene7.

## (Opcional) Configuración avanzada en Dynamic Media: modo Scene7 {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Si desea personalizar aún más la configuración y la configuración del modo Dynamic Media - Scene7, o optimizar su rendimiento, puede completar una o varias de las siguientes tareas opcionales:

* [(Opcional) Configuración y configuración de Dynamic Media - Configuración del modo Scene7](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [(Opcional) Ajuste del rendimiento de Dynamic Media: modo Scene7](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [(Opcional) Filtrado de recursos para replicación](#optional-filtering-assets-for-replication)

### (Opcional) Configuración y configuración de Dynamic Media - Configuración del modo Scene7</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

Cuando se encuentra en modo de ejecución, **dynamicmedia_scene7**, utilice la interfaz de usuario de Dynamic Media Classic (Scene7) para realizar cambios en la configuración de Dynamic Media.

Algunas de las tareas anteriores requieren que inicie sesión en Dynamic Media Classic aquí: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

Las tareas de configuración y configuración son:

* [Configuración de publicación para Image Server](#publishing-setup-for-image-server)
* [Configuración de la configuración general de la aplicación](#configuring-application-general-settings)
* [Configuración de la administración de color](#configuring-color-management)
* [Edición de tipos MIME para formatos admitidos](#editing-mime-types-for-supported-formats)
* [Añadir tipos MIME para formatos no admitidos](#adding-mime-types-for-unsupported-formats)
* [Creación de ajustes preestablecidos de conjunto de lotes para generar automáticamente conjuntos de imágenes y conjuntos de giros](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Configuración de publicación para Image Server {#publishing-setup-for-image-server}

La configuración de configuración de publicación determina cómo se envían los recursos de forma predeterminada desde Dynamic Media. Si no se especifica ninguna configuración, Medios dinámicos envía un recurso según la configuración predeterminada definida en Ajuste de publicación. Por ejemplo, una solicitud para entregar una imagen que no incluye un atributo resolution genera una imagen con la configuración de Resolución de objeto predeterminada.

Para configurar Ajuste de publicación: en Dynamic Media Classic, toque **[!UICONTROL Ajustes > Ajustes de aplicación > Ajustes de publicación > Servidor]** de imágenes.

La pantalla Servidor de imágenes establece la configuración predeterminada para la entrega de imágenes. Consulte la interfaz de usuario para ver una descripción de cada configuración.

* **[!UICONTROL Atributos]** de solicitud: Esta configuración impone límites a las imágenes que se pueden enviar desde el servidor.
* **[!UICONTROL Atributos]** de solicitud predeterminados: esta configuración se refiere al aspecto predeterminado de las imágenes.
* **[!UICONTROL Atributos]** de miniatura comunes: esta configuración se refiere al aspecto predeterminado de las imágenes en miniatura.
* **[!UICONTROL Valores predeterminados para los campos]** del catálogo: esta configuración se refiere a la resolución y al tipo de miniatura predeterminada de las imágenes.
* **[!UICONTROL Atributos]** de administración de color: esta configuración determina qué perfiles de color ICC se utilizan.
* **[!UICONTROL Atributos]** de compatibilidad: Esta configuración permite que los párrafos al inicio y al final de las capas de texto se traten como en la versión 3.6 para lograr compatibilidad con versiones anteriores.
* **[!UICONTROL Compatibilidad]** con localizaciones: Esta configuración le permite administrar varios atributos de configuración regional. También le permite especificar una cadena de asignación de configuración regional para que pueda definir qué idiomas desea admitir para las distintas sugerencias de herramientas en los visores. Para obtener más información sobre la configuración de la compatibilidad con Localizaciones, consulte [Consideraciones al configurar la localización de recursos](https://help.adobe.com/en_US/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html).

#### Configuración de la configuración general de la aplicación {#configuring-application-general-settings}

Para abrir la página Configuración [!UICONTROL general de] la aplicación, en la barra de navegación global de Dynamic Media Classic, toque **[!UICONTROL Ajustes > Ajustes de aplicación > Configuración]** general.

**[!UICONTROL Servidores]** : Al aprovisionar la cuenta, Dynamic Media proporciona automáticamente los servidores asignados para la compañía. Estos servidores se utilizan para construir cadenas URL para el sitio Web y las aplicaciones. Estas llamadas mediante URL son específicas de su cuenta. No cambie ninguno de los nombres de servidor a menos que se indique explícitamente que lo haga AEM soporte técnico.

**[!UICONTROL Sobrescribir imágenes]** : Dynamic Media no permite que dos archivos tengan el mismo nombre. El ID de URL de cada elemento (el nombre de archivo menos la extensión) debe ser único. Estas opciones especifican cómo se cargan los recursos de reemplazo: ya sea que reemplacen el original o se conviertan en duplicados. Se cambia el nombre de los recursos de duplicado por &quot;-1&quot; (por ejemplo, silla.tif se denomina silla-1.tif). Estas opciones afectan a los recursos cargados en una carpeta diferente a la original o a los recursos con una extensión de nombre de archivo diferente a la original (como JPG, TIF o PNG).

* **[!UICONTROL Sobrescribir en la carpeta actual, el mismo nombre/extensión]** de imagen base: esta opción es la regla más estricta para reemplazar. Requiere que la imagen de sustitución se cargue en la misma carpeta que la imagen original y que la imagen de sustitución tenga la misma extensión de nombre de archivo que la imagen original. Si no se cumplen estos requisitos, se crea un duplicado.

>[!NOTE]
>
>Para mantener la coherencia con AEM, seleccione **[!UICONTROL Sobrescribir en la carpeta actual, con la misma extensión]** o nombre de imagen base.

* **[!UICONTROL Sobrescribir en cualquier carpeta, con la misma extensión]** o nombre de recurso base: requiere que la imagen de reemplazo tenga la misma extensión de nombre de archivo que la imagen original (por ejemplo, reemplaza `chair.jpg` y no `chair.jpg` `chair.tif`). Sin embargo, puede cargar la imagen de reemplazo en una carpeta distinta a la original. La imagen actualizada reside en la nueva carpeta; el archivo ya no se encuentra en su ubicación original.
* **[!UICONTROL Sobrescribir en cualquier carpeta, el mismo nombre de recurso base independientemente de la extensión]** . Esta opción es la regla de reemplazo más inclusiva. Puede cargar una imagen de sustitución en una carpeta distinta a la original, cargar un archivo con una extensión de nombre de archivo diferente y reemplazar el archivo original. Si el archivo original se encuentra en una carpeta diferente, la imagen de reemplazo reside en la nueva carpeta en la que se cargó.

**[!UICONTROL Perfiles]** de color predeterminados: consulte [Configuración de la administración](#configuring-color-management) de color para obtener más información.

>[!NOTE]
>
>De forma predeterminada, el sistema muestra 15 representaciones al seleccionar **[!UICONTROL Representaciones]** y 15 ajustes preestablecidos de visualizador al seleccionar **[!UICONTROL Visualizadores]** en la vista de detalles del recurso. Puede aumentar este límite. See [Increasing the number of image presets that display](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) or [Increasing the number of viewer presets that display](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Configuración de la administración de color {#configuring-color-management}

La administración dinámica de color de los medios le permite colorear los recursos correctos. Con la corrección de color, los recursos ingestados conservan su espacio de color (RGB, CMYK, Gris) y su perfil de color incrustado. Cuando se solicita una representación dinámica, el color de la imagen se corrige en el espacio de color del destinatario mediante la salida CMYK, RGB o gris. See [Configuring Image Presets](managing-image-presets.md).

Para configurar las propiedades de color predeterminadas para habilitar la corrección de color al solicitar imágenes:

1. [Inicie sesión en Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) con las credenciales proporcionadas durante el aprovisionamiento. Vaya a **[!UICONTROL Ajustes > Ajustes]** de aplicación.
1. Expanda el área **[!UICONTROL Ajustes de publicación]** y seleccione **[!UICONTROL Servidor de imágenes]**. Configure **[!UICONTROL Publicar contexto]** en **[!UICONTROL Servicio de imágenes]** cuando establezca los valores predeterminados para las instancias de publicación.
1. Desplácese a la propiedad que necesite cambiar, por ejemplo, una propiedad en el área Atributos **[!UICONTROL de administración de]** color.

   Puede establecer las siguientes propiedades de corrección de color:

   * [!UICONTROL Espacio] de color predeterminado CMYK: nombre del perfil de color CMYK predeterminado
   * [!UICONTROL Espacio] de color predeterminado de escala de grises: nombre del perfil de color gris predeterminado
   * [!UICONTROL Espacio] de color predeterminado RGB: nombre del perfil de color RGB predeterminado
   * [!UICONTROL Calidad] de representación de conversión de color: especifica la interpretación. Los valores aceptables son `perceptual`, `relative``colometric`, `saturation`y `absolute colometric`. Adobe recommends `relative` as the default.

1. Toque **[!UICONTROL Guardar]**.

Por ejemplo, puede establecer el **[!UICONTROL espacio de color predeterminado RGB]** en `sRGB` y el **[!UICONTROL espacio de color predeterminado CMYK]** en `WebCoated`.

Al hacerlo, se haría lo siguiente:

* Permite la corrección de color para imágenes RGB y CMYK.
* Las imágenes RGB que no tengan un perfil de color se considerarán como en el espacio de `sRGB` color.
* Las imágenes CMYK que no tengan un perfil de color se considerarán en el espacio de `WebCoated` color.
* Las representaciones dinámicas que devuelven salida RGB la devolverán en el espacio de `sRGB` color.
* Las representaciones dinámicas que devuelven una salida CMYK la devolverán en el espacio de `WebCoated` color.

#### Edición de tipos MIME para formatos admitidos {#editing-mime-types-for-supported-formats}

Puede definir qué tipos de recursos deben procesarse con Dynamic Media y personalizar los parámetros avanzados de procesamiento de recursos. Por ejemplo, puede especificar parámetros de procesamiento de recursos para realizar lo siguiente:

* Convertir un Adobe PDF en un recurso de catálogo electrónico.
* Convertir un Documento de Adobe Photoshop (.PSD) en un recurso de plantilla de letrero para su personalización.
* Rasterizar un archivo Adobe Illustrator (.AI) o un archivo PostScript encapsulado de Adobe Photoshop (.EPS).
* [Se pueden utilizar Perfiles](/help/assets/video-profiles.md) de vídeo y Perfiles [de](/help/assets/image-profiles.md) imagen para definir el procesamiento de vídeos e imágenes, respectivamente.

Consulte [Carga de recursos](managing-assets-touch-ui.md#uploading-assets).

**Para editar tipos de MIME para formatos admitidos**

1. En AEM, toque el logotipo de AEM para acceder a la consola de navegación global y, a continuación, toque el icono **[!UICONTROL Herramientas]** (martillo) y vaya a **[!UICONTROL General > CRXDE Lite]**.
1. En el carril izquierdo, vaya a lo siguiente:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. En la `mimeTypes` carpeta, seleccione un tipo de MIME.
1. A la derecha de la página CRXDE Lite, en la parte inferior:

   * Haga clic con el doble en el campo **[!UICONTROL habilitado]** . De forma predeterminada, todos los tipos de MIME de recursos están activados (definidos como **[!UICONTROL true]**), lo que significa que los recursos se sincronizarán con Dynamic Media para su procesamiento. Si desea excluir el procesamiento de este tipo de MIME de recurso, cambie esta configuración a **[!UICONTROL false]**.
   * Haga clic con el botón doble en **[!UICONTROL jobParam]** para abrir el campo de texto asociado. Consulte Tipos [de MIME](assets-formats.md#supported-mime-types) admitidos para obtener una lista de los valores de parámetro de procesamiento permitidos que puede utilizar para un tipo de MIME determinado.

1. Realice una de las acciones siguientes:

   * Repita los pasos del 3 al 4 para editar tipos de MIME adicionales.
   * En la barra de menús de la página CRXDE Lite, toque **[!UICONTROL Guardar todo]**.

1. En la esquina superior izquierda de la página, toque **[!UICONTROL CRXDE Lite]** para volver a AEM.

#### Añadir tipos MIME personalizados para formatos no admitidos {#adding-custom-mime-types-for-unsupported-formats}

Puede agregar tipos MIME personalizados para formatos no admitidos en AEM Assets. To ensure that any new node you add in CRXDE Lite is not deleted by AEM, you must ensure that you move the MIME type before **[!UICONTROL image_]** and its enabled value is set to **[!UICONTROL false]**.

**Adición de tipos MIME personalizados para formatos no admitidos**

1. En AEM, haga clic en **[!UICONTROL Herramientas > Operaciones > Consola]** web.

   ![webconsole](assets/2019-08-02_16-13-14.png)

1. Se abre una nueva ficha de explorador en la página Configuración **[!UICONTROL de la consola web de]** Adobe Experience Manager.

   ![webconsole](assets/2019-08-02_16-17-29.png)

1. On the page, scroll down to the name **[!UICONTROL Adobe CQ Scene7 Asset MIME type Service]**. To the right of the name, tap **[!UICONTROL Edit the configuration values]** (pencil icon).

   ![editar](assets/2019-08-02_16-44-56.png)

1. En la página **[!UICONTROL Adobe CQ Scene7 Asset MIME type Service]** , haga clic en cualquier icono de signo más `+`. La ubicación en la tabla donde se hace clic en el signo más para agregar el nuevo tipo de MIME es trivial.

   ![plussign](assets/2019-08-02_16-27-27.png)

1. Escriba `DWG=image/vnd.dwg` el campo de texto vacío que acaba de agregar.

   Tenga en cuenta que el ejemplo `DWG=image/vnd.dwg` se muestra únicamente con fines ilustrativos. El tipo MIME que agregue aquí puede ser cualquier otro formato no admitido.

   ![dwg](assets/2019-08-02_16-36-36.png)

1. In the lower-right corner of the page, click **[!UICONTROL Save]**.

   En este punto, puede cerrar la ficha del explorador que tiene la página de configuración de la consola web de Adobe Experience Manager abierta.

1. Vuelva a la ficha del explorador que tiene la consola de AEM abierta.

1. En AEM, haga clic en **[!UICONTROL Herramientas > General > CRXDE Lite]**.

   ![crxdelite](assets/2019-08-02_16-55-41.png)

1. En el carril izquierdo, vaya a lo siguiente:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Arrastre el tipo MIME `image_vnd.dwg` y colóquelo directamente sobre `image_` el árbol.

   ![arrastrar](assets/CRXDELite_CQDOC-14627.png)

1. With the mime type `image_vnd.dwg` still selected in the tree, from the **[!UICONTROL Properties]** tab, in the **[!UICONTROL enabled]** row, under the **[!UICONTROL Value]** column header, double-click the value to open the **[!UICONTROL Value]** drop-down list.

1. Escriba `false` el campo (o selecciónelo `false` en la lista desplegable).

   ![falsevalue](assets/2019-08-02_16_60_30.png)

1. Cerca de la esquina superior izquierda de la página CRXDE Lite, haga clic en **[!UICONTROL Guardar todo]**.

#### Creación de ajustes preestablecidos de conjunto de lotes para generar automáticamente conjuntos de imágenes y conjuntos de giros {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Utilice los ajustes preestablecidos de conjunto de lotes para automatizar la creación de conjuntos de imágenes o conjuntos de giros mientras los recursos se cargan en Dynamic Media.

En primer lugar, defina la convención de nombre para la forma en que los recursos deben agruparse en un conjunto. A continuación, puede crear un ajuste preestablecido de conjunto de lotes con un nombre único y un conjunto independiente de instrucciones que definan cómo construir el conjunto con imágenes que coincidan con las convenciones de nombre definidas en la fórmula preestablecida.

Al cargar archivos, Dynamic Media crea automáticamente un conjunto con todos los archivos que coinciden con la convención de nombre definida en los ajustes preestablecidos activos.

**Configuración de la nomenclatura predeterminada**

Cree una convención de nombre predeterminada que se utilice en cualquier fórmula de ajuste preestablecido de conjunto de lotes. La convención de nombre predeterminada seleccionada en la definición del ajuste preestablecido de conjunto de lotes puede ser todo lo que la compañía necesita para generar conjuntos por lotes. Se crea un ajuste preestablecido de conjunto de lotes para utilizar la convención de nombre predeterminada que defina. Puede crear tantos ajustes preestablecidos de conjunto de lotes como desee con convenciones de nombre personalizadas alternativas necesarias para un conjunto concreto de contenido en casos en los que exista una excepción a la nomenclatura predeterminada definida por la compañía.

Aunque no es necesario configurar una convención de nombres predeterminada para utilizar la funcionalidad de ajuste preestablecido de conjunto de lotes, la práctica recomendada es utilizar la convención de nombres predeterminada para definir tantos elementos de la convención de nombres que desee agrupar en un conjunto para agilizar la creación de conjuntos de lotes.

Como alternativa, tenga en cuenta que puede utilizar el código **[!UICONTROL de]** Vista sin campos de formulario disponibles. En esta vista, puede crear las definiciones de convención de nombres utilizando expresiones normales.

Hay dos elementos disponibles para la definición, **[!UICONTROL Coincidencia]** y Nombre **[!UICONTROL base]**. Estos campos permiten definir todos los elementos de una convención de nombres e identificar la parte de la convención utilizada para asignar un nombre al conjunto en el que están contenidos. La convención de nombres individual de una compañía puede utilizar una o varias líneas de definición para cada uno de estos elementos. Puede utilizar tantas líneas como desee para su definición única y agruparlas en elementos distintos, como imagen principal, elemento de color, elemento de Vista alternativa y elemento de muestra.

**Para configurar la nominación predeterminada:**

1. Inicie sesión en su cuenta de Dynamic Media Classic (Scene7): [www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe proporcionó las credenciales y el inicio de sesión en el momento del aprovisionamiento. Si no dispone de esta información, póngase en contacto con el servicio de asistencia técnica.

1. En la barra de navegación situada cerca de la parte superior de la página, toque **[!UICONTROL Ajustes > Ajustes de aplicación > Valores preestablecidos de conjunto por lotes > Nombre]predeterminado.**
1. Seleccione **[!UICONTROL Ver formulario]** o **[!UICONTROL Ver código]** para especificar cómo desea ver e introducir información sobre cada elemento.

   Puede seleccionar la casilla de verificación Código **[!UICONTROL de]** Vista para realizar una vista de la creación del valor de expresión normal junto con las selecciones de formulario. Puede introducir o modificar estos valores para ayudar a definir los elementos de la convención de nombres, si la vista del formulario le limita por cualquier motivo. Si los valores no se pueden analizar en la vista del formulario, los campos del formulario se desactivan.

   >[!NOTE]
   >
   >Los campos de formulario desactivados no validan que las expresiones normales sean correctas. Verá los resultados de la expresión normal que está generando para cada elemento después de la línea de resultados. La expresión regular completa está visible en la parte inferior de la página.

1. Expanda cada elemento según sea necesario e introduzca las convenciones de nombres que desee utilizar.
1. Si es necesario, realice una de las siguientes acciones:

   * Toque **[!UICONTROL Añadir]** para agregar otra convención de nombre para un elemento.
   * Toque **[!UICONTROL Eliminar]** para eliminar una convención de nombre para un elemento.

1. Realice una de las acciones siguientes:

   * Toque **[!UICONTROL Guardar como]** y escriba un nombre para el ajuste preestablecido.
   * Toque **[!UICONTROL Guardar]** si está editando un ajuste preestablecido existente.

**Creación de un ajuste preestablecido de conjunto de lotes**

Dynamic Media utiliza ajustes preestablecidos de conjunto de lotes para organizar los recursos en conjuntos de imágenes (imágenes alternativas, opciones de color, giro de 360) para mostrarlos en los visores. Los ajustes preestablecidos de conjunto de lotes se ejecutan automáticamente junto con los procesos de carga de recursos en Dynamic Media.

Puede crear, editar y administrar los ajustes preestablecidos de conjunto de lotes. Existen dos formas de definiciones de ajustes preestablecidos de conjunto de lotes: una para una convención de nombre predeterminada que puede haber configurado y otra para convenciones de nombre personalizadas que cree sobre la marcha.

Puede utilizar el método de campo de formulario para definir un ajuste preestablecido de conjunto de lotes o el método de código, que le permite utilizar expresiones regulares. Como en Nombre predeterminado, puede elegir Código [!UICONTROL de] Vista al mismo tiempo que define en la Vista  Formulario y utilizar expresiones regulares para crear sus definiciones. También puede desactivar la vista para usar una u otra exclusivamente.

**Para crear un ajuste preestablecido de conjunto por lotes:**

1. Inicie sesión en su cuenta de Dynamic Media Classic (Scene7): [www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe proporcionó las credenciales y el inicio de sesión en el momento del aprovisionamiento. Si no dispone de esta información, póngase en contacto con el servicio de asistencia técnica.

1. En la barra de navegación situada cerca de la parte superior de la página, toque **[!UICONTROL Ajustes > Ajustes de aplicación > Valores preestablecidos de conjunto por lotes > Valor preestablecido]de conjunto por lotes.**

   Tenga en cuenta que Formulario [!UICONTROL de]Vista, tal como se define en la esquina superior derecha de la página [!UICONTROL Detalles] , es la vista predeterminada.

1. En el panel Lista de ajustes preestablecidos, toque **[!UICONTROL Añadir]** para activar los campos de definición en el panel **[!UICONTROL Detalles]** , en la parte derecha de la pantalla.
1. En el panel **[!UICONTROL Detalles]** , en el campo Nombre **[!UICONTROL de]** ajuste preestablecido, escriba un nombre para el ajuste preestablecido.
1. En el menú desplegable Tipo **[!UICONTROL de conjunto de]** lotes, seleccione un tipo de ajuste preestablecido.
1. Realice una de las acciones siguientes:

   * If you are using a default naming convention that you previously set up under **[!UICONTROL Application Setup > Batch Set Presets > Default Naming]**, expand **[!UICONTROL Asset Naming Conventions]**, and then in the **[!UICONTROL File Naming]** drop-down list, tap **[!UICONTROL Default]**.
   * To define a new naming convention as you set up the preset, **[!UICONTROL Asset Naming Conventions]**, and then in the **[!UICONTROL File Naming]** drop-down list, tap **[!UICONTROL Custom]**.

1. Para el orden [!UICONTROL de]secuencia, defina el orden en que se muestran las imágenes después de que el conjunto se agrupe en Dynamic Media.

   De forma predeterminada, los recursos se ordenan de forma alfanumérica. Sin embargo, puede utilizar una lista separada por comas de expresiones regulares para definir el orden.

1. Para **[!UICONTROL Definir convención]** de nombres y **[!UICONTROL creación de nombres]**, especifique el sufijo o el prefijo del nombre base definido en la convención **[!UICONTROL de nombres de]** recursos. Además, defina dónde se creará el conjunto dentro de la estructura de carpetas de Dynamic Media.

   Si define un gran número de conjuntos, puede que prefiera mantenerlos separados de las carpetas que contienen los propios recursos. Por ejemplo, puede crear una carpeta de conjuntos de imágenes y colocar aquí los conjuntos generados.

1. En el panel **[!UICONTROL Detalles]** , toque **[!UICONTROL Guardar]**.
1. Toque **[!UICONTROL Activo]** junto al nuevo nombre de ajuste preestablecido.

   Al activar el ajuste preestablecido, se garantiza que al cargar recursos en Dynamic Media, el ajuste preestablecido de conjunto de lotes se aplica para generar el conjunto.

**Creación de un ajuste preestablecido de conjunto de lotes para la generación automática de un conjunto de giros 2D**

Puede utilizar el tipo de conjunto de lotes Conjunto de giros de **[!UICONTROL varios ejes]** para crear una fórmula que automatice la generación de conjuntos de giros 2D. La agrupación de imágenes utiliza expresiones regulares de fila y columna para que los recursos de imagen estén correctamente alineados en la ubicación correspondiente de la matriz multidimensional. No hay un número mínimo o máximo de filas o columnas que debe tener en un conjunto de giros de varios ejes.

Por ejemplo, supongamos que desea crear un conjunto de giros de varios ejes denominado `spin-2dspin`. Tiene un conjunto de imágenes de conjunto de giros que contienen tres filas, con 12 imágenes por fila. Las imágenes reciben el siguiente nombre:

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

Con esta información, la fórmula de tipo [!UICONTROL de conjunto de] lotes podría crearse de la siguiente manera:

![chlimage_1-1](assets/chlimage_1-1.png)

La agrupación de la parte del nombre de recurso compartido del conjunto de giros se agrega al campo **[!UICONTROL Coincidencia]** (como resaltado). La parte variable del nombre del recurso que contiene la fila y la columna se agrega a los campos **[!UICONTROL Fila]** y **[!UICONTROL Columna]**, respectivamente.

When the Spin Set is uploaded and published, you activate the name of the 2D Spin Set recipe that is listed under **[!UICONTROL Batch Set Presets]** in the **[!UICONTROL Upload Job Options]** dialog box.

**Para crear un ajuste preestablecido de conjunto por lotes para la generación automática de un conjunto de giros 2D:**

1. Inicie sesión en su cuenta de Dynamic Media Classic (Scene7): [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe proporcionó las credenciales y el inicio de sesión en el momento del aprovisionamiento. Si no dispone de esta información, póngase en contacto con el servicio de asistencia técnica.

1. En la barra de navegación situada cerca de la parte superior de la página, toque **[!UICONTROL Ajustes > Ajustes de aplicación > Valores preestablecidos de conjunto por lotes > Valor preestablecido]** de conjunto por lotes.

   Tenga en cuenta que Formulario [!UICONTROL de]Vista, tal como se define en la esquina superior derecha de la página [!UICONTROL Detalles] , es la vista predeterminada.

1. En el panel Lista **** preestablecida, toque **[!UICONTROL Añadir]** para activar los campos de definición en el panel **[!UICONTROL Detalles]** del lado derecho de la pantalla.
1. En el panel **[!UICONTROL Detalles]** , en el campo Nombre [!UICONTROL de] ajuste preestablecido, escriba un nombre para el ajuste preestablecido.
1. In the **[!UICONTROL Batch Set Type]** drop-down menu, select **[!UICONTROL Asset Set]**.
1. En la lista desplegable **[!UICONTROL Subtipo]** , seleccione Conjunto de giros de **[!UICONTROL varios ejes]**.
1. Expanda Convenciones **[!UICONTROL de nombres de]** recursos y, a continuación, en la lista desplegable Nombre de **[!UICONTROL archivo]** , toque **[!UICONTROL Personalizar]**.
1. Utilice los atributos **[!UICONTROL Coincidencia]** y, opcionalmente, **[!UICONTROL Nombre base]** para establecer una expresión regular para la asignación de nombres a los recursos de imagen que conforman la agrupación.

   Por ejemplo, la expresión regular de coincidencia literal puede tener el siguiente aspecto:

   `(w+)-w+-w+`

1. Expanda Posición **[!UICONTROL de columna de]** fila y, a continuación, defina el formato de nombre para la posición del recurso de imagen en la matriz Conjunto de giros 2D.

   Utilice el paréntesis para abarcar la posición de fila o columna en el nombre del archivo.

   Por ejemplo, para la expresión regular de fila, puede tener el siguiente aspecto:

   `\w+-R([0-9]+)-\w+`

   o

   `\w+-(\d+)-\w+`

   Para la expresión regular de columna, puede tener el siguiente aspecto:

   `\w+-\w+-C([0-9]+)`

   o

   `\w+-\w+-C(\d+)`

   Recuerde que estos son sólo ejemplos. Puede crear la expresión normal según sus necesidades.

   >[!NOTE]
   >
   >Si la combinación de expresiones regulares de fila y columna no puede determinar la posición del recurso dentro de la matriz de conjuntos de giros multidimensional, ese recurso no se agrega al conjunto y se registra un error.

1. Para **[!UICONTROL Definir convención]** de nombres y **[!UICONTROL creación de nombres]**, especifique el sufijo o el prefijo del nombre base definido en la convención **[!UICONTROL de nombres de]** recursos.

   Además, defina dónde se creará el conjunto de giros en la estructura de carpetas de Dynamic Media Classic.

   Si define un gran número de conjuntos, puede que prefiera mantenerlos separados de las carpetas que contienen los propios recursos. Por ejemplo, cree una carpeta Conjuntos de giros para colocar los conjuntos generados aquí.

1. En el panel **[!UICONTROL Detalles]** , toque **[!UICONTROL Guardar]**.
1. Toque **[!UICONTROL Activo]** junto al nuevo nombre de ajuste preestablecido.

   Al activar el ajuste preestablecido, se garantiza que al cargar recursos en Dynamic Media, el ajuste preestablecido de conjunto de lotes se aplica para generar el conjunto.

### (Opcional) Ajuste del rendimiento de Dynamic Media: modo Scene7 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Para mantener el modo Dynamic Media - Scene7 funcionando sin problemas, Adobe recomienda los siguientes consejos de ajuste del rendimiento y la escalabilidad de la sincronización:

* Actualización de los parámetros de trabajo predefinidos para el procesamiento de diferentes formatos de archivo.
* Actualización de los subprocesos de trabajo de la cola de Granite (recursos de vídeo) predefinidos.
* Actualizando los subprocesos de trabajo en cola predefinidos de flujo de trabajo transitorio de Granite (imágenes y recursos que no son de vídeo).
* Actualización de las conexiones de carga máximas al servidor de Dynamic Media Classic.

#### Actualización de los parámetros de trabajo predefinidos para el procesamiento de diferentes formatos de archivo

Puede ajustar los parámetros de trabajo para un procesamiento más rápido al cargar archivos. Por ejemplo, si está cargando archivos PSD pero no desea procesarlos como plantillas, puede establecer la extracción de capas en false (desactivado). En ese caso, el parámetro de trabajo optimizado aparecerá como `process=None&createTemplate=false`.

Adobe recomienda utilizar los siguientes parámetros de trabajo &quot;optimizados&quot; para archivos PDF, Postscript y PSD:

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| Tipo de archivo | Parámetros de trabajo recomendados |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| Postscript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

Para actualizar cualquiera de estos parámetros, siga los pasos que se indican en [Activación de la compatibilidad](#enabling-mime-type-based-assets-scene-upload-job-parameter-support)con el parámetro de trabajo de carga de Dynamic Media Classic/Assets basado en tipos MIME.

#### Actualización de la cola Granite Transient Workflow {#updating-the-granite-transient-workflow-queue}

La cola de flujo de trabajo de tránsito de granito se utiliza para el flujo de trabajo de recursos **[!UICONTROL de actualización de]** DAM. En Dynamic Media, se utiliza para la ingesta y el procesamiento de imágenes.

**Para actualizar la cola Granite Transient Workflow**

1. Vaya a [https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr) y busque la **[!UICONTROL cola: Granite Transient Workflow Queue]**.

   >[!NOTE]
   >
   >Se necesita una búsqueda de texto en lugar de una dirección URL directa porque el OSGi PID se genera de forma dinámica.

1. En el campo **[!UICONTROL Número máximo de trabajos]** paralelos, cambie el número al valor deseado.

   Puede aumentar los trabajos **[!UICONTROL paralelos]** máximos para admitir correctamente la carga pesada de archivos en Dynamic Media. El valor exacto depende de la capacidad del hardware. En determinados escenarios (es decir, una migración inicial o una carga masiva única) puede utilizar un valor grande. Sin embargo, tenga en cuenta que el uso de un valor grande (por ejemplo, dos veces el número de núcleos) puede tener efectos negativos en otras actividades simultáneas. Como tal, debe probar y ajustar el valor en función de su caso de uso particular.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Toque **[!UICONTROL Guardar]**.

#### Actualización de la cola Granite Workflow {#updating-the-granite-workflow-queue}

La cola Granite Workflow se utiliza para flujos de trabajo no transitorios. En Dynamic Media, solía procesar vídeo con el flujo de trabajo de codificación de vídeo **[!UICONTROL de]** Dynamic Media.

**Para actualizar la cola Granite Workflow:**

1. Navegue hasta `https://<server>/system/console/configMgr` y busque la **[!UICONTROL cola: Cola]** de flujo de trabajo de granito.

   >[!NOTE]
   >
   >Se necesita una búsqueda de texto en lugar de una dirección URL directa porque el OSGi PID se genera de forma dinámica.

1. En el campo **[!UICONTROL Número máximo de trabajos]** paralelos, cambie el número al valor deseado.

   De forma predeterminada, el número máximo de trabajos paralelos depende del número de núcleos de CPU disponibles. Por ejemplo, en un servidor de 4 núcleos, asigna dos subprocesos de trabajo. (Un valor entre 0,0 y 1,0 está basado en la proporción, o cualquier número bueno que no sea 1 asignará el número de subprocesos de trabajo).

   En la mayoría de los casos de uso, la configuración predeterminada de 0,5 es suficiente.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Toque **[!UICONTROL Guardar]**.

#### Actualización de la conexión de carga de Scene7 {#updating-the-scene-upload-connection}

La configuración de la conexión de carga de Scene7 sincroniza AEM recursos con los servidores de Dynamic Media Classic.

**Para actualizar la conexión de carga de Scene7:**

1. Ir a `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. En el campo [!UICONTROL Número de conexiones] y/o el campo Tiempo de espera [!UICONTROL del trabajo] activo, cambie el número como desee.

   La opción **[!UICONTROL Número de conexiones]** controla el número máximo de conexiones HTTP permitidas para AEM a la carga de Dynamic Media; normalmente, el valor predefinido de 10 conexiones es suficiente.

   La configuración del tiempo de espera **[!UICONTROL del trabajo]** activo determina el tiempo de espera para que los recursos de Dynamic Media cargados se publiquen en el servidor de envío. Este valor es 2100 segundos o 35 minutos de forma predeterminada.

   Para la mayoría de los casos de uso, el ajuste de 2100 es suficiente.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Toque **[!UICONTROL Guardar]**.

### (Opcional) Filtrado de recursos para replicación {#optional-filtering-assets-for-replication}

En implementaciones de medios no dinámicos, puede replicar *todos los *recursos (imágenes y vídeo) del entorno de creación de AEM en el nodo de publicación de AEM. Este flujo de trabajo es necesario porque los servidores de publicación AEM también entregan los recursos.

Sin embargo, en las implementaciones de Dynamic Media, como los recursos se entregan a través del servicio en la nube, no es necesario replicar esos mismos recursos en AEM nodos de publicación. Este flujo de trabajo de &quot;publicación híbrida&quot; evita costes de almacenamiento adicionales y tiempos de procesamiento más largos para replicar recursos. Otros contenidos, como las páginas del sitio, se siguen ofreciendo desde los nodos de publicación AEM.

Los filtros permiten *excluir* recursos de la replicación en el nodo de publicación AEM.

#### Uso de filtros de recursos predeterminados para replicación {#using-default-asset-filters-for-replication}

Si utiliza Dynamic Media para imágenes y/o vídeos, puede utilizar los filtros predeterminados que se proporcionan tal cual. Los siguientes filtros están activos de forma predeterminada:

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filtro</strong></td> 
   <td><strong>Tipo MIME</strong></td> 
   <td><strong>Representaciones</strong></td> 
  </tr> 
  <tr> 
   <td>Envío de imágenes de Dynamic Media</td> 
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td> 
   <td><p>Inicios con <strong>imagen/</strong></p> <p>Contiene <strong>la aplicación/</strong> y termina con <strong>set</strong>.</p> </td> 
   <td>Las "imágenes de filtro" integradas (se aplican a recursos de imágenes únicas, incluidas imágenes interactivas) y "conjuntos de filtros" (se aplican a conjuntos de giros, conjuntos de imágenes, conjuntos de medios mixtos y conjuntos de carrusel): 
    <ul> 
     <li>Excluya de la replicación la imagen original y las representaciones de imágenes estáticas.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Envío de vídeo de Dynamic Media</td> 
   <td>filter-video</td> 
   <td>Inicios con <strong>vídeo/</strong></td> 
   <td>El "video-filtro" incorporado: 
    <ul> 
     <li>Excluya de la replicación el vídeo original y las representaciones de miniaturas estáticas.<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Los filtros se aplican a tipos de MIME y no pueden ser específicos de la ruta.

#### Personalización de filtros de recursos para replicación {#customizing-asset-filters-for-replication}

1. En AEM, toque el logotipo de AEM para acceder a la consola de navegación global y toque el icono **[!UICONTROL Herramientas]** y vaya a **[!UICONTROL General > CRXDE Lite]**.
1. En el árbol de carpetas izquierdo, vaya a para `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` revisar los filtros.

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. Para definir el tipo de MIME para el filtro, puede localizar el tipo de MIME de la siguiente manera:

   En el carril izquierdo, expanda **[!UICONTROL contenido > dam > &lt;`locate_your_asset`> > jcr:content > metadatos]** y, a continuación, en la tabla, busque **[!UICONTROL dc:format]**.

   El siguiente gráfico es un ejemplo de la ruta de un recurso al formato dc:format.

   ![climage_1-3](assets/chlimage_1-3.png)

   Observe que el `dc:format` del recurso `Fiji Red.jpg` es `image/jpeg`.

   Para que este filtro se aplique a todas las imágenes, independientemente de su formato, establezca el valor en `image/*` donde `*` es una expresión normal que se aplica a todas las imágenes de cualquier formato.

   Para que el filtro solo se aplique a imágenes del tipo JPEG, introduzca un valor de `image/jpeg`.

1. Defina qué representaciones desea incluir o excluir de la replicación.

   Los caracteres que se pueden usar para filtrar para la replicación son los siguientes:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Carácter que utilizar</strong></td> 
    <td><strong>Filtros de recursos para replicación</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>Wildcard character<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>Incluye recursos para replicación.</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>Excluye los recursos de la replicación.</td> 
    </tr> 
    </tbody> 
   </table>

   Vaya a **content/dam/&lt;`locate your asset`>/jcr:content/renditions**.

   El siguiente gráfico es un ejemplo de las representaciones de un recurso.

   ![climage_1-4](assets/chlimage_1-4.png)

   Si sólo quería replicar el original, entonces ingresaría `+original`.

