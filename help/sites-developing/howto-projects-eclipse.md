---
title: Desarrollo de AEM proyectos con Eclipse
seo-title: How to Develop AEM Projects Using Eclipse
description: En esta guía se describe cómo utilizar Eclipse para desarrollar proyectos basados en AEM
seo-description: This guide describes how to use Eclipse for developing AEM based projects
uuid: 79fee76f-6bcc-498f-af46-530816b41bbe
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: aa58cfb8-ec15-4698-a8f0-97683b0de51c
exl-id: 5fae4a4c-c97a-4541-bdc5-63ef4ca0172c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 1%

---

# Desarrollo de AEM proyectos con Eclipse{#how-to-develop-aem-projects-using-eclipse}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En esta guía se describe cómo utilizar Eclipse para desarrollar proyectos basados en AEM.

>[!NOTE]
>
>El Adobe ahora proporciona la variable [AEM herramientas de desarrollo para Eclipse](/help/sites-developing/aem-eclipse.md) que le ayuda a desarrollar soluciones AEM con Eclipse.

## Información general {#overview}

Para comenzar con AEM desarrollo en Eclipse, se requieren los siguientes pasos.

Cada uno de ellos se explica con más detalle en el resto de este Manual de procedimientos.

* Instalación de Eclipse 4.3 (Kepler)
* Configurar el proyecto de AEM en función de Maven
* Preparación de la compatibilidad con JSP para Eclipse en el POM de Maven
* Importar el proyecto Maven en Eclipse

>[!NOTE]
>
>Esta guía se basa en Eclipse 4.3 (Kepler) y AEM 5.6.1.

## Instalar Eclipse {#install-eclipse}

Descargue el &quot;Eclipse IDE para desarrolladores de Java EE&quot; desde el [Página Descargas de Eclipse](https://www.eclipse.org/downloads/).

Instale Eclipse siguiendo las instrucciones de [Instrucciones de instalación](https://wiki.eclipse.org/Eclipse/Installation).

## Configurar el proyecto de AEM en función de Maven {#set-up-your-aem-project-based-on-maven}

A continuación, configure el proyecto con Maven como se describe en [Cómo crear AEM proyectos con Apache Maven](/help/sites-developing/ht-projects-maven.md).

## Preparación de la compatibilidad con JSP para Eclipse {#prepare-jsp-support-for-eclipse}

Eclipse también puede proporcionar soporte para trabajar con JSP, por ejemplo

* finalización automática de bibliotecas de etiquetas
* Eclipse-reconocimiento de objetos definidos por &lt;cq:defineobjects /> y &lt;sling:defineobjects />

Para que funcione:

1. Siga las instrucciones indicadas en [Cómo trabajar con JSP](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) en [Cómo crear AEM proyectos con Apache Maven](/help/sites-developing/ht-projects-maven.md).
1. Agregue lo siguiente a &lt;build /> en el POM de su módulo de contenido.

   El complemento de soporte Maven de Eclipse, m2e, no proporciona soporte para el complemento maven-jspc-plugin, y esta configuración le dice a m2e que ignore el complemento y la tarea relacionada de limpiar los resultados de compilación temporales.

   Este no es un problema: tal como se indica en [Cómo trabajar con JSP](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps), el complemento maven-jspc-plugin de esta configuración solo se utiliza para validar que los JSP se compilan como parte del proceso de compilación. Eclipse ya informa de cualquier problema en JSPs y no depende de este complemento de Maven para poder hacerlo.

   **myproject/content/pom.xml**

   ```xml
   <build>
     <!-- ... -->
     <pluginManagement>
       <plugins>
         <!--This plugin's configuration is used to store Eclipse m2e settings only. It has no influence on the Maven build itself.-->
         <plugin>
           <groupId>org.eclipse.m2e</groupId>
           <artifactId>lifecycle-mapping</artifactId>
           <version>1.0.0</version>
           <configuration>
             <lifecycleMappingMetadata>
               <pluginExecutions>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.sling</groupId>
                     <artifactId>maven-jspc-plugin</artifactId>
                     <versionRange>[2.0.6,)</versionRange>
                     <goals>
                       <goal>jspc</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.maven.plugins</groupId>
                     <artifactId>maven-clean-plugin</artifactId>
                     <versionRange>[2.4.1,)</versionRange>
                     <goals>
                       <goal>clean</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
               </pluginExecutions>
             </lifecycleMappingMetadata>
           </configuration>
         </plugin>
       </plugins>
     </pluginManagement>
   </build>
   ```

### Importar el proyecto Maven en Eclipse {#import-the-maven-project-into-eclipse}

1. En Eclipse, seleccione Archivo > Importar...
1. En el cuadro de diálogo Importar, seleccione Maven > Proyectos Maven existentes y haga clic en &quot;Siguiente&quot;.

   ![imagen_1-41](assets/chlimage_1-41.png)

1. Introduzca la ruta a la carpeta de nivel superior del proyecto y haga clic en &quot;Seleccionar todo&quot; y &quot;Finalizar&quot;.

   ![imagen_1-42](assets/chlimage_1-42.png)

1. Ahora está todo configurado para usar Eclipse para desarrollar su proyecto de AEM, incluido el autocompletado de JSP.

   ![imagen_1-43](assets/chlimage_1-43.png)

   >[!NOTE]
   >
   >Si incluye `/libs/foundation/global.jsp` u otros JSP en `/libs`, deberá copiarlo en el proyecto para que Eclipse pueda resolver la inclusión. Al mismo tiempo, debe asegurarse de que Maven no lo incluye en el paquete de contenido. La forma de lograrlo se describe en [Cómo crear AEM proyectos con Apache Maven](/help/sites-developing/ht-projects-maven.md).
