---
title: Configuración del entorno de cuenta
seo-title: Configuring your account environment
description: AEM le permite configurar su cuenta y ciertos aspectos del entorno de creación
seo-description: AEM provides you with the capability to configure your account and certain aspects of the author environment
uuid: 01e76771-9ac8-4919-9e50-0a63826177d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6afbc889-c613-40e6-8a25-1570dff32d60
exl-id: f620e85e-8c77-41a3-a238-9b93c819909d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 54%

---

# Configuración del entorno de cuenta{#configuring-your-account-environment}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM le permite configurar su cuenta y ciertos aspectos del entorno de creación.

Al usar la variable [Usuario](/help/sites-authoring/user-properties.md#user-settings) en la [header](/help/sites-authoring/basic-handling.md#the-header) y el [Mis preferencias](#my-preferences) , puede modificar las opciones de usuario.

## Configuración de usuario {#user-settings}

La variable **Usuario** el cuadro de diálogo configuración le permite acceder a:

* Suplantar como

   * Con la variable [Suplantar como](/help/sites-administering/security.md#impersonating-another-user) funcionalidad que un usuario puede trabajar en nombre de otro usuario.

* Perfil

   * Ofrece un práctico vínculo a su [configuración de usuario](/help/sites-administering/security.md))

* [Mis preferencias](/help/sites-authoring/user-properties.md#my-preferences)

   * Especifique las distintas preferencias exclusivas al usuario 

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

## Mis preferencias {#my-preferences}

Puede acceder al cuadro de diálogo **Preferencias** a través de la opción [Usuario](/help/sites-authoring/user-properties.md#user-settings) en el encabezado.

Cada usuario puede establecer determinadas propiedades para sí mismo. 

![screen_shot_2018-03-20at102118](assets/screen_shot_2018-03-20at102118.png)

* **Idioma**

   Define el idioma que se utiliza para la IU del entorno de creación. Seleccione el idioma requerido en la lista de idiomas disponibles.

   Esta configuración también se utiliza para la IU clásica.

* **Gestión de ventanas**

   Esto define el comportamiento o la apertura de ventanas. Seleccione:

   * **Varias ventanas** (Predeterminado)

      * Las páginas se abrirán en una nueva ventana.
   * **Ventana única**

      * Las páginas se abrirán en la ventana actual.


* **Mostrar las acciones del escritorio para Assets**

   Esta opción requiere AEM aplicación de escritorio para su uso.

* **Color de anotación**

   Define el color predeterminado que se usa al crear anotaciones.

   * Haga clic en el bloque de color para abrir el selector de muestras y seleccionar un color.
   * Como alternativa, introduzca el código hexadecimal del color deseado en el campo. 

* **Presentación de fecha relativa**

   Para mejorar la legibilidad, AEM procesará las fechas dentro de los últimos siete días como fechas relativas (por ejemplo, hace tres días) y las fechas antiguas como fechas exactas (por ejemplo, el 20 de marzo de 2017).

   Esta opción define el modo en que se muestran las fechas del sistema. Las opciones disponibles son las siguientes:

   * **Mostrar siempre la fecha exacta**: se muestra siempre la fecha exacta (nunca una fecha relativa).
   * **1 día**: se muestra la fecha relativa para las fechas dentro de un día; de lo contrario, se muestra una fecha exacta. 
   * **7 días (valor predeterminado)**: se muestra la fecha relativa para las fechas dentro de siete días; de lo contrario, se muestra una fecha exacta. 
   * **1 mes**: se muestra la fecha relativa para las fechas dentro de un mes; de lo contrario, se muestra una fecha exacta. 
   * **1 año**: se muestra la fecha relativa para las fechas dentro de un año; de lo contrario se muestra una fecha exacta. 
   * **Mostrar siempre la fecha relativa**: las fechas exactas nunca se muestran, y solo se muestran fechas relativas.

* **Habilitar métodos abreviados**

   AEM admite varios métodos abreviados del teclado para mejorar la eficiencia de la creación de contenido.

   * [Métodos abreviados del teclado para editar páginas](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [Métodos abreviados del teclado para las consolas](/help/sites-authoring/keyboard-shortcuts.md)

   Esta opción habilita los métodos abreviados del teclado. De forma predeterminada, están habilitadas, pero pueden deshabilitarse, por ejemplo, si un usuario tiene determinados requisitos de accesibilidad.

* **Usar experiencia de autoría clásica**

   Esta opción habilita [IU clásica](/help/sites-classic-ui-authoring/home.md)Creación de páginas basada en . De forma predeterminada, se utiliza la IU estándar.

* **Activar la página principal de los recursos**

   Esta opción solo está disponible si el administrador del sistema ha habilitado la experiencia de la página principal de los recursos para toda la organización.
