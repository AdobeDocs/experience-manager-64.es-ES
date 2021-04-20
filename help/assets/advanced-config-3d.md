---
title: Ajustes de configuración avanzados
seo-title: Ajustes de configuración avanzados
description: Obtenga información sobre los ajustes de configuración avanzados que se aplican a la integración de AEM 3D tanto para implementaciones mayas como no mayas.
seo-description: Obtenga información sobre los ajustes de configuración avanzados que se aplican a la integración de AEM 3D tanto para implementaciones mayas como no mayas.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
exl-id: fdc82bca-e676-4052-b3e9-a198c685df96
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 1%

---

# Configuración avanzada {#advanced-configuration-settings}

Aunque los ajustes de configuración predeterminados son adecuados para casos de uso habituales, es posible que algunas situaciones requieran que realice cambios.

Los siguientes ajustes de configuración avanzados se aplican a la integración de AEM 3D tanto para implementaciones mayas como no mayas.

Se accede a todas las configuraciones mediante **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**).

>[!NOTE]
>
>Si vuelve a instalar el paquete, restablece todos los ajustes a sus valores predeterminados.

>[!CAUTION]
>
>La edición de cualquier configuración que no aparezca en la tabla siguiente puede provocar un comportamiento inesperado o no deseado del programa.

## Configuración de tipos de activos {#asset-types-configuration}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| Ruta | Descripción |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Especifica el tipo de archivo para el formato 3D intermedio creado durante la ingesta. Debe estar vacío para los formatos de archivo &quot;fbx&quot; y &quot;obj&quot; o &quot;fbx&quot; para los formatos habilitados por Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Se establece en true o false para habilitar o deshabilitar esta entrada en la lista **[!UICONTROL assetTypes]**. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Especifique uno o varios sufijos de archivo separados por comas o extensiones de archivo que se van a asociar a este tipo de recurso. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Debe ser `native` para los formatos de archivo FBX y OBJ y `maya` para los formatos habilitados por Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Especifica el tipo de MIME para este tipo de recurso. En el caso de los formatos habilitados por Maya, se recomienda utilizar `application/x-ext`, donde `ext` es la cadena especificada como valor `Extension`. |

## Configuración de ingesta {#ingestion-configuration}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Ruta</strong></td> 
   <td><strong>Descripción</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>Permite la generación de una sombra de caída de oclusión ambiental al ver o procesar con un escenario de IBL. Se aplica a la vista previa y el procesamiento con RapidRefine</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>Configúrelo en <strong>false</strong> para mantener los archivos temporales en la carpeta MayaWork después de la conversión y el procesamiento. Puede resultar útil a la hora de depurar problemas con la conversión y el procesamiento de Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>Cuando está habilitado, ImageMagick está instalado en el servidor y magickPath está configurado. Rapid Refine se utiliza para crear una animación simple para objetos 3D que se utilizan como miniaturas en la vista de tarjeta y otras vistas.</p> <p>La creación de animaciones consume importantes recursos de CPU durante el proceso de ingesta.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>Permite la creación automática de mapas de luz durante la ingesta. Establézcalo en <strong>false</strong> para deshabilitar la creación automática de mapas de luz; esto puede reducir significativamente el consumo de CPU a costa de una calidad reducida para la vista previa y el procesamiento con Rapid Refine. No afecta al procesamiento con Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>Cuando se establece en <strong>true</strong> (valor predeterminado), los objetos se mueven verticalmente, si es necesario, para garantizar que todas las partes del objeto estén encima del plano de tierra (y=0).</p> <p>Cuando se establece en <strong>false</strong> (predeterminado), los objetos no se vuelven a colocar y pueden estar parcialmente ocultos por el plano de tierra de un escenario. (Se aplica solo a la vista previa y el procesamiento con Rapid Refine). Sin embargo, no afecta al procesamiento con Maya. Cuando se establece en <strong>true</strong>, la posición vertical de los objetos en Maya puede ser diferente a la de la vista previa o al procesarlos con Rapid Refine.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>Ruta y nombre de la utilidad de conversión ImageMagick. Se requiere una ruta absoluta si está habilitada la creación de miniaturas animadas.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>Especifica la cantidad de CPUs que se utilizan como máximo para el procesamiento de ingesta de recursos 3D.</p> <p>Los valores más altos aceleran las ingestas, pero pueden hacer que los AEM se vuelvan menos interactivos en general. Esta configuración es aproximada. Es decir, la precisión aumenta con el número de núcleos de CPU disponibles.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Ajustes de configuración de Cloud Services {#cloud-services-configuration-settings}

El administrador de cuentas de Adobe, el experto en aprovisionamiento o el representante de asistencia proporcionan los valores para las siguientes configuraciones.

| **Ruta** | **Descripción** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | ID de cuenta de la cuenta de AWS de Adobe. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | el nombre del depósito de transferencia S3; normalmente `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | ID único asignado por Adobe a su organización. Se utiliza como ID de usuario de AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | La contraseña asociada a este customerId. Se utiliza como contraseña de AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/region` | Región de AWS donde se implementan los servicios de nube. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | El ID de grupo de usuarios de AWS Cognito aplicable. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | El ID de cliente de AWS Cognito para el servicio de conversión de dncr. |

## Configuración de procesamiento común {#common-processing-settings}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| **Ruta** | **Descripción** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Nombre y ubicación de la carpeta de trabajo para la conversión y renderización de Maya. La carpeta se crea automáticamente si no existe. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Nombre y ubicación de la carpeta de trabajo para la conversión máxima de 3ds. La carpeta se crea automáticamente si no existe. |
| `/libs/settings/dam/v3D/settings/debugNative` | Configúrelo en **[!UICONTROL true]** para habilitar la creación de información de depuración durante la conversión de formato y el procesamiento con el procesador RapidRefine. |

## Configuración del procesador {#renderer-configuration}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| **Ruta** | **Descripción** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | Cuando se establece en **[!UICONTROL true]** y los mapas de luz pregenerados no están disponibles (es decir, invokeLightMapsOnIngest=false), el procesador Rapid Refine crea mapas de luz durante el procesamiento para mejorar la calidad del procesamiento. Esta configuración puede aumentar sustancialmente el tiempo de procesamiento. Si se establece en **[!UICONTROL false]** se minimiza el uso de la CPU en estas situaciones, pero puede resultar en una menor calidad de procesamiento. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Configúrelo en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar un procesador, respectivamente. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Permite cambiar la cadena que se muestra para un procesador habilitado en el selector Procesador del panel Procesamiento . |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Especifica cuántas CPUs se utilizan como máximo para procesar escenas 3D. Los valores más altos aceleran el procesamiento, pero pueden hacer que los AEM se vuelvan menos interactivos en general. Esta configuración es aproximada. Es decir, la precisión aumenta con el número de núcleos de CPU disponibles. |

## Configuración de vista previa de recursos 3D {#d-asset-preview-settings}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| Ruta | Descripción |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Establézcalo en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar el giro automático (giro automático de cámara) al cargar la página. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Configúrelo en **[!UICONTROL true]** para reiniciar el giro automático después de presionar **[!UICONTROL Reset]**. Se omite cuando se desactiva el giro automático. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Especifica la velocidad (revoluciones por minuto) y la dirección del giro automático, con valores negativos para la rotación de derecha a izquierda y positivos para la de izquierda a derecha. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Establézcalo en **[!UICONTROL false]** para desactivar la continuación con atenuación gradual de las respuestas del espectador a los gestos de contacto y ratón. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Especifica el color de la cortina de carga que, opcionalmente, puede cubrir la ventanilla móvil de la vista previa de recursos 3D durante la carga y la inicialización. Valor R,G,B, con cada componente de color en el rango de 0 a 255. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | Cuando se establece en **[!UICONTROL true]**, la cortina de carga se disipará gradualmente durante las últimas partes de la inicialización del visor. Cuando se establece en **[!UICONTROL false]**, la cortina permanece opaca hasta que se completa la carga y la inicialización. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Configúrelo en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar la cortina de carga para la vista previa de recursos 3D. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Cuando el giro automático está activado, la posición vertical de la cámara se ajusta automáticamente en relación con la altura del objeto 3D. Cuando se establece en 0,5, la cámara se posiciona verticalmente a 1/2 de la altura del objeto, lo que hace que el horizonte quede centrado verticalmente en la ventanilla. Los valores más grandes hacen que la cámara mire hacia abajo el objeto y aumente la altura del horizonte procesado, los valores más pequeños hacen que la cámara busque el objeto y reduzca el horizonte. |

## Configuración del componente Sitios 3D {#d-sites-component-settings}

En **CRXDE Lite** en AEM (**[!UICONTROL Herramientas > General > CRXDE Lite]**), acceda a las siguientes configuraciones:

| Ruta | Descripción |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Configúrelo en **[!UICONTROL true]** para reactivar el giro automático (giro automático de la cámara) después de pulsar el inicio. Se omite cuando se desactiva el giro automático. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Establézcalo en **[!UICONTROL false]** para desactivar la continuación con atenuación gradual de las respuestas del espectador a los gestos de contacto y ratón. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Especifica el color de la cortina de carga que, opcionalmente, puede cubrir la ventanilla del componente Sitios 3D durante la carga. Valor R,G,B, con cada componente de color en el rango de 0 a 255. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | Cuando se establece en **[!UICONTROL true]**, la cortina de carga se disipará gradualmente durante las últimas partes de carga y de inicialización. Cuando se establece en **[!UICONTROL false]**, la cortina permanece opaca hasta que se completa la carga y la inicialización. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Configúrelo en **[!UICONTROL true]** o **[!UICONTROL false]** para habilitar o deshabilitar la cortina de carga para el componente Sitios 3D. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Cuando el giro automático está activado, la posición vertical de la cámara se ajusta automáticamente en relación con la altura del objeto 3D. Cuando se establece en 0,5, la cámara se posiciona verticalmente a 1/2 de la altura del objeto, lo que hace que el horizonte quede centrado verticalmente en la ventanilla. Los valores más grandes hacen que la cámara mire hacia abajo el objeto y aumente la altura del horizonte procesado, los valores más pequeños hacen que la cámara busque el objeto y reduzca el horizonte. |
