---
title: Experiencia de la página principal de AEM Assets
description: Personalice la página de inicio de AEM Assets para disfrutar de una experiencia de pantalla de bienvenida completa, que incluye una instantánea de las actividades recientes relacionadas con los recursos.
contentOwner: AG
feature: Herramientas para desarrolladores,Administración de recursos
role: Administrador, profesional empresarial
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 1%

---


# Experiencia de la página principal de AEM Assets {#aem-assets-home-page-experience}

Personalice la página de inicio de AEM Assets para disfrutar de una experiencia de pantalla de bienvenida completa, que incluye una instantánea de las actividades recientes relacionadas con los recursos.

La página de inicio de Recursos Adobe Experience Manager (AEM) proporciona una experiencia de pantalla de bienvenida enriquecida y personalizada, que incluye una instantánea de las actividades recientes, como los recursos que se han visualizado o cargado recientemente.

La página de inicio de Assets está desactivada de forma predeterminada. Para habilitarlo, realice los pasos siguientes:

1. Para acceder AEM Administrador de configuración, haga clic en **[!UICONTROL Herramientas > Operación > Consola web]**.
1. Abra el servicio **Day CQ DAM Event Recorder**.
1. Seleccione **[!UICONTROL Enable this service]** para habilitar el registro de actividades.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. En la lista **Tipos de eventos**, seleccione los eventos que desea registrar y guarde los cambios.

   >[!CAUTION]
   >
   >Al habilitar las opciones Recurso visto, Proyectos vistos y Colecciones vistas , aumenta significativamente la cantidad de eventos registrados.

1. Abra el servicio **[!UICONTROL DAM Asset Home Page Feature Flag]** desde Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Seleccione la opción **[!UICONTROL isEnabled.name]** para habilitar la función de página principal de los recursos. Guarde los cambios.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Abra el cuadro de diálogo **[!UICONTROL Preferencias de usuario]** y seleccione **[!UICONTROL Habilitar página principal de recursos]**. Guarde los cambios.

   ![user_Preferences](assets/user_preferences.png)

Después de habilitar la página principal de los recursos, vaya a la interfaz de usuario de Assets desde la página de navegación.

![home_page](assets/home_page.png)

Toque o haga clic en **[!UICONTROL Haga clic aquí para configurar el vínculo de experiencia]** y agregar su nombre de usuario, imagen de fondo e imagen de perfil.

La página de inicio de Recursos incluye las secciones siguientes:

* Sección de bienvenida
* Sección Widget

**Sección de bienvenida**

Si su perfil existe, la sección de bienvenida muestra un mensaje de bienvenida dirigido a usted. Además, muestra la imagen de perfil y una imagen de bienvenida (si ya está configurada).

Si el perfil está incompleto, la sección de bienvenida muestra un mensaje de bienvenida genérico y un marcador de posición para la imagen del perfil.

**Sección Widget**

Esta sección aparece debajo de la sección de bienvenida y muestra las utilidades integradas en las siguientes secciones:

* Actividad
* Reciente
* Descubrir

**Actividad**: En esta sección, el widget  **Mi** actividad muestra las actividades recientes realizadas por el usuario que ha iniciado sesión con recursos (incluidos recursos sin representaciones), por ejemplo, cargas de recursos, descargas, creación de recursos, ediciones, comentarios, anotaciones y compartidos.

**Reciente**: El widget  **Visualizar** recientemente en esta sección muestra las entidades a las que ha accedido recientemente el usuario que ha iniciado sesión, incluidas las carpetas, las colecciones y los proyectos.

**Discover**: La  **** utilidad Nueva de esta sección muestra los recursos y las representaciones cargados recientemente en la instancia de AEM Assets.

Para permitir la depuración de los datos de actividad del usuario, habilite el **servicio de depuración de eventos DAM** desde Configuration Manager. Después de habilitar este servicio, el sistema eliminará las actividades del usuario que ha iniciado sesión y que superen un número especificado.

La pantalla de bienvenida proporciona ayuda para la navegación sencilla, por ejemplo, iconos en la barra de herramientas para acceder a carpetas, colecciones y catálogos.

>[!NOTE]
>
>Al habilitar los servicios Day CQ DAM Event Recorder y DAM Event Purge , se aumentan las operaciones de escritura en JCR y la indexación de búsquedas, lo que aumenta significativamente la carga en el servidor AEM. La carga adicional en el servidor AEM puede afectar a su rendimiento.

>[!CAUTION]
>
>La captura, el filtrado y la depuración de las actividades de usuario necesarias para la página principal de los recursos imponen una sobrecarga en el rendimiento. Por lo tanto, los administradores deben configurar la página principal de forma eficaz para los usuarios objetivo.
>
>Adobe recomienda que los administradores y usuarios que realizan operaciones masivas eviten utilizar la función Página principal de los recursos para evitar un aumento en las actividades de los usuarios. Además, los administradores pueden excluir las actividades de grabación para usuarios específicos configurando **Day CQ DAM Event Recorder** desde Configuration Manager.
>
>Si utiliza la función , Adobe recomienda programar la frecuencia de depuración en función de la carga del servidor.
