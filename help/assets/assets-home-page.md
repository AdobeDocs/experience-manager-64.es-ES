---
title: Experiencia de Página de inicio de AEM Assets
description: Personalice la Página de inicio de AEM Assets para disfrutar de una amplia experiencia en la pantalla de bienvenida, incluida una instantánea de las actividades recientes sobre los recursos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 1%

---


# Experiencia de Página de inicio de AEM Assets {#aem-assets-home-page-experience}

Personalice la Página de inicio de AEM Assets para disfrutar de una amplia experiencia en la pantalla de bienvenida, incluida una instantánea de las actividades recientes sobre los recursos.

La Página de inicio Recursos Adobe Experience Manager (AEM) proporciona una experiencia de pantalla de bienvenida completa y personalizada, que incluye una instantánea de las actividades recientes, como los recursos que se han visualizado o cargado recientemente.

La Página de inicio Recursos está deshabilitada de forma predeterminada. Para habilitarlo, realice los siguientes pasos:

1. Para acceder a AEM Administrador de configuración, haga clic en **[!UICONTROL Herramientas > Operación > Consola]** web.
1. Abra el servicio **Day CQ DAM Evento Recorder** .
1. Seleccione **[!UICONTROL Activar este servicio]** para activar la grabación de actividades.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. En la lista **Tipos de evento** , seleccione los eventos que desea registrar y guarde los cambios.

   >[!CAUTION]
   >
   >Al habilitar las opciones de vista de recursos, de proyectos vistos y de colecciones, se aumenta considerablemente el número de eventos registrados.

1. Abra el servicio Marca **[!UICONTROL de característica de Página de inicio de recursos]** DAM desde Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Seleccione la opción **[!UICONTROL isEnabled.name]** para activar la función de Página de inicio de recursos. Guarde los cambios.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Abra el cuadro de diálogo Preferencias **[!UICONTROL de]** usuario y seleccione **[!UICONTROL Activar Página de inicio]** de recursos. Guarde los cambios.

   ![user_Preferences](assets/user_preferences.png)

Después de activar la Página de inicio Recursos, navegue a la interfaz de usuario de Recursos desde la página Navegación.

![home_page](assets/home_page.png)

Toque o haga clic en el **[!UICONTROL vínculo]** Haga clic aquí para configurar su experiencia y agregar su nombre de usuario, imagen de fondo e imagen de perfil.

La Página de inicio Recursos incluye las siguientes secciones:

* Sección de bienvenida
* Sección de utilidades

**Sección de bienvenida**

Si su perfil existe, la sección de bienvenida muestra un mensaje de bienvenida dirigido a usted. Además, muestra la imagen del perfil y una imagen de bienvenida (si ya está configurada).

Si el perfil está incompleto, la sección de bienvenida muestra un mensaje de bienvenida genérico y un marcador de posición para la imagen del perfil.

**Sección de utilidades**

Esta sección aparece debajo de la sección de bienvenida y muestra los widgets predeterminados en las siguientes secciones:

* Actividad
* Reciente
* Descubrir

**Actividad**: En esta sección, la utilidad **Mi Actividad** muestra las actividades recientes realizadas por el usuario que ha iniciado sesión con los recursos (incluidos los recursos sin representaciones), como cargas de recursos, descargas, creación de recursos, ediciones, comentarios, anotaciones y compartidos.

**Reciente**: La utilidad Vista **** recientemente de esta sección muestra las entidades a las que ha accedido recientemente el usuario que ha iniciado sesión, incluidas las carpetas, las colecciones y los proyectos.

**Discover**: La **nueva** utilidad de esta sección muestra los recursos y las representaciones cargados recientemente en la instancia de AEM Assets.

Para habilitar la depuración de datos de actividad de usuario, habilite el servicio **de depuración de Eventos** DAM desde Configuration Manager. Después de habilitar este servicio, el sistema elimina las actividades del usuario que ha iniciado sesión y que exceden un número especificado.

La pantalla de bienvenida proporciona ayuda para la navegación sencilla, por ejemplo, iconos en la barra de herramientas para acceder a carpetas, colecciones y catálogos.

>[!NOTE]
>
>Al habilitar los servicios Grabador de Eventos DAM y Depuración de Eventos DAM de CQ DAM, aumentan las operaciones de escritura en JCR e indexación de búsqueda, lo que aumenta considerablemente la carga en el servidor de AEM. La carga adicional en el servidor AEM puede afectar a su rendimiento.

>[!CAUTION]
>
>La captura, el filtrado y la depuración de actividades de usuario necesarias para la Página de inicio de recursos imponen una sobrecarga en el rendimiento. Por lo tanto, los administradores deben configurar la Página de inicio de forma eficaz para los usuarios de destinatario.
>
>Adobe recomienda que los administradores y usuarios que realizan operaciones masivas eviten utilizar la función de Página de inicio de recursos para evitar un aumento de las actividades de los usuarios. Además, los administradores pueden excluir actividades de grabación para usuarios específicos configurando el grabador **de Evento CQ DAM** de Day desde Configuration Manager.
>
>Si utiliza la función, Adobe recomienda programar la frecuencia de purga en función de la carga del servidor.
