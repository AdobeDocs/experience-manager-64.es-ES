---
title: Requisitos técnicos
seo-title: Requisitos técnicos
description: Una lista de las plataformas de cliente y servidor admitidas para AEM.
seo-description: Una lista de las plataformas de cliente y servidor admitidas para AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
translation-type: tm+mt
source-git-commit: d09956e5e7fb42e9c4b145e027778f209876239a
workflow-type: tm+mt
source-wordcount: '3142'
ht-degree: 2%

---


# Requisitos técnicos{#technical-requirements}

Adobe admite Adobe Experience Manager (AEM) en las plataformas como se detalla en la siguiente información de este documento.

Para cualquier problema relacionado específicamente con la plataforma en sí, póngase en contacto directamente con el proveedor de la plataforma.

>[!NOTE]
>
>Según la plataforma en la que instale AEM, podría haber diferentes conjuntos de requisitos para la administración de usuarios.

## Requisitos previos {#prerequisites}

Requisitos mínimos para instalar Adobe Experience Manager:

* Java Platform instalado, Standard Edition JDK u otras máquinas virtuales [Java admitidas](#java-virtual-machines)
* Archivo de inicio rápido Experience Manager (JAR independiente o WAR de implementación de aplicaciones web)

### Requisitos mínimos de tamaño {#minimum-sizing-requirements}

Requisitos mínimos para ejecutar Adobe Experience Manager:

* 5 GB de espacio libre en disco en el directorio de instalación
* 2 GB de memoria

>[!NOTE]
>
>* Los casos de uso de recursos digitales necesitan más memoria básica. Consulte [Implementación y mantenimiento](/help/sites-deploying/deploy.md#default-local-install) para obtener más información.
>* [El paquete](/help/forms/using/installing-configuring-aem-forms-osgi.md) de complementos de AEM Forms requiere 15 GB de espacio temporal.

>



Para obtener más información, consulte las Directrices [de cambio de tamaño de](/help/managing/hardware-sizing-guidelines.md) hardware.

### Niveles de soporte {#support-levels}

Este documento lista las plataformas de cliente y servidor admitidas para Adobe Experience Manager. Adobe proporciona varios niveles de soporte, tanto para configuraciones recomendadas como para otras configuraciones.

### Configuraciones admitidas {#supported-configurations}

Adobe recomienda estas configuraciones y proporciona soporte completo como parte del acuerdo de mantenimiento de software estándar.

<table> 
 <tbody> 
  <tr> 
   <td>Nivel de asistencia</td> 
   <td>Descripción<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>A: Admitido</strong></td> 
   <td>Adobe proporciona soporte y mantenimiento completos para esta configuración. Esta configuración está cubierta por el proceso de garantía de calidad del Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R: Compatibilidad restringida</strong></td> 
   <td>Para garantizar el éxito de los proyectos de nuestros clientes, Adobe proporciona soporte completo dentro de un programa de soporte restringido, que requiere que se cumplan condiciones específicas. El soporte de nivel R requiere una solicitud formal del cliente y confirmación por Adobe. Para obtener más información, póngase en contacto con el Servicio de atención al cliente de Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configuraciones no admitidas {#unsupported-configurations}

| Nivel de asistencia | Descripción |
|---|---|
| **Z: No admitido** | No se admite la configuración. Adobe no hace ninguna declaración sobre si la configuración funciona o no y no la admite. |

## Plataformas compatibles {#supported-platforms}

### Máquinas virtuales Java {#java-virtual-machines}

La aplicación requiere una máquina virtual Java para ejecutarse, que se proporciona mediante la distribución Java Development Kit (JDK).

Adobe Experience Manager funciona con las siguientes versiones de las máquinas virtuales Java:

>[!CAUTION]
>
>Se recomienda rastrear los boletines de seguridad del proveedor de Java para garantizar la seguridad de los entornos de producción e instalar las últimas actualizaciones de Java.

<table> 
 <tbody> 
  <tr> 
   <td>Plataforma</td> 
   <td>Nivel de asistencia<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z: No admitido </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z: No admitido </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z: No admitido</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64 bits</strong></td> 
   <td>A: Admitido [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - compilación 2.9, JRE 1.8.0 [2]</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - compilación 2.8, JRE 1.8.0 [2]</td> 
   <td>A: Admitido</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle ha adoptado un modelo de soporte a largo plazo (LTS) para los productos Oracle Java SE. Java 9 and 10 are non-LTS releases by Oracle (see [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe solo proporcionará soporte a las versiones LTS de Java para ejecutar AEM en producción.

1. IBM JRE sólo se admite junto con WebSphere Application Server.
1. El soporte y la distribución de JDK de Oracle Java SE, incluidas todas las actualizaciones de mantenimiento de las versiones de LTS más allá del final de las actualizaciones públicas, serán soportados directamente por Adobe para todos los clientes AEM que utilicen la tecnología de Oracle Java SE. Consulte la compatibilidad de [Oracle Java con Adobe Experience Manager Q&amp;A](assets/adobe-oracle-java-license-agreement.pdf) para obtener más información.

### Almacenamiento y persistencia {#storage-persistence}

Existen varias opciones para implementar el repositorio de Adobe Experience Manager. Consulte la siguiente lista para ver las opciones de almacenamiento y las tecnologías admitidas.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plataforma</strong></td> 
   <td><strong>Descripción</strong></td> 
   <td><strong>Nivel de asistencia</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Sistema de archivos con archivos TAR [1]</strong></td> 
   <td>Repositorio</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td><strong>Sistema de archivos con Almacén de datos [1]</strong></td> 
   <td>Binarios</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Almacenar archivos binarios en archivos TAR en el sistema de archivos [1]</td> 
   <td>Binarios</td> 
   <td>Z: No compatible con la producción</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binarios</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Almacenamiento de blob de Microsoft Azure</td> 
   <td>Binarios</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5]</td> 
   <td>Repositorio</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3]</td> 
   <td>Repositorio</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Base de datos de Forms</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Base de datos de Forms</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Repositorio y base de datos de Forms</td> 
   <td>R: Compatibilidad restringida (4)</td> 
  </tr> 
  <tr> 
   <td>Base de datos Oracle 12c (12.1.x)</td> 
   <td>Repositorio y base de datos de Forms</td> 
   <td>R: Compatibilidad restringida</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Base de datos de Forms</td> 
   <td>Z: No compatible (4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Base de datos de Forms</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Base de datos de Forms</td> 
   <td>R: Compatibilidad restringida (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (integrado de Quickstart)</strong></td> 
   <td>Servicio de búsqueda</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Servicio de búsqueda</td> 
   <td>A: Admitido</td> 
  </tr> 
 </tbody> 
</table>

1. &#39;File System&#39; incluye el almacenamiento de bloques que es compatible con POSIX. Esto incluye la tecnología de almacenamiento de red. Tenga en cuenta que el rendimiento del sistema de archivos puede variar e influir en el rendimiento general. Se recomienda cargar AEM de prueba en combinación con el sistema de archivos de red/remoto.
1. El uso compartido de MongoDB no se admite en AEM.
1. Solo se admite el motor de Almacenamiento MongoDB WiredTiger.
1. No compatible con AEM Forms.
1. MongoDB Enterprise 3.6 se admite a partir de la versión 6.4.2.0 de AEM.

>[!NOTE]
>
>Consulte [Implementación de comunidades](/help/communities/deploy-communities.md) para obtener información adicional sobre la capacidad de AEM Communities.

>[!NOTE]
>
>MongoDB es un software de terceros y no está incluido en el paquete de licencias de AEM. Para obtener más información, consulte la página de directivas [de licencias de](https://www.mongodb.org/about/licensing/) MongoDB.
>
>Para aprovechar al máximo su implementación AEM con MongoDB, Adobe recomienda la licencia de la versión empresarial MongoDB para beneficiarse de la asistencia profesional. Consulte Implementaciones [recomendadas](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) para obtener más información.
>
>La licencia incluye un conjunto de réplicas estándar, compuesto por una instancia primaria y dos instancias secundarias que se pueden usar para la implementación de publicación o del autor.
>
>Si desea ejecutar tanto la creación como la publicación en MongoDB, deberá adquirir dos licencias independientes.
>
>El Servicio de atención al cliente de Adobe asistirá en los problemas de calificación relacionados con el uso de MongoDB con AEM.
>
>Para obtener más información, consulte la página [](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)MongoDB para Adobe Experience Manager.

>[!NOTE]
>
>Las bases de datos relacionales admitidas, como se indica anteriormente, son software de terceros y no se incluyen en el paquete de licencias de AEM.
>
>Para ejecutar AEM 6.4 con una base de datos relacional admitida, se requiere un contrato de soporte independiente con un proveedor de base de datos. El Servicio de atención al cliente de Adobe asistirá en los problemas de calificación relacionados con el uso de bases de datos relacionales con AEM 6.4.
>
>**Tenga en cuenta que la mayoría de las bases de datos relacionales están actualmente admitidas en Level-R en el AEM 6.4, que incluye criterios de soporte y un programa de soporte, como se indica en la descripción de Level-R más arriba.**

### Motores de servlet / Servidores de aplicaciones {#servlet-engines-application-servers}

Adobe Experience Manager puede ejecutarse como servidor independiente (el archivo JAR de inicio rápido) o como aplicación web dentro de un servidor de aplicaciones de terceros (el archivo WAR).

La versión mínima de la API de servlet requerida es Servlet 3.1, pero inferior a Servlet 4.0.

| Plataforma | Nivel de asistencia |
|---|---|
| **Motor Servlet integrado de arranque rápido (Jetty 9.3)** | A: Admitido |
| Oracle WebLogic Server 12.2 (12cR2) | A: Admitido |
| ENVÍO continuo (LibertyProfile) de Application Server para IBM WebSphere con Web Perfil 7.0 e IBM JRE 1.8 | A: Admitido |
| IBM WebSphere Application Server 9.0 | A: Admitido |
| Apache Tomcat 8.5.x | A: Admitido |
| JBoss EAP 7.1.0 con el servidor de aplicaciones JBoss | A: Admitido (1) |
| JBoss EAP 7.0.0 con el servidor de aplicaciones JBoss | A: Admitido |

1. No compatible con AEM Forms.

### Sistemas operativos de servidor {#server-operating-systems}

Adobe Experience Manager funciona con las siguientes plataformas de servidor:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plataforma</strong></td> 
   <td><strong>Nivel de asistencia</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, basado en la distribución de Red Hat</strong></td> 
   <td>A: Admitido (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, basado en la distribución Debian incl. Ubuntu</td> 
   <td>A: Admitido (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, basado en la distribución SUSE</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A: Compatible con limitaciones (3,5,7)<br /> R: Compatibilidad restringida para nuevos contratos</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A: Compatible con limitaciones (2,5,7)<br /> R: Compatibilidad restringida para nuevos contratos</td> 
  </tr> 
 </tbody> 
</table>

1. Linux Kernel 2.6, 3.x y 4.x incluye derivados de la distribución de Red Hat, incluyendo Red Hat Enterprise Linux, CentOS, Oracle Linux y Amazon Linux. Las funciones adicionales de AEM Forms solo son compatibles con CentOS 7 y Red Hat Enterprise Linux 7.
1. AEM Assets: Consulte la sección [Compatibilidad con XMP eliminación de metadatos](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: No es compatible con Dynamic Media Imaging. Se admite el vídeo de Dynamic Media.
1. AEM Forms solo se admite en Ubuntu 16.04 LTS.
1. AEM Assets: No es compatible con la transformación de archivos [sin procesar](/help/assets/camera-raw.md)
1. AEM Forms: Sin soporte para entorno de producción
1. AEM Assets: No es compatible con el rasterizador de PDF [mejorado](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms: No admitido

### Entornos de informática virtual y en la nube {#virtual-cloud-computing-environments}

Adobe Experience Manager es compatible con la ejecución en una máquina virtual en entornos informáticos en la nube, como Microsoft Azure y Amazon Web Services (AWS), de acuerdo con los requisitos técnicos que se enumeran en esta página y según los términos de asistencia estándar de Adobe.

Adobe recomienda utilizar los servicios gestionados de Adobe para implementar AEM en Azure o AWS. Los servicios gestionados de Adobe proporcionan a los expertos experiencia y habilidades para implementar y operar AEM en estos entornos de cloud computing. Consulte nuestra documentación [adicional sobre los servicios](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t)administrados de Adobe.

En todos los demás casos de implementación de AEM en Azure o AWS, o en cualquier otro entorno de computación en nube, la compatibilidad con Adobe se contendrá en el entorno de cómputo virtual de conformidad con las especificaciones técnicas enumeradas en esta página. Cualquier problema informado relacionado con AEM que se ejecute en cualquiera de estos entornos de nube deberá ser reproducible independientemente de cualquier servicio de nube específico del entorno de cloud computing, a menos que el servicio de nube sea específicamente compatible como parte de los requisitos técnicos enumerados en esta página, por ejemplo, Azure Blob almacenamiento o AWS S3.

Para obtener recomendaciones sobre cómo implementar AEM en Azure o AWS, fuera de los servicios gestionados de Adobe, recomendamos encarecidamente trabajar directamente con el proveedor de nube o los socios de Adobe que admiten la implementación de AEM en el entorno de nube de su elección. El proveedor o socio de nube seleccionado se encargará de las especificaciones de tamaño, el diseño y la implementación de la arquitectura. Para satisfacer sus requisitos específicos de rendimiento, carga, escalabilidad y seguridad.

### Plataformas Dispatcher (Servidores Web) {#dispatcher-platforms-web-servers}

Dispatcher es el componente de almacenamiento en caché y equilibrio de carga. [Descargue la última versión](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html)de Dispatcher. Experience Manager 6.4 requiere Dispatcher versión 4.3.1 o superior.

Se admiten los siguientes servidores web para su uso con Dispatcher versión 4.3.1:

| Plataforma | Nivel de asistencia |
|---|---|
| **Apache httpd 2.4.x** (véase también 1,2 más adelante) | A: Admitido |
| Microsoft IIS 10 (Servidor de información de Internet) | A: Admitido |
| Microsoft IIS 8.5 (Servidor de información de Internet) | A: Admitido |

1. Los servidores Web creados sobre la base del código fuente httpd Apache tendrán el mismo nivel de soporte que la versión de httpd en la que se basa. En caso de duda, pida al Adobe que confirme el nivel de asistencia relacionado con el producto de servidor correspondiente. Casos siguientes:

   1. El servidor HTTP se creó utilizando únicamente las distribuciones oficiales de fuentes Apache, o
   1. El servidor HTTP se entregó como parte del sistema operativo en el que se ejecuta. Ejemplos: Servidor HTTP IBM, servidor HTTP Oracle

1. Dispatcher no está disponible para Apache 2.4.x en sistemas operativos Windows.

## Plataformas de cliente admitidas {#supported-client-platforms}

### Exploradores admitidos para la creación de la interfaz de usuario {#supported-browsers-for-authoring-user-interface}

La interfaz de usuario de Adobe Experience Manager funciona con las siguientes plataformas de cliente. Todos los exploradores se prueban con el conjunto predeterminado de complementos.

La interfaz de usuario de AEM está optimizada para pantallas más grandes (normalmente portátiles y equipos de escritorio) y factor de forma de tablet (como Apple iPad o Microsoft Surface). No se admite el factor de formulario de teléfono.

>[!NOTE]
>
>**Compatibilidad con exploradores con ciclos de versión rápidos:**
>
>Mozilla Firefox, Google Chrome y Microsoft Edge se actualizan cada pocos meses. Adobe se ha comprometido a proporcionar actualizaciones para Adobe Experience Manager a fin de mantener el nivel de asistencia que se indica a continuación con las próximas versiones de estos exploradores.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Explorador</strong></td> 
   <td><strong>Compatibilidad con la interfaz de usuario<br /> </strong></td> 
   <td><strong>Compatibilidad con la IU clásica</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox última ESR [1]</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x en macOS</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x en macOS</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x en macOS</td> 
   <td>A: Admitido</td> 
   <td>A: Admitido</td> 
  </tr> 
  <tr> 
   <td>Apple Safari en iOS 12.x</td> 
   <td>A: Admitido [2]</td> 
   <td>Z: No admitido</td> 
  </tr> 
  <tr> 
   <td>Apple Safari en iOS 11.x</td> 
   <td>A: Admitido [2]</td> 
   <td>Z: No admitido</td> 
  </tr> 
  <tr> 
   <td>Apple Safari en iOS 10.3</td> 
   <td>A: Admitido [2]</td> 
   <td>Z: No admitido</td> 
  </tr> 
 </tbody> 
</table>

1. Ampliación de la versión de soporte de Firefox [Obtenga más información sobre esto en mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. compatibilidad con Apple iPad

### Exploradores admitidos para sitios web {#supported-browsers-for-websites}

Por lo general, la compatibilidad de los navegadores con los sitios web procesados por AEM Sites depende de la implementación de plantillas de página AEM, diseño y salida de componentes, y por lo tanto controla a la parte que los implementa.

### Clientes WebDAV {#webdav-clients}

**Microsoft Windows 7+**

Para conectarse correctamente con Microsoft Windows 7+ a una instancia de AEM que no está segura con SSL, la autenticación básica a través de una red no segura debe estar habilitada en Windows. Esto requiere un cambio en el Registro de Windows de WebClient:

1. Busque la subclave del Registro:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Añada la entrada del Registro BasicAuthLevel a esta subclave con un valor de 2 o más.

Consulte [Soporte técnico de Microsoft KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Para mejorar la capacidad de respuesta del cliente WebDav en Windows, consulte Soporte técnico de [Microsoft KB 2445570](https://support.microsoft.com/kb/2445570)

## Notas adicionales de la plataforma {#additional-platform-notes}

Esta sección proporciona notas especiales e información más detallada sobre la ejecución de Adobe Experience Manager y sus complementos.

### IPv4 e IPv6 {#ipv-and-ipv}

Todos los elementos de Adobe Experience Manager (Instance, Dispatcher) se pueden instalar en redes IPv4 e IPv6.

La operación es fluida, ya que no se requiere ninguna configuración especial. Puede simplemente especificar una dirección IP con el formato adecuado para su tipo de red, si es necesario.

Esto significa que cuando se necesita especificar una dirección IP, puede seleccionar (según sea necesario) de:

* una dirección IPv6

   for example `https://[ab12::34c5:6d7:8e90:1234]:4502`

* una dirección IPv4

   for example `https://123.1.1.4:4502`

* un nombre de servidor

   for example, `https://www.yourserver.com:4502`

* el caso predeterminado de `localhost` se interpretará para las instalaciones de red IPv4 e IPv6

   for example, `http://localhost:4502`

### Requisitos para AEM Añada de Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media está deshabilitado de forma predeterminada. See [Enabling Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Con Dynamic Media habilitado, se aplican los siguientes requisitos adicionales del sistema:
>[!NOTE]
>
>Los siguientes requisitos del sistema **_solo_** se aplican si utiliza Dynamic Media - modo híbrido; Medios dinámicos: el modo híbrido tiene un servidor de imágenes incrustado, que solo está certificado en determinados sistemas operativos.
>
>Para los clientes de Dynamic Media que ejecutan Dynamic Media - modo Scene7 (es decir, modo de ejecución **dynamicmedia_scene7** ), no hay requisitos adicionales del sistema; solo los mismos requisitos del sistema que AEM. Medios dinámicos: la arquitectura del modo Scene7 utiliza el servicio de imágenes basado en la nube, no el servicio incrustado en AEM.

#### Hardware {#hardware}

Los siguientes requisitos de hardware se aplican a los sistemas operativos Linux y Windows:

* CPU Intel Xeon o AMD Opteron con al menos 4 núcleos
* 16 GB de RAM como mínimo

#### Linux {#linux}

El uso de Dynamic Media en Linux requiere los siguientes requisitos previos:

* RedHat Enterprise 7 o CentOS 7 y posterior con los parches de corrección más recientes
* Sistema operativo de 64 bits
* Intercambio deshabilitado (recomendado)
* SELinux deshabilitado (ver nota a continuación)

>[!NOTE]
>
>Si la configuración regional está configurada de manera que LC_CTYPE no sea igual a en_US.UTF-8, impedirá que los medios dinámicos funcionen. Para ver cuál es su valor, escriba &quot;locale&quot; en el símbolo del sistema. Si no se establece en eso, establezca la variable de entorno LC_CTYPE en la cadena vacía escribiendo &quot;export LC_CTYPE=&quot; antes de ejecutar AEM.

>[!NOTE]
>
>**Desactivación de SELinux:** El servicio de imágenes no funciona con SELinux activado. Esta opción está activada de forma predeterminada. Para solucionar este problema, edite el archivo **/etc/selinux/config** y cambie el valor de SELinux de:
>
>`SELINUX=enforcing` hasta  `SELINUX=disabled`

>[!NOTE]
>
>**Arquitectura NUMA:** Los sistemas con procesadores con AMD64 e Intel EM64T se suelen configurar como plataformas de arquitectura de memoria no uniforme (NUMA), lo que significa que el núcleo construye varios nodos de memoria en el momento del arranque en lugar de construir un solo nodo de memoria.
>
>La construcción de varios nodos puede resultar en agotamiento de la memoria en uno o más nodos antes de agotarse otros nodos. Cuando ocurre el agotamiento de la memoria, el núcleo puede decidir eliminar procesos (por ejemplo, el Servidor de imágenes o el Servidor de plataformas) aunque haya memoria disponible.
>
>Por lo tanto, Adobe recomienda que si está ejecutando un sistema de este tipo, desactive NUMA usando la opción **numa=off** boot para evitar que el núcleo mate estos procesos.

>[!NOTE]
>
>**El nombre de host del servidor debe ser resuelto:** Asegúrese de que el nombre de host del servidor se puede resolver en una dirección IP. Si esto no es posible, agregue el nombre de host completo y la dirección IP a **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Intercambiar espacio igual al menos al doble de la cantidad de memoria física (RAM)

Para utilizar Dynamic Media en Windows, se deben instalar los redistribuibles de Microsoft Visual Studio 2010, 2013 y 2015 para x64 y x86.

x64

* Puede encontrar el redistribuible de Microsoft Visual Studio 2010 en [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* El redistribuible de Microsoft Visual Studio 2013 se encuentra en [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Puede encontrar el redistribuible de Microsoft Visual Studio 2015 en [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* Puede encontrar el redistribuible de Microsoft Visual Studio 2010 en [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* El redistribuible de Microsoft Visual Studio 2013 se encuentra en [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Puede encontrar el redistribuible de Microsoft Visual Studio 2015 en [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x y posterior
* Solo se admite con fines de prueba y demostración

### Requisitos para AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Producto</strong></p> </th> 
   <th><p><strong>Formatos admitidos para la conversión a PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Seguimiento clásico de Acrobat 2017</a></p> </td> 
   <td><p>XPS, formatos de imagen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF y DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF y TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF y TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, TF y TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, TF y TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator solo admite versiones en inglés, francés, alemán y japonés de los sistemas operativos y las aplicaciones compatibles.
>
>Además:
>
>* PDF Generator requiere [Acrobat 2017 Classic track version 17.011.30078 o posterior](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) para realizar la conversión.
>* AEM Forms solo admite ediciones de 32 bits de software compatible.
>* Las funciones de OCR PDF (PDF con capacidad de búsqueda), Optimize PDF y Export PDF solo son compatibles con Microsoft Windows.
>* El servicio HTML2PDF está obsoleto en AIX.
>* Las conversiones de PDF Generator para OpenOffice solo son compatibles con Windows, Linux y Solaris.
>* Las funciones de OCR PDF, Optimize PDF y Export PDF solo son compatibles con Windows.
>* Una versión de Acrobat se incluye con AEM Forms para habilitar la funcionalidad de PDF Generator. Sólo se debe acceder a la versión compilada mediante programación con AEM Forms, durante el período de vigencia de la licencia de AEM Forms, para su uso con AEM Forms PDF Generator. Para obtener más información, consulte la descripción del producto de AEM Forms según su implementación ([in situ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) o [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;

>



### Requisitos para la escritura de metadatos de AEM Assets XMP {#requirements-for-aem-assets-xmp-metadata-write-back}

Se admite y activa la XMP de escritura en retorno para las plataformas y formatos de archivo siguientes:

**Sistemas operativos**

* Linux (32 bits, necesita compatibilidad con aplicaciones de 32 bits en sistemas de 64 bits). Para ver los pasos para instalar bibliotecas de cliente de 32 bits, consulte [Cómo habilitar XMP extracción y escritura en RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)de 64 bits.

* Windows Server
* Oracle Solaris
* Mac OS X (64 bits)

**Formatos de archivo**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Requirements for AEM Screens Player {#requirements-for-aem-screens-player}

La versión 3.3.x de AEM Screens Player admite los siguientes sistemas operativos:

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1 con Android System WebView versión 52+ actualizada
* Apple iOS 10.3+
* Apple macOS 10.12+
