---
title: Visualización de recursos 3D
description: Obtenga información sobre el visor 3D interactivo disponible en la página de detalles de recursos de AEM y cómo utilizarlo para ver recursos 3D.
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
exl-id: 71f89564-a413-49f6-8d6e-c5305bf92c75
feature: Recursos 3D
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1780'
ht-degree: 32%

---

# Visualización de recursos 3D {#viewing-d-assets}

>[!IMPORTANT]
>
>AEM 3D en AEM 6.4 ya no es compatible. Adobe recomienda utilizar la función Recursos 3D en [AEM como Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia) o [AEM 6.5.3 o superior.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic) para ver los recursos 3D.

Este documento describe cómo ver los recursos 3D en los detalles de los recursos y cómo ver los recursos que se encuentran en el componente 3D en los sitios.

## Visualización de recursos 3D en la página Detalles del recurso {#viewing-d-assets-in-the-asset-details-page}

El visor interactivo 3D está disponible en la página de información de recursos de AEM. El visor incluye, entre otras cosas, una colección de controles de cámara interactivos que le permiten girar, ampliar o reducir y panoramizar el recurso 3D.

![chlimage_1-139](assets/chlimage_1-139.png)

Además de utilizar los escenarios predeterminados en AEM 3D, también puede utilizar los escenarios que haya creado en una aplicación de terceros y cargado en AEM.

Consulte [Acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Para ver un recurso 3D, el navegador de su dispositivo o de escritorio debe tener WebGL activado. Además, el hardware de gráficos subyacente debe tener suficientes capacidades y memoria para representar modelos de tamaño y complejidad deseados. Algunas funciones de vista previa, como sombra proyectada, no están disponibles en todos los navegadores.

### Consideraciones de rendimiento al ver recursos 3D {#performance-considerations-when-you-view-d-assets}

El tiempo que se tarda en abrir un recurso 3D en la vista de la página de información del recurso depende de varios factores. Estos factores incluyen elementos como los siguientes:

* Ancho de banda y latencias al servidor.
* Tamaño del modelo (número de caras).
* Número y tamaño de los mapas.
* Complejidad del escenario. Por ejemplo, el tamaño de la imagen de IBL.

Además, las capacidades del equipo cliente (como una estación de trabajo, un portátil o un dispositivo táctil móvil) también son importantes de tener en cuenta al manipular la cámara de forma interactiva. Un sistema razonablemente potente con buenas capacidades gráficas puede hacer que la experiencia de visualización interactiva en 3D sea más cómoda y agradable.

**Para ver los recursos 3D**:

1. Asegúrese de que ha cargado los recursos 3D en AEM.

   Consulte [Acerca de la carga y el procesamiento de los recursos 3D en AEM](upload-processing-3d-assets.md).

1. Desde AEM, en la página **[!UICONTROL Navegación]**, pulse **[!UICONTROL Recursos]**.
1. Cerca de la esquina superior derecha de la página, en la lista desplegable **[!UICONTROL Ver]**, pulse **[!UICONTROL Vista de tarjeta]**.
1. Vaya a un recurso 3D que desee ver.
1. Toque la tarjeta del recurso 3D para abrirlo en la página de información del recurso.
1. Realice una de las acciones siguientes:

   * En la esquina inferior derecha de la página de información del recurso, utilice la paleta de control de cámara para cambiar las distintas vistas del recurso.

      Si utiliza un dispositivo de entrada que no sea táctil ni tenga una rueda de desplazamiento, por ejemplo, un ratón Apple clásico de un solo botón, sigue siendo posible cambiar el zoom o la perspectiva de un recurso 3D, mientras esté en cada modo respectivo. Para realizar la acción, mantenga pulsada la tecla `SHIFT`mientras pulsa el botón del ratón y arrastra hacia arriba o hacia abajo.

      Al utilizar un panel táctil en un equipo portátil típico, a menudo resulta difícil controlar los comportamientos del zoom o de la perspectiva con el gesto de pellizcar con dos dedos. En estos casos, puede mantener pulsada la tecla `SHIFT`durante la acción. Este tipo de esfuerzo reduce la velocidad del gesto de pellizcar y hace que sea más fácil conseguir el nivel de zoom exacto o la perspectiva que desea. Como alternativa, puede usar un dedo para arrastrar hacia arriba o hacia abajo mientras presiona la tecla `SHIFT`para afectar a los comportamientos de zoom o perspectiva.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Nombre de control de cámara</strong><br /> </td> 
      <td><strong>Descripción</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p>o</p> <p>Persp</p> </td> 
      <td><p>Toque o haga clic para alternar entre los modos Zoom y Perspectiva.</p> <p>O bien, mantenga pulsada la tecla <code>ALT/OPTION</code> durante la acción para alternar temporalmente al modo Perspectiva<br />. Suelte la tecla para volver al modo de Zoom.</p> 
      <ul> 
      <li><strong>Zoom</strong>: comportamiento de entrada y salida que mueve la cámara más cerca o más lejos del <br /> recurso que está viendo. El zoom es el comportamiento predeterminado de la rueda de desplazamiento de un ratón (si está disponible), de los gestos de pellizcar con dos dedos en los dispositivos móviles, o cuando mantiene pulsada la tecla Mayús mientras arrastra hacia arriba o abajo con el botón izquierdo del ratón.</li> 
      <li><strong>Perspectiva</strong>: cambia la distancia focal (también conocida como campo de visión) de la cámara mientras mantiene el tamaño relativo del recurso en la vista. La perspectiva es el comportamiento alternativo de la rueda de desplazamiento de un ratón (si está disponible), de los gestos de pellizcar con dos dedos en los dispositivos móviles, o cuando mantiene pulsada la tecla Mayús mientras arrastra hacia arriba o abajo con el botón izquierdo del ratón.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Orbit</p> <p>o</p> <p>Panorámica</p> </td> 
      <td><p>Toque o haga clic para alternar entre los modos Giro y Panorámica.</p> <p>O bien, mantenga pulsada la tecla <code>ALT/OPTION</code> durante la acción para alternar temporalmente al modo Panorámica. Suelte la tecla para volver al modo de Giro.</p> 
      <ul> 
      <li><strong>Giro</strong>: mueve la cámara de visualización en una esfera centrada en un punto de destino que se encuentra cerca del centro del recurso 3D predeterminado. El giro es el comportamiento predeterminado al arrastrar con el botón izquierdo o al arrastrar con un solo toque en dispositivos móviles.</li> 
      <li><strong>Panorámica</strong>: mueve la cámara en el plano de visualización. El punto de destino se mueve en consecuencia, de manera que las acciones de giro posteriores moverán la cámara alrededor de un nuevo punto de destino. La panorámica es el comportamiento alternativo al arrastrar con el botón izquierdo y al arrastrar con un solo toque.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Examinar</p> <p>o</p> <p>Destino</p> </td> 
      <td><p>Toque o haga clic para alternar entre los modos Examinar y Destino.</p> 
      <ul> 
      <li><strong>Examinar</strong>: toque o haga clic para entrar en el modo Destino.</li> 
      <li><strong>Destino</strong>: toque o haga clic en un punto en cualquier lugar del recurso 3D para centrar la vista en esa parte del recurso.<br /> Las acciones de giro utilizan el nuevo punto de destino.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Restablecer</td> 
      <td>Toque o haga clic para restaurar el punto de destino de la vista al centro del modelo. Restablecer también mueve la cámara<br /> más cerca o más lejos para mostrar el recurso en su totalidad y con un tamaño de visualización razonable.</td> 
      </tr> 
    </tbody> 
    </table>

   * Cerca de la esquina superior derecha de la página de detalles del recurso, pulse el icono **[!UICONTROL Selector de escenario]**. Seleccione un nombre de escenario con el fondo y la iluminación que desee aplicar al recurso 3D.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   Los escenarios proporcionan el entorno (fondo, plano de tierra e iluminación) en el que se ve el modelo 3D.

   Consulte [Información acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Cerca de la esquina superior derecha de la página de detalles del recurso, pulse el icono **[!UICONTROL Selector de cámara]** y, a continuación, seleccione una vista de cámara que desee aplicar al recurso 3D.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   A menudo, los escenarios proporcionan cámaras predefinidas. Puede volver a seleccionar la cámara actual para restaurarla a su configuración predefinida.

   Consulte [Información acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. En la esquina superior derecha de la página, toque **[!UICONTROL Guardar]**.
1. Realice una de las acciones siguientes:

   * Procesar el recurso 3D.

      Consulte [Procesamiento de recursos 3D](rendering-3d-assets.md).

   * En la esquina superior derecha de la página, toque **[!UICONTROL Cerrar]** para volver a la página Recursos.

## Visualización de recursos 3D en el componente 3D de Sites {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Esta sección se aplica solo al visor webGL clásico utilizado para tipos de recursos 3D distintos de Adobe Dimension.

Según el tipo de dispositivo, puede acceder a las funciones de los componentes 3D de varias formas.

Para obtener más información, consulte:

* [Dispositivos de pantalla táctil](#touchscreen-devices)
* [Dispositivos Touchpad](#touchpad-devices)
* [Dispositivos Mouse y trackball](#mouse-and-trackball-devices)

Consulte también [Vista previa de una página web que tiene un componente 3D](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component).

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Dispositivos de pantalla táctil {#touchscreen-devices}

Para trabajar con componentes 3D con dispositivos de pantalla táctil:

1. Use un dedo para arrastrar o deslizar para mover (&quot;orbitar&quot;) el punto de vista (&quot;cámara&quot;) alrededor del objeto. Puede ver el objeto desde cualquier dirección.

1. Utilice un pellizco de dos dedos para mover la cámara más cerca o más lejos del objeto. Esta acción es similar a ampliar o reducir y permite inspeccionar los detalles del objeto. Como alternativa, mantenga pulsados los botones + o - para mover la cámara más cerca o más lejos del objeto.

1. Arrastre con dos dedos para panorámica de la cámara. Esta acción mueve la cámara lateralmente para permitirle ver diferentes partes del objeto mientras se amplía. También puede pulsar el botón **[!UICONTROL Giro/Panorámica]** para alternar al modo Panorámica y, a continuación, arrastrar un dedo para recorrer la cámara. Pulse el botón **[!UICONTROL Giro de giro/giro]** para volver al modo **[!UICONTROL Giro]**.

1. Pulse **[!UICONTROL Restablecer visor]** para reiniciar la cámara. Esta acción lleva el objeto a la vista completa y, si está activado, reanuda el giro automático.

1. Toque **[!UICONTROL Pantalla completa]** para entrar al modo de pantalla completa (si es compatible con el dispositivo). Toque **[!UICONTROL Pantalla completa]** de nuevo para restaurar el visor 3D al modo incrustado en la página.

### Dispositivos Touchpad {#touchpad-devices}

Para trabajar con componentes 3D con dispositivos táctiles:

1. Arrastre con un dedo mientras mantiene presionado el botón del panel táctil (izquierdo) hacia abajo para mover (&quot;órbita&quot;) el punto de vista (&quot;cámara&quot;) alrededor del objeto. Puede ver el objeto desde cualquier dirección.

1. Utilice un botón de dos dedos para arrastrar hacia abajo o hacia arriba con los botones del panel táctil hacia arriba para mover la cámara más cerca o más lejos del objeto. Esta acción es similar a ampliar o reducir y permite inspeccionar los detalles del objeto. Como alternativa, mantenga pulsados los botones **[!UICONTROL Ampliar]** o **[!UICONTROL Reducir]** para acercar o alejar la cámara del objeto.

1. Arrastre con un dedo mientras mantiene presionada la tecla **ALT/option** y el botón del panel táctil (izquierdo) para panorámica de la cámara. Esta acción mueve la cámara lateralmente para permitirle ver diferentes partes del objeto mientras se amplía. Como alternativa, haga clic en el botón **[!UICONTROL Giro de giro]** para cambiar al modo **[!UICONTROL Panorámica]** y, a continuación, arrastre con un dedo mientras mantiene presionado el botón (izquierdo) para panoramizar la cámara. Haga clic en el botón **[!UICONTROL Giro/Panorámica]** de nuevo para volver al modo **[!UICONTROL Giro]**.

1. Haga clic en **[!UICONTROL Restablecer visor]** para restablecer la cámara. Esta acción lleva el objeto a la vista completa y, si está activado, reanuda el giro automático.

1. Haga clic en **[!UICONTROL Pantalla completa]** para entrar al modo de pantalla completa. Utilice la tecla **Escape** del teclado o haga clic en **[!UICONTROL Pantalla completa]** de nuevo para restaurar el visor 3D al modo incrustado en la página.

### Dispositivos de mouse y trackball {#mouse-and-trackball-devices}

Para trabajar con componentes 3D con dispositivos de ratón y trackball:

1. Arrastre mientras mantiene presionado el botón izquierdo del ratón para mover (&quot;orbitar&quot;) el punto de vista (&quot;cámara&quot;) alrededor del objeto. Puede ver el objeto desde cualquier dirección.

1. Utilice la rueda de desplazamiento para acercar o alejar la cámara del objeto. Esto es similar a acercar o alejar y permite inspeccionar los detalles del objeto. Como alternativa, mantenga pulsados los botones **[!UICONTROL Ampliar]** o **[!UICONTROL Reducir]** para acercar o alejar la cámara del objeto.

1. Arrastre mientras mantiene pulsada la tecla **ALT/option** y el botón izquierdo del ratón para recorrer la cámara. Esto mueve la cámara lateralmente para permitir ver diferentes partes del objeto mientras se amplía. Como alternativa, haga clic en el botón **[!UICONTROL Giro de giro/giro]** para alternar al modo **[!UICONTROL Panorámica]** y, a continuación, arrastre mientras mantiene presionado el botón izquierdo del ratón para panoramizar la cámara. Vuelva a hacer clic en **[!UICONTROL Giro/Panorámica]** para volver al modo **[!UICONTROL Giro]**.
1. Haga clic en **[!UICONTROL Restablecer visor]** para restablecer la cámara. Esta acción lleva el objeto a la vista completa y, si está activado, reanuda el giro automático.
1. Haga clic en **[!UICONTROL Pantalla completa]** para entrar al modo de pantalla completa. Utilice la tecla **[!UICONTROL Escape]** del teclado o haga clic en **[!UICONTROL Pantalla completa]** de nuevo para restaurar el visor 3D al modo incrustado en la página.
