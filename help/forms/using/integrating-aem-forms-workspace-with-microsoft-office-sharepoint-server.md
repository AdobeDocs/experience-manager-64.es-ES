---
title: Integrar AEM Forms Workspace con el servidor de Microsoft Office SharePoint
seo-title: Integrating AEM forms workspace with Microsoft Office SharePoint Server
description: Puede integrar AEM Forms Workspace con Microsoft Office SharePoint Server.
seo-description: You can integrate AEM forms workspace with Microsoft Office SharePoint Server.
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
exl-id: 43149456-8ff8-4ce1-9c51-1d950f60ff5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 81%

---

# Integrar AEM Forms Workspace con el servidor de Microsoft Office SharePoint {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

**- Requisitos**

**Conocimientos previos**
Para poder agregar AEM Forms Workspace al servidor de SharePoint, debe tener acceso al servidor de SharePoint con los privilegios correspondientes y conocer la URL para acceder a Workspace. Los siguientes pasos se basan en el supuesto de que está familiarizado con SharePoint Server. Para obtener más información acerca de los elementos Web del servidor de SharePoint, vea Elementos Web en los servicios de Windows SharePoint.

**Nivel de usuario**
Inicio

Puede utilizar AEM Forms Workspace como elemento web en Microsoft Office SharePoint Server (por ejemplo, Microsoft Office SharePoint Server 2007). Los usuarios pueden acceder a AEM Forms Workspace conectándose al servidor de SharePoint a través de un navegador web para proporcionar una experiencia unificada. En este artículo, aprenderá los pasos básicos para mostrar AEM Forms Workspace como un elemento web en Microsoft Office SharePoint Server. Puede llevar a cabo los pasos descritos en este artículo para proporcionar una experiencia unificada, de modo que los usuarios que se conecten al servidor de SharePoint puedan acceder a AEM Forms Workspace desde el mismo puerto.

>[!NOTE]
>
>Los pasos que aparecen en este artículo son específicos de Microsoft Office SharePoint Server 2007. También puede configurar HTML Workspace con otras versiones compatibles de Microsoft SharePoint.

## Integración de AEM Forms Workspace con Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Siga los siguientes pasos para integrar AEM Forms Workspace en un elemento web:

1. En un explorador web, vaya al sitio de SharePoint, como https://*[myMOSSserver]:*44299/default.aspx donde *[myMOSSserver]* es el nombre o la dirección IP del servidor de Sharepoint.

   >[!NOTE]
   >
   >44299 es el número de puerto predeterminado del servidor de SharePoint. El número de puerto depende de la instalación de SharePoint Server.

1. En la parte superior derecha de la página web, haga clic en **Acciones del sitio** y seleccione **Editar página**.
1. Haga clic en el botón **Agregar elemento web**.
1. En el cuadro de diálogo Agregar elementos web - Página Web, en Miscelánea, seleccione **Elemento web del visor de páginas** y haga clic en **Agregar**.
1. En el cuadro Elemento web del visor de páginas, haga clic en **Editar** y seleccione **Modificar elemento web compartido**.

   >[!NOTE]
   >
   >El cuadro Elemento web del visor de páginas aparece debajo del botón **Agregar elemento web** en el que ha hecho clic en el paso 3, como se muestra en la siguiente ilustración (Figura 1):

   ![Cuadro Elemento web del visor de páginas de Microsoft Office SharePoint Server.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **Figura:** *Cuadro Elemento Web Visor de páginas en el servidor SharePoint de Microsoft Office.*

1. En la página Visor de páginas, realice las siguientes tareas:

   1. En el cuadro Vínculo, escriba la dirección URL de AEM Forms Workspace, como https://*[AEM_forms_Server]:*8080/lc/ws donde *[AEM_forms_Server]* representa la IP o el nombre de AEM servidor de formularios.
   1. Haga clic en **Apariencia** y modifique la altura, la anchura y el título para que pueda ver la interfaz de usuario de Workspace completa. Por ejemplo, puede establecer la altura y la anchura en 6 y 11 pulgadas, respectivamente.
   1. Haga clic en **Probar vínculo**. Aparece una nueva ventana del explorador web que muestra Workspace.
   1. (Opcional) Haga clic en **Diseño** y modifique el diseño de Workspace en Elemento web.
   1. (Opcional) Haga clic en **Avanzadas** y modifique otras opciones de configuración, como la descripción y si Workspace se puede minimizar o cerrar en el elemento web.

      Haga clic en **Aplicar**.

1. Haga clic en **Salir del modo de edición** y compruebe que puede acceder a Workspace.

Después de completar los pasos anteriores, el sitio de SharePoint tiene un aspecto similar al de la siguiente ilustración (Figura 2):

![AEM Forms Workspace integrado con Microsoft Office SharePoint Server](assets/aem-forms-workspace.jpg)

**Figura:** *AEM Forms Workspace integrado con Microsoft Office SharePoint Server*
