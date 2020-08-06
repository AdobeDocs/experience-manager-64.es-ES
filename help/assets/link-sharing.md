---
title: Uso compartido de vínculos de recursos
description: Cómo compartir recursos, carpetas y colecciones dentro de AEM Assets como una dirección URL para terceros externos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 13%

---


# Uso compartido de vínculos de activos {#asset-link-sharing}

Recursos Adobe Experience Manager (AEM) permite compartir recursos, carpetas y colecciones como URL con miembros de la organización y entidades externas, incluidos socios y proveedores. El uso compartido de recursos a través de un vínculo es una forma práctica de poner los recursos a disposición de terceros externos sin que estos tengan que iniciar sesión en AEM Assets en primer lugar.

>[!NOTE]
>
>Se requiere el permiso Editar ACL en las carpetas y recursos que se desea compartir como vínculo.

## Compartir recursos {#share-assets}

Para generar la URL de los recursos que desea compartir con los usuarios, utilice el cuadro de diálogo Uso compartido de vínculos. Los usuarios con privilegios de administrador o con permisos de lectura en la `/var/dam/share` ubicación pueden realizar la vista de los vínculos compartidos con ellos.

>[!NOTE]
>
>Antes de compartir un vínculo con los usuarios, asegúrese de que [!UICONTROL Day CQ Mail Service] está configurado. Se produce un error si intenta compartir un vínculo sin [configurar primero el servicio](link-sharing.md#configure-day-cq-mail-service)de correo de Day CQ.

1. En la interfaz de usuario de Recursos, seleccione el recurso que desea compartir como vínculo.
1. En la barra de herramientas, toque o haga clic en el icono **[!UICONTROL Compartir]** recursos del vínculo ![](assets/assets_share.png).

   Se crea automáticamente un vínculo de recurso en el campo **[!UICONTROL Compartir vínculo]** . Copie este vínculo y compártalo con los usuarios. El tiempo de caducidad predeterminado para el vínculo es un día.

   ![Cuadro de diálogo con el recurso compartido de vínculos](assets/chlimage_1-542.png)

   Como alternativa, realice los pasos 3 a 7 de este procedimiento para agregar destinatarios de correo electrónico, configurar la caducidad del vínculo y enviarlo desde el cuadro de diálogo.

   >[!NOTE]
   >
   >Para compartir vínculos de AEM Author con entidades externas, exponga solo las siguientes URL utilizadas para compartir vínculos en solicitudes de GET. Bloquee otras direcciones URL para asegurarse de que la implementación AEM es segura.
   >
   >* &lt;AEM Server>/linkshare.html
   * &lt;AEM Server>/linksharepreview.html
   * &lt;AEM Server>/linkexpired.html


   >[!NOTE]
   Si un recurso compartido se mueve a una ubicación diferente, su vínculo deja de funcionar. Vuelva a crear el vínculo y vuelva a compartirlo con los usuarios.

1. Desde la consola web, abra la configuración **[!UICONTROL Day CQ Link Externalizer]** y modifique las siguientes propiedades en el campo **[!UICONTROL Dominios]** con los valores mencionados en relación con cada uno de ellos:

   * local
   * author
   * instancias de publicación

   Para las propiedades `local` y `author` , proporcione la URL para la instancia local y de autor respectivamente. Tanto `local` como `author` las propiedades tienen el mismo valor si se ejecuta una única instancia de autor AEM. Por `publish`, proporcione la URL para la instancia de publicación.

1. En el apartado de la dirección de correo electrónico del cuadro de diálogo **[!UICONTROL Uso compartido de vínculos]**, escriba el ID de correo electrónico del usuario con el que desea compartir el vínculo. También puede compartir el vínculo con varios usuarios.

   Si el usuario es miembro de su organización, seleccione el ID de correo electrónico del usuario en los ID de correo electrónico sugeridos que aparecen en la lista debajo del área de escritura. Para un usuario externo, escriba el ID de correo electrónico completo y selecciónelo en la lista.

   Para habilitar el envío de mensajes de correo electrónico a los usuarios, configure los detalles del servidor SMTP en [Día del servicio](link-sharing.md#configure-day-cq-mail-service)de correo de CQ.

   ![Uso compartido de vínculos a recursos directamente desde el cuadro de diálogo Uso compartido de vínculos](assets/chlimage_1-543.png)

   Uso compartido de vínculos a recursos directamente desde el cuadro de diálogo Uso compartido de vínculos

   >[!NOTE]
   Si introduce un ID de correo electrónico de un usuario que no es miembro de su organización, las palabras &quot;Usuario externo&quot; llevan el prefijo &quot;ID de correo electrónico del usuario.

1. En el **[!UICONTROL cuadro Asunto]** , introduzca un asunto para el recurso que desea compartir.
1. En el cuadro **[!UICONTROL Mensaje]** , escriba un mensaje opcional.
1. En el campo **[!UICONTROL Caducidad]** , especifique una fecha y hora de caducidad para el vínculo mediante el selector de fechas. De forma predeterminada, la fecha de caducidad se establece para una semana a partir de la fecha en que comparta el vínculo.

   ![Establecer fecha y hora de caducidad para el vínculo compartido](assets/chlimage_1-544.png)

1. Para permitir que los usuarios descarguen la imagen original junto con las representaciones, seleccione **[!UICONTROL Permitir la descarga del archivo]** original.

   >[!NOTE]
   De forma predeterminada, los usuarios solo pueden descargar las representaciones del recurso que se comparten como vínculo.

1. Haga clic en **[!UICONTROL Compartir]**. Un mensaje confirma que el vínculo se comparte con los usuarios a través de un correo electrónico.
1. Para vista del recurso compartido, toque o haga clic en el vínculo del correo electrónico que se envía al usuario. El recurso compartido se muestra en la página de [!UICONTROL Adobe Marketing Cloud] .

   ![Los recursos compartidos están disponibles en Adobe Marketing Cloud](assets/chlimage_1-545.png)

   Para cambiar a la vista de lista, toque o haga clic en el icono de diseño de la barra de herramientas.

1. Para generar una vista previa del recurso, pulse o haga clic en el recurso compartido. Toque o haga clic en **[!UICONTROL Atrás]** en la barra de herramientas para cerrar la previsualización y volver a la página de [!UICONTROL Marketing Cloud] . Si ha compartido una carpeta, pulse o haga clic en **[!UICONTROL Carpeta principal]** para regresar a la carpeta principal.

   ![chlimage_1-546](assets/chlimage_1-546.png)

   >[!NOTE]
   AEM permite generar la previsualización de recursos de estos tipos MIME: JPG, PNG, GIF, BMP, INDD, PDF y PPT. Solo puede descargar los recursos de los otros tipos MIME.

1. Para descargar el recurso compartido, toque o haga clic en el icono **[!UICONTROL Seleccionar]** de la barra de herramientas, toque o haga clic en el recurso y, a continuación, toque o haga clic en **[!UICONTROL Descargar]** de la barra de herramientas.

   ![Opción de barra de herramientas para descargar el recurso compartido](assets/chlimage_1-547.png)

1. Para vista de los recursos que ha compartido como vínculos, vaya a la interfaz de usuario de Recursos y toque o haga clic en el icono de **[!UICONTROL GlobalNav]** . Elija **[!UICONTROL Navegación]** en la lista para mostrar el panel Navegación.
1. En el panel Navegación, seleccione **[!UICONTROL Vínculos compartidos]** para mostrar una lista de recursos compartidos.
1. Para dejar de compartir un recurso, selecciónelo y toque o haga clic en **[!UICONTROL Dejar de compartir]** en la barra de herramientas. Un mensaje confirma que se ha dejado de compartir el recurso. Además, la entrada del recurso se elimina de la lista.

## Configurar el servicio de correo de CQ Day {#configure-day-cq-mail-service}

1. Pulse o haga clic en el logotipo de AEM y, a continuación, vaya a **[!UICONTROL Herramientas > Operaciones > Consola web]**.
1. En la lista de servicios, localice **[!UICONTROL Day CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * Nombre de host del servidor SMTP: nombre de host del servidor de correo electrónico
   * Puerto del servidor SMTP: puerto del servidor de correo electrónico
   * Usuario SMTP: nombre de usuario del servidor de correo electrónico
   * Contraseña SMTP: contraseña del servidor de correo electrónico

   ![chlimage_1-548](assets/chlimage_1-548.png)

1. Click/tap **[!UICONTROL Save]**.

## Configurar el tamaño máximo de datos {#configure-maximum-data-size}

Al descargar recursos del vínculo compartido mediante la función Compartir vínculos, AEM comprime toda la jerarquía de recursos del repositorio y, a continuación, devuelve el recurso en un archivo ZIP. Sin embargo, a falta de límites a la cantidad de datos que se pueden comprimir en un archivo ZIP, grandes cantidades de datos están sujetas a compresión, lo que causa errores de memoria insuficiente en JVM. Para proteger el sistema de un posible ataque de denegación de servicio debido a esta situación, configure el tamaño máximo usando el parámetro Tamaño de contenido **[!UICONTROL máximo (sin comprimir)]** para el servlet proxy **[!UICONTROL Day CQ DAM Adhoc Asset Share]** en Configuration Manager. Si el tamaño sin comprimir del recurso supera el valor configurado, se rechazan las solicitudes de descarga de recursos. El valor predeterminado es 100 MB.

1. Haga clic o pulse el logotipo de AEM y, a continuación, vaya a **[!UICONTROL Herramientas > Operaciones > Consola web]**.
1. Desde la consola web, busque la configuración del servlet proxy **[!UICONTROL Day CQ DAM Adhoc Asset Share]** .
1. Abra la configuración del servlet proxy **[!UICONTROL Day CQ DAM Adhoc Asset Share]** en modo de edición y modifique el valor del parámetro **[!UICONTROL Tamaño de contenido máximo (sin comprimir)]**.

   ![chlimage_1-549](assets/chlimage_1-549.png)

1. Guarde los cambios.

## Best practices and troubleshooting {#best-practices-and-troubleshooting}

* Es posible que las carpetas de recursos o las colecciones que contengan un espacio en blanco en su nombre no se compartan.
* Si los usuarios no pueden descargar los recursos compartidos, compruebe con el administrador de AEM cuáles son los límites [de](#configure-maximum-data-size) descarga.
* Si no puede enviar correos electrónicos con vínculos a recursos compartidos o si los demás usuarios no pueden recibir su correo electrónico, consulte con el administrador de AEM si el servicio [de](#configure-day-cq-mail-service) correo electrónico está configurado o no.
* Si no puede compartir recursos con la funcionalidad de uso compartido de vínculos, asegúrese de que dispone de los permisos adecuados. Consulte [Uso compartido de recursos](#share-assets).
