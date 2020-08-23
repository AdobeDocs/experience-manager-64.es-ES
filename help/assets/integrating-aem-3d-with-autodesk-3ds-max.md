---
title: Integración de AEM 3D con Autodesk 3ds Max
seo-title: Integración de AEM 3D con AutoDesk 3ds Max
description: Opcionalmente, puede integrar AEM 3D con el software Autodesk 3ds Max para permitir la compatibilidad con archivos 3ds Max nativos (.MAX). El procesamiento mediante 3ds Max no se admite en este momento.
seo-description: Opcionalmente, puede integrar AEM 3D con el software Autodesk 3ds Max para permitir la compatibilidad con archivos 3ds Max nativos (.MAX). El procesamiento mediante 3ds Max no se admite en este momento.
uuid: 6c160ad3-6b6f-43f5-9e97-5b5d962a8d1a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
topic-tags: 3D
discoiquuid: 0d7fefc0-6923-4ac3-9e90-335c08fa56f0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Integración de AEM 3D con Autodesk 3ds Max {#integrating-aem-d-with-autodesk-ds-max}

>[!NOTE]
>
>Esta tarea es opcional y se aplica solo a Windows.

Opcionalmente, puede integrar AEM 3D con el software Autodesk 3ds Max para permitir la compatibilidad con archivos 3ds Max nativos (.MAX). El procesamiento mediante 3ds Max no se admite en este momento.

Consulte Configuración [avanzada](advanced-config-3d.md).

Consulte también [Integración de AEM 3D con AutoDesk Maya](integrate-maya-with-3d.md).

**Para integrar AEM 3D con Autodesk 3ds Max**:

1. Instale el software Autodesk 3ds Max en los mismos servidores donde están instalados los nodos de AEM Author.

   Después de la instalación, compruebe que puede abrir y utilizar Maya y que no hay problemas con las licencias.

   >[!NOTE]
   >
   >Para evitar problemas de acceso denegado, instale 3ds Max con la misma cuenta de usuario administrador que AEM.

1. En 3ds Max, haga clic en **[!UICONTROL Personalizar > Administrador]** de complementos.

   Busque `FBXMAX.DLU` y verifique que su **[!UICONTROL estado]** esté **[!UICONTROL cargado]**.

   Cierre el cuadro de diálogo Administrador **[!UICONTROL de complementos]** y 3ds Max.

1. Actualice la secuencia de comandos de conversión.

   AEM utiliza una secuencia de comandos de línea de comandos para invocar la utilidad de línea de comandos 3ds Max `3dsmaxcmd.exe`. Debe editar esta secuencia de comandos si ha instalado una versión distinta a 3ds Max 2016, si ha instalado 3ds Max en una ubicación no estándar o si ha instalado AEM en una partición o unidad diferente.

   1. Abra el CRXDE Lite y vaya a `/libs/settings/dam/v3D/scripts/max`.
   1. Haga clic con el doble `export-fbx.bat` para abrirlo.
   1. Edite la primera línea de la secuencia de comandos según sea necesario para reflejar la ubicación de la `3dsmaxcmd.exe` utilidad. Por ejemplo, si se utiliza 3ds Max 2017 y AEM está instalado en una unidad de disco diferente:

   ![image2018-6-22_13-35-8](assets/image2018-6-22_13-35-8.png)

1. Cerca de la esquina superior izquierda de la página CRXDE Lite, toque **[!UICONTROL Guardar todo]**.

   Cerca de la esquina superior izquierda de la página CRXDE Lite, toque **[!UICONTROL Guardar todo]**.

1. Quite la carpeta de trabajo (solo es necesario si se ha intentado ingestar un archivo .MAX).

   1. En CRXDE Lite, vaya a `/libs/settings/dam/v3D/Paths/maxWorkPath`. De forma predeterminada, el valor de esta configuración es `./MaxWork`, que es relativo a la carpeta raíz de la instalación de AEM.
   1. Inicie sesión en el propio servidor y utilice el Explorador de archivos para desplazarse a la carpeta raíz de la instalación de AEM.
   1. Elimine la carpeta **[!UICONTROL MaxWork]** , incluido todo su contenido, si existe.

      La carpeta se vuelve a crear automáticamente la próxima vez que se ingrese un archivo .MAX.

1. Habilite 3ds Max para la ingestión haciendo lo siguiente:

   1. En CRXDE Lite, vaya a `/libs/settings/dam/v3D/assetTypes/max` y establezca la propiedad **[!UICONTROL Enabled]** en true:

   ![image2018-6-22_13-50-50](assets/image2018-6-22_13-50-50.png)

1. Cerca de la esquina superior izquierda de la página CRXDE Lite, toque **[!UICONTROL Guardar todo]**.

## Prueba de la integración de AEM 3D con Autodesk 3ds Max {#testing-the-integration-of-aem-d-with-autodesk-ds-max}

1. Abra AEM Assets y, a continuación, cargue el `.max` archivo ubicado en `sample-3D-content/models` la carpeta **[!UICONTROL test3d]** .

   Tenga en cuenta que sample-3D-content.zip se ha descargado anteriormente para validar la funcionalidad 3D básica.

1. Vuelva a la vista **[!UICONTROL Tarjeta]** y observe los letreros de mensaje que se muestran en los recursos cargados.

   La pancarta Formato de conversión se muestra mientras 3ds Max está convirtiendo el formato nativo 3ds Max a .FBX.

1. Una vez finalizado el procesamiento, abra `logo-sphere.max` en la vista **[!UICONTROL Detalle]** .

   La experiencia de Previsualización es la misma que con `logo_sphere.fbx`.

