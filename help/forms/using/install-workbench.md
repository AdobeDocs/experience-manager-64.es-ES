---
title: Instalar área de trabajo
seo-title: Instalar área de trabajo
description: Instale el área de trabajo.
uuid: null
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: null
translation-type: tm+mt
source-git-commit: 19dcda357b34e7160792d43cb9335fc3be0dedbc
workflow-type: tm+mt
source-wordcount: '2745'
ht-degree: 0%

---


# Instalar área de trabajo {#install-workbench}

Este documento proporciona instrucciones para instalar y configurar el área de trabajo. El programa de instalación también instala Designer.

## Acerca de {#about}

Este documento está dirigido a administradores o desarrolladores responsables de la instalación, configuración, administración o implementación de Workbench.
También se incluye la información necesaria para configurar el sistema para que admita los procesos actualizados de Adobe® AEM forms® Enterprise Suite (ES) Update 1 (8.2.x) y Adobe® AEM forms® Enterprise Suite 2 (ES2).
La información proporcionada se basa en el supuesto de que cualquiera que lea este documento está familiarizado con el sistema operativo Microsoft® Windows®.

## Información adicional {#additional-information}

Los recursos de esta tabla pueden ayudarle a obtener más información y a empezar a utilizar AEM Forms.
<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Para obtener información acerca de</strong></p> </td> 
   <td><p><strong>Consulte</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Información de procedimiento para Workbench</p> </td> 
   <td><p><a href="http://www.adobe.com/go/learn_aemforms_workbench_61">Ayuda de Workbench</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Información general sobre AEM Forms y cómo se integra con otros productos de Adobe</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Información general de AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Un tutorial para crear una aplicación de AEM Forms y probarla en el espacio de trabajo</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_firstapp_ds_65">Creación de la primera aplicación de AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Toda la documentación disponible para AEM Forms</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Documentación de AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Otros servicios y productos que se integran con AEM Forms</p> </td> 
   <td><p><a href="http://www.adobe.com/es/">www.adobe.com</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Actualizaciones de parches, notas técnicas e información adicional sobre esta versión de producto</p> </td> 
   <td><p><a href="https://www.adobe.com/account/sign-in.supportportal.html">Póngase en contacto con el servicio de asistencia para empresas de Adobe</a><br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Flex Workspace está obsoleto para AEM Forms. Está disponible para la versión de AEM Forms.

## Antes de instalar {#before-you-install}

### Información general sobre la instalación de Workbench {#workbench-installation-overview}

Workbench es un entorno de desarrollo integrado (IDE) que utilizan los desarrolladores y los autores de formularios para crear formularios y procesos empresariales automatizados. También se utiliza para administrar los recursos y servicios que utilizan los procesos y formularios.

En la ilustración siguiente se muestra la instalación de Workbench, que incluye:
* Diseño de procesos con Workbench
* Diseño de formularios con Designer

>[!NOTE]
>
>El servidor de AEM Forms requiere un programa de instalación independiente. Para obtener más información, consulte la documentación de instalación de AEM Forms en JEE.

## Requisitos previos del sistema {#system-prerequisites}

Esta sección describe los requisitos de hardware y software y las plataformas admitidas.

### Requisitos mínimos de hardware y software {#minimum-hardware-software-requirements}

**Área de**
trabajoSe recomiendan como mínimo los siguientes requisitos: Espacio en disco para la instalación:
* 680 MB solo para Workbench.
* 2,15 GB en una sola unidad para una instalación completa de Workbench, Designer y el conjunto de muestras.
* 400 MB para directorios de instalación temporales: 200 MB en el directorio \temp del usuario y 200 MB en el directorio temporal de Windows.

>[!NOTE]
>
>Si todas estas ubicaciones residen en una sola unidad, debe haber 1,5 GB de espacio disponible durante la instalación. Los archivos copiados en los directorios temporales se eliminan al finalizar la instalación.

* Requisitos de hardware: Procesador Intel® Pentium® 4 o AMD equivalente, 1 GHz.
* Descargue e instale la versión más reciente de Adobe AIR (de <a href="http://www.adobe.com/">www.adobe.com</a>) necesaria para el cliente de ayuda de comunidad, integrado con Workbench.
* Java™ Runtime Entorno (JRE) 6.0 actualización 22 o posterior se actualiza a 6.0 *Nuevo para 10*.
* Resolución mínima de pantalla de 1024 X 768 píxeles o buena resolución de pantalla con color de 16 bits o superior.
* Conexión de red TCP/IPv4 o TCP/IPv6 al servidor de AEM Forms.
* Instale los paquetes de tiempo de ejecución redistribuibles de Visual C++ 2012 de 32 bits.
* Instale los paquetes de tiempo de ejecución redistribuibles de Visual C++ 2013 de 32 bits.

>[!NOTE]
>
>Si tiene Adobe® Acrobat® X instalado en el equipo, asegúrese de desinstalarlo antes de instalar Workbench. Puede volver a instalar Acrobat después de instalar Workbench.

>[!NOTE]
>
>Debe tener privilegios de administrador para instalar Workbench. Si va a realizar la instalación con una cuenta que no sea de administrador, el programa de instalación le pedirá las credenciales de una cuenta adecuada.

### Plataformas compatibles {#supported-platforms}

Consulte la lista completa de plataformas admitidas para Workbench en [Plataformas admitidas por AEM Forms](http://adobe.com/go/learn_aemforms_supportedplatforms_65).

## Consideraciones de instalación de Designer {#designer-installation-considerations}

De forma predeterminada, la instalación de Workbench incluye una versión correspondiente solo en inglés de Designer. Si la aplicación de instalación de Workbench detecta una versión existente de Designer en el equipo, la instalación puede finalizar y se le solicitará que elimine la versión actual de Designer antes de poder continuar.
La tabla siguiente contiene una lista completa de los posibles escenarios de instalación de Designer que puede encontrar, así como de las acciones que debe realizar al instalar Workbench.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Versión de Designer instalada actualmente</strong></p> </td> 
   <td><p><strong>Acciones necesarias</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Pro o Acrobat Pro Extended (incluye Designer)</p> </td> 
   <td><p>Ninguna. La instalación de Workbench detecta una instancia de Designer en el equipo que se instaló con Acrobat Pro o Acrobat Pro Extended.
Las distintas versiones de Designer pueden coexistir en el mismo sistema, por ejemplo, Designer 8.2.x y 9.0.x. No es necesario desinstalar la versión de Designer instalada con Acrobat 10 Pro o Acrobat 10 Pro Extended.
<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Designer (independiente)</p> </td> 
   <td><p>Ninguna. La versión de Designer incluida con Workbench solo está disponible en inglés. El instalador de Workbench no reinstalará una nueva versión de Designer. En su lugar, se realizará una revisión de una versión actualizada, incluida con el instalador de Workbench. Esto también le permite utilizar la versión localizada de Designer en Workbench.<br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

### Para desinstalar Designer (independiente) {#uninstall-designer-standalone}

1. Vaya a **Panel de control de Campaign > Programas > Programas y características**
1. En la lista programas instalados actualmente, seleccione **Diseñador de Adobes**.
1. Haga clic en **Desinstalar** y luego haga clic en **Sí**.

### Para desinstalar Designer (independiente) en Windows 10 {#uninstall-designer-standalone-windows10}

1. Vaya a **Panel de control de Campaign > Programas > Programas y características**
1. En la lista programas instalados actualmente, seleccione **Diseñador de Adobes**.
1. Haga clic en **Desinstalar** y luego haga clic en **Sí**.

### Para desinstalar Designer incluido con Acrobat Pro o Acrobat Pro Extended {#uninstall-designer-included-with-acrobatpro-or-acrobatextended}

1. Vaya a **Panel de control de Campaign > Programas > Programas y características**
1. En la lista programas instalados actualmente, seleccione **Adobe Acrobat Pro** o **Adobe Acrobat Pro Extended**.
1. Haga clic en **Cambiar** y, a continuación, haga clic en **Siguiente**.
1. Seleccione **Modificar** y haga clic en **Siguiente**.
1. Seleccione **Diseñador de Adobe**, seleccione **Esta función no estará disponible** y haga clic en **Siguiente**
1. Haga clic en **Actualizar** y luego haga clic en **Finalizar**

### Para desinstalar Designer incluido con Acrobat Pro o Acrobat Pro Extended en Windows 10 {#uninstall-designer-included-with-acrobatpro-or-acrobatextended-windows10}

1. Vaya a **Panel de control de Campaign > Programas > Programas y características**
1. En la lista programas instalados actualmente, seleccione **Adobe Acrobat Pro** o **Adobe Acrobat Pro Extended**.
1. Haga clic en **Cambiar** y, a continuación, haga clic en **Siguiente**.
1. Seleccione **Modificar** y haga clic en **Siguiente**.
1. Seleccione **Diseñador de Adobe**, seleccione **Esta función no estará disponible** y haga clic en **Siguiente**
1. Haga clic en **Actualizar** y luego haga clic en **Finalizar**

## Instalación de Workbench {#installing-workbench}

En este capítulo se describe cómo instalar Workbench.

### Instalación y ejecución de Workbench {#installing-and-running-workbench}

Antes de instalar Workbench, debe asegurarse de que el entorno incluye el software y el hardware necesarios para ejecutarlo (consulte la sección: **Antes de instalar**).

**Para instalar y ejecutar Workbench:**

1. Realice una de estas tareas:
   * Vaya al directorio \Workbench del medio de instalación y doble haga clic en el archivo run_windows_installer.bat.
   * Descargue y descomprima Workbench en el sistema de archivos. Después de descargarlo, vaya al directorio \Workbench y haga clic en el doble run_windows_installer.bat.

   >[!IMPORTANT]
   >
   >El programa de instalación de Workbench solo se ejecuta desde un DVD o una unidad local. No se puede ejecutar desde un sitio remoto.

   >[!NOTE]
   >
   >Si aparece un error &quot;No se pudo crear la máquina virtual Java&quot;, cree una variable de entorno denominada _JAVA_OPTIONS con el valor -Xmx512M y ejecute el programa de instalación.

1. En la pantalla Introducción, haga clic en Siguiente.
1. Lea el contrato de licencia del producto, seleccione Acepto los términos del contrato de licencia y haga clic en Siguiente.
1. (Opcional) Seleccione Instalar Adobe Designer si necesita esta herramienta para crear y modificar formularios.

   >[!NOTE]
   >
   >Puede seguir utilizando Designer instalado con Acrobat 10 si deja esta opción sin seleccionar.

1. Acepte el directorio predeterminado como se muestra o   haga clic en Elegir y vaya al directorio en el que va a instalar Workbench y, a continuación, haga clic en Siguiente.

   >[!NOTE]
   >
   >La ruta del directorio de instalación no debe contener los caracteres # (libras) y $ (dólares).

1. Revise el resumen de la preinstalación y haga clic en Instalar. El programa de instalación muestra el progreso de la instalación.
1. Revise el resumen de la instalación. Seleccione Inicio AEM Forms Workbench para iniciar Workbench y haga clic en Siguiente.
1. Revise las Notas de la versión y haga clic en Finalizado.
1. Los siguientes elementos ya están instalados en el equipo:
   * **Workbench**: Para ejecutar Workbench desde el menú Inicio, seleccione Todos los Programas > AEM Forms > Workbench si elige almacenar la carpeta de acceso directo allí. Para obtener información,   consulte la documentación Uso de Workbench.
   * **Designer**: Puede acceder a Designer desde Workbench. Para obtener más información, consulte el tema Introducción en la Ayuda de Designer.
   * **Complemento** de Workbench: Siga las instrucciones de &quot;3.3 Instalación de la función Eclipse de Workbench&quot; en la página 6.
   * **SDK** de AEM Forms: Para obtener más información sobre el uso del SDK, consulte  <a href="http://www.adobe.com/go/learn_lc_programming_10">Programación con AEM Forms</a>.

## Actualizando procesos {#upgrading-processes}

Los procesos de AEM Forms Update 1 y LiveCycle ES2 se pueden actualizar a aplicaciones de AEM Forms mediante el Asistente para actualización. Consulte Actualización de la documentación de artefactos heredados en la Ayuda de Workbench para obtener más información.

### Instalación de la función Eclipse de Workbench {#installing-workbench-eclipse-feature}

Si lo desea, puede agregar la función Área de trabajo a Eclipse. Puede agregar Workbench después de instalar Workbench. Por ejemplo, para JBoss, la siguiente ubicación contiene el archivo:

* Workbench_DVD/adicional/eclipse
Descargue e instale Eclipse 3.6 desde <a href="https://www.eclipse.org/downloads/">www.eclipse.org/downloads</a>.

### Configuración de la función de actualización de Eclipse para Workbench {#configuring-eclipse-update-feature-for-workbench}

Workbench admite la función de actualización para asegurarse de que utiliza la versión Eclipse más actualizada. Sin embargo, debe asegurarse de que se incluyen determinados módulos adicionales en cada descarga:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Versión de Eclipse</strong></p> </td> 
   <td><p><strong>Módulos requeridos por Workbench</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Eclipse 3.6.x</p> </td> 
   <td><p>

* Marco de edición gráfica FMAM [org.eclipse.gef.feature.group]: Esto se encuentra en el &#39;SDK de marco de modelado gráfico&#39; [org.eclipse.gmf.sdk.feature.group]

* WST XML Core [org.eclipse.wst.xml_core.feature.feature.group]: Esto se encuentra en &quot;Eclipse XML Editors and Tools&quot; [org.eclipse.wst.xml_ui.feature.feature.group]

* Complemento &#39;org.apache.commons.lang_2.3.0&#39; [n/a]: Esto se encuentra en la &quot;Lista de Tarea de Mylyn (obligatoria)&quot; [org.eclipse.mylyn_feature.feature.group]

   </p> </td> 
  </tbody>
  </table>

**Para instalar e implementar la función Workbench en Eclipse**:
1. Eclipse de inicio.
1. Seleccione Ayuda > Instalar nuevo software, haga clic en Añadir para abrir el cuadro de diálogo Añadir repositorio.
1. En el cuadro de diálogo Añadir repositorio, haga clic en Local y busque el directorio en el que la instalación de Workbench guardó el archivo ZIP del complemento, seleccione Workbench-updatesite.zip y, a continuación, haga clic en Abrir.
1. Siga las instrucciones de las pantallas subsiguientes para implementar la función Área de trabajo en Eclipse.

   >[!NOTE]
   >
   >Ignore el mensaje &quot;Advertencia: Está a punto de instalar una función sin firmar&quot; y haga clic en Instalar para continuar.

   >[!NOTE]
   >
   >El complemento AEM Forms Discovery de Adobe para Flash Builder le permite crear rápidamente aplicaciones de Flex y AIR de Adobe que invocan un servicio que forma parte de AEM Forms a través de sus extremos remotos. La información sobre cómo instalar y actualizar el complemento está disponible en el sitio Web de Adobe en **Vínculo requerido**.

### Configuración y registro en el servidor {#configuring-and-logging-server}

Para utilizar Workbench, debe tener una instancia de AEM Forms en ejecución, normalmente en un equipo independiente. Debe tener un nombre de usuario y una contraseña para iniciar sesión en AEM Forms, así como detalles sobre la ubicación del servidor.

>[!NOTE]
>
>Si ha configurado AEM Forms para utilizar el proveedor de repositorio Documentum de EMC o IBM FileNet y desea iniciar sesión en un repositorio distinto del repositorio configurado como predeterminado en AEM consola de administración de formularios, proporcione el nombre de usuario como username@Repository.

### Configuración de la configuración del tiempo de espera {#configuring-timeout-settings}

De forma predeterminada, el tiempo de espera de Workbench finaliza al cabo de dos horas, independientemente de la actividad o inactividad. Para editar la configuración de tiempo de espera, consulte &quot;Configuración de la administración de usuarios > Configuración de atributos avanzados del sistema&quot; en la Ayuda de la consola de administración.

### Configuración de Workbench para conectarse a través de HTTPS {#configuring-workbench-to-connect-over-HTTPS}

Para conectar Workbench con un servidor de AEM Forms a través de HTTPS, debe asegurarse de que la entidad de certificación (CA) que emitió la clave pública sea reconocida como de confianza por Workbench. Si no se reconoce que el certificado proviene de un origen de confianza, debe actualizar el archivo cacert ubicado en el directorio [Workbench_HOME]/workbench/jre/lib/security.

>[!NOTE]
>
>[Workbench_] HOME representa el directorio en el que se instaló Workbench. La ubicación predeterminada es C:\Program Files (x86)\Adobe Experience Manager Forms Workbench.

Asegúrese de conectarse a HTTPS utilizando el nombre especificado en el certificado. Normalmente, este nombre es el nombre de host completo.

**Para actualizar el archivo** cacert:
1. Asegúrese de que dispone de una copia del certificado de Capa de sockets seguros (SSL). Póngase en contacto con el administrador que configuró el servidor SSL o exporte el certificado mediante un navegador web.

   >[!NOTE]
   >
   >Para exportar el certificado, abra un explorador Web e inicie sesión en la consola de administración, instale el certificado en el explorador y, a continuación, exporte el certificado desde el explorador a una ubicación de almacenamiento temporal (o directamente al directorio [Workbench_HOME]/Workbench/jre/lib/security).

1. Copie el certificado en el directorio [Workbench_HOME]/Workbench/jre/lib/security.

1. Abra una ventana del símbolo del sistema, vaya a [Workbench_HOME]/Workbench/jre/bin y, a continuación, escriba el siguiente comando:
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
Donde:
   * change es la contraseña predeterminada para el almacén de claves cacerts.
   * certname es el certificado seleccionado en el paso 1.
   * ejemplo es el alias que elija para el certificado. Este valor se puede cambiar

1. Cuando se le pida que confíe en el certificado, escriba Sí y pulse la tecla Intro. La herramienta de clave procede a importar el archivo cacerts en el directorio [Workbench_HOME]/Workbench/jre/lib/security.

1. Cierre y reinicie Workbench para aplicar los cambios.

### Configuración de la caché para plantillas generadas dinámicamente {#configuring-cache-settings-for-dynamically-generated-templates}

Se deben tener en cuenta los siguientes aspectos de la operación de caché si la aplicación genera plantillas únicas sobre la marcha mediante la actualización automática del contenido XFA. De hecho, cada transacción utiliza una plantilla nueva y única.

Cuando el generador de formularios o la salida buscan o actualizan entradas en la caché para una plantilla de formulario específica, utiliza varios valores clave para ubicar la entrada de caché específica a la que se accederá.

* **Nombre** del archivo de plantilla: Ubicación y nombre de archivo de la plantilla utilizada como identificador único principal del formulario en caché.
* **Marca de hora**: El archivo de plantilla contiene una marca de hora que se utiliza para determinar la hora de la última actualización del formulario.
* **UUID** de plantilla: Designer inserta en cada plantilla un identificador único (UUID) para el formulario y su versión. Cada vez que se actualiza el formulario, se actualiza el UUID incrustado. Por ejemplo, una plantilla XDP puede mostrar el siguiente contenido:

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=http://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="http://www.xfa.org/schema/xfa-template/2.6/">`

* **Opciones** de procesamiento: Dentro de la caché de formularios procesada, el contenido de la caché se almacena por separado para cada conjunto de opciones de procesamiento únicas.


El servicio Forms recibe las plantillas por referencia al nombre de archivo o la ubicación del repositorio, o por valor como un objeto XML en la memoria.
* **Plantillas pasadas por referencia**: Utiliza la raíz de contenido y el nombre del formulario. Si se pasan plantillas únicas con nombres de archivo diferentes en cada solicitud mediante este método, la caché de disco crecerá indefinidamente y nunca se volverá a utilizar. Para evitar esto, las plantillas únicas deben pasarse con el mismo nombre de archivo para garantizar que la misma caché se actualice para todas las solicitudes.
* **Plantillas pasadas por valor**: Utiliza bytes de plantilla pasados junto con los datos mediante el parámetro theinDataDoc. Si se pasan plantillas únicas con UUID diferentes mediante este método, la caché de disco crecerá indefinidamente y nunca se volverá a utilizar. Para evitar esto, el atributo UUID debe eliminarse de todas las plantillas para garantizar que no se cree ninguna caché para la plantilla. De forma alternativa, si se pasa el mismo UUID que no sea nulo, se pueden crear los objetos de caché, pero se garantiza que la misma caché se actualiza con cada solicitud.

Para evitar que la caché crezca indefinidamente, tenga en cuenta los siguientes factores para procesar plantillas generadas dinámicamente con las nuevas API de AEM Forms, las cuales son renderizarHTMLForm2 y procesarPDFForm2.

Al utilizar las nuevas API, la plantilla se pasa como un objeto documento, que se gestiona en el servicio Forms en función de si está pasivada o no.

Para los documentos pasivos en los que UUID y la raíz de contenido sirven como clave de caché, tenga en cuenta los siguientes aspectos:
* La caché no se crea para plantillas de entrada pasivas sin UUID.
* Si se pasa más de una plantilla de entrada pasiva con el mismo UUID y la misma raíz de contenido, se sobrescribe la misma caché.

Para documentos no pasivos en los que el nombre de archivo y la raíz de contenido sirven como clave de caché, tenga en cuenta lo siguiente:
* Para las plantillas de entrada no pasivas, el almacenamiento en caché depende de la raíz de contenido y el nombre de archivo desde los que se generó el documento.
La misma caché se utilizará solamente para solicitudes con la misma raíz de contenido y nombre de archivo de plantilla.
Las siguientes optimizaciones garantizan que la caché no crezca indefinidamente cuando se pasen plantillas generadas dinámicamente al servicio Forms:
   * Elimine el UUID o pase el mismo UUID en todas las plantillas generadas dinámicamente.
   * Genere el documento a partir de bytes de plantilla o del mismo nombre de archivo del disco.

### Desinstalación de Workbench {#uninstalling-workbench}

Utilice la función Añadir o quitar Programas del Panel de control de Campaign para inicio del programa de desinstalación. Las aplicaciones de Workbench y Designer tienen programas de desinstalación independientes.

## Configuración del Editor XDC de AEM Forms {#configuring-aem-forms-xdc-editor}

Con el Editor XDC, los administradores de impresoras en red pueden crear y modificar archivos de Configuración de dispositivos de arquitectura XML de Forms (XDC). Los archivos XDC describen las funciones de las impresoras, como el idioma de la impresora o la correlación entre el tamaño del papel y la ubicación de la bandeja.

Antes de que el administrador de impresoras en red utilice el Editor XDC, vuelva a ubicar los archivos XDC de ejemplo y consulte Creación de perfiles de dispositivo mediante el Editor XDC.

**Para obtener los archivos** XDC de ejemplo:
1. En el servidor de AEM Forms, busque la carpeta XDC en [AEM Forms root]\sdk\samples\Output\IVS.
1. Copie el contenido de esta carpeta en un directorio al que se pueda acceder desde el sistema Workbench o Eclipse.

**Para obtener la ayuda** del Editor XDC:
1. Vaya al sitio web de documentación de AEM Forms.
1. Haga clic en la ficha Desarrollar y vaya a Creación de perfiles de dispositivo mediante el Editor XDC. Descargue el archivo xdc_editor_help_web.zip e instale los archivos de ayuda siguiendo las instrucciones que se proporcionan en el archivo Léame.

