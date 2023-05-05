---
title: Problemas conocidos en AEM 6.4
seo-title: Known Issues in AEM 6.4
description: Problemas conocidos en Adobe Experience Manager 6.4
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 7%

---

# Problemas conocidos {#known-issues}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Esta página contiene una lista de problemas conocidos que Adobe Experience Manager 6.4 publicó en abril de 2018. Para obtener más información sobre problemas conocidos, [póngase en contacto con el servicio de asistencia técnica](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=es).

## Dispositivos híbridos {#hybrid-devices}

Los dispositivos híbridos no son compatibles. Se pueden encontrar varios problemas al utilizar estos dispositivos. Los siguientes procedimientos sugeridos ayudan a resolver muchos problemas:

Si utiliza Google Chrome como navegador:

* Tipo `chrome://flags/` en la barra de direcciones y pulse Intro.
* Haga clic en Habilitar eventos táctiles > Deshabilitado.
* Reinicie el explorador (todas las pestañas y ventanas).

Si usa Mozilla Firefox como navegador:

* Tipo `about:config` en la barra de direcciones y pulse Intro.
* Filtre la configuración a `dom.w3c`.
* Asegúrese de que la configuración esté `0` y `false`.
* Reinicie el explorador.

Si utiliza Microsoft Edge como explorador:

* Tipo `about:flags` en la barra de direcciones y pulse Retorno.
* Desplácese hasta las funciones experimentales y, a continuación, **[!UICONTROL Táctil]**.
* Haga clic en **[!UICONTROL Habilitar eventos táctiles]**.
* Select **[!UICONTROL Always Off]**.
* Reinicie el explorador.

## Plataforma {#platform}

* **Tablero de operaciones:** La barra de progreso no se muestra cuando falta la extensión .zip en el archivo de copia de seguridad. (GRANITE-10713)
* **HTL:** El objeto Java Use con espacio en blanco final en la declaración del paquete bloquea SightlyJavaCompilerService (GRANITE-20836)
* **Apache Felix/Sling:** El archivo de configuración sigue presente en el repositorio incluso después de configuration.delete() (GRANITE-20618)
* **Configuración de nube:** La consola se rompe después de editar el contenedor de configuración (GRANITE-20726)
* **Seguridad:** La integración de IMS falla con la ruta de contexto personalizada (GRANITE-20639)
* **Seguridad:** Mejorar la clasificación JAAS predeterminada de SSO, External y Default LoginModules (GRANITE-20590)
* **Tooling - CRX DE Lite:** El rango de las propiedades sigue creciendo (GRANITE-12040)
* **Tooling - CRX DE Lite:** No se pueden guardar los cambios en los tipos de valores &quot;largos&quot; a menos que haga doble clic en Nombre de propiedad (GRANITE-12351)

* **Tooling - CRX DE Lite:** la búsqueda ctrl+F en archivos de texto abiertos se atasca en la búsqueda de RegExp (GRANITE-5996)

* **Tooling - CRX DE Lite:** La propiedad Node no se muestra después de cambiar el nombre del nodo (GRANITE-7160)
* **IU:** Desplegable &quot;más...&quot; no muestra todos los elementos al abrirlos en un elemento de popover en IE y Firefox (GRANITE-16326)
* **IU:** La información sobre herramientas se oculta al utilizar el diseño de columnas fijas con 2 columnas contiguas (GRANITE-16869)
* **IU:** Error no gestionado al suplantar como usuario que no existe (GRANITE-23228). Solución alternativa [implementación de un controlador de error](/help/sites-developing/customizing-errorhandler-pages.md) para personalizar el mensaje de error.

* **Omnisearch:** Búsquedas con excepción de causa de barra invertida (GRANITE-11769)
* **Omnisearch:** Abrir &quot;Ver configuración&quot; en la vista de lista hace que cambie el filtro de búsqueda (GRANITE-16524)
* **Omnisearch:** Lista incorrecta de configuraciones de columnas que se muestran al realizar búsquedas de recursos desde Sitios (GRANITE-16527)

* **Omnisearch:** Los predicados del carril izquierdo se llevan bien con la solicitud del servidor Omnisearch (GRANITE-20524)
* **Omnisearch:** Omnisearch no admite rutas de contexto (GRANITE-16044)

## Assets {#assets}

* **Buscar**: La búsqueda no devuelve ningún resultado si la cadena de búsqueda comienza con un espacio en blanco [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **Buscar**: En la IU clásica y las etiquetas no están visibles en la búsqueda (CQ-4235239)

* **IU**: La interfaz de usuario de los recursos deja de responder después de Copiar-Pegar y Seleccionar todo (CQ-4236142)

* **IU**: No se pueden mover los recursos después de la carga diferida (CQ-4236134)

* **Informes**: Error en la creación del informe de modificación de recursos (CQ-4239744)

* **Informes**: La generación de informes de recursos programados y regulares falla de forma inconsistente (algunos informes permanecen en cola) (CQ-4239089)

* **Metadatos**: Al añadir un campo de texto de varios valores al esquema de Asset, la regla de cascada de campo necesaria no funciona (CQ-4239333)

* **BrandPortal**: Publicar en BrandPortal no funciona para colecciones (CQ-4238731)

* **Cargar**: Al cargar recursos con caracteres especiales en el nombre del archivo, no se muestra el mensaje de error de validación de los caracteres no permitidos para cada recurso. Aunque se muestra solo para el primer recurso, la interfaz indica claramente al usuario que no se permite el nombre de archivo del recurso proporcionado. (CQ-4256876)

## Communities {#communities}

* **Moderación** - No se puede eliminar la publicación principal como una sola operación de eliminación desde la interfaz de usuario de moderación masiva (CQ-4236797)

* **Consola** - El nombre de usuario olvidado o el vínculo Contraseña se redirigen a la página de inicio de sesión en lugar del formulario correspondiente de recuperación de contraseña (CQ-4237682)

## Forms {#forms}

### Instalación e implementación

* (Solo AEM Forms JEE) Al reforzar el servidor de aplicaciones JBoss mientras se ejecuta Configuration Manager, se devuelven errores de invocación de EJB y error de arranque. Sin embargo, puede ignorarlos. (Ref# CQ-4229793)
* Cuando se inicia AEM Forms, la variable `SAX Security Manager could not be setup` aparece la advertencia. (CQ-4297403)

### Comunicaciones interactivas

* La interfaz de usuario del agente tarda un tiempo en cargar las comunicaciones interactivas que incluyen elementos de gráficos o imágenes. (CQ-4236630)
* El formato de visualización de datos en la vista previa de impresión es dd-mm-aaaa mientras que en la vista previa web es `dd-mmm-yy` (CQ-4237045)
* El canal web de comunicación interactiva solo admite listas ordenadas y sin ordenar. En los fragmentos de la lista de documentos, las listas compuestas y la sangría no son compatibles con el canal web de la comunicación interactiva. (CQ-4233672)
* Los siguientes problemas se observan cuando el canal web se sincroniza con el canal de impresión:

   * El canal web tarda unos minutos en sincronizarse al cambiar del canal de impresión por primera vez.
   * El canal web no se sincroniza si el canal de impresión incluye un componente de gráfico no configurado. Para resolver el problema, elimine el componente del gráfico y vuelva a sincronizar.
   * La sincronización a veces falla con el error &quot;Se ha producido un error al sincronizar Live Copy&quot;. Para resolver el problema, actualice la página.
   * El texto estático de un fragmento de diseño se reemplaza por el nombre de celda de tabla cuando la primera columna de la tabla es una columna de encabezado en la plantilla de canal de impresión.
   * No se pueden agregar componentes o recursos en ninguna ubicación que no sea la parte inferior de una comunicación de canal web. Para colocarlo en otra ubicación, agregue un panel en la parte inferior del canal web y reordene mediante el árbol de contenido.
   * Puede mover contenido al área de destino heredada del canal web sin eliminar la herencia de Live Copy.

(CQ-4239780)

### Integración de datos

* Las configuraciones de autenticación para servicios web basados en SOAP no son visibles y, por lo tanto, no se pueden configurar en servicios en la nube. Para resolver el problema:

   1. En la consola de CRXDE Lite, vaya al nodo siguiente.\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      selectAuthentication/items/custom.
   1. Actualice el valor de la propiedad value al mismo nivel que el valor de la propiedad text .
   1. Haga clic en Guardar todo para guardar la configuración.

(CQ-4238462)

### Integración con Acrobat Sign

* El programador de Acrobat Sign deja de funcionar de forma intermitente y, por lo tanto, los formularios pendientes no se mueven al envío. Para resolver el problema, reinicie el **Compatibilidad con el programador de Apache Sling** paquete desde AEM consola web en https://[*server*]:[*puerto*]/system/console/bundles.

### Creación adaptativa de Forms

* El componente Gráfico de los formularios adaptables ocupa más espacio del que ocupa normalmente.
* Se devuelve una excepción al guardar propiedades para formularios adaptables, fragmentos de formularios adaptables o comunicaciones interactivas en la interfaz de usuario de Forms Manager.
* El número máximo especificado de caracteres para un cuadro de texto de formulario adaptable no se acepta en los dispositivos Android 6.0 Samsung. (Ref# CQ-4235205)
* Cuando envía un formulario que contiene un campo de carga de HTML estándar desde un dispositivo iOS de Apple, a veces, el contenido del archivo no se envía y se recibe un archivo de 0 bytes en el otro extremo. Apple iOS 15.1 proporciona una solución para el problema.

