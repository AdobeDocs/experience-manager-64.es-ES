---
title: Configuración del componente Vídeo
seo-title: Configure the Video component
description: Obtenga información sobre cómo configurar el componente de vídeo.
seo-description: Learn how to configure the Video Component.
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 2%

---

# Configuración del componente Vídeo {#configure-the-video-component}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La variable [Componente de vídeo](/help/sites-authoring/default-components-foundation.md#video) permite colocar un elemento de vídeo predefinido y listo para usar (OOTB) en la página.

Para que se produzca la transcodificación adecuada, el administrador debe [Instalar FFmpeg y configurar AEM](#install-ffmpeg) por separado. También pueden [Configurar los perfiles de vídeo](#configure-video-profiles) para su uso con elementos HTML5.

>[!CAUTION]
>
>Ya no se espera que este componente funcione de forma predeterminada sin una amplia personalización a nivel de proyecto.

## Configuración de perfiles de vídeo {#configure-video-profiles}

Puede que desee definir perfiles de vídeo para utilizarlos en elementos HTML5. Los elegidos aquí se utilizan en orden. Para acceder, utilice [Modo de diseño](/help/sites-authoring/default-components-designmode.md) (Solo IU clásica) y seleccione la **[!UICONTROL Perfiles]** pestaña:

![chlimage_1-317](assets/chlimage_1-317.png)

También puede configurar el diseño de los componentes y parámetros de vídeo para [!UICONTROL Reproducción], [!UICONTROL Flash]y [!UICONTROL Avanzadas].

## Instalar FFmpeg y configurar AEM {#install-ffmpeg}

El componente Vídeo se basa en el producto de terceros de código abierto FFmpeg para una transcodificación adecuada de los vídeos que se pueden descargar de [https://ffmpeg.org/](https://ffmpeg.org/). Después de instalar FFmpeg, debe configurar AEM para utilizar un códec de audio específico y opciones de tiempo de ejecución específicas.

**Para instalar FFmpeg en su plataforma**:

* **En Windows:**

   1. Descargue el binario compilado como `ffmpeg.zip`
   1. Descomprima a una carpeta.
   1. Configure la variable de entorno del sistema `PATH` a `<*your-ffmpeg-locatio*n>\bin`
   1. Reinicie AEM.

* **En Mac OS X:**

   1. Instale Xcode ([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. Instale XQuartz/X11.
   1. Instalar MacPorts ([https://www.macports.org/](https://www.macports.org/))
   1. En la consola, ejecute el siguiente comando y siga las instrucciones:

      `sudo port install ffmpeg`

      `FFmpeg` debe estar en `PATH` así AEM puede recogerlo a través de la línea de comandos.

* **Uso de la versión precompilada para OS X 10.6:**

   1. Descargue la versión precompilada.
   1. Extráigala en el `/usr/local` directorio.
   1. Desde el terminal, ejecute:

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**Para configurar AEM**:

1. Apertura [!UICONTROL CRXDE Lite] en el explorador web. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. Seleccione el `/libs/settings/dam/video/format_aac/jcr:content` y asegúrese de que las propiedades del nodo son las siguientes:

   * audioCodec:

      ```
       aac
      ```

   * customArgs:

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. Para personalizar la configuración, cree una superposición en `/apps/settings/` y mueva la misma estructura debajo de `/conf/global/settings/` nodo . No se puede editar en `/libs` nodo . Por ejemplo, para superponer la ruta `/libs/settings/dam/video/fullhd-bp`, créelo en `/conf/global/settings/dam/video/fullhd-bp`.

   >[!NOTE]
   >
   >Superponga y edite todo el nodo de perfil y no solo la propiedad que necesita modificación. Estos recursos no se resuelven mediante SlingResourceMerger.

1. Si ha cambiado cualquiera de las propiedades, haga clic en **[!UICONTROL Guardar todo]**.

>[!NOTE]
>
>Los modelos de flujo de trabajo de OOTB no se conservan al actualizar la instancia de AEM. Adobe recomienda copiar los modelos de flujo de trabajo de OOTB antes de editarlos. Por ejemplo, copie el modelo OOTB DAM Update Asset antes de editar el paso FFmpeg Transcoding en el modelo DAM Update Asset para elegir los nombres de perfil de vídeo que existían antes de la actualización. A continuación, puede superponer la variable `/apps` para permitir AEM recupere los cambios personalizados del modelo OOTB.
