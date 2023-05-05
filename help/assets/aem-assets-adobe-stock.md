---
title: Administrar [!DNL Adobe Stock] recursos en [!DNL Adobe Experience Manager Assets].
description: Buscar, recuperar, obtener licencias y administrar [!DNL Adobe Stock] activos desde dentro [!DNL Adobe Experience Manager]. Utilice los recursos con licencia como cualquier otro recurso digital.
contentOwner: AG
feature: Search,Adobe Stock
role: User,Admin
exl-id: f360abaf-a812-46ed-a160-ff569b6bec1c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 11%

---

# Uso [!DNL Adobe Stock] recursos en [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Las organizaciones pueden integrar sus [!DNL Adobe Stock] plan empresarial con [!DNL Experience Manager Assets] para garantizar que los recursos con licencia estén disponibles en general para sus proyectos creativos y de marketing, con las potentes capacidades de administración de recursos de [!DNL Experience Manager].

[!DNL Adobe Stock] ofrece a los diseñadores y a las empresas acceso a millones de fotos, vectores, ilustraciones, vídeos, plantillas y recursos 3D de alta calidad, depurados y libres de derechos de autor para todos sus proyectos creativos. [!DNL Experience Manager] los usuarios pueden encontrar, previsualizar y obtener licencias rápidamente [!DNL Adobe Stock] recursos que se guardan en [!DNL Experience Manager], sin salir del [!DNL Experience Manager] interfaz.

## Requisitos previos {#prerequisites}

La integración requiere un [plan de enterprise Adobe Stock](https://stockenterprise.adobe.com/) y [!DNL Experience Manager] 6.4 con al menos el Service Pack 2 implementado. Para [!DNL Experience Manager] Detalles del Service Pack 6.4, consulte estos [notas de la versión](/help/release-notes/sp-release-notes.md).

## Integrar [!DNL Experience Manager] y [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

Para permitir la comunicación entre [!DNL Experience Manager] y [!DNL Adobe Stock], cree una configuración de IMS y un [!DNL Adobe Stock] configuración en [!DNL Experience Manager].

>[!NOTE]
>
>Solo [!DNL Experience Manager] administradores y [!DNL Admin Console] los administradores de una organización pueden realizar la integración ya que requiere privilegios de administrador.

### Crear una configuración de IMS {#create-an-ims-configuration}

1. En el [!DNL Experience Manager] interfaz de usuario, vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Seguridad]** > **[!UICONTROL Configuraciones de IMS de Adobe]**. Haga clic en **[!UICONTROL Crear]** y seleccione **[!UICONTROL Solución de nube]** > **[!UICONTROL Adobe Stock]**.
1. Vuelva a utilizar un certificado existente o seleccione **[!UICONTROL Crear nuevo certificado]**.
1. Haga clic en **[!UICONTROL Crear certificado]**. Una vez creada, descargue la clave pública. Haga clic en **[!UICONTROL Siguiente]**. Deje el [!UICONTROL Configuración de cuenta técnica de Adobe IMS] se abre para proporcionar los valores necesarios en breve.
1. Acceso [Consola de Adobe Developer](https://console.adobe.io). Asegúrese de que su cuenta tiene permisos de administrador para la organización para la que se requiere la integración.
1. Haga clic en **[!UICONTROL Crear nuevo proyecto]** y haga clic en **[!UICONTROL Añadir API]**. Select **[!UICONTROL Adobe Stock]** de la lista de API disponibles para usted. Select [!UICONTROL OAUTH 2.0 Web].
1. Proporcionar **[!UICONTROL URI de redirección predeterminado]** y **[!UICONTROL Patrón de URI de redirección]** valores. Haga clic en **[!UICONTROL Guardar API configurada]**. Copie el ID y el secreto generados.
1. En [!UICONTROL Configuración de cuenta técnica de Adobe IMS] , proporcione los valores en los cuadros con título **[!UICONTROL Título]**, **[!UICONTROL Servidor de autorización]**, **[!UICONTROL Clave de API]**, **[!UICONTROL Secreto del cliente]** y **[!UICONTROL Carga útil]**. Para obtener información detallada sobre estos valores, consulte [Inicio rápido de la autenticación JWT](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

<!-- TBD: Update the URL when the new URL is available. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### Crear [!DNL Adobe Stock] configuración en [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. En el [!DNL Experience Manager] interfaz de usuario, vaya a **[!UICONTROL Herramientas]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Haga clic en **[!UICONTROL Crear]** para crear una configuración y asociarla con la configuración de IMS existente. Select `PROD` como parámetro de entorno.
1. En **[!UICONTROL Ruta de recursos con licencia]** , deje una ubicación tal cual. No cambie la ubicación donde desea almacenar la variable [!DNL Adobe Stock] activos.
1. Complete la creación añadiendo todas las propiedades necesarias. Haga clic en **[!UICONTROL Guardar y cerrar]**.
1. Agregar [!DNL Experience Manager] usuarios o grupos que pueden obtener una licencia de los recursos.

>[!NOTE]
>
>Si hay varios [!DNL Adobe Stock] , seleccione la configuración que desee en el panel Preferencias de usuario (**[!UICONTROL AEM]** > **[!UICONTROL Icono de usuario]** > **[!UICONTROL Preferencias de usuario]** > **[!UICONTROL Configuración de Stock]**).

## Usar y administrar [!DNL Adobe Stock] recursos en [!DNL Experience Manager] {#usemanage}

Con esta capacidad, las organizaciones pueden permitir que sus usuarios trabajen utilizando [!DNL Adobe Stock] recursos en [!DNL Experience Manager Assets]. Desde dentro de la variable [!DNL Experience Manager] interfaz de usuario, los usuarios pueden buscar [!DNL Adobe Stock] activos y licencia de los recursos necesarios.

Una vez [!DNL Adobe Stock] el recurso tiene licencia en [!DNL Experience Manager], se puede utilizar y administrar como un recurso típico. En [!DNL Experience Manager], los usuarios pueden buscar y previsualizar los recursos; copiar y publicar los recursos; compartir los recursos en [!DNL Brand Portal]; acceder y utilizar los recursos mediante [!DNL Experience Manager] aplicación de escritorio; y así sucesivamente.

![Busque recursos de Adobe Stock y filtre los resultados del espacio de trabajo de Adobe Experience Manager](assets/adobe-stock-search-results-workspace.png)

*Figura: Buscar [!DNL Adobe Stock] recursos y filtrar los resultados de [!DNL Experience Manager] interfaz.*

**A.**[!DNL Adobe Stock] Busque recursos similares a los del ID de proporcionado. **B.** Busque recursos que coincidan con la selección de forma u orientación. **C.** Busque uno de los tipos de recurso más admitidos **D.** Abra o contraiga el panel de filtros **E.** Obtenga la licencia y guarde el recurso seleccionado en [!DNL Experience Manager]**F.**[!DNL Experience Manager] Guarde el recurso en con la marca de agua **G.**[!DNL Adobe Stock] Explore los recursos del sitio web de que sean similares al recurso **H.**[!DNL Adobe Stock] Vea los recursos seleccionados en el sitio web de . **I.** Número de recursos seleccionados de los resultados de búsqueda **J.** Cambie entre la vista de tarjeta y la vista de lista

### Buscar recursos {#find-assets}

Su [!DNL Experience Manager] usuarios, puede buscar recursos en ambos, [!DNL Experience Manager] y [!DNL Adobe Stock]. Cuando la ubicación de búsqueda no está limitada a [!DNL Adobe Stock], los resultados de la búsqueda de [!DNL Experience Manager] y [!DNL Adobe Stock] se muestran.

* Para buscar [!DNL Adobe Stock] recursos, haga clic en **[!UICONTROL Navegación]** > **[!UICONTROL Recursos]** > **[!UICONTROL Buscar en Adobe Stock]**.

* Para buscar recursos en [!DNL Adobe Stock] y [!DNL Experience Manager Assets], haga clic en buscar ![search_icon](assets/search_icon.png).

También puede empezar a escribir `Location: Adobe Stock` en la barra de búsqueda para seleccionar [!DNL Adobe Stock] activos. [!DNL Experience Manager] ofrece funciones de filtrado avanzadas en los recursos buscados, lo que permite a los usuarios centrarse rápidamente en los recursos necesarios mediante filtros, como tipos de recursos admitidos, orientación de imagen y estado con licencia.

>[!NOTE]
>
>Recursos buscados desde [!DNL Adobe Stock] solo se muestran en [!DNL Experience Manager]. [!DNL Adobe Stock] los recursos se recuperan y se almacenan en [!DNL Experience Manager] repositorio solo después de que un usuario [guarda un recurso](/help/assets/aem-assets-adobe-stock.md#saveassets) o [concede licencias y guarda un recurso](/help/assets/aem-assets-adobe-stock.md#licenseassets). Recursos que ya están almacenados en [!DNL Experience Manager] se muestran y resaltan para facilitar la referencia y el acceso. Además, el [!DNL Stock] los recursos se guardan con algunos metadatos adicionales para indicar el origen como [!DNL Stock].

![Filtros de búsqueda en el Experience Manager y recursos de Adobe Stock resaltados en los resultados de búsqueda](assets/aem-search-filters2.jpg)

*Figura: Filtros de búsqueda en [!DNL Experience Manager] y resaltado [!DNL Adobe Stock] recursos en los resultados de búsqueda.*

### Guarde y vea los recursos necesarios {#saveassets}

Seleccione un recurso en el que desee guardar [!DNL Experience Manager]. Haga clic en [!UICONTROL Guardar] en la barra de herramientas de la parte superior y proporcione el nombre y la ubicación del recurso. Los recursos sin licencia se guardan localmente con una marca de agua.

La próxima vez que busque recursos, los recursos guardados se resaltarán con un distintivo para indicar que dichos recursos están disponibles en [!DNL Experience Manager Assets].

>[!NOTE]
>
>Los recursos añadidos recientemente muestran un distintivo Nuevo en lugar de un distintivo Con licencia .

### Recursos de licencia {#licenseassets}

Los usuarios pueden obtener licencias [!DNL Adobe Stock] los recursos utilizando la cuota de sus [!DNL Adobe Stock] plan empresarial. Al conceder una licencia a un recurso, este se guarda sin marca de agua y está disponible para su búsqueda y uso en [!DNL Experience Manager Assets].

![Cuadro de diálogo para obtener una licencia y guardar los recursos de Adobe Stock en Experience Manager Assets](assets/aem-stock_licenseandsave.jpg)

*Figura: Cuadro de diálogo para obtener una licencia y guardar [!DNL Adobe Stock] recursos en [!DNL Experience Manager Assets].*

### Acceso a metadatos y propiedades de recursos {#access-metadata-and-asset-properties}

Los usuarios pueden acceder a los metadatos y previsualizarlos, incluido el [!DNL Adobe Stock] propiedades de metadatos para los recursos guardados en [!DNL Experience Manager]y agregue **[!UICONTROL Referencias de licencia]** para un recurso. Sin embargo, las actualizaciones de la referencia de licencia no se sincronizan entre [!DNL Experience Manager] y [!DNL Adobe Stock] sitio web.

Los usuarios pueden ver las propiedades de los recursos, con licencia y sin licencia.

![Ver y acceder a metadatos y referencias de licencia de recursos guardados](assets/metadata_properties.jpg)

*Figura: Vea y acceda a metadatos y referencias de licencia de recursos guardados.*

## Limitaciones conocidas {#known-limitations}

* **La advertencia de imágenes editoriales no se muestra**: Al conceder licencias para una imagen, los usuarios no pueden comprobar si una imagen es de uso editorial solamente. Para evitar un posible uso indebido, los administradores pueden desactivar el acceso del Admin Console a los recursos editoriales.

* **Se muestra un tipo de licencia incorrecto**: Es posible que se muestre un tipo de licencia incorrecto en [!DNL Experience Manager] para un recurso. Los usuarios pueden iniciar sesión en [!DNL Adobe Stock] para ver el tipo de licencia.

* **Los campos de referencia y los metadatos no se sincronizan**: Cuando un usuario actualiza un campo de referencia de licencia, la información de referencia de licencia se actualiza en [!DNL Experience Manager] pero no en el [!DNL Adobe Stock] sitio web. Del mismo modo, si el usuario actualiza los campos de referencia en la variable [!DNL Adobe Stock] sitio web, las actualizaciones no se sincronizan en [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Tutorial de vídeo sobre el uso de [!DNL Adobe Stock] recursos con [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [[!DNL Adobe Stock] ayuda del plan empresarial](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-stock-enterprise.ug.html)
>* [[!DNL Adobe Stock] Preguntas más frecuentes](https://helpx.adobe.com/stock/faq.html)

