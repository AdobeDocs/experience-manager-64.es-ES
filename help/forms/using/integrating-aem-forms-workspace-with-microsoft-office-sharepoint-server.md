---
title: Integración del espacio de trabajo de formularios AEM con Microsoft Office SharePoint Server
seo-title: Integración del espacio de trabajo de formularios AEM con Microsoft Office SharePoint Server
description: 'Puede integrar AEM espacio de trabajo de formularios con Microsoft Office SharePoint Server. '
seo-description: 'Puede integrar AEM espacio de trabajo de formularios con Microsoft Office SharePoint Server. '
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---


# Integración del espacio de trabajo de formularios AEM con Microsoft Office SharePoint Server {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**- Requisitos**

**Conocimientos** previos Para poder agregar AEM Forms Workspace a SharePoint Server, debe tener acceso a SharePoint Server con los privilegios correspondientes y conocer la dirección URL para acceder a Workspace. Los pasos a continuación suponen que usted conoce bien SharePoint Server. Para obtener más información sobre los elementos Web en SharePoint Server, consulte Elementos Web en Windows SharePoint Services.

**Nivel** de usuario Comienzo

Puede utilizar AEM Forms Workspace como elemento Web en Microsoft Office SharePoint Server( Por ejemplo, Microsoft Office SharePoint Server 2007). Los usuarios pueden acceder a AEM Forms Workspace conectándose a su servidor de SharePoint mediante un navegador web para proporcionar una experiencia unificada. En este artículo, aprenderá los pasos básicos para mostrar AEM Forms Workspace como elemento Web en Microsoft Office SharePoint Server. Puede realizar los pasos descritos en este artículo para proporcionar una experiencia unificada de modo que los usuarios que se conecten a su servidor de SharePoint puedan acceder a AEM Forms Workspace desde el mismo puerto.

>[!NOTE]
>
>Los pasos enumerados en este artículo son específicos de Microsoft SharePoint Server 2007. También puede configurar HTML Workspace con otras versiones compatibles de Microsoft SharePoint.

## Integración de AEM Forms Workspace con Microsoft Office SharePoint Server 2007 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

Siga estos pasos para integrar AEM Forms Workspace en un elemento Web:

1. En un navegador web, navegue al sitio de SharePoint como, por ejemplo, https://*[myMOSSserver]:*44299/default.aspx donde *[myMOSSserver]* es el nombre o la dirección IP del servidor de SharePoint.

   >[!NOTE]
   >
   >44299 es el número de puerto predeterminado para el servidor de SharePoint. El número de puerto depende de la instalación de SharePoint Server.

1. En la parte superior derecha de la página web, haga clic en Acciones **** del sitio y seleccione **Editar página**.
1. Haga clic en el botón **Añadir un elemento** Web.
1. En el cuadro de diálogo Añadir elementos Web - página Web, en Miscelánea, seleccione Elemento **Web Visor de** páginas y, a continuación, haga clic en **Añadir**.
1. En el cuadro Elemento Web del visor de páginas, haga clic en **editar** y seleccione **Modificar elemento** Web compartido.

   >[!NOTE]
   >
   >El cuadro Elemento Web Visor de páginas aparece debajo del botón **Añadir un elemento** Web en el que hizo clic en el paso 3, como se muestra en la siguiente ilustración (Figura 1):

   ![Cuadro de elemento Web del visor de páginas en el servidor de Microsoft Office SharePoint.](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **Figura:** *Cuadro Elemento Web del visor de páginas en el servidor de Microsoft Office SharePoint.*

1. En la página Visor de páginas, realice las siguientes tareas:

   1. En el cuadro Vínculo, escriba la dirección URL de AEM Forms Workspace, como https://*[AEM_forms_Server]:*8080/lc/ws, donde *[AEM_forms_Server]* representa la dirección IP o el nombre de AEM servidor de formularios.
   1. Haga clic en **Aspecto** y modifique la altura, la anchura y el título para que pueda ver toda la interfaz de usuario de Workspace. Por ejemplo, puede establecer la altura y la anchura en 6 pulgadas y 11 pulgadas, respectivamente.
   1. Haga clic en **Test Link**. Aparece una nueva ventana del navegador web con Workspace.
   1. (Opcional) Haga clic en **Diseño** y modifique el diseño de Espacio de trabajo en el elemento Web.
   1. (Opcional) Haga clic en **Avanzadas** y modifique otros ajustes, como la descripción y si Workspace puede minimizarse o cerrarse en el elemento Web.

      Haga clic en **Aplicar**.

1. Haga clic en **Salir del modo** de edición y compruebe que puede acceder a Workspace.

Después de completar los pasos anteriores, el sitio de SharePoint tiene un aspecto similar al de la siguiente ilustración (Figura 2):

![AEM Forms Workspace integrado con Microsoft Office SharePoint Server](assets/aem-forms-workspace.jpg)

**Figura:** *AEM Forms Workspace integrado con Microsoft Office SharePoint Server*

