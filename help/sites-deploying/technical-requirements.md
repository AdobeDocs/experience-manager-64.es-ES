---
title: Requisitos técnicos
seo-title: Technical Requirements
description: Una lista de las plataformas de cliente y servidor compatibles para AEM.
seo-description: A list of the supported client and server platforms for AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3294'
ht-degree: 19%

---

# Requisitos técnicos{#technical-requirements}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe es compatible con Adobe Experience Manager (AEM) en las plataformas tal como se detalla en la siguiente información de este documento.

Para cualquier problema relacionado específicamente con la plataforma en sí, póngase en contacto directamente con el proveedor de la plataforma.

>[!NOTE]
>
>Según la plataforma en la que instale AEM, podría haber diferentes conjuntos de requisitos para la administración de usuarios.

## Requisitos previos {#prerequisites}

Requisitos mínimos para instalar Adobe Experience Manager:

* Java Platform instalado, Standard Edition JDK u otro soporte [Máquinas virtuales Java](#java-virtual-machines)
* Archivo de inicio rápido del Experience Manager (JAR independiente o WAR de implementación de aplicaciones web)

### Requisitos mínimos de tamaño {#minimum-sizing-requirements}

Requisitos mínimos para ejecutar Adobe Experience Manager:

* 5 GB de espacio libre en disco en el directorio de instalación
* 2 GB de memoria

>[!NOTE]
>
>* Los casos de uso de recursos digitales necesitan más memoria base. Consulte [Implementación y mantenimiento](/help/sites-deploying/deploy.md#default-local-install) para obtener más información.
>* [Paquete de complementos de AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) requiere 15 GB de espacio temporal.
>


Consulte la [Pautas para el tamaño del hardware](/help/managing/hardware-sizing-guidelines.md) para obtener más información.

### Niveles de compatibilidad {#support-levels}

Este documento enumera las plataformas de cliente y servidor compatibles con Adobe Experience Manager. Adobe proporciona varios niveles de soporte, tanto para configuraciones recomendadas como para otras configuraciones.

### Configuraciones admitidas {#supported-configurations}

Adobe recomienda estas configuraciones y proporciona soporte completo como parte del acuerdo de mantenimiento de software estándar.

<table> 
 <tbody> 
  <tr> 
   <td>Nivel de soporte</td> 
   <td>Descripción<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>A: Compatible</strong></td> 
   <td>Adobe proporciona soporte y mantenimiento completos para esta configuración. Esta configuración está cubierta por el proceso de garantía de calidad de Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R: Compatibilidad restringida</strong></td> 
   <td>Para garantizar el éxito del proyecto de nuestros clientes, Adobe proporciona soporte completo dentro de un programa de soporte restringido, que requiere que se cumplan condiciones específicas. El soporte de nivel R requiere una solicitud formal del cliente y confirmación por parte del Adobe. Para obtener más información, póngase en contacto con el Servicio de atención al cliente de Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configuraciones no admitidas {#unsupported-configurations}

| Nivel de soporte | Descripción |
|---|---|
| **Z: No compatible** | La configuración no es compatible. Adobe no realiza ninguna declaración sobre si la configuración funciona o no y no la admite. |

## Plataformas compatibles {#supported-platforms}

### Máquinas virtuales Java {#java-virtual-machines}

La aplicación requiere una máquina virtual Java para ejecutarse, que proporciona la distribución Java Development Kit (JDK) .

Adobe Experience Manager funciona con las siguientes versiones de las máquinas virtuales Java:

>[!CAUTION]
>
>Se recomienda realizar un seguimiento de los boletines de seguridad del proveedor de Java para garantizar la seguridad de los entornos de producción e instalar las últimas actualizaciones de Java.

<table> 
 <tbody> 
  <tr> 
   <td>Plataforma</td> 
   <td>Nivel de soporte<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z: No compatible </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z: No compatible </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z: No compatible</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK - 64 bits</strong></td> 
   <td>A: Admitido [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM: versión 2.9, JRE 1.8.0 [2]</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM: versión 2.8, JRE 1.8.0 [2]</td> 
   <td>A: Compatible</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle se ha trasladado a un modelo de &quot;compatibilidad a largo plazo&quot; (LTS) para los productos Oracle Java SE. Java 9 y 10 son versiones no LTS por Oracle (consulte [Plan de soporte de Oracle Java SE](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe solo proporcionará soporte para las versiones LTS de Java para ejecutar AEM en producción.

1. IBM JRE solo es compatible con el servidor de aplicaciones WebSphere.
1. El soporte técnico y la distribución del Oracle Java SE JDK, incluidas todas las actualizaciones de mantenimiento de las versiones LTS más allá del final de las actualizaciones públicas, serán compatibles directamente con el Adobe para todos los clientes AEM que utilicen la tecnología Oracle Java SE. Consulte la [Compatibilidad de Oracle Java con Preguntas y respuestas de Adobe Experience Manager](assets/adobe-oracle-java-license-agreement.pdf) para obtener más información.

### Almacenamiento y persistencia {#storage-persistence}

Existen varias opciones para implementar el repositorio de Adobe Experience Manager. Consulte la siguiente lista para ver las tecnologías compatibles y las opciones de almacenamiento.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plataforma</strong></td> 
   <td><strong>Descripción</strong></td> 
   <td><strong>Nivel de soporte</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Sistema de archivos con archivos TAR [1]</strong></td> 
   <td>Repositorio</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td><strong>Sistema de archivos con almacén de datos [1]</strong></td> 
   <td>Binarios</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Almacenar binarios en archivos TAR en el sistema de archivos [1]</td> 
   <td>Binarios</td> 
   <td>Z: No compatible con la producción</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binarios</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Almacenamiento del Blob de Microsoft Azure</td> 
   <td>Binarios</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>Repositorio</td> 
   <td>A: Compatible con limitaciones</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>Repositorio</td> 
   <td>A: Compatible con limitaciones</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Base de datos de Forms</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Base de datos de Forms</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Base de datos de repositorio y Forms</td> 
   <td>R: Compatibilidad restringida (4)</td> 
  </tr> 
  <tr> 
   <td>Base de datos de oracle 12c (12.1.x)</td> 
   <td>Base de datos de repositorio y Forms</td> 
   <td>R: Compatibilidad restringida</td> 
  </tr> 
  <tr> 
   <td>Servidor Microsoft SQL 2017</td> 
   <td>Base de datos de Forms</td> 
   <td>Z: No compatible (4)</td> 
  </tr> 
  <tr> 
   <td>Servidor Microsoft SQL 2016</td> 
   <td>Base de datos de Forms</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Servidor Microsoft SQL 2014</td> 
   <td>Base de datos de Forms</td> 
   <td>R: Compatibilidad restringida (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (integrado de Quickstart)</strong></td> 
   <td>Servicio de búsqueda</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Servicio de búsqueda</td> 
   <td>A: Compatible</td> 
  </tr> 
 </tbody> 
</table>

1. “File System” incluye almacenamiento en bloque compatible con POSIX. Esto incluye la tecnología de almacenamiento en red. Tenga en cuenta que el rendimiento del sistema de archivos puede variar e influir en el rendimiento general. Se recomienda cargar AEM de prueba en combinación con el sistema de archivos de red/remoto.
1. El uso compartido de MongoDB no es compatible con AEM.
1. Sólo se admite el motor de almacenamiento MongoDB WiredTiger.
1. No es compatible con AEM Forms.
1. MongoDB Enterprise 3.6 es compatible a partir de AEM versión 6.4.2.0.
1. El soporte para MongoDB 3.4 ha llegado al fin de su vida útil (EOL), mientras que se espera que MongoDB 3.6 alcance el 30 de abril de 2021. Tenga en cuenta que el Adobe solo proporcionará soporte para AEM problemas relacionados con el producto a partir de ahora.

>[!NOTE]
>
>Consulte [Implementación de comunidades](/help/communities/deploy-communities.md) para obtener información adicional sobre la capacidad de AEM Communities.

>[!NOTE]
>
>MongoDB es software de terceros y no está incluido en el paquete de licencias de AEM. Para obtener más información, consulte la página [Directiva de licencias de MongoDB](https://www.mongodb.org/about/licensing/).
>
>Para aprovechar al máximo su implementación de AEM con MongoDB, Adobe recomienda licenciar la versión de MongoDB Enterprise para beneficiarse del soporte profesional. Consulte [Implementaciones recomendadas](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) para obtener más información.
>
>La licencia incluye un conjunto de réplicas estándar, que consta de una instancia principal y dos instancias secundarias que pueden utilizarse para el autor o para las implementaciones de publicación.
>
>En caso de que desee ejecutar el autor y publicar en MongoDB, se deben adquirir dos licencias independientes.
>
>El Servicio de atención al cliente de Adobe ayudará a calificar los problemas relacionados con el uso de MongoDB con AEM.
>
>Para obtener más información, consulte la [Página MongoDB para Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Las bases de datos relacionales compatibles que se enumeran anteriormente son software de terceros y no se incluyen en el paquete de licencias de AEM.
>
>Para ejecutar AEM 6.4 con una base de datos relacional admitida, se requiere un contrato de soporte independiente con un proveedor de base de datos. El Servicio de atención al cliente de Adobe ayudará a calificar los problemas relacionados con el uso de bases de datos relacionales con AEM 6.4.
>
>**Tenga en cuenta que actualmente la mayoría de las bases de datos relacionales son compatibles con Level-R en la AEM 6.4, que incluye criterios de soporte y un programa de soporte como se indica en la descripción de Level-R anterior.**

### Motores Servlet / Servidores de aplicaciones {#servlet-engines-application-servers}

Adobe Experience Manager puede ejecutarse como servidor independiente (el archivo JAR de inicio rápido) o como aplicación web dentro de un servidor de aplicaciones de terceros (el archivo WAR).

La versión mínima de la API de servlet requerida es Servlet 3.1, pero inferior a Servlet 4.0.

| Plataforma | Nivel de soporte |
|---|---|
| **Motor Servlet integrado de inicio rápido (Jetty 9.3)** | A: Compatible |
| Oracle WebLogic Server 12.2 (12cR2) | A: Compatible |
| Entrega continua del servidor de aplicaciones IBM WebSphere (LibertyProfile) con perfil web 7.0 y IBM JRE 1.8 | A: Compatible |
| IBM WebSphere Application Server 9.0 | A: Compatible |
| Apache Tomcat 8.5.x | A: Compatible |
| JBoss EAP 7.1.0 con servidor de aplicaciones JBoss | A: Admitido (1) |
| JBoss EAP 7.0.0 con el servidor de aplicaciones JBoss | A: Compatible |

1. No es compatible con AEM Forms.

### Sistemas operativos del servidor {#server-operating-systems}

Adobe Experience Manager funciona con las siguientes plataformas de servidor:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plataforma</strong></td> 
   <td><strong>Nivel de soporte</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, basado en la distribución de Red Hat</strong></td> 
   <td>A: Admitido (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, basado en la distribución de Debian incl. Ubuntu</td> 
   <td>A: Admitido (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, basado en la distribución SUSE</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A: Admitido con limitaciones (3,5,7)<br /> R: Compatibilidad restringida para nuevos contratos</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A: Admitido con limitaciones (2,5,7)<br /> R: Compatibilidad restringida para nuevos contratos</td> 
  </tr> 
 </tbody> 
</table>

1. Linux Kernel 2.6, 3.x y 4.x incluye derivados de la distribución de Red Hat, incluyendo Red Hat Enterprise Linux, CentOS, Oracle Linux y Amazon Linux. Las funciones de complementos de AEM Forms solo son compatibles con CentOS 7 y Red Hat Enterprise Linux 7.
1. AEM Assets: Consulte la sección [Compatibilidad con la reescritura de metadatos XMP](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets: No es compatible con Dynamic Media Imaging. Dynamic Media Video es compatible.
1. AEM Forms solo es compatible con Ubuntu 16.04 LTS.
1. AEM Assets: No hay compatibilidad con [Transformación de archivos sin procesar](/help/assets/camera-raw.md)
1. AEM Forms: No hay soporte para el entorno de producción
1. AEM Assets: No hay compatibilidad con [PDF Rasterizador mejorado](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms: No admitido

### Entornos de computación virtual y en la nube {#virtual-cloud-computing-environments}

Adobe Experience Manager es compatible con la ejecución en una máquina virtual en entornos de computación en la nube, como Microsoft Azure y Amazon Web Service (AWS), de acuerdo con los requisitos técnicos enumerados en esta página y según los términos de asistencia estándar de Adobe.

Adobe recomienda utilizar Adobe Managed Services para implementar AEM en Azure o AWS. Adobe Managed Services proporciona a los expertos experiencia y habilidades para implementar y operar AEM en estos entornos de computación en la nube. Consulte nuestra [documentación adicional sobre Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

En todos los demás casos de implementación de AEM en Azure o AWS, o en cualquier otro entorno de computación en nube, la compatibilidad con Adobe se contendrá en el entorno de computación virtual de acuerdo con las especificaciones técnicas enumeradas en esta página. Cualquier problema informado relativo a AEM que se ejecute en cualquiera de estos entornos de nube tendrá que ser reproducible de forma independiente de cualquier servicio de nube específico para el entorno de computación en nube, a menos que el servicio de nube sea compatible específicamente como parte de los requisitos técnicos enumerados en esta página, por ejemplo, almacenamiento Azure Blob o AWS S3.

Para obtener recomendaciones sobre cómo implementar AEM en Azure o AWS, fuera de Adobe Managed Services, le recomendamos encarecidamente que trabaje directamente con el proveedor de nube o los socios de Adobe que admitan la implementación de AEM en el entorno de nube que elija. El proveedor o socio de nube seleccionado será responsable de las especificaciones de tamaño, el diseño y la implementación de la arquitectura, para satisfacer sus requisitos específicos de rendimiento, carga, escalabilidad y seguridad.

### Plataformas de Dispatcher (servidores web) {#dispatcher-platforms-web-servers}

Dispatcher es el componente de almacenamiento en caché y equilibrio de carga. [Descargar la última versión de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Experience Manager 6.4 requiere la versión 4.3.1 o superior de Dispatcher.

Los siguientes servidores web son compatibles para su uso con Dispatcher versión 4.3.1:

| Plataforma | Nivel de soporte |
|---|---|
| **Apache httpd 2.4.x** (véase también 1,2 infra) | A: Compatible |
| Microsoft IIS 10 (Servidor de información de Internet) | A: Compatible |
| Microsoft IIS 8.5 (Servidor de información de Internet) | A: Compatible |

1. Los servidores web creados sobre la base del código fuente httpd de Apache tendrán el mismo nivel de compatibilidad que la versión de httpd en la que se basa. En caso de duda, pida al Adobe que confirme el nivel de asistencia relacionado con el producto del servidor correspondiente. Los siguientes casos:

   1. El servidor HTTP se creó utilizando solamente las distribuciones de fuentes oficiales de Apache, o
   1. El servidor HTTP se entregó como parte del sistema operativo en el que se está ejecutando. Ejemplos: Servidor HTTP de IBM, servidor HTTP de Oracle

1. Dispatcher no está disponible para Apache 2.4.x para sistemas operativos Windows.

## Plataformas de cliente compatibles {#supported-client-platforms}

### Exploradores admitidos para la creación de la interfaz de usuario {#supported-browsers-for-authoring-user-interface}

La interfaz de usuario de Adobe Experience Manager funciona con las siguientes plataformas de cliente. Todos los exploradores se prueban con el conjunto predeterminado de complementos.

La interfaz de usuario de AEM está optimizada para pantallas más grandes (normalmente portátiles y equipos de escritorio) y factor de forma de tableta (como Apple iPad o Microsoft Surface). No se admite el factor de formulario telefónico.

>[!NOTE]
>
>**Compatibilidad con exploradores con ciclos de versiones rápidos:**
>
>Mozilla Firefox, Google Chrome y Microsoft Edge se actualizan cada pocos meses. Adobe se compromete a proporcionar actualizaciones para Adobe Experience Manager para mantener el nivel de asistencia que se indica a continuación con las próximas versiones de estos navegadores.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Explorador</strong></td> 
   <td><strong>Compatibilidad con la interfaz de usuario<br /> </strong></td> 
   <td><strong>Compatibilidad con la IU clásica</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox último ESR [1]</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x en macOS</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x en macOS</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x en macOS</td> 
   <td>A: Compatible</td> 
   <td>A: Compatible</td> 
  </tr> 
  <tr> 
   <td>Apple Safari en iOS 12.x</td> 
   <td>A: Admitido [2]</td> 
   <td>Z: No compatible</td> 
  </tr> 
  <tr> 
   <td>Apple Safari en iOS 11.x</td> 
   <td>A: Admitido [2]</td> 
   <td>Z: No compatible</td> 
  </tr> 
  <tr> 
   <td>Apple Safari en iOS 10.3</td> 
   <td>A: Admitido [2]</td> 
   <td>Z: No compatible</td> 
  </tr> 
 </tbody> 
</table>

1. Versión ampliada de soporte de Firefox [Más información sobre esto en mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. compatibilidad con Apple iPad

### Exploradores admitidos para sitios web {#supported-browsers-for-websites}

Por lo general, la compatibilidad del explorador con los sitios web procesados por AEM Sites depende de la implementación de AEM plantillas de página, el diseño y la salida de componentes, y por lo tanto controla a la parte que implementa estas partes.

### Clientes de WebDAV {#webdav-clients}

**Microsoft Windows 7+**

Para conectarse correctamente con Microsoft Windows 7+ a una instancia de AEM que no esté segura con SSL, la autenticación básica sobre una red no segura debe estar habilitada en Windows. Esto requiere un cambio en el Registro de Windows de WebClient:

1. Busque la subclave del Registro:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Agregue la entrada de registro BasicAuthLevel a esta subclave con un valor de 2 o más.

Consulte [Compatibilidad con Microsoft KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Para mejorar la capacidad de respuesta del cliente WebDav en Windows, consulte [Compatibilidad con Microsoft KB 2445570](https://support.microsoft.com/kb/2445570)

## Notas adicionales de la plataforma {#additional-platform-notes}

Esta sección proporciona notas especiales e información más detallada sobre la ejecución de Adobe Experience Manager y sus complementos.

### IPv4 e IPv6 {#ipv-and-ipv}

Todos los elementos de Adobe Experience Manager (instancia, Dispatcher) se pueden instalar en redes IPv4 e IPv6.

La operación es perfecta, ya que no se requiere ninguna configuración especial. Puede simplemente especificar una dirección IP con el formato apropiado para su tipo de red, si es necesario.

Esto significa que, cuando se debe especificar una dirección IP, se puede seleccionar (según sea necesario) de:

* una dirección IPv6

   por ejemplo `https://[ab12::34c5:6d7:8e90:1234]:4502`

* una dirección IPv4

   por ejemplo `https://123.1.1.4:4502`

* un nombre de servidor

   por ejemplo, `https://www.yourserver.com:4502`

* el caso predeterminado de `localhost` se interpretará para las instalaciones de red IPv4 e IPv6

   por ejemplo, `http://localhost:4502`

### Requisitos para AEM complemento de Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media está desactivado de forma predeterminada. Consulte [Habilitación de Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Con Dynamic Media habilitado, se aplican los siguientes requisitos adicionales del sistema:
>[!NOTE]
>
>Se aplican los siguientes requisitos del sistema **_only_** si utiliza Dynamic Media - Modo híbrido; Dynamic Media - El modo híbrido tiene un servidor de imágenes integrado, que solo está certificado en determinados sistemas operativos.
>
>Para los clientes de Dynamic Media que ejecutan Dynamic Media: modo Scene7 (es decir, **dynamic_media_scene7** runmode), no hay requisitos adicionales del sistema; solo los mismos requisitos del sistema que AEM. Dynamic Media: la arquitectura del modo Scene7 utiliza el servicio de imagen basado en la nube, no el servicio incrustado en AEM.

#### Hardware {#hardware}

Los siguientes requisitos de hardware se aplican a los sistemas operativos Linux y Windows:

* CPU Intel Xeon o AMD Opteron con al menos 4 núcleos
* 16 GB de RAM como mínimo

#### Linux {#linux}

El uso de Dynamic Media en Linux requiere los siguientes requisitos previos:

* RedHat Enterprise 7 o CentOS 7 y posteriores con los parches de correcciones más recientes
* Sistema operativo de 64 bits
* Intercambio desactivado (recomendado)
* SELinux deshabilitado (ver nota a continuación)

>[!NOTE]
>
>Si la configuración regional está configurada de tal modo que LC_CTYPE no sea igual a en_US.UTF-8, evitará que los medios dinámicos funcionen. Para ver cuál es su valor, escriba &quot;locale&quot; en el símbolo del sistema. Si no se establece en eso, entonces establezca la variable de entorno LC_CTYPE en la cadena vacía escribiendo &quot;export LC_CTYPE=&quot; antes de ejecutar AEM.

>[!NOTE]
>
>**Desactivación de SELinux:** Image Serving no funciona con SELinux activado. Esta opción está activada de forma predeterminada. Para solucionar este problema, edite la **/etc/selinux/config** y cambie el valor SELinux de:
>
>`SELINUX=enforcing` hasta  `SELINUX=disabled`

>[!NOTE]
>
>**Arquitectura NUMA:** Los sistemas con procesadores AMD64 e Intel EM64T suelen configurarse como plataformas de arquitectura de memoria no uniforme (NUMA), lo que significa que el núcleo construye varios nodos de memoria en el momento del inicio en lugar de construir un solo nodo de memoria.
>
>La construcción de varios nodos puede provocar el agotamiento de la memoria en uno o varios nodos antes de que otros se agoten. Cuando ocurre el agotamiento de la memoria, el núcleo puede decidir matar procesos (por ejemplo, Image Server o Platform Server) aunque haya memoria disponible.
>
>Por lo tanto, Adobe recomienda que, si está ejecutando un sistema de este tipo, desactive NUMA mediante el **numa=off** para evitar que el núcleo mate estos procesos.

>[!NOTE]
>
>**El nombre del host del servidor debe ser resoluble:** Asegúrese de que el nombre de host del servidor se puede resolver en una dirección IP. Si no es posible, añada el nombre de host completo y la dirección IP a **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Intercambiar espacio igual a al menos el doble de la memoria física (RAM)

Para usar Dynamic Media en Windows, Microsoft Visual Studio 2010, 2013 y 2015 es necesario instalar los redistribuibles para x64 y x86.

x64

* La redistribución de Microsoft Visual Studio 2010 se puede encontrar en [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/en-us/download/details.aspx?id=13523)
* La redistribución de Microsoft Visual Studio 2013 se puede encontrar en [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* La redistribución de Microsoft Visual Studio 2015 se puede encontrar en [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

x86

* La redistribución de Microsoft Visual Studio 2010 se puede encontrar en [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* La redistribución de Microsoft Visual Studio 2013 se puede encontrar en [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* La redistribución de Microsoft Visual Studio 2015 se puede encontrar en [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x y posteriores
* Solo se admite con fines de prueba y demostración

### Requisitos del Generador de PDF de AEM Forms {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Producto</strong></p> </th> 
   <th><p><strong>Formatos compatibles para la conversión a PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/es/acrobat/release-note/release-notes-acrobat-reader.html">Seguimiento clásico de Acrobat 2017</a></p> </td> 
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
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF y TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formatos de imagen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF y TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>El generador de PDF solo admite versiones en alemán, francés, inglés y japonés de los sistemas operativos y aplicaciones compatibles.
>
>Además:
>
>* PDF Generator requiere [Acrobat 2017 Classic track versión 17.011.30078 o posterior](https://helpx.adobe.com/es/acrobat/release-note/release-notes-acrobat-reader.html) para realizar la conversión.
>* AEM Forms solo admite ediciones de 32 bits de software compatible.
>* Las características PDF OCR (PDF de búsqueda), Optimize PDF y Export PDF solo son compatibles con Microsoft Windows.
>* El servicio HTML2PDF está obsoleto en AIX.
>* Las conversiones de PDF Generator para OpenOffice solo son compatibles con Windows, Linux y Solaris.
>* Las características de PDF, Optimizar PDF y Exportar PDF de OCR solo son compatibles con Windows.
>* Una versión de Acrobat se incluye con AEM Forms para habilitar la funcionalidad Generador de PDF. Solo se debe acceder a la versión agrupada mediante programación con AEM Forms, durante el período de licencia de AEM Forms, para usarlo con el generador de PDF de AEM Forms. Para obtener más información, consulte la descripción del producto de AEM Forms según la implementación ([On-Premise](https://helpx.adobe.com/es/legal/product-descriptions/adobe-experience-manager-on-premise.html) o [Managed Services](https://helpx.adobe.com/es/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>


### Requisitos de AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2012 Server R2, Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10
* Procesador de 1 GHz o más rápido con soporte para PAE, NX y SSE2.
* 1 GB de RAM para 32 bits o 2 GB de RAM para SO de 64 bits;
* 16 GB de espacio en disco para 32 bits o 20 GB de espacio en disco para el sistema operativo de 64 bits
* Memoria gráfica: 128 MB de GPU (se recomiendan 256 MB);
* 2,35 GB de espacio disponible en disco duro;
* 1024 X 768 píxeles de resolución de monitor o superior;
* Aceleración de hardware de vídeo (opcional);
* Acrobat Pro DC, Acrobat Standard DC o Adobe Acrobat Reader DC
* Privilegios administrativos para instalar Designer

### Requisitos para la reescritura de metadatos de AEM Assets XMP {#requirements-for-aem-assets-xmp-metadata-write-back}

XMP reescritura es compatible y está habilitada para las siguientes plataformas y formatos de archivo:

**Sistemas operativos**

* Linux (32 bits, necesita soporte de aplicaciones de 32 bits en sistemas de 64 bits). Para ver los pasos para instalar bibliotecas de cliente de 32 bits, consulte [Cómo habilitar la extracción y escritura de XMP en RedHat Linux de 64 bits](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

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

### Requisitos de AEM Screens Player {#requirements-for-aem-screens-player}

La versión 3.3.x de AEM Screens Player admite los siguientes sistemas operativos:

* Microsoft Windows 10 Enterprise LTSB
* Google Chome OS 62+
* Google Android 5.1.1 con Android System WebView versión 52 o posterior actualizado
* Apple iOS 10.3+
* Apple macOS 10.12+
