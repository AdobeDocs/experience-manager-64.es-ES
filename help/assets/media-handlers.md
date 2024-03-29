---
title: Procesamiento de recursos con controladores de medios y flujos de trabajo
description: Obtenga información sobre los distintos controladores de medios y cómo utilizarlos en flujos de trabajo para realizar tareas en los recursos.
contentOwner: AG
feature: Workflow,Renditions
role: User
exl-id: 7694c68d-0a17-4052-8fbe-9bf45b229e81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 4%

---

# Procesamiento de recursos Uso de controladores de medios y flujos de trabajo {#processing-assets-using-media-handlers-and-workflows}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets proporciona un conjunto de flujos de trabajo predeterminados y controladores de medios para procesar los recursos. Un flujo de trabajo define una tarea de procesamiento y administración de recursos típica y, a continuación, delega las tareas específicas a los controladores de medios, por ejemplo, la generación de miniaturas o la extracción de metadatos.

Se puede definir un flujo de trabajo que se ejecute automáticamente cuando se cargue en el servidor un recurso de un tipo o formato determinado. Los pasos de procesamiento se definen como una serie de controladores de medios de Experience Manager Assets. Adobe Experience Manager proporciona algunas [controladores integrados,](#default-media-handlers) y más puede ser [desarrollo personalizado](#creating-a-new-media-handler) o se definen delegando el proceso a un [herramienta línea de comandos](#command-line-based-media-handler).

Los controladores de medios son servicios dentro de Experience Manager Assets que realizan acciones específicas en los recursos. Por ejemplo, cuando se carga un archivo de audio MP3 en el Experience Manager, un flujo de trabajo déclencheur un controlador MP3 que extrae los metadatos y genera una miniatura. Los controladores de medios se utilizan con flujos de trabajo. La mayoría de los tipos MIME comunes se admiten en Experience Manager. Puede realizar tareas específicas en los recursos realizando una de las siguientes acciones

* Ampliación o creación de flujos de trabajo.
* Ampliación o creación de controladores de medios.
* Desactivación o activación de controladores de medios.

>[!NOTE]
>
>Consulte [Formatos compatibles con Assets](assets-formats.md) para obtener una descripción de todos los formatos compatibles con Experience Manager Assets y las funciones compatibles con cada formato.

## Controladores de medios predeterminados {#default-media-handlers}

Los siguientes controladores de medios están disponibles en Experience Manager Assets y administran los tipos MIME más comunes:

| Nombre del controlador | Nombre del servicio (en la consola del sistema) | Tipos MIME admitidos |
|---|---|---|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>aplicación/ilustrador</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg<br><b>Importante</b> - Cuando se carga un archivo MP3, es [procesado con una biblioteca de terceros](https://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html). La biblioteca calcula una longitud aproximada no precisa si el MP3 tiene velocidad de bits variable (VBR). |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>aplicación/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | aplicación/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | reserva en caso de que no se encontrara ningún otro controlador para extraer datos de un recurso |

Todos los controladores realizan las siguientes tareas:

* extraer todos los metadatos disponibles del recurso.
* crear una imagen en miniatura a partir del recurso.

Es posible ver los controladores de medios activos:

1. En el navegador, vaya a `http://localhost:4502/system/console/components`.
1. Haga clic en el vínculo `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Se muestra una lista con todos los controladores de medios activos. Por ejemplo:

![chlimage_1-437](assets/chlimage_1-437.png)

## Uso de controladores de medios en flujos de trabajo para realizar tareas en Assets {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Los controladores de medios son servicios que se utilizan con flujos de trabajo.

El Experience Manager tiene algunos flujos de trabajo predeterminados para procesar los recursos. Para visualizarlos, abra la consola Flujo de trabajo y haga clic en el botón **[!UICONTROL Modelos]** pestaña: los títulos de flujo de trabajo que comienzan con Experience Manager Assets son los específicos de recursos.

Los flujos de trabajo existentes se pueden ampliar y se pueden crear nuevos para procesar los recursos según requisitos específicos.

El siguiente ejemplo muestra cómo mejorar la variable **[!UICONTROL Sincronización de AEM Assets]** flujo de trabajo para que se generen subrecursos para todos los recursos, excepto para los documentos del PDF.

### Desactivación/activación de un controlador de medios {#disabling-enabling-a-media-handler}

Los controladores de medios pueden desactivarse o habilitarse a través de la Consola de gestión web Apache Felix. Cuando el controlador de medios está desactivado, sus tareas no se realizan en los recursos.

Para habilitar/deshabilitar un controlador de medios:

1. En el navegador, vaya a `https://<host>:<port>/system/console/components`.
1. Haga clic en **[!UICONTROL Deshabilitar]** junto al nombre del controlador de medios. Por ejemplo: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Actualice la página: se muestra un icono junto al controlador de medios que indica que está desactivado.
1. Para habilitar el controlador de medios, haga clic en **[!UICONTROL Habilitar]** junto al nombre del controlador de medios.

### Creación de un controlador de medios {#creating-a-new-media-handler}

Para admitir un nuevo tipo de contenido o ejecutar tareas específicas en un recurso, es necesario crear un controlador de medios. En esta sección se describe cómo continuar.

#### Clases e interfaces importantes {#important-classes-and-interfaces}

La mejor manera de iniciar una implementación es heredar de una implementación abstracta proporcionada que se ocupe de la mayoría de las cosas y proporcione un comportamiento predeterminado razonable: el `com.day.cq.dam.core.AbstractAssetHandler` Clase .

Esta clase ya proporciona un descriptor de servicio abstracto. Por lo tanto, si hereda de esta clase y utiliza el complemento maven-sling, asegúrese de establecer el indicador heredado en `true`.

Implemente los siguientes métodos:

* `extractMetadata()`: extrae todos los metadatos disponibles.
* `getThumbnailImage()`: crea una imagen en miniatura a partir del recurso pasado.
* `getMimeTypes()`: devuelve los tipos MIME de recurso.

Esta es un ejemplo de plantilla:

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

La interfaz y las clases incluyen:

* `com.day.cq.dam.api.handler.AssetHandler` interfaz: Esta interfaz describe el servicio que agrega compatibilidad con tipos MIME específicos. La adición de un tipo MIME requiere para implementar esta interfaz. La interfaz contiene métodos para importar y exportar documentos específicos, para crear miniaturas y extraer metadatos.
* `com.day.cq.dam.core.AbstractAssetHandler` Clase : Esta clase sirve de base para todas las demás implementaciones de controladores de recursos y proporciona funcionalidad utilizada en común.
* `com.day.cq.dam.core.AbstractSubAssetHandler` clase:
   * Esta clase sirve de base para todas las demás implementaciones de controladores de recursos y proporciona una funcionalidad utilizada comúnmente, además de otra funcionalidad utilizada comúnmente para la extracción de subrecursos.
   * La mejor manera de iniciar una implementación es heredar de una implementación abstracta proporcionada que se ocupe de la mayoría de las cosas y proporcione un comportamiento predeterminado razonable: la clase com.day.cq.dam.core.AbstractAssetHandler .
   * Esta clase ya proporciona un descriptor de servicio abstracto. Por lo tanto, si hereda de esta clase y utiliza el complemento maven-sling, asegúrese de establecer el indicador heredado en true.

Se deben implementar los siguientes métodos:

* `extractMetadata()`: este método extrae todos los metadatos disponibles.
* `getThumbnailImage()`: este método crea una imagen en miniatura del recurso pasado.
* `getMimeTypes()`: este método devuelve los tipos MIME de recurso.

Esta es un ejemplo de plantilla:

paquete my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component herit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ clase pública MyMediaHandler amplía com.day.cq.dam.core.AbstractAssetHandler { // implementa las partes relevantes }

La interfaz y las clases incluyen:

* `com.day.cq.dam.api.handler.AssetHandler` interfaz: Esta interfaz describe el servicio que agrega compatibilidad con tipos de mime específicos. La adición de un tipo MIME requiere para implementar esta interfaz. La interfaz contiene métodos para importar y exportar documentos específicos, para crear miniaturas y extraer metadatos.
* `com.day.cq.dam.core.AbstractAssetHandler` Clase : Esta clase sirve de base para todas las demás implementaciones de controladores de recursos y proporciona funcionalidad utilizada en común.
* `com.day.cq.dam.core.AbstractSubAssetHandler` Clase : Esta clase sirve de base para todas las demás implementaciones de controladores de recursos y proporciona funcionalidad utilizada comúnmente, además de funcionalidad utilizada comúnmente para la extracción de subrecursos.

#### Ejemplo: crear un controlador de texto específico {#example-create-a-specific-text-handler}

En esta sección, creará un controlador de texto específico que genere miniaturas con una marca de agua.

Proceda de la siguiente manera:

Consulte [Herramientas de desarrollo](../sites-developing/dev-tools.md) para instalar y configurar Eclipse con un complemento de Maven y para configurar las dependencias necesarias para el proyecto de Maven.

Después de realizar el siguiente procedimiento, al cargar un archivo txt en el Experience Manager, se extraen los metadatos del archivo y se generan dos miniaturas con una marca de agua.

1. En Eclipse, cree `myBundle` Proyecto Maven:

   1. En la barra de menús, haga clic en **[!UICONTROL Archivo > Nuevo > Otro]**.
   1. En el cuadro de diálogo, expanda la carpeta Maven, seleccione Maven Project y haga clic en **[!UICONTROL Siguiente]**.
   1. Marque la **[!UICONTROL Crear un proyecto simple]** y **[!UICONTROL Usar ubicaciones predeterminadas de Workspace]** y haga clic en **[!UICONTROL Siguiente]**.
   1. Defina el proyecto Maven con los siguientes valores:

      * Id De Grupo: com.day.cq5.myhandler
      * Id De Artefacto: myBundle
      * Nombre: Mi paquete Experience Manager
      * Descripción: Este es mi paquete Experience Manager
   1. Haga clic en **[!UICONTROL Finalizar]**.


1. Establezca el compilador de Java™ en la versión 1.5:

   1. Haga clic con el botón derecho en el `myBundle` proyecto, seleccione Propiedades.
   1. Seleccione Java™ Compiler y establezca las siguientes propiedades en 1.5:

      * Nivel de cumplimiento del compilador
      * Compatibilidad generada con archivos .class
      * Compatibilidad de origen
   1. Haga clic en **[!UICONTROL Aceptar]**. En la ventana de diálogo, haga clic en Sí.


1. Reemplace el código del archivo pom.xml con el siguiente código:

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion> 
    <!-- ====================================================================== --> 
    <!-- P A R E N T P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <parent>
     <groupId>com.day.cq.dam</groupId>
     <artifactId>dam</artifactId>
     <version>5.2.14</version>
     <relativePath>../parent</relativePath>
    </parent> 
    <!-- ====================================================================== --> 
    <!-- P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <groupId>com.day.cq5.myhandler</groupId>
    <artifactId>myBundle</artifactId>
    <name>My CQ5 bundle</name>
    <version>0.0.1-SNAPSHOT</version>
    <description>This is my CQ5 bundle</description>
    <packaging>bundle</packaging> 
    <!-- ====================================================================== --> 
    <!-- B U I L D D E F I N I T I O N --> 
    <!-- ====================================================================== -->
    <build>
     <plugins>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-scr-plugin</artifactId>
      </plugin>
      <plugin>
       <groupId>org.apache.sling</groupId>
       <artifactId>maven-sling-plugin</artifactId>
       <configuration>
        <slingUrlSuffix>/libs/dam/install/</slingUrlSuffix>
       </configuration>
      </plugin>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-bundle-plugin</artifactId>
       <extensions>true</extensions>
       <configuration>
        <instructions>
         <Bundle-Category>cq5</Bundle-Category>
         <Export-Package> com.day.cq5.myhandler </Export-Package>
        </instructions>
       </configuration>
      </plugin>
     </plugins>
    </build> 
    <!-- ====================================================================== --> 
    <!-- D E P E N D E N C I E S --> 
    <!-- ====================================================================== -->
    <dependencies>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-api</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-core</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq</groupId>
      <artifactId>cq-commons</artifactId>
     </dependency>
     <dependency>
      <groupId>javax.jcr</groupId>
      <artifactId>jcr</artifactId>
     </dependency>
     <dependency>
      <groupId>org.apache.felix</groupId>
      <artifactId>org.osgi.compendium</artifactId>
     </dependency>
     <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-collections</groupId>
      <artifactId>commons-collections</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-gfx</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-text</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.workflow</groupId>
      <artifactId>cq-workflow-api</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.wcm</groupId>
      <artifactId>cq-wcm-foundation</artifactId>
      <version>5.2.22</version>
     </dependency>
    </dependencies>
   ```

1. Creación del paquete `com.day.cq5.myhandler` que contiene las clases Java™ en `myBundle/src/main/java`:

   1. En myBundle, haga clic con el botón derecho `src/main/java`, seleccione Nuevo y, a continuación, Paquete.
   1. Asigne un nombre `com.day.cq5.myhandler` y haga clic en Finalizar.

1. Creación de la clase Java™ `MyHandler`:

   1. En Eclipse, debajo de `myBundle/src/main/java`, haga clic con el botón derecho en el `com.day.cq5.myhandler` paquete, seleccione Nuevo y, a continuación, Clase.
   1. En la ventana del cuadro de diálogo, asigne un nombre a la clase MyHandler de Java™ y haga clic en Finalizar. Eclipse crea y abre el archivo MyHandler.java.
   1. En `MyHandler.java` reemplace el código existente por el siguiente y, a continuación, guarde los cambios:

   ```java
   package com.day.cq5.myhandler; 
   import java.awt.Color; 
   import java.awt.Rectangle; 
   import java.awt.image.BufferedImage; 
   import java.io.IOException; 
   import java.io.InputStream; 
   import java.io.InputStreamReader; 
   import javax.jcr.Node; 
   import javax.jcr.RepositoryException; 
   import javax.jcr.Session; 
   import org.apache.commons.io.IOUtils; 
   import org.slf4j.Logger; 
   import org.slf4j.LoggerFactory; 
   import com.day.cq.dam.api.metadata.ExtractedMetadata; 
   import com.day.cq.dam.core.AbstractAssetHandler; 
   import com.day.image.Font; 
   import com.day.image.Layer; 
   import com.day.cq.wcm.foundation.ImageHelper; 
   
   /** 
    * The <code>MyHandler</code> can extract text files 
    * @scr.component inherit="true" immediate="true" metatype="false" 
    * @scr.service 
    * 
    **/ 
   
   public class MyHandler extends AbstractAssetHandler { 
    /** * Logger instance for this class. */ 
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class); 
    /** * Music icon margin */ 
    private static final int MARGIN = 10; 
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */ 
    public String[] getMimeTypes() {
     return new String[] {"text/plain"}; 
    }
   
    public ExtractedMetadata extractMetadata(Node asset) { 
     ExtractedMetadata extractedMetadata = new ExtractedMetadata(); 
     InputStream data = getInputStream(asset); 
     try { 
      // read text data 
      InputStreamReader reader = new InputStreamReader(data); 
      char[] buffer = new char[4096]; 
      String text = ""; 
      while (reader.read(buffer) != -1) { 
       text += new String(buffer); 
      } 
      reader.close(); 
      long wordCount = this.wordCount(text); 
      extractedMetadata.setProperty("text", text); 
      extractedMetadata.setMetaDataProperty("Word Count",wordCount); 
      setMimetype(extractedMetadata, asset); 
     } catch (Throwable t) { 
      log.error("handling error: " + t.toString(), t); 
     } finally { 
      IOUtils.closeQuietly(data); 
     } 
     return extractedMetadata; } 
    // ----------------------< helpers >---------------------------------------- 
    protected BufferedImage getThumbnailImage(Node node) { 
     ExtractedMetadata metadata = extractMetadata(node); 
     final String text = (String) metadata.getProperty("text"); 
     // create text layer 
     final Layer layer = new Layer(500, 600, Color.WHITE); 
     layer.setPaint(Color.black); 
     Font font = new Font("Arial", 12); 
     String displayText = this.getDisplayText(text, 600, 12); 
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text 
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0); 
     } 
     // create watermark and merge with text layer 
     Layer watermarkLayer; 
     try { 
      final Session session = node.getSession(); 
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png"); 
      watermarkLayer.setX(MARGIN); 
      watermarkLayer.setY(MARGIN); 
      layer.merge(watermarkLayer); 
     } catch (RepositoryException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); 
     } catch (IOException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); } 
     layer.crop(new Rectangle(510, 600)); 
     return layer.getImage(); } 
    // ---------------< private >----------------------------------------------- 
    /** 
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px) 
     * * @return the text which will fit into the box 
     */ 
    private String getDisplayText(String text, int height, int fontheight) { 
     String trimmedText = text.trim(); 
     int numOfLines = height / fontheight; 
     String lines[] = trimmedText.split("\n"); 
     if (lines.length <= numOfLines) { 
      return trimmedText; 
     } else { 
      String cuttetText = ""; 
      for (int i = 0; i < numOfLines; i++) { 
       cuttetText += lines[i] + "\n"; 
      } 
      return cuttetText; 
     } 
    } 
    /**
     * * This method counts the number of words in a string 
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */ 
    private long wordCount(String text) { 
     // We need to keep track of the last character, if we have two whitespace in a row we don't want to double count.
     // The starting of the document is always a whitespace.
     boolean prevWhiteSpace = true; 
     boolean currentWhiteSpace = true; 
     char c; long numwords = 0; 
     int j = text.length(); 
     int i = 0; 
     while (i < j) { 
      c = text.charAt(i++); 
      if (c == 0) { break; } 
      currentWhiteSpace = Character.isWhitespace(c); 
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; } 
      prevWhiteSpace = currentWhiteSpace; 
     } 
     // If we do not end with a whitespace then we need to add one extra word.
     if (!currentWhiteSpace) { numwords++; } 
     return numwords; 
    } 
   }
   ```

1. Compile la clase Java™ y cree el paquete:

   1. Haga clic con el botón derecho en el proyecto myBundle y seleccione **[!UICONTROL Ejecutar como]**, luego **[!UICONTROL Instalación de Maven]**.
   1. El paquete `myBundle-0.0.1-SNAPSHOT.jar` (que contiene la clase compilada) se crea en `myBundle/target`.

1. En CRX Explorer, cree un nodo en `/apps/myApp`. Nombre = `install`, Tipo = `nt:folder`.
1. Copiar el paquete `myBundle-0.0.1-SNAPSHOT.jar` y guardarlo debajo de `/apps/myApp/install` (por ejemplo, con WebDAV). El nuevo controlador de texto está ahora activo en Experience Manager.
1. En el navegador, abra la Consola de Gestión Web Apache Felix. Seleccione la ficha Componentes y deshabilite el controlador de texto predeterminado `com.day.cq.dam.core.impl.handler.TextHandler`.

## Controlador de medios basado en líneas de comandos {#command-line-based-media-handler}

Experience Manager permite ejecutar cualquier herramienta de línea de comandos dentro de un flujo de trabajo para convertir recursos (como ImageMagick) y agregar la nueva representación al recurso. Instale la herramienta de línea de comandos en el disco que aloja el servidor Experience Manager y añada y configure un paso de proceso en el flujo de trabajo. El proceso invocado, llamado `CommandLineProcess`, filtra según tipos MIME específicos y crea varias miniaturas basadas en la nueva representación.

Las siguientes conversiones se pueden ejecutar y almacenar automáticamente en [!DNL Experience Manager Assets]:

* Transformación de EPS e AI mediante [ImageMagick](https://www.imagemagick.org/script/index.php) y [Ghostscript](https://www.ghostscript.com/)
* Transcodificación de vídeo FLV mediante [FFmpeg](https://ffmpeg.org/)
* Codificación MP3 con [LAME](https://lame.sourceforge.io)
* Procesamiento de audio mediante [SOX](https://sox.sourceforge.io)

>[!NOTE]
>
>En sistemas que no son de Windows, la herramienta FFMpeg devuelve un error al generar representaciones para un recurso de vídeo que tiene una comilla simple (&#39;) en su nombre de archivo. Si el nombre del archivo de vídeo incluye una comilla simple, elimínelo antes de cargarlo en el Experience Manager.

La variable `CommandLineProcess` process realiza las siguientes operaciones en el orden en que aparecen en la lista:

* Filtra el archivo según tipos de mime específicos, si se especifica.
* Crea un directorio temporal en el disco que aloja el servidor Experience Manager.
* Transmite el archivo original al directorio temporal.
* Ejecuta el comando definido por los argumentos del paso. El comando se está ejecutando dentro del directorio temporal con los permisos del usuario que ejecuta el Experience Manager.
* Transmite el resultado de nuevo a la carpeta de representación del servidor Experience Manager.
* Elimina el directorio temporal.
* Crea miniaturas basadas en esas representaciones, si se especifica. El número y las dimensiones de las miniaturas se definen mediante los argumentos del paso.

### Ejemplo con ImageMagick {#an-example-using-imagemagick}

El siguiente ejemplo muestra cómo configurar el paso de proceso de la línea de comandos. Cada vez que se añade un recurso con el tipo MIME gif o tiff `/content/dam` en el servidor Experience Manager, se crea una imagen giratoria del original junto con tres miniaturas más (140x100, 48x48 y 10x250).

Para realizar este paso del proceso, utilice ImageMagick. Instale ImageMagick en el disco que aloja el servidor Experience Manager:

1. Instale ImageMagick. Consulte [Documentación de ImageMagick](https://www.imagemagick.org/script/download.php) para obtener más información.
1. Configure la herramienta para que pueda ejecutar `convert` en la línea de comandos.
1. Para ver si la herramienta está instalada correctamente, ejecute el siguiente comando `convert -h` en la línea de comandos.

   Muestra una pantalla Ayuda con todas las opciones posibles de la herramienta de conversión.

   >[!NOTE]
   >
   >En algunas versiones de Windows® (por ejemplo, Windows® SE), el comando convertir no se ejecuta porque está en conflicto con la utilidad de conversión nativa que forma parte de la instalación de Windows®. En este caso, mencione la ruta completa de la utilidad ImageMagick utilizada para convertir archivos de imagen en miniaturas. Por ejemplo, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Para ver si la herramienta se ejecuta correctamente, añada una imagen de JPG al directorio de trabajo y ejecute el comando `convert <image-name>.jpg -flip <image-name>-flipped.jpg` en la línea de comandos.

   Se añade una imagen invertida al directorio.

A continuación, agregue el paso del proceso de la línea de comandos al flujo de trabajo de **[!UICONTROL recursos de actualización de DAM]**:

1. Vaya a la **[!UICONTROL Flujo de trabajo]** consola.
1. En el **[!UICONTROL Modelos]** , edite la **[!UICONTROL Recurso de actualización DAM]** modelo.
1. Cambiar la configuración de la variable **[!UICONTROL Representación habilitada para web]** paso como se indica a continuación:

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Guarde el flujo de trabajo.

Para probar el flujo de trabajo modificado, añada un recurso a `/content/dam`.

1. En el sistema de archivos, obtenga una imagen TIFF de su elección. Cambiar el nombre a `myImage.tiff` y cópielo en `/content/dam`, por ejemplo, utilizando WebDAV.
1. Vaya a la **[!UICONTROL DAM CQ5]** consola, por ejemplo `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Abrir el recurso `myImage.tiff` y compruebe que se hayan creado la imagen girada y las tres miniaturas.

#### Configurar el paso del proceso CommandLineProcess {#configuring-the-commandlineprocess-process-step}

En esta sección se describe cómo establecer los **[!UICONTROL argumentos de proceso]** de `CommandLineProcess`. Separe los valores de [!UICONTROL Argumentos de proceso] con una coma y no inicie un valor con un espacio en blanco.

| Argument-Format | Descripción |
|---|---|
| mime:&lt;mime-type> | Argumento opcional. El proceso se aplica si el recurso tiene el mismo tipo MIME que uno de los argumentos. <br>Se pueden definir varios tipos MIME. |
| tn:&lt;width>:&lt;height> | Argumento opcional. El proceso crea una miniatura con las dimensiones definidas en el argumento . <br>Se pueden definir varias miniaturas. |
| cmd: &lt;command> | Define el comando que se ejecuta. La sintaxis depende de la herramienta de línea de comandos. Solo se puede definir un comando. <br>Para crear el comando se pueden usar las siguientes variables:<br>`${filename}`: nombre del archivo de entrada, por ejemplo original.jpg <br> `${file}`: nombre de ruta completo del archivo de entrada, por ejemplo /tmp/cqdam0816.tmp/original.jpg <br> `${directory}`: directorio del archivo de entrada, por ejemplo /tmp/cqdam0816.tmp <br>`${basename}`: nombre del archivo de entrada sin su extensión, por ejemplo, original <br>`${extension}`: extensión del archivo de entrada, por ejemplo jpg |

Por ejemplo, si ImageMagick está instalado en el disco que aloja el servidor Experience Manager y si crea un paso de proceso utilizando **CommandLineProcess** como Implementación y los siguientes valores como **Argumentos de proceso**:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

A continuación, cuando se ejecute el flujo de trabajo, el paso solo se aplicará a los recursos que tengan `image/gif` o `mime:image/tiff` como mime-types. Crea una imagen girada del original, la convierte en .jpg y crea tres miniaturas con las dimensiones: 140x100, 48x48 y 10x250.

Utilice lo siguiente [!UICONTROL Argumentos de proceso] para crear las tres miniaturas estándar con ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Utilice lo siguiente [!UICONTROL Argumentos de proceso] para crear la representación habilitada para web mediante ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>La variable `CommandLineProcess` el paso solo se aplica a Assets (nodos de tipo `dam:Asset`) o descendientes de un recurso.
