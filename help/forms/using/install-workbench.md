---
title: Instalación de Workbench
seo-title: Install workbench
description: Instale Workbench.
uuid: null
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: null
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2779'
ht-degree: 74%

---


# Instalación de Workbench {#install-workbench}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Este documento proporciona instrucciones para instalar y configurar el área de trabajo. El programa de instalación también instala  Designer.

## Acerca de {#about}

Este documento va dirigido a los administradores o los desarrolladores responsables de la instalación, configuración, administración o implementación de Workbench.
También se incluye información necesaria para configurar el sistema de modo que admita los procesos actualizados de Adobe® AEM forms® Enterprise Suite (ES) Update 1 (8.2.x) y Adobe® AEM forms® Enterprise Suite 2 (ES2).
La información proporcionada se basa en la suposición de que cualquiera que lea este documento está familiarizado con el sistema operativo Microsoft® Windows®.

## Información adicional {#additional-information}

Los recursos de esta tabla pueden ayudarle a obtener más información y a empezar a utilizar AEM Forms.
<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Para obtener información acerca de</strong></p> </td> 
   <td><p><strong>Consulte</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Información sobre los procedimientos de Workbench</p> </td> 
   <td><p><a href="http://www.adobe.com/go/learn_aemforms_workbench_61_es">Ayuda de Workbench</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Información general sobre AEM Forms y su integración con otros productos de Adobe</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Información general sobre AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Un tutorial para crear una aplicación de AEM Forms y probarla en el espacio de trabajo</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_firstapp_ds_65">Creación de la primera aplicación de AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Toda la documentación disponible para AEM Forms</p> </td> 
   <td><p><a href="http://adobe.com/go/learn_aemforms_introduction_65">Documentación de AEM Forms</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Otros servicios y productos que se integran con AEM Forms</p> </td> 
   <td><p><a href="http://www.adobe.com/es/">www.adobe.com</a><br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Actualizaciones de parches, notas técnicas e información adicional sobre esta versión del producto</p> </td> 
   <td><p><a href="https://www.adobe.com/account/sign-in.supportportal.html">Contacte con el soporte técnico de Adobe Enterprise</a><br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Espacio de trabajo de Flex ya no se utiliza para AEM Forms. Está disponible para la versión de AEM Forms.

## Antes de la instalación {#before-you-install}

### Información general sobre la instalación de Workbench {#workbench-installation-overview}

Workbench es un entorno de desarrollo integrado (IDE) que utilizan los desarrolladores y los autores de formularios para crear formularios y procesos empresariales automatizados. También se utiliza para administrar los recursos y los servicios que utilizan los procesos y los formularios.

La siguiente ilustración muestra la instalación de Workbench, la cual incluye:
* Diseño de procesos con Workbench
* Diseño de formularios con Designer

>[!NOTE]
>
>El servidor de AEM Forms requiere un programa de instalación independiente. Para obtener más información, consulte la documentación de instalación de AEM Forms en JEE.

## Requisitos previos del sistema {#system-prerequisites}

Esta sección describe los requisitos de hardware y software y las plataformas compatibles.

### Requisitos mínimos de hardware y software {#minimum-hardware-software-requirements}

**Workbench**
Se recomiendan los siguientes requisitos mínimos:
Espacio en disco para la instalación:
* 680 MB solo para Workbench.
* 2,15 GB en una sola unidad para una instalación completa de Workbench, Designer y el conjunto de muestras.
* 400 MB para directorios de instalación temporales - 200 MB en el directorio \temp de usuario y 200 MB en el directorio temporal de Windows.

>[!NOTE]
>
>Si todas estas ubicaciones residen en una sola unidad, es necesario disponer de 1,5 GB de espacio disponible durante la instalación. Los archivos copiados en los directorios temporales se eliminan cuando finaliza la instalación.

* Requisitos de hardware: Procesador Intel® Pentium® 4 o AMD equivalente de 1 GHz.
* Descargue e instale la versión más reciente de Adobe AIR (desde <a href="http://www.adobe.com/es/">www.adobe.com</a>) necesario para el cliente de ayuda de la comunidad, integrado con Workbench.
* Java™ Runtime Environment (JRE) 6.0 update 22 o posterior se actualiza a 6.0 *Nuevo para 10*.
* Resolución de monitor mínima de 1024 X 768 píxeles o superior con color de 16 bits o superior.
* Conexión de red TCP/IPv4 o TCP/IPv6 al servidor AEM Forms.
* Instale los paquetes de tiempo de ejecución redistribuibles de Visual C++ 2012 de 32 bits.
* Instale los paquetes de tiempo de ejecución redistribuibles de Visual C++ 2013 de 32 bits.

>[!NOTE]
>
>Si tiene instalado Adobe® Acrobat® X en su equipo, asegúrese de desinstalarlo antes de instalar Workbench. Puede volver a instalar Acrobat después de instalar Workbench.

>[!NOTE]
>
>Debe tener privilegios administrativos para instalar Workbench. Si va a realizar la instalación con una cuenta que no sea de administrador, el instalador le pedirá las credenciales de una cuenta adecuada.

### Plataformas compatibles {#supported-platforms}

Consulte la lista completa de plataformas compatibles con Workbench en [Plataformas compatibles con AEM Forms](http://adobe.com/go/learn_aemforms_supportedplatforms_65).

## Consideraciones sobre la instalación de Designer {#designer-installation-considerations}

De forma predeterminada, la instalación de Workbench incluye únicamente la versión correspondiente de Designer en inglés. Si la aplicación de instalación de Workbench detecta una versión existente de Designer en el equipo, es posible que la instalación termine y se le pida que elimine la versión actual de Designer antes de poder continuar.
La siguiente tabla contiene una lista completa de los posibles escenarios de instalación de Designer que puede encontrar, así como las acciones que debe realizar al instalar Workbench.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Versión de Designer instalada actualmente</strong></p> </td> 
   <td><p><strong>Acciones necesarias</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Acrobat Pro o Acrobat Pro Extended (incluye Designer)</p> </td> 
   <td><p>Ninguna. La instalación de Workbench detecta una instancia de Designer instalada en el equipo con Acrobat Pro o Acrobat Pro Extended.
Las distintas versiones de Designer pueden coexistir en el mismo sistema, por ejemplo Designer 8.2.x y 9.0.x. No es necesario desinstalar la versión de Designer instalada con Acrobat 10 Pro o Acrobat 10 Pro Extended.
<br /> <br /> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Designer (independiente)</p> </td> 
   <td><p>Ninguna. La versión de Designer incluida con Workbench solo está disponible en inglés. El instalador de Workbench no reinstala una nueva versión de Designer. En su lugar, se instalará un parche con una versión actualizada integrada en el programa de instalación de Workbench. Esto le permite asimismo utilizar una versión localizada de Designer en Workbench.<br /> <br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

### Para desinstalar Designer (independiente) {#uninstall-designer-standalone}

1. Vaya a **Panel de control > Programas > Programas y características**.
1. En la lista Programas actualmente instalados, seleccione **Adobe Designer**.
1. Haga clic en **Desinstalar** y después en **Sí**.

### Desinstalación de Designer (independiente) en Windows 10 {#uninstall-designer-standalone-windows10}

1. Vaya a **Panel de control > Programas > Programas y características**.
1. En la lista Programas actualmente instalados, seleccione **Adobe Designer**.
1. Haga clic en **Desinstalar** y después en **Sí**.

### Para desinstalar Designer incluido con Acrobat Pro o Acrobat Pro Extended {#uninstall-designer-included-with-acrobatpro-or-acrobatextended}

1. Vaya a **Panel de control > Programas > Programas y características**.
1. En la lista Programas instalados actualmente, seleccione **Adobe Acrobat Pro** o **Adobe Acrobat Pro Extended**.
1. Haga clic en **Cambiar** y haga clic en **Siguiente**.
1. Select **Modificar** y haga clic en **Siguiente**.
1. Select **Diseñador de Adobes**, seleccione **Esta función no estará disponible** y, a continuación, haga clic en **Siguiente**
1. Haga clic en **Actualizar** y haga clic en **Finalizar**

### Para desinstalar Designer incluido con Acrobat Pro o Acrobat Pro Extended en Windows 10 {#uninstall-designer-included-with-acrobatpro-or-acrobatextended-windows10}

1. Vaya a **Panel de control > Programas > Programas y características**.
1. En la lista Programas instalados actualmente, seleccione **Adobe Acrobat Pro** o **Adobe Acrobat Pro Extended**.
1. Haga clic en **Cambiar** y haga clic en **Siguiente**.
1. Select **Modificar** y haga clic en **Siguiente**.
1. Select **Diseñador de Adobes**, seleccione **Esta función no estará disponible** y, a continuación, haga clic en **Siguiente**
1. Haga clic en **Actualizar** y haga clic en **Finalizar**

## Instalación de Workbench {#installing-workbench}

Este capítulo describe cómo instalar Workbench.

### Instalación y ejecución de Workbench {#installing-and-running-workbench}

Antes de instalar Workbench, debe asegurarse de que su entorno incluye el software y el hardware necesarios para ejecutarlo (consulte la sección: **Antes de la instalación**).

**Para instalar y ejecutar Workbench:**

1. Realice una de las siguientes tareas:
   * Vaya al directorio \workbench en los medios de instalación y haga doble clic en el archivo run_windows_installer.bat.
   * Descargue y descomprima Workbench en su sistema de archivos. Una vez descargado, vaya al directorio \workbench y haga doble clic en el archivo run_windows_installer.bat.

   >[!IMPORTANT]
   >
   >El instalador de Workbench solo se ejecuta desde un DVD o una unidad local. No se puede ejecutar desde un sitio remoto.

   >[!NOTE]
   >
   >Si aparece el error &quot;No se pudo crear la máquina virtual Java&quot;, cree una variable de entorno llamada _JAVA_OPTIONS con valor -Xmx512M y ejecute el programa de instalación.

1. En la pantalla Introducción, haga clic en Siguiente.
1. Lea el Acuerdo de licencia del producto, seleccione Acepto los términos del Acuerdo de licencia y, a continuación, haga clic en Siguiente.
1. (Opcional) Seleccione Instalar Adobe Designer si necesita esta herramienta para crear y modificar formularios.

   >[!NOTE]
   >
   >Puede seguir utilizando la versión de Designer instalada con Acrobat 10 sin seleccionar esta opción.

1. Acepte el directorio predeterminado como se muestra o haga clic en Elegir y vaya al directorio en el que desea instalar Workbench y, a continuación, haga clic en Siguiente.

   >[!NOTE]
   >
   >La ruta del directorio de instalación no debe contener los caracteres # (libras) y $ (dólares).

1. Revise el resumen a la instalación y haga clic en Instalar. El programa de instalación muestra el progreso de la instalación.
1. Revise el resumen de la instalación. Seleccione Iniciar AEM Forms Workbench para iniciar Workbench y haga clic en Siguiente.
1. Revise las Notas de la versión y haga clic en Listo.
1. Los siguientes elementos ya están instalados en el equipo:
   * **Workbench**: para ejecutar Workbench desde el menú Inicio, seleccione Todos los programas > AEM Forms > Workbench si decide almacenar la carpeta de acceso directo allí. Para obtener más información, consulte la documentación sobre el uso de Workbench.
   * **Designer**: puede acceder a Designer desde Workbench. Para obtener más información, consulte el tema Introducción en la Ayuda de Designer.
   * **Complemento de Workbench**: Siga las instrucciones de &quot;3.3 Instalación de la función Eclipse de Workbench&quot; en la página 6.
   * **SDK de AEM Forms**: para obtener más información sobre el uso del SDK, consulte <a href="http://www.adobe.com/go/learn_lc_programming_10">Programación con AEM Forms</a>.

## Actualización de procesos {#upgrading-processes}

Los procesos AEM Forms Update 1 y LiveCycle ES2 se pueden actualizar a aplicaciones de AEM Forms mediante el Asistente para actualización. Consulte Actualización de la documentación de artefactos heredados en la Ayuda de Workbench para obtener más información.

### Instalación de la función Eclipse de Workbench {#installing-workbench-eclipse-feature}

Si lo desea, puede agregar la función Workbench a Eclipse. Puede agregar Workbench después de instalar Workbench. Por ejemplo, para JBoss, la siguiente ubicación contiene el archivo :

* Workbench_DVD/additional/eclipse Descargue e instale Eclipse 3.6 desde <a href="https://www.eclipse.org/downloads/">www.eclipse.org/downloads</a>.

### Configuración de la función de actualización de Eclipse para Workbench {#configuring-eclipse-update-feature-for-workbench}

Workbench admite la función de actualización para asegurarse de que está utilizando la versión más actualizada de Eclipse. Sin embargo, debe asegurarse de que se incluyen ciertos módulos adicionales en cada descarga:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Versión de Eclipse</strong></p> </td> 
   <td><p><strong>Módulos necesarios de Workbench</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Eclipse 3.6.x</p> </td> 
   <td><p>

* Marco de edición gráfica FMAM [org.eclipse.gef.feature.group]: Esto se incluye en el SDK de la plataforma de modelado gráfico [org.eclipse.gmf.sdk.feature.group]

* Núcleo XML de WST [org.eclipse.wst.xml_core.feature.group]: Esto está contenido en las herramientas y editores XML de Eclipse [org.eclipse.wst.xml_ui.feature.group]

* Complemento &#39;org.apache.commons.lang_2.3.0&#39; [n.a]: Esto se incluye en la &quot;Lista de tareas de Mylyn (obligatoria)&quot; [org.eclipse.mylyn_feature.feature.group]

   </p> </td> 
  </tbody>
  </table>

**Para instalar e implementar la función Workbench en Eclipse**:
1. Inicie Eclipse.
1. Seleccione Ayuda > Instalar nuevo software, haga clic en Agregar para abrir el cuadro de diálogo Agregar repositorio .
1. En el cuadro de diálogo Agregar repositorio, haga clic en Local y busque el directorio donde la instalación de Workbench guardó el archivo ZIP del complemento, seleccione workbench-updatesite.zip y, a continuación, haga clic en Abrir.
1. Siga las instrucciones de las pantallas siguientes para implementar la función Workbench en Eclipse.

   >[!NOTE]
   >
   >Ignore el mensaje &quot;Advertencia: Está a punto de instalar una función sin firmar&quot; y haga clic en Instalar para continuar.

   >[!NOTE]
   >
   >El complemento AEM Forms Discovery de Adobe para Flash Builder le permite crear rápidamente aplicaciones Flex y AIR de Adobe que invoquen un servicio que forma parte de AEM Forms a través de sus extremos remotos. La información sobre cómo instalar y actualizar el complemento está disponible en el sitio web de Adobe en **Vínculo obligatorio**.

### Configuración e inicio de sesión en el servidor {#configuring-and-logging-server}

Para utilizar Workbench, debe tener una instancia de AEM Forms en ejecución, normalmente en un equipo independiente. Debe disponer de un nombre de usuario y una contraseña para iniciar sesión en AEM Forms y conocer la ubicación del servidor.

>[!NOTE]
>
>Si configuró AEM Forms para utilizar los proveedores de repositorios EMC Documentum o IBM FileNet y desea iniciar sesión en un repositorio que no sea el repositorio configurado como predeterminado en la consola de administración de AEM Forms, introduzca el nombre de usuario username@Repository.

### Configuración del tiempo de espera {#configuring-timeout-settings}

De forma predeterminada, el valor del tiempo de espera de Workbench es de dos horas, independientemente de la actividad o la inactividad. Para editar la configuración de tiempo de espera, consulte &quot;Configuración de la administración de usuarios > Configurar atributos avanzados del sistema&quot; en la Ayuda de la consola de administración.

### Configurar Workbench para que se conecte a través de HTTPS {#configuring-workbench-to-connect-over-HTTPS}

Para conectar Workbench a un servidor de AEM Forms a través de HTTPS, debe asegurarse de que Workbench reconozca la autoridad de certificación (CA) que emitió la clave pública como de confianza. Si no se reconoce que el certificado proviene de una fuente de confianza, debe actualizar el archivo cacert ubicado en el directorio [Workbench_HOME]/workbench/jre/lib/security.

>[!NOTE]
>
>[Workbench_HOME] representa el directorio donde instaló Workbench. La ubicación predeterminada es C:\Program Files (x86)\Adobe Experience Manager forms Workbench.

Asegúrese de conectarse a HTTPS utilizando el nombre especificado en el certificado. Normalmente, este nombre es el nombre de host completo.

**Para actualizar el archivo cacert**:
1. Asegúrese de disponer de una copia del certificado Secure Sockets Layer (SSL). Póngase en contacto con el administrador que configuró el servidor SSL o exporte el certificado utilizando un explorador web.

   >[!NOTE]
   >
   >Para exportar el certificado, abra un explorador web e inicie sesión en la consola de administración, instale el certificado en el explorador y, a continuación, exporte el certificado desde el explorador a una ubicación de almacenamiento temporal (o directamente al directorio [Workbench_HOME]/workbench/jre/lib/security).

1. Copie el certificado en el directorio [Workbench_HOME]/workbench/jre/lib/security.

1. Abra una ventana del Símbolo del sistema, vaya a [Workbench_HOME]/workbench/jre/bin y luego escriba el siguiente comando:
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
donde:
   * changeit es la contraseña predeterminada para el almacén de claves cacerts.
   * certname es el certificado seleccionado en el paso 1.
   * Por ejemplo, el alias que elija para el certificado. Este valor puede cambiarse

1. Cuando se le pida que confíe en el certificado, escriba Yes y pulse la tecla Intro. keytool procede a importar el archivo cacerts en el directorio [Workbench_HOME]/workbench/jre/lib/security.

1. Cierre y reinicie Workbench para aplicar los cambios.

### Configuración de la caché para plantillas generadas dinámicamente {#configuring-cache-settings-for-dynamically-generated-templates}

Los siguientes aspectos de la operación de caché deben tenerse en cuenta si la aplicación genera plantillas únicas sobre la marcha al actualizar automáticamente el contenido XFA. De hecho, cada transacción utiliza una plantilla nueva y única.

Cuando Forms Generator o Output buscan, o actualizan, las entradas en la caché de una plantilla de formulario específica, utilizan varios valores clave para localizar la entrada de caché específica a la que se accederá.

* **Nombre del archivo de plantilla**: la ubicación y el nombre de archivo de la plantilla utilizada como identificador único principal del formulario en caché.
* **Marca de tiempo**: el archivo de plantilla contiene una marca de tiempo que se utiliza para determinar la hora a la que el formulario se actualizó por última vez.
* **UUID de plantilla**: Designer inserta en cada plantilla un identificador único (UUID) para el formulario y su versión. Cada vez que se actualiza el formulario, se actualiza el UUID incrustado. Por ejemplo, una plantilla XDP puede mostrar el siguiente contenido:

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=http://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="http://www.xfa.org/schema/xfa-template/2.6/">`

* **Opciones de procesamiento**: en la caché de los formularios procesados, el contenido de la caché se almacena de forma independiente para cada conjunto de opciones de procesamiento únicas.


El servicio Forms recibe las plantillas por referencia al nombre de archivo o la ubicación del repositorio, o por valor como objeto XML en la memoria.
* **Plantillas pasadas por referencia**: utiliza la raíz de contenido y el nombre del formulario. Si se pasan plantillas únicas con diferentes nombres de archivo en cada solicitud utilizando este método, la caché de disco crecerá constantemente y nunca se reutilizará. Para evitarlo, las plantillas únicas deben pasarse con el mismo nombre de archivo para garantizar que se actualice la misma caché para todas las solicitudes.
* **Plantillas transferidas por valor**: utiliza bytes de plantilla pasados junto con los datos mediante el parámetro inDataDoc. Si se pasan plantillas únicas con un UUID diferente mediante este método, la caché del disco crecerá constantemente y nunca se reutilizará. Para evitarlo, el atributo UUID debe eliminarse de todas las plantillas para garantizar que no se cree ninguna caché para la plantilla. En cambio, pasar el mismo UUID no nulo permite crear los objetos de caché, pero garantiza que se actualice la misma caché con cada solicitud.

Para evitar que la caché crezca indefinidamente, tenga en cuenta los siguientes factores para procesar plantillas generadas dinámicamente con las nuevas API de AEM Forms, que son renderHTMLForm2 y renderPDFForm2.

Al utilizar las nuevas API, la plantilla se pasa como un objeto document, el cual se gestiona en el servicio Forms dependiendo de si está pasivada o no.

Para documentos pasivados en los que el UUID y la raíz de contenido sirven como clave de caché, tenga en cuenta los siguientes aspectos:
* La caché no se crea para plantillas de entrada pasivadas sin UUID.
* Si se pasa más de una plantilla de entrada pasivada que tiene el mismo UUID y la misma raíz de contenido, se sobrescribe la misma caché.

En el caso de los documentos no pasivados en los que el nombre de archivo y la raíz de contenido sirven como clave de caché, tenga en cuenta el siguiente aspecto:
* En el caso de las plantillas de entrada no pasivadas, el almacenamiento en caché depende de la raíz de contenido y del nombre de archivo a partir del cual se generó el documento.
Únicamente se utilizará la misma caché para aquellas solicitudes que tengan la misma raíz de contenido y el mismo nombre de archivo de plantilla.
Las siguientes prácticas recomendadas garantizarán que la caché no crezca constantemente al pasar plantillas generadas dinámicamente al servicio Forms:
   * Elimine el UUID o pase el mismo UUID en todas las plantillas generadas dinámicamente.
   * Genere el documento desde bytes de plantilla o desde el mismo nombre de archivo en disco.

### Desinstalación de Workbench {#uninstalling-workbench}

Utilice la función Agregar o quitar programas del Panel de control para iniciar el programa de desinstalación. Las aplicaciones Workbench y Designer tienen programas de desinstalación independientes.

## Configuración del Editor XDC de AEM Forms {#configuring-aem-forms-xdc-editor}

Con el Editor XDC, los administradores de impresoras de red pueden crear y modificar archivos XML Forms Architecture Device Configuration (XDC). Los archivos XDC describen las capacidades de las impresoras, como el idioma de la impresora o la correlación entre el tamaño del papel y la ubicación de la bandeja.

Antes de que el administrador de la impresora de red utilice el Editor XDC, cambie la ubicación de los archivos XDC de ejemplo y consulte la sección Creación de perfiles de dispositivo mediante el Editor XDC.

**Para obtener los archivos XDC de ejemplo**:
1. En el servidor de AEM Forms, busque la carpeta XDC en [AEM Forms root]\sdk\samples\Output\IVS.
1. Copie el contenido de esta carpeta en un directorio al que se pueda acceder desde el sistema Workbench o Eclipse.

**Para obtener ayuda sobre el Editor XDC**:
1. Vaya al sitio web de documentación de AEM Forms.
1. Haga clic en la pestaña Desarrollo y vaya a la sección Creación de perfiles de dispositivo mediante el Editor XDC. Descargue el archivo xdc_editor_help_web.zip e instale los archivos de ayuda siguiendo las instrucciones proporcionadas en el archivo Léame.

