---
title: Configuración avanzada
seo-title: Configuración avanzada
description: Obtenga información sobre los ajustes de configuración avanzados que se aplican a la integración de AEM 3D para implementaciones tanto Maya como no Maya.
seo-description: Obtenga información sobre los ajustes de configuración avanzados que se aplican a la integración de AEM 3D para implementaciones tanto Maya como no Maya.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 1%

---


# Configuración avanzada {#advanced-configuration-settings}

Aunque las opciones de configuración predeterminadas son adecuadas para casos de uso típicos, algunas situaciones pueden requerir que realice cambios.

Los siguientes ajustes de configuración avanzados se aplican a la integración de AEM 3D para implementaciones tanto Maya como no Maya.

Se puede acceder a todas las configuraciones mediante **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**).

>[!NOTE]
>
>Si vuelve a instalar el paquete, restablece todos los valores predeterminados de configuración.

>[!CAUTION]
>
>Editar cualquier configuración que no aparezca en la tabla siguiente puede provocar un comportamiento de programa inesperado o no deseado.

## Configuración de tipos de recursos {#asset-types-configuration}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| Ruta | Descripción |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Especifica el tipo de archivo para el formato 3D intermedio creado durante la ingesta. Debe estar vacío para los formatos de archivo &#39;fbx&#39; y &#39;obj&#39; o &#39;fbx&#39; para los formatos activados por Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Establezca en true o false para habilitar o deshabilitar esta entrada en la lista **[!UICONTROL assetTypes]** . |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Especifique uno o varios sufijos de archivo separados por comas o extensiones de archivo que se asociarán a este tipo de recurso. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Debe ser `native` para formatos de archivo FBX y OBJ y `maya` para formatos habilitados por Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Especifica el tipo de MIME para este tipo de recurso. Para los formatos habilitados por Maya, se recomienda su uso `application/x-ext`, donde `ext` es la cadena especificada como `Extension` valor. |

## Configuración de ingestión {#ingestion-configuration}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ruta</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>Permite la generación de una sombra paralela de oclusión ambiental cuando se visualiza o procesa con un escenario IBL. Se aplica a la Previsualización y el procesamiento con RapidRefine</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanRenderWorkDir</p> </td> 
   <td>Establezca en <strong>false</strong> para mantener los archivos temporales en la carpeta MayaWork después de la conversión y el procesamiento. Puede resultar útil al depurar problemas con la conversión y el procesamiento de Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>Cuando se habilita, ImageMagick se instala en el servidor y se configura magickPath. El ajuste rápido se utiliza para crear una animación sencilla para objetos 3D que se utilizan como miniatura en la Vista de tarjetas y otras vistas.</p> <p>La creación de animaciones consume importantes recursos de CPU durante el proceso de ingestión.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>Permite la creación automática de mapas de luz durante la ingestión. Establezca en <strong>false</strong> para desactivar la creación automática de mapas de luz; esto puede reducir significativamente el consumo de CPU a costa de reducir la calidad de la previsualización y el procesamiento con la función de refinamiento rápido. No afecta al procesamiento con Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>Cuando se establece en <strong>true</strong> (valor predeterminado), los objetos se mueven verticalmente, si es necesario, para garantizar que todas las partes del objeto están por encima del plano de tierra (y=0).</p> <p>Cuando se establece en <strong>false</strong> (predeterminado), los objetos no se vuelven a colocar y pueden estar parcialmente ocultos por el plano de tierra de un escenario. (Solo se aplica a la previsualización y el procesamiento con una refinación rápida). Sin embargo, no afecta al procesamiento con Maya. Cuando se establece en <strong>true</strong>, la posición vertical de los objetos en Maya puede ser diferente a la de la previsualización o al procesar con Rapid Refine.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>Ruta y nombre de la utilidad de conversión ImageMagick. Se requiere una ruta absoluta si está habilitada la creación de miniaturas animadas.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPerpercentage</td> 
   <td><p>Especifica cuántas CPU se utilizan como máximo para el procesamiento de ingestión de recursos 3D.</p> <p>Los valores más altos aceleran las ingestas, pero pueden hacer que AEM se torne menos receptivo en general. Esta configuración es aproximada. Es decir, la precisión aumenta con el número de núcleos de CPU disponibles.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Ajustes de configuración de Cloud Services {#cloud-services-configuration-settings}

El administrador de cuentas de Adobe, el experto en aprovisionamiento o el representante de asistencia técnica proporcionan los valores para las siguientes configuraciones.

| **Ruta** | **Descripción** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | ID de cuenta de la cuenta de Adobe AWS. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | Nombre del depósito de transferencia S3; normalmente `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | ID única asignada por Adobe a su organización. Se utiliza como ID de usuario de AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | La contraseña asociada a este ID de cliente. Se utiliza como contraseña de AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/region` | Región de AWS donde se implementan los servicios en la nube. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | ID del grupo de usuarios de AWS Cognito aplicable. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | ID de cliente de AWS Cognito para el servicio de conversión dncr. |

## Ajustes comunes de procesamiento {#common-processing-settings}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| **Ruta** | **Descripción** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | El nombre y la ubicación de la carpeta de trabajo para la conversión y representación de Maya. La carpeta se crea automáticamente si no existe. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Nombre y ubicación de la carpeta de trabajo para la conversión máxima de 3ds. La carpeta se crea automáticamente si no existe. |
| `/libs/settings/dam/v3D/settings/debugNative` | Establezca en **[!UICONTROL true]** para habilitar la creación de información de depuración durante la conversión de formato y el procesamiento con el procesador RapidRefine. |

## Configuración del procesador {#renderer-configuration}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| **Ruta** | **Descripción** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | Cuando se establece en **[!UICONTROL true]** y los mapas de luz pregenerados no están disponibles (es decir, invokeLightMapsOnIngest=false), el procesador de refinamiento rápido crea mapas de luz durante el procesamiento para mejorar la calidad del procesamiento. Este ajuste puede aumentar considerablemente el tiempo de procesamiento. Si se establece en **[!UICONTROL false]** , se minimiza el uso de CPU en estas situaciones, pero puede resultar en una calidad de procesamiento inferior. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Establezca en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar un procesador, respectivamente. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Permite cambiar la cadena que se muestra para un procesador habilitado en el selector de procesamiento del panel Procesar. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Especifica cuántas CPU se utilizan como máximo para procesar escenas 3D. Los valores más altos aceleran el procesamiento, pero pueden hacer que los AEM sean menos interactivos en general. Esta configuración es aproximada. Es decir, la precisión aumenta con el número de núcleos de CPU disponibles. |

## Ajustes de previsualización de recursos 3D {#d-asset-preview-settings}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| Ruta | Descripción |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Establezca en **[!UICONTROL true]** o **[!UICONTROL false]** para activar o desactivar el giro automático (órbita automática de la cámara) al cargar la página. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Establezca en **[!UICONTROL true]** para reiniciar el giro automático después de pulsar **[!UICONTROL Restablecer]** . Se omite cuando el giro automático está desactivado. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Especifica la velocidad (revoluciones por minuto) y la dirección del giro automático, con valores negativos para la rotación de derecha a izquierda y valores positivos para la rotación de izquierda a derecha. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Establezca en **[!UICONTROL false]** para desactivar la continuación con la atenuación gradual de las respuestas del visor a los gestos táctiles y del ratón. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Especifica el color de la cortina de carga que puede, opcionalmente, cubrir la ventanilla móvil de la previsualización de recursos 3D durante la carga y la inicialización. Valor R,G,B, con cada componente de color en el rango de 0 a 255. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | Cuando se establece en **[!UICONTROL true]**, la cortina de carga se desvanecerá gradualmente durante las últimas partes de la inicialización del visor. Cuando se establece en **[!UICONTROL false]**, la cortina permanece opaca hasta que se complete la carga y la inicialización. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Establezca en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar la cortina de carga para la previsualización de recursos 3D. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Cuando el giro automático está activado, la posición vertical de la cámara se ajusta automáticamente en relación con la altura del objeto 3D. Cuando se establece en 0,5, la cámara se posiciona verticalmente a 1/2 de la altura del objeto, lo que hace que el horizonte se centre verticalmente en la ventanilla. Los valores más altos hacen que la cámara mire hacia abajo en el objeto y aumente la altura del horizonte procesado, mientras que los valores más pequeños hacen que la cámara mire hacia arriba el objeto y reduzca el horizonte. |

## Configuración del componente Sitios 3D {#d-sites-component-settings}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| Ruta | Descripción |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Establezca en **[!UICONTROL true]** para reactivar el giro automático (órbita automática de la cámara) después de pulsar el inicio. Se omite cuando el giro automático está desactivado. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Establezca en **[!UICONTROL false]** para desactivar la continuación con la atenuación gradual de las respuestas del visor a los gestos táctiles y del ratón. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Especifica el color de la cortina de carga que puede, opcionalmente, cubrir la ventanilla del componente Sitios 3D durante la carga. Valor R,G,B, con cada componente de color en el rango de 0 a 255. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | Cuando se establece en **[!UICONTROL true]**, la cortina de carga desaparecerá gradualmente durante las últimas partes de carga e inicialización. Cuando se establece en **[!UICONTROL false]**, la cortina permanece opaca hasta que se complete la carga y la inicialización. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Establezca en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar la cortina de carga para el componente Sitios 3D. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Cuando el giro automático está activado, la posición vertical de la cámara se ajusta automáticamente en relación con la altura del objeto 3D. Cuando se establece en 0,5, la cámara se posiciona verticalmente a 1/2 de la altura del objeto, lo que hace que el horizonte se centre verticalmente en la ventanilla. Los valores más altos hacen que la cámara mire hacia abajo en el objeto y aumente la altura del horizonte procesado, mientras que los valores más pequeños hacen que la cámara mire hacia arriba el objeto y reduzca el horizonte. |

