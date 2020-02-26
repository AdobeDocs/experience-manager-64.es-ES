---
title: Uso del componente Sitios 3D
seo-title: Uso del componente Sitios 3D
description: AEM 3D incluye un componente Sitios AEM que se puede utilizar para implementar la visualización interactiva de modelos 3D en páginas web.
seo-description: AEM 3D incluye un componente Sitios AEM que se puede utilizar para implementar la visualización interactiva de modelos 3D en páginas web.
uuid: 4f06bab3-1e31-49ef-89e3-b26195966538
contentOwner: Rick Brough
topic-tags: 3D
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: 9017ab55-6d4a-4306-922f-223ab1b2504b
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f

---


# Uso del componente Sitios 3D {#working-with-the-d-sites-component}

AEM 3D incluye un componente Sitios AEM que puede utilizar para implementar la visualización interactiva de modelos 3D en páginas web.

Una vez agregado el componente 3D, puede [ver el recurso 3D en dicho componente.](viewing-3d-assets.md)

## Adición del componente 3D a la plantilla de página {#adding-the-d-component-to-the-page-template}

Debe habilitar el componente 3D en la página para poder colocarlo en una página. Consulte [Edición de plantillas](/help/sites-authoring/templates.md#editing-a-template-layout-template-author) para obtener información detallada sobre cómo activar componentes en plantillas.

**Adición del componente 3D a la plantilla** de página:

1. Vaya a **[!UICONTROL Herramientas > General > Plantillas]**.

1. Vaya a la plantilla de página en la que desea habilitar el componente 3D y seleccione la plantilla.

1. Toque **[!UICONTROL Editar]** para abrir la plantilla.
1. Cerca de la esquina superior derecha de la página, en el menú desplegable, seleccione el modo **[!UICONTROL Estructura]** , si aún no está activo.

   ![image2017-11-14_15-33-57](assets/image2017-11-14_15-33-57.png)

1. Toque en la región Contenedor **[!UICONTROL de]** diseño para seleccionarla.

1. Toque el botón **[!UICONTROL Política]** para abrir el Editor **[!UICONTROL de directivas]**.
1. En la sección **[!UICONTROL Propiedades]** , seleccione la marca de verificación **[!UICONTROL 3D]** y, a continuación, toque **[!UICONTROL Listo]** para guardar los cambios y cerrar el Editor **[!UICONTROL de]** directivas.

   Ahora puede colocar el componente Sitios 3D en todas las páginas que utilicen esta plantilla.

## Adición del componente de visor 3D a una página web {#adding-the-d-viewer-component-to-a-web-page}

>[!CAUTION]
>
>Esta versión de AEM 3D solo admite una instancia del componente 3D en cada página web. Varios componentes 3D en la misma página no funcionan correctamente.

**Para añadir el componente de visor 3D a una página** web:

1. Abra Sitios AEM y seleccione la página web a la que desea añadir el componente 3D.

1. Toque el icono **[!UICONTROL Editar]** (lápiz) para abrir la página en el editor de páginas. Asegúrese de seleccionar el modo **[!UICONTROL Editar]** cerca de la parte superior derecha de la página.

   ![image2017-11-14_15-44-40](assets/image2017-11-14_15-44-40.png)

1. Puntee en el selector de rieles para abrir el panel lateral.

1. Toque el icono de signo más para abrir la lista **[!UICONTROL Componentes]** .

1. Arrastre el componente Visor **[!UICONTROL 3D de la lista]** Componentes **** a la ubicación de la página en la que desea que aparezca el visor 3D.

## Configuración del componente 3D {#configuring-the-d-component}

1. En el editor de páginas de AEM Sites, seleccione el componente de visor **** 3D que agregó anteriormente a la página.

1. Toque el icono **[!UICONTROL Configuración]** (llave inglesa) para abrir el cuadro de diálogo de configuración del componente.

   Puede definir las siguientes propiedades de componente:

   <table> 
    <tbody> 
    <tr> 
    <td>Propiedad</td> 
    <td>Descripción</td> 
    <td>Aplicabilidad</td> 
    </tr> 
    <tr> 
    <td>Altura (px)</td> 
    <td>Especifique la altura deseada del componente 3D en píxeles. Si se deja vacío, el valor predeterminado es 600 píxeles.</td> 
    <td> </td> 
    </tr> 
    <tr> 
    <td>Nombre de la etapa</td> 
    <td><p>Seleccione un escenario 3D en la lista de etapas disponibles. El escenario ofrece un fondo y una iluminación.</p> <p>See <a href="/help/assets/about-the-use-of-stages-in-aem-3d.md" target="_blank">About the use of stages in AEM 3D Sites</a>.</p> </td> 
    <td>Se omite para recursos de dimensión de Adobe.</td> 
    </tr> 
    <tr> 
    <td>Velocidad de giro automático (RPM)</td> 
    <td><p>El visor 3D orbita la cámara continuamente después de la carga y el reinicio. El giro automático termina cuando el usuario inicia una acción de órbita manual.</p> <p>Puede especificar la velocidad de giro en RPM con los siguientes valores:</p> 
        <ul> 
        <li>Definir un valor positivo para girar a la derecha</li> 
        <li>Definir un valor negativo para girar a la izquierda</li> 
        <li>Establezca un valor 0 para deshabilitar el giro automático.</li> 
        </ul> <p>El valor predeterminado es 3 RPM, equivalente a 20 segundos por revolución completa.<br /><br /> <strong> Nota: </strong>Nota: La velocidad de giro supone una velocidad de fotogramas de 60/seg. Esta tasa se consigue normalmente con modelos pequeños o de tamaño moderado en hardware de gráficos más potente. Modelos más grandes o dispositivos más lentos giran automáticamente a velocidades más bajas.</p> </td> 
    <td>Se omite para recursos de dimensión de Adobe.</td> 
    </tr> 
    <tr> 
    <td>Color del botón de navegación</td> 
    <td>Utilice el selector de color para elegir el color principal de los botones de control del visor.</td> 
    <td>Se omite para los recursos de dimensión de Adobe.</td> 
    </tr> 
    <tr> 
    <td>Color al pasar sobre la navegación</td> 
    <td>Use el selector de color para elegir el color seleccionado o al que desea pasar el ratón por encima para los botones de control del visor.</td> 
    <td>Se omite para recursos de dimensión de Adobe.</td> 
    </tr> 
    <tr> 
    <td>Mostrar muestras</td> 
    <td>Para uso futuro.</td> 
    <td>Se omite para recursos de dimensión de Adobe.</td> 
    </tr> 
    <tr> 
    <td>Mostrar ajustes preestablecidos de cámara GLTF</td> 
    <td>Muestre u oculte los ajustes preestablecidos de cámara que pueden estar presentes en los recursos de dimensión de Adobe.</td> 
    <td>Solo para recursos de dimensión de Adobe.</td> 
    </tr> 
    <tr> 
    <td>Color de fondo GLTF</td> 
    <td>Color de fondo predeterminado si el modelo 3D no incluye un fondo.</td> 
    <td>Solo para recursos de dimensión de Adobe.</td> 
    </tr> 
    </tbody> 
   </table>

1. Toque la marca de verificación para guardar los cambios.

   Además de las opciones disponibles en el cuadro de diálogo de configuración de componentes, hay una serie de opciones de configuración global que pueden modificarse mediante CRXDE Lite.
Consulte Configuración [avanzada](advanced-config-3d.md) para obtener información detallada sobre esta configuración global.

## Asignación de un modelo 3D al componente {#assigning-a-d-model-to-the-component}

1. En el editor de páginas de AEM Sites, haga clic en el icono **[!UICONTROL Recursos]** para abrir la lista Recursos en el panel lateral.

1. Seleccione el filtro Modelos **** 3D para ocultar los tipos de recursos no deseados.

   ![screen_shot_2017-12-11at124258](assets/screen_shot_2017-12-11at124258.png)

1. Busque o desplácese hasta el recurso 3D que desea ver en la página que se está editando.

1. Arrastre el recurso 3D de la lista **[!UICONTROL Recursos]** al componente Visor **** 3D que se ha colocado anteriormente en la página.

   Los recursos de dimensión de Adobe se representan con la nueva tecnología de visor basada en el estándar abierto glTF, mientras que todos los demás tipos de recursos 3D se basan en el visor webGL clásico de AEM 3D. El componente selecciona automáticamente el visor adecuado en función del tipo de modelo 3D.

## Vista previa de una página web con un componente 3D {#previewing-a-web-page-that-has-a-d-component}

Mientras la página web está en modo **[!UICONTROL Editar]** , el componente 3D muestra el modelo 3D, pero no es posible interactuar con el modelo.

Puede obtener una vista previa de la página web en el editor de páginas con acceso completo a la funcionalidad del componente 3D.

Consulte también [Visualización de recursos 3D en el componente](viewing-3d-assets.md#viewing-d-assets-in-the-sites-d-component)Sitios 3D.

**Para obtener una vista previa de una página web que tiene un componente** 3D:

1. Realice una de las siguientes acciones:

   * Cerca de la esquina superior derecha de la página, haga clic en **[!UICONTROL Vista previa]** para acceder al modo de vista previa.
   * Elimine `/edit.html` de la dirección URL de la página en el explorador.

## Publicación de la página y los recursos {#publishing-the-page-and-assets}

Consulte [Publicación de recursos](managing-assets-touch-ui.md) para obtener información sobre cómo publicar recursos. Consulte [Publicación de páginas](/help/sites-authoring/publishing-pages.md) para obtener información sobre cómo publicar páginas.

>[!NOTE]
>
>Si utiliza el elemento de menú **[!UICONTROL Publicar página]** del menú Información **[!UICONTROL de]** página, se publicará la página y todas las dependencias de la página principal. Las dependencias secundarias a las que puede hacer referencia el modelo 3D y/o la fase 3D, como los mapas de textura y las imágenes IBL, no se publican al publicar la página de esta manera.
>
>Adobe recomienda publicar todos los recursos 3D y sus dependencias directamente desde Recursos AEM antes de publicar la página web que hace referencia a estos recursos.

