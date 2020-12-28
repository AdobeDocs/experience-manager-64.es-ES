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
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 4%

---


# Problemas conocidos {#known-issues}

Esta página mantiene una lista de los problemas conocidos que Adobe Experience Manager 6.4 lanzó en abril de 2018. Para obtener más información sobre problemas conocidos, [póngase en contacto con el servicio de soporte técnico](https://helpx.adobe.com/support/experience-manager.html).

## Dispositivos híbridos {#hybrid-devices}

No se admiten dispositivos híbridos. Se pueden encontrar varios problemas al utilizar estos dispositivos. Los siguientes procedimientos sugeridos ayudan a resolver muchos problemas:

Si utiliza Google Chrome como navegador:

* Escriba `chrome://flags/` en la barra de direcciones y pulse Intro.
* Haga clic en Habilitar eventos táctiles > Deshabilitado.
* Reinicie el explorador (todas las fichas y ventanas).

Si utiliza Mozilla Firefox como navegador:

* Escriba `about:config` en la barra de direcciones y pulse Intro.
* Filtre la configuración a `dom.w3c`.
* Asegúrese de que la configuración sea `0` y `false`.
* Reinicie el explorador.

Si utiliza Microsoft Edge como explorador:

* Escriba `about:flags` en la barra de direcciones y pulse Retorno.
* Desplácese a las funciones experimentales y, a continuación, **[!UICONTROL toque]**.
* Haga clic en **[!UICONTROL Habilitar eventos táctiles]**.
* Seleccione **[!UICONTROL Siempre desactivado]**.
* Reinicie el explorador.

## Plataforma {#platform}

* **Panel de operaciones: la barra de** progreso no se muestra cuando falta la extensión .zip en el archivo de copia de seguridad. (GRANITE-10713)
* **HTL:** El objeto de uso de Java con espacio en blanco final en la declaración del paquete bloquea SightlyJavaCompilerService (GRANITE-20836)
* **Apache Felix/Sling:Archivo** Config aún presente en el repositorio incluso después de configuration.delete() (GRANITE-20618)
* **Configuración de nube:** la consola se interrumpe tras editar el contenedor de configuración (GRANITE-20726)
* **Seguridad:error en la integración de** IMS con la ruta de contexto personalizada (GRANITE-20639)
* **Seguridad:** Mejore la clasificación JAAS predeterminada de SSO, Externo y Módulos de inicio de sesión predeterminados (GRANITE-20590)
* **Tooling - CRX DE Lite:** Amplitud de propiedades vista sigue avanzando (GRANITE-12040)
* **Tooling - CRX DE Lite:** No se pueden guardar los cambios en los tipos de valor &quot;Long&quot; a menos que haga clic con el doble en el nombre de la propiedad (GRANITE-12351)

* **Tooling - CRX DE Lite:** ctrl+F la búsqueda en archivos de texto abierto se queda atascada en la búsqueda de RegExp (GRANITE-5996)

* **Tooling - CRX DE Lite:propiedad** Node no mostrada después de cambiar el nombre del nodo (GRANITE-7160)
* **IU:** Desplegar &quot;más...&quot; no muestra todos los elementos cuando se abren en un elemento emergente en IE y Firefox (GRANITE-16326)
* **UI:** Información sobre herramientas se oculta al utilizar el diseño de columnas fijas con dos columnas contiguas (GRANITE-16869)
* **UI:** Error no controlado al suplantar como usuario que no existe (GRANITE-23228). Solución para [implementar un controlador de error](/help/sites-developing/customizing-errorhandler-pages.md) para personalizar el mensaje de error.

* **Omniture:** Búsquedas con excepción de causa de barra invertida (GRANITE-11769)
* **Omniture:** Abrir &quot;Configuración de Vista&quot; en la vista de listas hace que el filtro de búsqueda cambie (GRANITE-16524)
* **Omniture:lista** incorrecta de las configuraciones de columnas al realizar la búsqueda de recursos desde sitios (GRANITE-16527)

* **Omnisearch:Los predicados de carril** izquierdo se llevan bien con la solicitud del servidor de Omniture (GRANITE-20524)
* **Omnisearch:** Omnisearch no admite rutas de contexto (GRANITE-16044)

## Assets {#assets}

* **Buscar**: La búsqueda no devuelve ningún resultado si la cadena de búsqueda inicio con un espacio en blanco  [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Buscar**: En la IU clásica, las etiquetas y la interfaz de usuario no están visibles en la búsqueda (CQ-4235239)

* **UI**: La interfaz de usuario del recurso deja de responder después de copiar-pegar y seleccionar todo (CQ-4236142)

* **UI**: No se pueden mover los recursos después de la carga diferida (CQ-4236134)

* **Informes**: Error al crear el informe de modificación de recursos (CQ-4239744)

* **Informes**: La generación de informes de activos regulares y programados falla de manera inconsistente (algunos informes permanecen en cola) (CQ-4239089)

* **Metadatos**: Al agregar un campo de texto con varios valores al esquema de recursos, la regla de cascada de campos requerida no funciona (CQ-4239333)

* **BrandPortal**: Publicar en BrandPortal no funciona para colecciones (CQ-4238731)

* **Cargar**: Al cargar recursos con caracteres especiales en el nombre del archivo, no se muestra el mensaje de error de validación de los caracteres no permitidos para cada recurso. Aunque solo se muestra para el primer recurso, la interfaz indica claramente al usuario que no se permite el nombre de archivo del recurso proporcionado. (CQ-4256876)

## Communities {#communities}

* **Moderación** : no se puede eliminar una publicación principal como una sola operación de eliminación desde la interfaz de usuario de moderación masiva (CQ-4236797)

* **Consola** : el vínculo Nombre de usuario olvidado o Contraseña se redirige a la página de inicio de sesión en lugar del formulario de recuperación de contraseña correspondiente (CQ-4237682)

## Forms {#forms}

### Instalación e implementación

* (Solo AEM Forms JEE) Al reforzar el servidor de aplicaciones JBoss mientras se ejecuta Configuration Manager, se devuelven errores de invocación de EJB y error de arranque. Sin embargo, puede ignorarlos. (Ref# CQ-4229793)
* Cuando se inicia AEM Forms, aparece la advertencia `SAX Security Manager could not be setup`. (CQ-4297403)

### Comunicaciones interactivas

* La interfaz de usuario del agente tarda un tiempo en cargar las comunicaciones interactivas que incluyen elementos de gráficos o imágenes. (CQ-4236630)
* El formato de visualización de datos en la previsualización de impresión es dd-mm-aaaa mientras que en la previsualización web es `dd-mmm-yy` (CQ-4237045)
* El canal Web de comunicación interactiva solo admite listas ordenadas y sin ordenar. En los fragmentos de documento de lista, el listado compuesto y la sangría no son compatibles con el canal web de la comunicación interactiva. (CQ-4233672)
* Se observan los siguientes problemas al sincronizar el canal web con el canal de impresión:

   * El canal Web tarda un tiempo en sincronizarse al cambiar del canal de impresión por primera vez.
   * El canal web no se sincroniza si el canal de impresión incluye un componente de gráfico no configurado. Para resolver el problema, elimine el componente del gráfico y vuelva a sincronizarlo.
   * La sincronización a veces falla con el error &quot;Error al sincronizar Live Copy&quot;. Para resolver el problema, actualice la página.
   * El texto estático de un fragmento de diseño se sustituye por el nombre de celda de tabla cuando la primera columna de la tabla es una columna de encabezado de la plantilla de canal de impresión.
   * No se pueden agregar componentes o recursos en ninguna ubicación que no sea la parte inferior de una comunicación de canal web. Para colocarlo en otra ubicación, agregue un panel en la parte inferior del canal web y vuelva a ordenarlo mediante el árbol de contenido.
   * Puede mover contenido al área de destinatario heredada del canal web sin eliminar la herencia de Live Copy.

(CQ-4239780)

### Integración de datos

* Las configuraciones de autenticación para los servicios web basados en SOAP no están visibles y, por lo tanto, no se pueden configurar en los servicios en la nube. Para resolver el problema:

   1. En la consola CRXDE Lite, vaya al nodo siguiente.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigWizard/cloudservices/\
      wsdlauthentication settings/items/fixedcolumns/items/contenedor/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Actualice el valor de la propiedad value al mismo valor que el de la propiedad text.
   1. Haga clic en Guardar todo para guardar la configuración.

(CQ-4238462)

### Integración con Adobe Sign

* El Planificador de Adobe Sign deja de funcionar de forma intermitente y, por tanto, los formularios pendientes de firma no pasan al envío. Para resolver el problema, reinicie el paquete **Compatibilidad con Planificadoras Sling de Apache** desde AEM consola web en https://[*server*]:[*port*]/system/console/buncles.

### Creación adaptable de Forms

* El componente Gráfico en formularios adaptables ocupa más espacio del que ocupa normalmente.
* Se devuelve una excepción al guardar propiedades para formularios adaptables, fragmentos de formularios adaptables o comunicaciones interactivas en la interfaz de usuario de Forms Manager.
* El número máximo especificado de caracteres para un cuadro de texto del formulario adaptable no se acepta en los dispositivos Android 6.0 Samsung. (Ref# CQ-4235205)
