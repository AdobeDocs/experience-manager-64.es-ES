---
title: "[!DNL Experience Manager Assets] Experiencia de la página principal"
description: Personalice la página principal de los recursos para disfrutar de una experiencia de pantalla de bienvenida completa, que incluye una instantánea de las actividades recientes relacionadas con los recursos.
contentOwner: AG
feature: Developer Tools,Asset Management
role: Admin,User
exl-id: f47c6da7-aa21-4f49-9c66-2a8091e19561
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# [!DNL Adobe Experience Manager Assets] Experiencia de la página principal {#aem-assets-home-page-experience}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Personalice el [!DNL Experience Manager Assets] Página de inicio para una experiencia de pantalla de bienvenida completa, que incluye una instantánea de las actividades recientes relacionadas con los recursos.

La variable [!DNL Adobe Experience Manager Assets] La página principal proporciona una experiencia de pantalla de bienvenida completa y personalizada, que incluye una instantánea de actividades recientes, como recursos que se han visualizado o cargado recientemente.

La página de inicio de Assets está desactivada de forma predeterminada. Para habilitarlo, realice los pasos siguientes:

1. Para acceder a [!DNL Experience Manager] Administrador de configuración, haga clic en **[!UICONTROL Herramientas > Operación > Consola web]**.
1. Abra el **Grabador de eventos de CQ DAM de día** servicio.
1. Seleccione el **[!UICONTROL Habilitar este servicio]** para activar el registro de actividades.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. En el **Tipos de eventos** , seleccione los eventos que desea registrar y guarde los cambios.

   >[!CAUTION]
   >
   >Al habilitar las opciones Recurso visto, Proyectos vistos y Colecciones vistas , aumenta significativamente la cantidad de eventos registrados.

1. Abra el **[!UICONTROL Indicador de características de la página principal del recurso DAM]** servicio desde Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`.
1. Seleccione el **[!UICONTROL isEnabled.name]** para activar la función Página principal de Assets. Guarde los cambios.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Abra el **[!UICONTROL Preferencias de usuario]** y seleccione **[!UICONTROL Activar la página principal de los recursos]**. Guarde los cambios.

   ![user_Preferences](assets/user_preferences.png)

Después de habilitar la página principal de los recursos, vaya a la interfaz de usuario de Assets desde la página de navegación.

![home_page](assets/home_page.png)

Toque o haga clic en el botón **[!UICONTROL Haga clic aquí para configurar el vínculo de experiencia]** para agregar su nombre de usuario, imagen de fondo e imagen de perfil.

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

**Actividad**: En esta sección, la variable **Mi actividad** widget muestra las actividades recientes realizadas por el usuario que ha iniciado sesión con recursos (incluidos los recursos sin representaciones), por ejemplo, cargas de recursos, descargas, creación de recursos, ediciones, comentarios, anotaciones y compartidos.

**Reciente**: La variable **Vistos recientemente** en esta sección se muestran las entidades a las que el usuario que ha iniciado sesión ha accedido recientemente, incluidas las carpetas, las colecciones y los proyectos.

**Discover**: La variable **Nuevo** en esta sección se muestran los recursos y las representaciones cargados recientemente en el [!DNL Assets] instancia.

Para habilitar la depuración de los datos de actividad del usuario, habilite la variable **Servicio de depuración de eventos DAM** de Configuration Manager. Después de habilitar este servicio, el sistema eliminará las actividades del usuario que ha iniciado sesión y que superen un número especificado.

La pantalla de bienvenida proporciona ayuda para la navegación sencilla, por ejemplo, iconos en la barra de herramientas para acceder a carpetas, colecciones y catálogos.

>[!NOTE]
>
>Al habilitar los servicios Day CQ DAM Event Recorder y DAM Event Purge , se aumentan las operaciones de escritura en JCR y la indexación de búsquedas, lo que aumenta significativamente la carga en la variable [!DNL Experience Manager] servidor. La carga adicional en el [!DNL Experience Manager] el servidor puede afectar a su rendimiento.

>[!CAUTION]
>
>La captura, el filtrado y la depuración de las actividades de usuario necesarias para la página principal de los recursos imponen una sobrecarga en el rendimiento. Por lo tanto, los administradores deben configurar la página principal de forma eficaz para los usuarios objetivo.
>
>Adobe recomienda que los administradores y usuarios que realizan operaciones masivas eviten utilizar la función Página principal de los recursos para evitar un aumento en las actividades de los usuarios. Además, los administradores pueden excluir las actividades de grabación para usuarios específicos configurando **Grabador de eventos de CQ DAM de día** de Configuration Manager.
>
>Si utiliza la función , Adobe recomienda programar la frecuencia de depuración en función de la carga del servidor.
