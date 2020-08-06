---
title: ASRP - Proveedor de recursos de Almacenamiento de Adobe
seo-title: ASRP - Proveedor de recursos de Almacenamiento de Adobe
description: Configure AEM Communities para utilizar una base de datos relacional como su almacén común
seo-description: Configure AEM Communities para utilizar una base de datos relacional como su almacén común
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 2%

---


# ASRP - Proveedor de recursos de Almacenamiento de Adobe {#asrp-adobe-storage-resource-provider}

## Acerca de ASRP {#about-asrp}

Cuando AEM Communities está configurado para utilizar ASRP como su almacén común, el contenido generado por el usuario (UGC) es accesible desde todas las instancias de creación y publicación sin necesidad de sincronización ni replicación.

Consulte también [Características de las Opciones](working-with-srp.md#characteristics-of-srp-options) de SRP y Topologías [](topologies.md)recomendadas.

## Requisitos {#requirements}

Se requiere una licencia adicional para el uso de ASRP.

Para configurar el sitio de AEM Communities para que utilice ASRP para UGC, póngase en contacto con su representante de cuentas para:

* Dirección URL del centro de datos (dirección del extremo ASRP)
* Clave de consumidor
* Clave secreta
* ID del grupo de informes

Las claves de consumidor y clave secreta se comparten en todos los grupos de informes de una compañía. Hay un grupo de informes por inquilino.

## Configuración {#configuration}

### Seleccionar ASRP {#select-asrp}

La consola [Configuración de](srp-config.md) Almacenamiento permite seleccionar la configuración de almacenamiento predeterminada, que identifica la implementación de SRP que se va a utilizar.

**Sobre el autor**:

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Configuración de Almacenamiento]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Select **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
* La siguiente información proviene del proceso de aprovisionamiento

   * **[!UICONTROL URL del centro de datos]**

      Despliegue para seleccionar el centro de datos de producción identificado por el representante de cuentas

   * **[!UICONTROL Grupo de informes predeterminado]**

      Escriba el nombre del grupo de informes predeterminado

   * **[!UICONTROL Clave de consumidor]**

      Introduzca la clave del cliente

   * **[!UICONTROL Secreto]**

      Escriba la clave secreta

* Seleccione **[!UICONTROL Enviar]**

Prepare las instancias de publicación:

* [Replicar la clave criptográfica](#replicate-the-crypto-key)
* [Replicar la configuración](#publishing-the-configuration)

Después de enviar la configuración, pruebe la conexión:

* Seleccione **[!UICONTROL Probar configuración]** para cada instancia de creación y publicación, pruebe la conexión al centro de datos desde la consola Configuración de Almacenamiento

* Por último, asegúrese de que las direcciones URL del sitio para los datos de perfil se pueden enrutar desde el centro de datos [externalizando los vínculos](#externalize-links).

### Replicar la clave de cifrado {#replicate-the-crypto-key}

La Clave del cliente y la clave secreta están cifradas. Para que las claves se cifren o descifren correctamente, la clave de cifrado de granito principal debe ser la misma en todas las instancias AEM.

Siga las instrucciones de [Replicar la clave](deploy-communities.md#replicate-the-crypto-key)de cifrado.

### Externalizar vínculos {#externalize-links}

Para los vínculos de imagen de perfil y perfil correctos, asegúrese de [configurar correctamente el Externalizador](../../help/sites-developing/externalizer.md)de vínculos.

Asegúrese de establecer los dominios como direcciones URL que se pueden enrutar desde la dirección URL del centro de datos (extremo ASRP).

### Sincronización de tiempo {#time-synchronization}

Para que la autenticación con el extremo ASRP tenga éxito, los equipos que ejecutan el AEM Communities alojado deben sincronizarse a la hora, como por ejemplo con el Protocolo de tiempo de [red (NTP)](https://www.ntp.org/).

### Publicación de la configuración {#publishing-the-configuration}

ASRP debe identificarse como el almacén común en todas las instancias de creación y publicación.

Para que la configuración idéntica esté disponible en el entorno de publicación:

* **Sobre el autor**:

   * Vaya del menú principal a **[!UICONTROL Herramientas > Operaciones > Replicación]**
   * Seleccione **[!UICONTROL Activar árbol]**
   * **[!UICONTROL Ruta de inicio]**:

      * Vaya a `/etc/socialconfig/srpc/`
   * Desmarcar **[!UICONTROL sólo modificado]**
   * Seleccionar **[!UICONTROL activar]**


## Actualización desde AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Si habilita ASRP en un sitio de comunidad publicado, cualquier UGC ya almacenado en [JCR](jsrp.md) dejará de ser visible, ya que no hay sincronización de datos entre el almacenamiento local y el almacenamiento en la nube.

**`AEM Communities Extension`** previamente se introdujo en AEM comunidades sociales 6.0 como servicio de nube. A partir de AEM comunidades 6.1, no es necesaria ninguna configuración de nube, simplemente seleccione ASRP en la consola [de configuración de](srp-config.md)almacenamiento.

Debido a la nueva estructura de almacenamientos, es necesario seguir las instrucciones de [actualización](upgrade.md#adobe-cloud-storage) al pasar de las comunidades sociales a las comunidades.

## Administración de datos de usuario {#managing-user-data}

Para obtener información sobre *usuarios*, perfiles *de* usuarios y grupos *de* usuarios, que se especifican a menudo en el entorno de publicación, visite

* [Sincronización de usuarios](sync.md)
* [Administración de usuarios y grupos de usuarios](users.md)

## Solución de problemas {#troubleshooting}

### UGC desaparece tras la actualización {#ugc-disappears-after-upgrade}

Si actualiza desde un sitio de comunidad social existente AEM 6.0, asegúrese de seguir las instrucciones [de](upgrade.md#adobe-cloud-storage)actualización, de lo contrario, *parece* que UGC se pierde.

### Errores de autenticación {#authentication-errors}

Si recibe errores de autenticación con la dirección URL del centro de datos y el AEM error.log contiene mensajes sobre marcas de hora antiguas, compruebe que se está realizando la sincronización de hora.

Se recomienda utilizar una herramienta como el Protocolo de tiempo de [red (NTP)](https://www.ntp.org/) para sincronizar con el tiempo todos los servidores de publicación y creación AEM.

### El nuevo contenido no aparece en las búsquedas {#new-content-does-not-appear-in-searches}

La infraestructura de almacenamiento de nube de Adobe utiliza *una consistencia* eventual para ayudar a lograr sus objetivos de escalamiento y rendimiento. Por este motivo, el nuevo contenido no está disponible al instante y puede tardar varios segundos en aparecer en los resultados de búsqueda.

Mientras se supervisa el intervalo que afecta a la coherencia final, póngase en contacto con el representante de cuentas si el contenido nuevo tarda más de unos segundos en aparecer en las búsquedas.

### UGC no visible en ASRP {#ugc-not-visible-in-asrp}

Compruebe la configuración de la opción de almacenamiento para asegurarse de que ASRP se ha configurado como el proveedor predeterminado. De forma predeterminada, el proveedor de recursos de almacenamiento es JSRP, no ASRP.

En todas las instancias de creación y publicación de AEM, vuelva a la consola de Configuración de Almacenamiento o compruebe el repositorio de AEM:

* En JCR, if [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * No contiene un nodo [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , significa que el proveedor de almacenamiento es JSRP
   * Si el nodo srpc existe y contiene la configuración [predeterminada](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)del nodo, las propiedades de configuración predeterminada deben definir ASRP para que sea el proveedor predeterminado

