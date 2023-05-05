---
title: 'ASRP: proveedor de recursos de almacenamiento de Adobe'
seo-title: ASRP - Adobe Storage Resource Provider
description: Configuración de AEM Communities para utilizar una base de datos relacional como su tienda común
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 3%

---

# ASRP: proveedor de recursos de almacenamiento de Adobe {#asrp-adobe-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Acerca de ASRP {#about-asrp}

Cuando AEM Communities está configurado para utilizar ASRP como su almacén común, el contenido generado por el usuario (UGC) es accesible desde todas las instancias de autor y publicación sin necesidad de sincronización ni replicación.

Consulte también [Características de las opciones de SRP](working-with-srp.md#characteristics-of-srp-options) y [Topologías recomendadas](topologies.md).

## Requisitos  {#requirements}

Se requiere una licencia adicional para el uso de ASRP.

Para configurar el sitio de AEM Communities para que use ASRP para UGC, póngase en contacto con el representante de cuentas para:

* URL del centro de datos (dirección del extremo ASRP)
* Clave de consumidor
* Clave secreta
* ID del grupo de informes

Las claves de consumidor y secreto se comparten entre todos los grupos de informes de una empresa. Hay un grupo de informes por inquilino.

## Configuración {#configuration}

### Seleccionar ASRP {#select-asrp}

La variable [Consola de configuración de almacenamiento](srp-config.md) permite seleccionar la configuración de almacenamiento predeterminada, que identifica qué implementación de SRP utilizar.

**Sobre el autor**:

* Desde la navegación global: **[!UICONTROL Herramientas > Comunidades > Configuración de almacenamiento]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Select **[!UICONTROL Proveedor de recursos de almacenamiento de Adobe (ASRP)]**
* La siguiente información proviene del proceso de aprovisionamiento

   * **[!UICONTROL URL del centro de datos]**

      Desplegable para seleccionar el centro de datos de producción identificado por el representante de cuentas

   * **[!UICONTROL Grupo de informes predeterminado]**

      Introduzca el nombre del grupo de informes predeterminado

   * **[!UICONTROL Clave de consumidor]**

      Introduzca la clave de cliente

   * **[!UICONTROL Secreto]**

      Escriba la clave secreta

* Seleccione **[!UICONTROL Enviar]**

Prepare las instancias de publicación:

* [Replicar la clave criptográfica](#replicate-the-crypto-key)
* [Replicar la configuración](#publishing-the-configuration)

Después de enviar la configuración, pruebe la conexión:

* Select **[!UICONTROL Probar configuración]**
para cada instancia de autor y publicación, pruebe la conexión al centro de datos desde la consola de configuración de almacenamiento

* Por último, asegúrese de que las direcciones URL del sitio para los datos de perfil se puedan enrutar desde el centro de datos mediante [externalización de vínculos](#externalize-links).

### Replicar la clave criptográfica {#replicate-the-crypto-key}

La clave de consumidor y la clave secreta están cifradas. Para que las claves se cifren o desencripten correctamente, la clave principal de Granite Crypto debe ser la misma en todas las instancias AEM.

Siga las instrucciones indicadas en [Replicar la clave criptográfica](deploy-communities.md#replicate-the-crypto-key).

### Externalizar vínculos {#externalize-links}

Para obtener los vínculos correctos de perfil e imagen de perfil, asegúrese de realizar correctamente las acciones siguientes: [Configuración del externalizador de vínculos](../../help/sites-developing/externalizer.md).

Asegúrese de que los dominios sean direcciones URL que se puedan enrutar desde la URL del centro de datos (extremo ASRP).

### Sincronización de tiempo {#time-synchronization}

Para que la autenticación con el extremo ASRP se realice correctamente, los equipos que ejecuten su AEM Communities alojado deben sincronizarse a la hora, como con la variable [Protocolo de tiempo de red (NTP)](https://www.ntp.org/).

### Publicación de la configuración {#publishing-the-configuration}

ASRP debe identificarse como el almacén común en todas las instancias de autor y publicación.

Para que la configuración idéntica esté disponible en el entorno de publicación:

* **Sobre el autor**:

   * Vaya del menú principal a **[!UICONTROL Herramientas > Operaciones > Replicación]**
   * Select **[!UICONTROL Activar árbol]**
   * **[!UICONTROL Ruta de inicio]**:

      * Vaya a `/etc/socialconfig/srpc/`
   * Desmarcar **[!UICONTROL Solo modificado]**
   * Select **[!UICONTROL Activar]**


## Actualización desde AEM 6.0 {#upgrading-from-aem}

>[!CAUTION]
>
>Si habilita ASRP en un sitio de comunidad publicado, cualquier UGC ya almacenado en [JCR](jsrp.md) ya no estará visible, ya que no hay sincronización de datos entre el almacenamiento local y el almacenamiento en la nube.

**`AEM Communities Extension`** se ha introducido anteriormente en AEM 6.0 social communities as a cloud service. A partir de AEM 6.1 Communities, no es necesaria ninguna configuración de nube, simplemente seleccione ASRP en el [consola de configuración de almacenamiento](srp-config.md).

Debido a la nueva estructura de almacenamiento, es necesario seguir la [actualización](upgrade.md#adobe-cloud-storage) instrucciones para actualizar de comunidades sociales a comunidades.

## Administración de datos de usuario {#managing-user-data}

Para obtener información sobre *usuarios*, *perfiles de usuario* y *grupos de usuarios*, introducidos a menudo en el entorno de publicación, visita

* [Sincronización de usuarios](sync.md)
* [Administración de usuarios y grupos de usuarios](users.md)

## Solución de problemas {#troubleshooting}

### UGC desaparece después de la actualización {#ugc-disappears-after-upgrade}

Si actualiza desde un sitio AEM comunidad social 6.0 existente, asegúrese de seguir la [instrucciones de actualización](upgrade.md#adobe-cloud-storage), de lo contrario UGC *aparecer* que se pierdan.

### Errores de autenticación {#authentication-errors}

Si recibe errores de autenticación contra la dirección URL del centro de datos y el archivo error.log AEM contiene mensajes sobre marcas de hora antiguas, compruebe que se esté realizando la sincronización de hora.

Se recomienda utilizar una herramienta como la [Protocolo de tiempo de red (NTP)](https://www.ntp.org/) para sincronizar con el tiempo todos los servidores AEM de creación y publicación.

### El contenido nuevo no aparece en las búsquedas {#new-content-does-not-appear-in-searches}

La infraestructura de almacenamiento en la nube de Adobe utiliza *coherencia final* para ayudar a lograr sus objetivos de escalado y rendimiento. Por este motivo, el nuevo contenido no está disponible al instante y puede tardar varios segundos en aparecer en los resultados de búsqueda.

Mientras se supervisa el intervalo que afecta a la coherencia final, póngase en contacto con su representante de cuentas si el contenido nuevo tarda más de unos segundos en aparecer en las búsquedas.

### UGC no visible en ASRP {#ugc-not-visible-in-asrp}

Asegúrese de que ASRP se haya configurado para ser el proveedor predeterminado comprobando la configuración de la opción de almacenamiento. De forma predeterminada, el proveedor de recursos de almacenamiento es JSRP, no ASRP.

En todas las instancias de creación y publicación de AEM, vuelva a la consola Configuración de almacenamiento o compruebe el repositorio de AEM:

* En JCR, si [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * No contiene un [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) , significa que el proveedor de almacenamiento es JSRP
   * Si el nodo srpc existe y contiene el nodo [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration), las propiedades de configuración predeterminada deben definir ASRP para que sea el proveedor predeterminado
