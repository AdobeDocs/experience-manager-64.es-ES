---
title: Integración AEM 3D con Autodesk Maya
seo-title: Integración AEM 3D con Autodesk Maya
description: Opcionalmente, puede integrar AEM 3D con el software Autodesk® Maya® para permitir el soporte de archivos Maya nativos (.MA y .MB) y para permitirle procesar recursos 3D en AEM con cualquier renderizador Maya disponible.
seo-description: Opcionalmente, puede integrar AEM 3D con el software Autodesk® Maya® para permitir el soporte de archivos Maya nativos (.MA y .MB) y para permitirle procesar recursos 3D en AEM con cualquier renderizador Maya disponible.
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
exl-id: 52ecbf81-0953-4c44-bc2c-d40e507b8d98
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# Integración de AEM 3D con Autodesk Maya {#integrating-aem-d-with-autodesk-maya}

>[!NOTE]
>
>Esta tarea es opcional y solo pertenece a Windows.

Si lo desea, puede integrar AEM 3D con el software Autodesk® Maya® para permitir la compatibilidad con archivos maya nativos (`.MA` y `.MB`) y permitirle procesar recursos 3D en AEM con cualquier renderizador maya disponible.

*Esta integración solo* es para Windows.

Al integrar con Autodesk Maya, debe instalar y configurar Autodesk Maya, añadir la ruta a la carpeta ejecutable Maya, habilitar Maya para la ingesta y renderización y probar la integración.

Consulte [Configuración avanzada](advanced-config-3d.md).

Consulte también [Integración AEM 3D con AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md).

**Para integrar AEM 3D con Autodesk Maya**:

1. Instale el software de Autodesk Maya 2016 en los mismos servidores en los que está alojado AEM.

   Después de la instalación, compruebe que puede abrir y utilizar Maya y que no hay problemas de licencia.

   >[!NOTE]
   >
   >AEM sólo utiliza la herramienta de renderización de la línea de comandos Maya (`render.exe`). Una sola licencia de red Maya permite que hasta cinco servidores procesen o procesen contenido Maya simultáneamente.

1. En Maya, habilite el complemento Autodesk FBX®.
1. Instale el complemento de renderización MentalRay u otro procesador que desee.

   Después de la instalación, verifique que MentalRay esté disponible en Maya.

1. Agregue la ruta a la carpeta ejecutable Maya a la variable de entorno de Windows PATH.

   Por ejemplo, en Windows Server 2012, pulse **[!UICONTROL Inicio] > [!UICONTROL Panel de control de Campaign] > [!UICONTROL Sistema y seguridad] > [!UICONTROL Sistema] > [!UICONTROL Configuración avanzada del sistema] > [!UICONTROL Variables de entorno]**. Anexe la ruta completa a la carpeta `Maya2016\bin` a la variable `Path`del sistema.

   ![imagen_1-53](assets/chlimage_1-53.png)

1. Para habilitar Maya para la ingesta y el procesamiento, abra **[!UICONTROL CRXDE Lite]**, vaya a `/libs/settings/dam/v3D/assetTypes/maya` y establezca la propiedad **[!UICONTROL Enabled]** en `true`.

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. Para habilitar el formato de archivo JT (Siemens PLM Open CAD), vaya a `/libs/settings/dam/v3D/assetTypes/jt` y establezca la propiedad **[!UICONTROL Enabled]** en `true`.
1. En AEM, habilite Maya como procesador. Para empezar, vaya a **[!UICONTROL Herramientas > General > CRXDE Lite]**.
1. En la página **[!UICONTROL CRXDE Lite]**, en el panel izquierdo, vaya a lo siguiente:

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. Establezca la propiedad **[!UICONTROL Enabled]** en `true`.

1. Cerca de la esquina superior izquierda de la página **[!UICONTROL CRXDE Lite]**, pulse **[!UICONTROL Guardar todo]**.

   Maya ahora está habilitada como renderizador.

## Prueba de la integración de AEM 3D con Autodesk Maya {#testing-the-integration-of-aem-d-with-autodesk-maya}

1. Abra AEM Assets y, a continuación, cargue los archivos `.MA` ubicados en `sample-3D-content/models` en la carpeta `test3d`.

   Tenga en cuenta que `sample-3D-content.zip` se ha descargado anteriormente para validar la funcionalidad 3D básica.

1. Vuelva a la vista **[!UICONTROL Card]** y observe los banners de mensaje que se muestran en los recursos cargados.

   El banner de formato de conversión se muestra mientras Maya convierte el formato nativo `.MA` a `.FBX`.

1. Una vez finalizado todo el procesamiento, abra el recurso `logo-sphere.ma` y seleccione la etapa `stage-helipad.ma`.

   La experiencia de vista previa es la misma que con `logo_sphere.fbx` y `stage-helipad.fbx`.

1. Cerca de la esquina superior izquierda de la página, toque o haga clic en la lista desplegable y seleccione **[!UICONTROL CRender]**.

   ![imagen_1-54](assets/chlimage_1-54.png)

1. En la lista desplegable **[!UICONTROL Renderer]**, seleccione **[!UICONTROL Autodesk Maya]** y, a continuación, pulse **[!UICONTROL Start Render]**.
1. Cerca de la esquina superior derecha de la página, toque o haga clic en **[!UICONTROL Cerrar]** para volver a la vista **[!UICONTROL Tarjeta]**.

   Observe el banner del mensaje en el recurso de imagen que se está procesando (`logo-sphere`, a menos que se especifique un nombre de imagen diferente). Una barra de progreso en el banner muestra el progreso del procesamiento.

   >[!NOTE]
   >
   >El procesamiento es muy intensivo en la CPU y puede tardar varios minutos en completarse

1. Una vez finalizada la renderización, abra el recurso de imagen procesado.

   Compruebe que la imagen representada coincida razonablemente con la imagen que estaba viendo en el momento en que hizo clic en **[!UICONTROL Representar ahora]**.

## Habilitación de formatos adicionales admitidos por Maya {#enabling-additional-formats-supported-by-maya}

(Opcional) Maya admite varios formatos de entrada 3D, cualquiera de los cuales se puede habilitar para que AEM reconozca el tipo de archivo. Cuando está habilitado, AEM envía el archivo a Maya para convertirlo en un formato intermedio que AEM pueda ingerir directamente.

Según el formato, la compatibilidad con las funciones puede ser limitada (por ejemplo, es posible que los materiales no pasen a través de ellas) y la calidad/fidelidad puede ser limitada (por ejemplo, caras invertidas). Adobe solo admite el mecanismo general, pero no cualquier conversión de formato específica.

Consulte [Formatos de importación de datos compatibles | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html) para obtener información sobre los formatos admitidos por Maya.

**Para habilitar formatos adicionales compatibles con AEM**:

1. Usando **[!UICONTROL CRXDE Lite]**, vaya a `/libs/settings/dam/v3D/assetTypes`.
1. Realice una copia del nodo **[!UICONTROL jt]**. Haga clic con el botón derecho en el nodo **[!UICONTROL jt]** y seleccione **[!UICONTROL Copy]**, luego haga clic con el botón derecho en la carpeta **[!UICONTROL assetTypes]** y seleccione **[!UICONTROL Pegar]**. Esto debería producir un nuevo nodo `/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`.
1. Cambie el nombre del nuevo nodo para darle un nombre único que represente el tipo de archivo que se va a agregar. El sufijo del archivo puede utilizarse o cualquier otro identificador único.

1. Establezca la propiedad **[!UICONTROL Enabled]** del nuevo nodo en `true`.

1. Establezca la propiedad **[!UICONTROL Extension]** de la nueva nota en el sufijo de archivo/extensión del formato que se está agregando.
1. Establezca la propiedad **[!UICONTROL MimeType]** en un valor apropiado. `application/x-` seguido del valor de la propiedad  **** Extensionproperty debe funcionar para la mayoría de los tipos de archivo.
1. Asegúrese de que la propiedad **[!UICONTROL Conversion]** está establecida en `fbx` y **[!UICONTROL IngestRegime]** en `Maya`.
1. Haga clic en **[!UICONTROL Guardar todo]** cerca de la parte superior izquierda de la página.

La siguiente captura de pantalla ilustra un formato de archivo agregado, usando como ejemplo COLLADA DAE:

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)
