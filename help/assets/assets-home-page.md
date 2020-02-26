---
title: Experiencia de la página principal de AEM Assets
description: Personalice la página de inicio de Recursos AEM para disfrutar de una amplia experiencia en la pantalla de bienvenida, incluida una instantánea de las actividades recientes relacionadas con los recursos.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Experiencia de la página principal de AEM Assets {#aem-assets-home-page-experience}

Personalice la página de inicio de Recursos AEM para disfrutar de una amplia experiencia en la pantalla de bienvenida, incluida una instantánea de las actividades recientes relacionadas con los recursos.

La página de inicio de Recursos Adobe Experience Manager (AEM) proporciona una experiencia de pantalla de bienvenida completa y personalizada, que incluye una instantánea de las actividades recientes, como los recursos que se han visualizado o cargado recientemente.

La página principal de recursos está deshabilitada de forma predeterminada. Para habilitarlo, realice los siguientes pasos:

1. Para acceder a AEM Configuration Manager, haga clic en **[!UICONTROL Herramientas > Operación > Consola]** web.
1. Abra el servicio **Day CQ DAM Event Recorder** .
1. Seleccione **[!UICONTROL Activar este servicio]** para activar la grabación de actividades.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. En la lista Tipos **de** eventos, seleccione los eventos que desea registrar y guarde los cambios.

   >[!CAUTION]
   >
   >Al habilitar las opciones de vista de recursos, de proyectos vistos y de colecciones, se aumenta considerablemente el número de eventos registrados.

1. Abra el servicio Indicador **[!UICONTROL de característica de la página principal de recursos]** DAM desde Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Seleccione la opción **[!UICONTROL isEnabled.name]** para habilitar la función de página principal de recursos. Guarde los cambios.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Abra el cuadro de diálogo Preferencias **[!UICONTROL de]** usuario y seleccione **[!UICONTROL Activar página]** principal de recursos. Guarde los cambios.

   ![user_Preferences](assets/user_preferences.png)

Después de activar la página de inicio de Recursos, navegue a la interfaz de usuario de Recursos desde la página de navegación.

![home_page](assets/home_page.png)

Toque o haga clic en el **[!UICONTROL vínculo]** Haga clic aquí para configurar su experiencia y agregar su nombre de usuario, imagen de fondo e imagen de perfil.

La página principal de recursos incluye las secciones siguientes:

* Sección de bienvenida
* Sección de utilidades

**Sección de bienvenida**

Si su perfil existe, la sección de bienvenida muestra un mensaje de bienvenida dirigido a usted. Además, muestra la imagen de perfil y una imagen de bienvenida (si ya está configurada).

Si el perfil está incompleto, la sección de bienvenida muestra un mensaje de bienvenida genérico y un marcador de posición para la imagen del perfil.

**Sección de utilidades**

Esta sección aparece debajo de la sección de bienvenida y muestra los widgets predeterminados en las siguientes secciones:

* Actividad
* Reciente
* Descubrir

**Actividad**: En esta sección, la utilidad **Mi actividad** muestra las actividades recientes realizadas por el usuario que ha iniciado sesión con recursos (incluidos recursos sin representaciones), como cargas de recursos, descargas, creación de recursos, ediciones, comentarios, anotaciones y compartidos.

**Reciente**: La utilidad Vista **** recientemente de esta sección muestra las entidades a las que ha accedido recientemente el usuario que ha iniciado sesión, incluidas las carpetas, las colecciones y los proyectos.

**Discover**: La **nueva** utilidad de esta sección muestra los recursos y las representaciones cargados recientemente en la instancia de Recursos AEM.

Para habilitar la depuración de datos de actividad de usuario, habilite el servicio **de depuración de eventos** DAM desde Configuration Manager. Después de habilitar este servicio, el sistema elimina las actividades del usuario que ha iniciado sesión y que exceden un número especificado.

La pantalla de bienvenida proporciona ayuda para la navegación sencilla, por ejemplo, iconos en la barra de herramientas para acceder a carpetas, colecciones y catálogos.

>[!NOTE]
>
>Al habilitar los servicios Grabador de eventos DAM y Depuración de eventos DAM de CQ Day, aumentan las operaciones de escritura en JCR e indexación de búsqueda, lo que aumenta considerablemente la carga en el servidor AEM. La carga adicional en el servidor AEM puede afectar a su rendimiento.

>[!CAUTION]
>
>Capturar, filtrar y purgar las actividades de usuario necesarias para la página principal de recursos impone una sobrecarga en el rendimiento. Por lo tanto, los administradores deben configurar la página principal de forma eficaz para los usuarios objetivo.
>
>Adobe recomienda que los administradores y usuarios que realizan operaciones masivas eviten utilizar la función Página principal de recursos para evitar un aumento en las actividades de los usuarios. Además, los administradores pueden excluir las actividades de grabación para usuarios específicos configurando el grabador **de eventos de CQ DAM de** día desde Configuration Manager.
>
>Si utiliza la función, Adobe recomienda programar la frecuencia de purga en función de la carga del servidor.
