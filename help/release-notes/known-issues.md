---
title: Problemas conocidos en AEM 6.4
seo-title: Problemas conocidos en AEM 6.4
description: Problemas conocidos en Adobe Experience Manager 6.4
seo-description: Problemas conocidos en Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: 9b6c1efe1f6281892648c7b41820856d2e3fcac1

---


# Problemas conocidos {#known-issues}

Esta página contiene una lista de problemas conocidos que Adobe Experience Manager 6.4 publicó en abril de 2018. Para obtener más información sobre problemas conocidos, [póngase en contacto con el servicio de asistencia](https://helpx.adobe.com/support/experience-manager.html).

## Dispositivos híbridos {#hybrid-devices}

No se admiten dispositivos híbridos. Se pueden encontrar varios problemas al utilizar estos dispositivos. Los siguientes procedimientos sugeridos ayudan a resolver muchos problemas:

Si utiliza Google Chrome como navegador:
* Escriba `chrome://flags/` en la barra de direcciones y pulse Intro.
* Haga clic en Habilitar eventos táctiles > Deshabilitado.
* Reinicie el explorador (todas las fichas y ventanas).

Si utiliza Mozilla Firefox como navegador:
* Escriba `about:config` en la barra de direcciones y pulse Intro.
* Filtre la configuración a `dom.w3c`.
* Asegúrese de que la configuración es `0` y `false`.
* Reinicie el explorador.

Si utiliza Microsoft Edge como explorador:

* Escriba `about:flags` en la barra de direcciones y pulse Retorno.
* Desplácese a las funciones de Experimental y, a continuación, **[!UICONTROL toque]**.
* Haga clic en **[!UICONTROL Habilitar eventos]** táctiles.
* Seleccione **[!UICONTROL Siempre desactivado]**.
* Reinicie el explorador.

## Plataforma {#platform}

* **** Tablero de operaciones: La barra de progreso no se muestra cuando falta la extensión .zip en el archivo de copia de seguridad. (GRANITE-10713)
* **** HTL: El objeto Java Use con espacio en blanco final en la declaración del paquete bloquea SightlyJavaCompilerService (GRANITE-20836)
* **** Apache Felix/Sling: El archivo de configuración sigue presente en el repositorio incluso después de configuration.delete() (GRANITE-20618)
* **** Configuración de nube: La consola se interrumpe tras editar el contenedor de configuración (GRANITE-20726)
* **** Seguridad: La integración de IMS falla con la ruta de contexto personalizada (GRANITE-20639)
* **** Seguridad: Mejore la clasificación JAAS predeterminada de SSO, External y Default LoginModules (GRANITE-20590)
* **** Tooling - CRX DE Lite: El rango de la vista de propiedades sigue subiendo (GRANITE-12040)
* **** Tooling - CRX DE Lite: No se pueden guardar los cambios en los tipos de valores &quot;largos&quot; a menos que haga doble clic en Nombre de propiedad (GRANITE-12351)

* **** Tooling - CRX DE Lite: la búsqueda de ctrl+F en archivos de texto abiertos se queda atascada en la búsqueda de RegExp (GRANITE-5996)

* **** Tooling - CRX DE Lite: No se muestra la propiedad Node después de cambiar el nombre del nodo (GRANITE-7160)
* **** UI: Desplegar &quot;más...&quot; no muestra todos los elementos cuando se abren en un elemento emergente en IE y Firefox (GRANITE-16326)
* **** UI: La información sobre herramientas se oculta cuando se utiliza el diseño de columnas fijas con 2 columnas paralelas (GRANITE-16869)
* **** UI: Error no controlado al suplantar como usuario que no existe (GRANITE-23228). Solución para [implementar un controlador](/help/sites-developing/customizing-errorhandler-pages.md) de errores para personalizar el mensaje de error.

* **** Omnisearch: Búsquedas con excepción de causa de barra invertida (GRANITE-11769)
* **** Omnisearch: Abrir &quot;Ver configuración&quot; en la vista de lista hace que cambie el filtro de búsqueda (GRANITE-16524)
* **** Omnisearch: Lista incorrecta de configuraciones de columnas que se muestran al realizar la búsqueda de recursos desde sitios (GRANITE-16527)

* **** Omnisearch: Los predicados del carril izquierdo se llevan bien con la solicitud del servidor de Omniture (GRANITE-20524)
* **** Omnisearch: Omnisearch no admite rutas de contexto (GRANITE-16044)

## Assets {#assets}

* **Buscar**: La búsqueda no devuelve ningún resultado si la cadena de búsqueda comienza con un espacio en blanco [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Buscar**: En la IU clásica, las etiquetas y la interfaz de usuario no están visibles en la búsqueda (CQ-4235239)

* **UI**: La interfaz de usuario del recurso deja de responder después de copiar-pegar y seleccionar todo (CQ-4236142)

* **UI**: No se pueden mover los recursos después de la carga diferida (CQ-4236134)

* **Informes**: Error al crear el informe de modificación de recursos (CQ-4239744)

* **Informes**: La generación de informes de activos regulares y programados falla de manera inconsistente (algunos informes permanecen en cola) (CQ-4239089)

* **Metadatos**: Al agregar un campo de texto de varios valores al esquema de recursos, la regla de cascada de campos requerida no funciona (CQ-4239333)

* **BrandPortal**: Publicar en BrandPortal no funciona para colecciones (CQ-4238731)

* **Cargar**: Al cargar recursos con caracteres especiales en el nombre del archivo, no se muestra el mensaje de error de validación de los caracteres no permitidos para cada recurso. Aunque solo se muestra para el primer recurso, la interfaz indica claramente al usuario que no se permite el nombre de archivo del recurso proporcionado. (CQ-4256876)

## Communities {#communities}

* **Moderación** : no se puede eliminar una publicación principal como una sola operación de eliminación desde la interfaz de usuario de moderación masiva (CQ-4236797)

* **Consola** : el vínculo Nombre de usuario olvidado o Contraseña se está redirigiendo a la página de inicio de sesión en lugar del formulario de recuperación de contraseña correspondiente (CQ-4237682)

## Formularios {#forms}

### Instalación e implementación

* (Solo AEM Forms JEE) Al reforzar el servidor de aplicaciones JBoss mientras se ejecuta Configuration Manager, se devuelven errores de invocación de EJB y error de arranque. Sin embargo, puede ignorarlos. (Ref# CQ-4229793)

### Comunicaciones interactivas

* La interfaz de usuario del agente tarda un tiempo en cargar las comunicaciones interactivas que incluyen elementos de gráficos o imágenes. (CQ-4236630)
* El formato de visualización de datos en la vista previa de impresión es dd-mm-aaaa mientras que en la vista previa web es `dd-mmm-yy` (CQ-4237045)
* El canal Web de comunicación interactiva solo admite listas ordenadas y sin ordenar. En la lista de fragmentos de documento, el listado compuesto y la sangría no son compatibles con el canal Web de la comunicación interactiva. (CQ-4233672)
* Se observan los siguientes problemas cuando el canal web se sincroniza con el canal de impresión:

   * El canal Web tarda un tiempo en sincronizarse al cambiar del canal de impresión por primera vez.
   * El canal web no se sincroniza si el canal de impresión incluye un componente de gráfico no configurado. Para resolver el problema, elimine el componente del gráfico y vuelva a sincronizarlo.
   * La sincronización a veces falla con el error &quot;Error al sincronizar Live Copy&quot;. Para resolver el problema, actualice la página.
   * El texto estático de un fragmento de diseño se sustituye por el nombre de celda de tabla cuando la primera columna de la tabla es una columna de encabezado en la plantilla de canal de impresión.
   * No se pueden agregar componentes o recursos en ninguna ubicación que no sea la parte inferior de una comunicación de canal web. Para colocarlo en otra ubicación, agregue un panel en la parte inferior del canal web y reordene con el árbol de contenido.
   * Puede mover contenido al área de destino heredada del canal web sin eliminar la herencia de Live Copy.

(CQ-4239780)

### Integración de datos

* Las configuraciones de autenticación para los servicios web basados en SOAP no están visibles y, por lo tanto, no se pueden configurar en los servicios en la nube. Para resolver el problema:

   1. En la consola CRXDE Lite, vaya al nodo siguiente.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigWizard/cloudservices/\
      wsdlauthationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Actualice el valor de la propiedad value al mismo valor que el de la propiedad text.
   1. Haga clic en Guardar todo para guardar la configuración.

(CQ-4238462)

### Integración de Adobe Sign

* El programador de Adobe Sign deja de funcionar de forma intermitente y, por tanto, los formularios pendientes de firma no pasan al envío. Para resolver el problema, reinicie el paquete de compatibilidad con **el programador de Sling de** Apache desde la consola web de AEM en https://[*server*]:[*port*]/system/console/buncles.

### Creación de formularios adaptables

* El componente Gráfico en formularios adaptables ocupa más espacio del que ocupa normalmente.
* Se devuelve una excepción al guardar propiedades para formularios adaptables, fragmentos de formularios adaptables o comunicaciones interactivas en la interfaz de usuario de Forms Manager.
* El número máximo especificado de caracteres para un cuadro de texto del formulario adaptable no se acepta en los dispositivos Android 6.0 Samsung. (Ref# CQ-4235205)
