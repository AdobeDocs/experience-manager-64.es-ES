---
title: Visualización de recursos 3D
seo-title: Visualización de recursos 3D
description: Obtenga información sobre el visor 3D interactivo disponible en la página de detalles de recursos de AEM y cómo utilizarlo para la vista de recursos 3D.
seo-description: Obtenga información sobre el visor 3D interactivo disponible en la página de detalles de recursos de AEM y cómo utilizarlo para la vista de recursos 3D.
uuid: 7d8133ac-3110-4979-8e19-e65090e791be
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 65040923-a8a8-4e27-82c0-67a04348e238
translation-type: tm+mt
source-git-commit: 11b65cf2d180f04168d4c5d0929957c95a372e3c
workflow-type: tm+mt
source-wordcount: '1806'
ht-degree: 32%

---


# Visualización de recursos 3D {#viewing-d-assets}

>[!IMPORTANT]
>
>Ya no se admite AEM 3D en AEM 6.4. Adobe recomienda utilizar la función de recursos 3D en [AEM como Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) o [AEM 6.5.3 o superior.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html) para vista de recursos 3D.

En este documento se describe cómo realizar la vista de recursos 3D en los detalles de recursos y cómo realizar la vista de recursos que se encuentran en el componente 3D de los sitios.

## Visualización de recursos 3D en la página Detalles del recurso {#viewing-d-assets-in-the-asset-details-page}

El visor interactivo 3D está disponible en la página de información de recursos de AEM. El visor incluye, entre otras cosas, una colección de controles de cámara interactivos que le permiten girar, ampliar o reducir y panoramizar el recurso 3D.

![chlimage_1-139](assets/chlimage_1-139.png)

Además de utilizar los escenarios predeterminados en AEM 3D, también puede utilizar los escenarios que haya creado en una aplicación de terceros y cargado en AEM.

Consulte [Acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

>[!NOTE]
>
>Para ver un recurso 3D, el navegador de su dispositivo o de escritorio debe tener WebGL activado. Además, el hardware de gráficos subyacente debe tener suficientes capacidades y memoria para procesar modelos de tamaño y complejidad deseados. Algunas funciones de previsualización, como sombra proyectada, no están disponibles en todos los navegadores.

### Consideraciones de rendimiento al ver recursos 3D {#performance-considerations-when-you-view-d-assets}

El tiempo que se tarda en abrir un recurso 3D en la vista de la página de información del recurso depende de varios factores. Estos factores incluyen elementos como los siguientes:

* Ancho de banda y latencias al servidor.
* Tamaño del modelo (número de caras).
* Número y tamaño de los mapas.
* Complejidad del escenario. Por ejemplo, el tamaño de la imagen de IBL.

Además, las capacidades del ordenador cliente, como una estación de trabajo, un ordenador portátil o un dispositivo móvil táctil, también son importantes para tener en cuenta al manipular la cámara de forma interactiva. Un sistema razonablemente potente con buenas capacidades gráficas puede hacer que la experiencia de visualización interactiva en 3D sea más cómoda y agradable.

**Para ver los recursos 3D**:

1. Asegúrese de que ha cargado los recursos 3D en AEM.

   Consulte [Acerca de la carga y el procesamiento de los recursos 3D en AEM](upload-processing-3d-assets.md).

1. From AEM, on the **[!UICONTROL Navigation]** page, tap **[!UICONTROL Assets]**.
1. Near the upper-right corner of the page, from the **[!UICONTROL View]** drop-down list, tap **[!UICONTROL Card View]**.
1. Vaya a un recurso 3D que desee ver.
1. Toque la tarjeta del recurso 3D para abrirlo en la página de información del recurso.
1. Realice una de las acciones siguientes:

   * En la esquina inferior derecha de la página de información del recurso, utilice la paleta de control de cámara para cambiar las distintas vistas del recurso.

      Si utiliza un dispositivo de entrada que no sea táctil ni tenga una rueda de desplazamiento, por ejemplo, un ratón Apple clásico de un solo botón, sigue siendo posible cambiar el zoom o la perspectiva de un recurso 3D, mientras esté en cada modo respectivo. You accomplish the action by pressing and holding down the `SHIFT`key while depressing the mouse button and dragging up or down.

      Al utilizar un panel táctil en un equipo portátil típico, a menudo resulta difícil controlar los comportamientos del zoom o de la perspectiva con el gesto de pellizcar con dos dedos. In such cases, you can press and hold down `SHIFT`during the action. Este tipo de esfuerzo reduce la velocidad del gesto de pellizcar y hace que sea más fácil conseguir el nivel de zoom exacto o la perspectiva que desea. Alternately, you can use a one finger drag up or down while the `SHIFT`key is pressed to affect zoom or perspective behaviors.
   <table> 
    <tbody> 
      <tr> 
      <td><strong>Nombre del control de cámara</strong><br /> </td> 
      <td><strong>Descripción</strong></td> 
      </tr> 
      <tr> 
      <td><p>Zoom</p> <p>o</p> <p>Persp</p> </td> 
      <td><p>Toque o haga clic para alternar entre los modos Zoom y Perspectiva.</p> <p>O bien, mantenga presionada la <code>ALT/OPTION</code> tecla durante la acción para cambiar temporalmente al modo de perspectiva<br /> . Suelte la tecla para volver al modo de Zoom.</p> 
      <ul> 
      <li><strong>Zoom</strong>-Acercar y alejar la cámara, lo que la aleja del recurso<br /> que está viendo. El zoom es el comportamiento predeterminado de la rueda de desplazamiento de un ratón (si está disponible), de los gestos de pellizcar con dos dedos en los dispositivos móviles, o cuando mantiene pulsada la tecla Mayús mientras arrastra hacia arriba o abajo con el botón izquierdo del ratón.</li> 
      <li><strong>Perspectiva</strong>: cambia la distancia focal (también conocida como campo de vista) de la cámara mientras se mantiene el tamaño relativo del recurso en la vista. La perspectiva es el comportamiento alternativo de la rueda de desplazamiento de un ratón (si está disponible), de los gestos de pellizcar con dos dedos en los dispositivos móviles, o cuando mantiene pulsada la tecla Mayús mientras arrastra hacia arriba o abajo con el botón izquierdo del ratón.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Orbit</p> <p>o</p> <p>Panorámica</p> </td> 
      <td><p>Toque o haga clic para alternar entre los modos Orbit y Pan.</p> <p>O bien, mantenga pulsada la <code>ALT/OPTION</code> tecla durante la acción para cambiar temporalmente al modo de desplazamiento. Suelte la tecla para volver al modo de Giro.</p> 
      <ul> 
      <li><strong>Orbit</strong>: Mueve la cámara de visualización en una esfera centrada en un punto de destinatario que se encuentra cerca del centro del recurso 3D por defecto. El giro es el comportamiento predeterminado al arrastrar con el botón izquierdo o al arrastrar con un solo toque en dispositivos móviles.</li> 
      <li><strong>Recorrido</strong>: mueve la cámara en el plano de visualización. El punto de destino se mueve en consecuencia, de manera que las acciones de giro posteriores moverán la cámara alrededor de un nuevo punto de destino. La panorámica es el comportamiento alternativo al arrastrar con el botón izquierdo y al arrastrar con un solo toque.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td><p>Examinar</p> <p>o</p> <p>Destino</p> </td> 
      <td><p>Toque o haga clic para alternar entre los modos Examinar y Destinatario.</p> 
      <ul> 
      <li><strong>Examine</strong>-Toque o haga clic para entrar en el modo Destinatario.</li> 
      <li><strong>Destinatario</strong>: toque o haga clic en un punto del recurso 3D para centrar la vista en esa parte del recurso.<br /> Las acciones de giro utilizan el nuevo punto de destino.</li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td>Restablecer</td> 
      <td>Toque o haga clic para restaurar el punto de destinatario de la vista al centro del modelo. Reset also moves the camera<br /> closer or further away to show the asset in its entirety and at a reasonable viewing size.</td> 
      </tr> 
    </tbody> 
    </table>

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Stage Selector]** icon. Seleccione un nombre de escenario con el fondo y la iluminación que desee aplicar al recurso 3D.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   Las etapas proporcionan el fondo del entorno, el plano de tierra y la iluminación en la que se ve el modelo 3D.

   Consulte [Información acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

   * Near the upper-right corner of the asset details page, tap the **[!UICONTROL Camera Selector]** icon, then select a camera view that you want to apply to the 3D asset.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   A menudo, los escenarios proporcionan cámaras predefinidas. Puede volver a seleccionar la cámara actual para restaurarla a su configuración predefinida.

   Consulte [Información acerca del uso de escenarios en AEM 3D](about-the-use-of-stages-in-aem-3d.md).

1. En la esquina superior derecha de la página, toque **[!UICONTROL Guardar]**.
1. Realice una de las acciones siguientes:

   * Procesar el recurso 3D.

      Consulte [Procesamiento de recursos 3D](rendering-3d-assets.md).

   * En la esquina superior derecha de la página, toque **[!UICONTROL Cerrar]** para volver a la página Recursos.

## Visualización de recursos 3D en el componente Sitios 3D {#viewing-d-assets-in-the-sites-d-component}

>[!NOTE]
>
>Esta sección se aplica únicamente al visor webGL clásico utilizado para tipos de recursos 3D distintos de Adobe Dimension.

Según el tipo de dispositivo, se accede a las funciones del componente 3D de diversas formas.

Para obtener más información, consulte:

* [Dispositivos de pantalla táctil](#touchscreen-devices)
* [Dispositivos táctiles](#touchpad-devices)
* [Dispositivos de ratón y trackball](#mouse-and-trackball-devices)

Consulte también [Vista previa de una página web que tiene un componente](using-the-3d-sites-component.md#previewing-a-web-page-that-has-a-d-component)3D.

![screen_shot_2017-12-11at145654](assets/screen_shot_2017-12-11at145654.png)

### Dispositivos de pantalla táctil {#touchscreen-devices}

Para trabajar con componentes 3D con dispositivos de pantalla táctil:

1. Utilice un dedo para arrastrar o realizar un barrido para mover (&quot;orbitar&quot;) el punto de vista (&quot;cámara&quot;) alrededor del objeto. Puede realizar una vista del objeto desde cualquier dirección.

1. Utilice un pellizco de dos dedos para mover la cámara hacia el objeto o más lejos de él. Esta acción es similar a acercar o alejar y permite inspeccionar los detalles del objeto. Como alternativa, mantenga pulsados los botones + o - para mover la cámara más cerca o más lejos del objeto.

1. Utilice un arrastre de dos dedos para desplazar la cámara. Esta acción mueve la cámara lateralmente para permitirle ver diferentes partes del objeto mientras se amplía. Como alternativa, toque el botón Alternar **[!UICONTROL órbita/giro]** para cambiar al modo de desplazamiento y, a continuación, arrastre un dedo para recorrer la cámara. Toque el botón Alternar **[!UICONTROL giro/]** órbita para volver al modo de **[!UICONTROL órbita]** .

1. Toque **[!UICONTROL Restablecer visor]** para restablecer la cámara. Esta acción lleva al objeto a una vista completa y, si está activada, reanuda el giro automático.

1. Toque **[!UICONTROL Pantalla]** completa para acceder al modo de pantalla completa (si el dispositivo lo admite). Vuelva a tocar Pantalla **[!UICONTROL completa]** para restaurar el visor 3D al modo incrustado en la página.

### Dispositivos táctiles {#touchpad-devices}

Para trabajar con componentes 3D con dispositivos táctiles:

1. Arrastre con un dedo mientras mantiene pulsado el botón (izquierdo) del panel táctil para mover (&quot;órbita&quot;) el punto de vista (&quot;cámara&quot;) alrededor del objeto. Puede realizar una vista del objeto desde cualquier dirección.

1. Utilice un arrastre de dos dedos hacia abajo o hacia arriba con los botones de la almohadilla táctil para mover la cámara más cerca o más lejos del objeto. Esta acción es similar a acercar o alejar y permite inspeccionar los detalles del objeto. También puede hacer clic y mantener pulsados los botones **[!UICONTROL Acercar]** o **[!UICONTROL Alejar]** para acercar o alejar la cámara del objeto.

1. Arrastre un dedo mientras mantiene presionada la tecla **ALT/opción** y el botón (izquierdo) del panel táctil para recorrer la cámara. Esta acción mueve la cámara lateralmente para permitirle ver diferentes partes del objeto mientras se amplía. Como alternativa, haga clic en el botón Alternar **[!UICONTROL órbita/giro]** para cambiar al modo **[!UICONTROL de desplazamiento]** y, a continuación, arrastre un dedo mientras mantiene presionado el botón (izquierda) para recorrer la cámara. Vuelva a hacer clic en el botón Alternar **[!UICONTROL giro/]** órbita para volver al modo **[!UICONTROL Orbit]** .

1. Haga clic en **[!UICONTROL Restablecer visor]** para restablecer la cámara. Esta acción lleva al objeto a una vista completa y, si está activada, reanuda el giro automático.

1. Haga clic en Pantalla **[!UICONTROL completa]** para acceder al modo de pantalla completa. Utilice la tecla **Escape** del teclado o haga clic en Pantalla **** completa de nuevo para restaurar el visor 3D al modo incrustado en la página.

### Dispositivos de ratón y trackball {#mouse-and-trackball-devices}

Para trabajar con componentes 3D con dispositivos mouse y trackball:

1. Arrastre mientras mantiene pulsado el botón izquierdo del ratón para mover (&quot;órbita&quot;) el punto de vista (&quot;cámara&quot;) alrededor del objeto. Puede realizar una vista del objeto desde cualquier dirección.

1. Utilice la rueda de desplazamiento para acercar o alejar la cámara del objeto. Esto es similar a acercar o alejar y permite inspeccionar los detalles del objeto. También puede hacer clic y mantener pulsados los botones **[!UICONTROL Acercar]** o **[!UICONTROL Alejar]** para acercar o alejar la cámara del objeto.

1. Arrastre mientras mantiene presionada la tecla **ALT/opción** y el botón izquierdo del ratón para recorrer la cámara. Esto mueve la cámara lateralmente para permitir observar diferentes partes del objeto mientras se amplía. Como alternativa, haga clic en el botón Alternar **[!UICONTROL órbita/recorrido]** para cambiar al modo de **[!UICONTROL desplazamiento]** y, a continuación, arrastre mientras mantiene pulsado el botón izquierdo del ratón para recorrer la cámara. Vuelva a hacer clic en el **[!UICONTROL alternador]** Orbit/Pan para volver al modo **[!UICONTROL Orbit]** .
1. Haga clic en **[!UICONTROL Restablecer visor]** para restablecer la cámara. Esta acción lleva al objeto a una vista completa y, si está activada, reanuda el giro automático.
1. Haga clic en Pantalla **[!UICONTROL completa]** para acceder al modo de pantalla completa. Utilice la tecla **[!UICONTROL Escape]** del teclado o haga clic en Pantalla **** completa de nuevo para restaurar el visor 3D al modo incrustado en la página.

