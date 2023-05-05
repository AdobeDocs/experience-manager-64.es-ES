---
title: Flujo de trabajo centrado en Forms en OSGi
seo-title: Rapidly build adaptive forms-based processes, automate document services operations, and use Acrobat Sign with AEM workflows
description: Utilice el flujo de trabajo de AEM Forms para automatizar y generar rápidamente revisiones y aprobaciones, para iniciar servicios de documento (Por ejemplo, para convertir un documento de PDF a otro formato), integre el flujo de trabajo de firma de Acrobat Sign y mucho más.
seo-description: Use AEM Forms Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Acrobat Sign signature workflow, and more.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
exl-id: fa39a4e8-ae22-4356-8935-44fdf1f4f609
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2902'
ht-degree: 90%

---

# Flujo de trabajo centrado en Forms en OSGi {#forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

![](do-not-localize/header.png)

Las empresas recopilan datos de cientos y miles de formularios, varios sistemas back-end y fuentes de datos en línea o sin conexión. También tienen un conjunto dinámico de usuarios para tomar decisiones sobre los datos, lo que implica procesos de revisión y aprobación iterativos.

Junto con los flujos de trabajo de revisión y aprobación para audiencias internas y externas, las organizaciones y empresas grandes tienen tareas repetitivas. Por ejemplo, convertir un documento PDF a otro formato. Cuando se realizan manualmente, estas tareas consumen mucho tiempo y recursos. Las empresas también tienen requisitos legales para firmar digitalmente un documento y archivar datos de formulario para su uso posterior en formatos predefinidos.

## Introducción al flujo de trabajo centrado en Forms en OSGi {#introduction-to-forms-centric-workflow-on-osgi}

Puede utilizar flujos de trabajo de AEM para generar rápidamente flujos de trabajo adaptables basados en Forms. Estos flujos de trabajo se pueden utilizar para revisiones y aprobaciones, flujos de procesos empresariales, para iniciar document services, integrarse con el flujo de trabajo de firmas de Acrobat Sign y operaciones similares. Por ejemplo, en el procesamiento de la solicitud de tarjeta de crédito, el empleado deja los flujos de trabajo de aprobación y guarda un formulario como documento de PDF. Además, estos flujos de trabajo se pueden utilizar dentro de una organización o entre firewall de redes.

Con el flujo de trabajo centrado en formularios en OSGi, puede generar e implementar rápidamente flujos de trabajo para diversas tareas en la pila OSGi, sin tener que instalar la funcionalidad de administración de procesos completa en la pila JEE. El desarrollo y la administración de flujos de trabajo utilizan las funciones conocidas de los flujo de trabajo de AEM y la bandeja de entrada AEM. Los flujos de trabajo forman la base de la automatización de los procesos empresariales en el mundo real que abarcan varios sistemas de software, redes, departamentos e incluso organizaciones.

Una vez configurados, estos flujos de trabajo se pueden habilitar manualmente para completar un proceso definido o ejecutarse programáticamente cuando los usuarios envíen un formulario o cartas de[ Administración de correspondencia](/help/forms/using/cm-overview.md). Con estas funciones mejoradas del flujo de trabajo de AEM, AEM Forms ofrece dos funciones distintas, aunque similares. Como parte de su estrategia de implementación, debe decidir cuál funciona para usted. Consulte una [comparación](/help/forms/using/capabilities-osgi-jee-workflows.md) de los flujos de trabajo de AEM centrados en Forms en OSGi y Process Management en JEE. Además, para la topología de implementación, consulte, [Arquitectura y topologías de implementación para AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

El flujo de trabajo centrado en Forms en OSGi amplía [la bandeja de entrada de AEM](/help/sites-authoring/inbox.md) y proporciona componentes adicionales (pasos) para el editor de flujos de trabajo de AEM para agregar compatibilidad con flujos de trabajo centrados en AEM Forms. La bandeja de entrada extendida de AEM tiene funcionalidades similares a las de [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md). Junto con la administración de flujos de trabajo centrados en las personas (aprobación, revisión, etc.), puede utilizar flujos de trabajo de AEM para automatizar [document services](/help/sites-developing/workflows-step-ref.md)Operaciones relacionadas con (por ejemplo, Generar PDF) y documentos de firma electrónica (Acrobat Sign).

En el siguiente diagrama se describe el procedimiento de extremo a extremo para crear, ejecutar y monitorizar un flujo de trabajo centrado en Forms en OSGi.

![introduction-to-aem-forms-workflow](assets/introduction-to-aem-forms-workflow.jpg)

## Antes de comenzar {#before-you-start}

* Un flujo de trabajo es una representación de un proceso empresarial real. Tenga preparados su proceso empresarial real y la lista de los participantes del proceso. Además, prepare el material colateral (formularios adaptables, documentos PDF, etc.) antes de empezar a crear un flujo de trabajo.
* Un flujo de trabajo puede tener varias fases. Estas fases se muestran en la bandeja de entrada AEM y ayudan a informar sobre el progreso del flujo de trabajo. Divida el proceso empresarial en fases lógicas.
* Puede configurar el paso Asignar tarea del flujo de trabajo de AEM para enviar notificaciones por correo electrónico a los usuarios o a los usuarios asignados. [habilita las notificaciones por correo electrónico](#configure-email-service).
* Un flujo de trabajo también puede utilizar Acrobat Sign para firmas digitales. Si planea utilizar Acrobat Sign en un flujo de trabajo, la variable [configuración de Acrobat Sign para AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) antes de utilizarla en un flujo de trabajo.

## Cree un modelo del flujo de trabajo {#create-a-workflow-model}

Un modelo del flujo de trabajo consiste en la lógica y el flujo de un proceso empresarial. Se compone de una serie de pasos. Estos pasos son componentes de AEM. Puede ampliar los pasos del flujo de trabajo con parámetros y scripts para proporcionar más funcionalidad y control, según sea necesario. AEM Forms proporciona algunos pasos además de pasos de AEM disponibles de forma predeterminada. Para obtener una lista detallada de AEM Forms y de sus pasos, consulte [Pasos de referencia del flujo de trabajo de AEM](/help/sites-developing/workflows-step-ref.md) y [Flujo de trabajo centrado en Forms en OSGi: pasos de referencia](/help/forms/using/aem-forms-workflow.md).

AEM proporciona una interfaz de usuario intuitiva para crear un modelo del flujo de trabajo siguiendo los pasos proporcionados. Para obtener instrucciones paso a paso para crear un modelo del flujo de trabajo, consulte [Creación de modelos de flujo de trabajo](/help/sites-developing/workflows-models.md). El siguiente ejemplo proporciona instrucciones paso a paso para crear un modelo del flujo de trabajo para un flujo de trabajo de aprobación y revisión:

>[!NOTE]
>
>Debe ser miembro del grupo de editor del flujo de trabajo para crear o editar un modelo del flujo de trabajo.

### Creación de un modelo para un flujo de trabajo de aprobación y revisión {#create-a-model-for-an-approval-and-review-workflow}

El flujo de trabajo de aprobación y revisión corresponde a las tareas que requieren intervención humana para tomar decisiones. En el siguiente ejemplo se crea un modelo del flujo de trabajo para una solicitud de préstamo hipotecario que debe rellenar un agente bancario de la oficina principal. Una vez completada la solicitud, se envía para su aprobación. Posteriormente, la solicitud aprobada se envía al solicitante para que la firme utilizando Acrobat Sign.

A continuación, puede encontrar el ejemplo como paquete adjunto. Importe e instale el ejemplo mediante el administrador de paquetes. También puede realizar los siguientes pasos para crear manualmente el modelo del flujo de trabajo para la solicitud:

En el ejemplo se crea un modelo del flujo de trabajo con una solicitud hipotecaria que rellenará un agente bancario de la oficina principal. Una vez completada, la solicitud se envía para su aprobación. Posteriormente, la aplicación aprobada se envía al cliente para que la firme mediante Acrobat Sign. Puede importar e instalar el ejemplo mediante el administrador de paquetes.

[Obtener archivo](assets/example-mortgage-loan-application.zip)

1. Abra la consola Modelos de flujo de trabajo. La URL predeterminada es `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Seleccione **[!UICONTROL Crear]** y, a continuación, **[!UICONTROL Crear modelo]**. Aparecerá el cuadro de diálogo Agregar modelo del flujo de trabajo.
1. Escriba el **[!UICONTROL Título]** y el **[!UICONTROL Nombre]** (opcional). Por ejemplo, una solicitud hipotecaria. Pulse **[!UICONTROL Listo]**.
1. Seleccione el modelo del flujo de trabajo recién creado y pulse **Editar.** Ahora puede agregar pasos al flujo de trabajo para crear lógica empresarial. La primera vez que cree un modelo del flujo de trabajo, contendrá:

   * Los pasos: Inicio del flujo y Fin del flujo. Estos pasos representan el principio y el final del flujo de trabajo. Estos pasos son obligatorios y no se pueden editar ni eliminar.
   * Un ejemplo de paso de participante denominado Paso 1. Este paso está configurado para asignar un elemento de trabajo al administrador. Elimine este paso.

1. Habilitar las notificaciones por correo electrónico. Puede configurar el flujo de trabajo centrado en Forms en OSGi para enviar notificaciones por correo electrónico a los usuarios o a los usuarios asignados. Realice las siguientes configuraciones para habilitar las notificaciones por correo electrónico:

   1. Vaya al administrador de configuración de AEM en `https://[server]:[port]/system/console/configMgr`.
   1. Abra la configuración de **[!UICONTROL Day CQ Mail Service]**. Especifique un valor para el **[!UICONTROL nombre del host del servidor SMTP]**, **[!UICONTROL el puerto del servidor SMTP]** y **[!UICONTROL los campos de la dirección “Desde”]**. Haga clic en **[!UICONTROL Guardar]**.
   1. Abra la configuración de **[!UICONTROL Day CQ Link Externalizer]**. En el campo **[!UICONTROL Dominios]** especifique el nombre del host o la dirección IP real y el número de puerto para las instancias locales, Autor y Publicación. Haga clic en **[!UICONTROL Guardar]**.

1. Crear fases del flujo de trabajo. Un flujo de trabajo puede tener varias fases. Estas fases se muestran en la bandeja de entrada AEM y en el progreso del informe del flujo de trabajo.

   Para definir una fase, pulse el icono de ![info-círculo](assets/info-circle.png) para abrir las propiedades del modelo del flujo de trabajo, abra la pestaña **[!UICONTROL Fases]**, agregue fases para el modelo del flujo de trabajo y pulse **[!UICONTROL Guardar y cerrar]**. Para la solicitud de hipoteca de ejemplo, cree fases: solicitud del préstamo, estado de la solicitud del préstamo, documentos a firmar y documento del préstamo firmado.

1. Arrastre y suelte el explorador de fases **[!UICONTROL Asignar tarea]** al modelo del flujo de trabajo. Conviértalo en el primer paso del modelo.

   El componente Asignar tarea asigna la tarea que ha creado el flujo de trabajo, a un usuario o grupo. Además de asignar la tarea, puede utilizar el componente para especificar un formulario adaptable o un PDF no interactivo para la tarea. El formulario adaptable es necesario para aceptar los datos que han introducido los usuarios y un PDF no interactivo o un formulario adaptable de solo lectura solo se utiliza para revisar los flujos de trabajo.

   También puede utilizar el paso para controlar el comportamiento de la tarea. Por ejemplo, al crear un documento de registro automático, asignar la tarea a un usuario o grupo específico, la ruta de los datos enviados, la ruta de los datos que se van a rellenar previamente y las acciones predeterminadas. Para obtener información detallada sobre las opciones del paso Asignar tarea, consulte el documento [Flujo de trabajo centrado en Forms en OSGi: pasos de referencia](/help/forms/using/aem-forms-workflow.md).

   ![workflow-editor](assets/workflow-editor.png)

   Para el ejemplo de la solicitud de la hipoteca, configure el paso Asignar tarea para utilizar un formulario adaptable de solo lectura y mostrar el documento PDF una vez que se haya completado la tarea. Además, seleccione el grupo de usuarios autorizado para aprobar la solicitud del préstamo. En la pestaña **[!UICONTROL Acciones]**, deshabilite la opción **[!UICONTROL Enviar]**. Especifique un **[!UICONTROL Variable de ruta]**. Por ejemplo, actionTaken. Además, agregue las rutas Aprobar y Rechazar. Las rutas se muestran como acciones independientes (botones) en la bandeja de entrada AEM. El flujo de trabajo selecciona una rama en función de la acción (botón) que pulse un usuario.

   Puede importar el paquete de ejemplo, que está disponible para descargar al principio de la sección, para el conjunto completo de valores de todos los campos del paso Asignar tarea configurado, para el ejemplo de solicitud de hipoteca.

1. Arrastre y suelte el componente OR Split desde el explorador de pasos al modelo del flujo de trabajo. OR Splits crea una división en el flujo de trabajo, tras la cual solo una rama está activa. Este paso le permite introducir rutas de procesamiento condicionales en su flujo de trabajo. Los pasos del flujo de trabajo se agregan a cada rama según sea necesario.

   Abra las propiedades de la división OR y agregue los siguientes fragmentos de código a Branch1 y Branch2. Estos fragmentos de código ayudan a elegir una rama basada en la acción del usuario en AEM Bandeja de entrada.

   **Fragmento de código para la Rama 1**

   Cuando el usuario pulse **[!UICONTROL Aprobar]** en la bandeja de entrada AEM, se activará la rama 1.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **Fragmento de código para la Rama 2**

   Cuando el usuario pulse **[!UICONTROL Rechazar]** en la bandeja de entrada AEM, se activará la rama 2.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. Agregue otros pasos del flujo de trabajo para crear la lógica empresarial.

   Para el ejemplo de la hipoteca, agregue un documento de registro generado, dos pasos de la asignación de tareas y un paso del documento de firma a la rama 1 del modelo, como se muestra en la siguiente imagen. Un paso de la asignación de tareas es mostrar y enviar **documentos de préstamo a firmar al solicitante** y otro componente de asignación de tareas es **mostrar documentos firmados**. Además, agregue un componente de la asignación de tareas a la rama 2. Se activará cuando un usuario pulse Rechazar en la bandeja de entrada AEM.

   Para obtener el conjunto completo de valores de todos los campos de los pasos de la asignación de tareas, el paso Documento de registro y el de documento de firma configurado para, por ejemplo, la solicitud de hipoteca, importe el paquete de ejemplo, disponible para descargar al principio de esta sección.

   El modelo del flujo de trabajo está listo. Puede iniciar el flujo de trabajo mediante varios métodos. Para obtener más información, consulte [Iniciar un flujo de trabajo centrado en Forms en OSGi](#launch).

   ![workflow-editor-mortgage](assets/workflow-editor-mortgage.png)

## Crear una solicitud de flujo de trabajo centrada en formularios  {#create-a-forms-centric-workflow-application}

La solicitud es el formulario adaptable asociado al flujo de trabajo. Cuando una solicitud se envía a través de la bandeja de entrada, inicia el flujo de trabajo asociado. Para que un flujo de trabajo de Forms esté disponible como solicitud en la bandeja de entrada de AEM y la aplicación de AEM Forms, haga lo siguiente para crear una solicitud del flujo de trabajo:

>[!NOTE]
>
>Debe ser miembro del grupo fd-administrator para poder crear y administrar solicitudes de flujo de trabajo.

1. En la instancia de autor de AEM, vaya a ![herramientas](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL Administrar aplicación de flujo de trabajo]** y toques **[!UICONTROL Crear]**.
1. En la ventana Crear aplicación de flujo de trabajo , introduzca entradas para los campos siguientes y pulse **[!UICONTROL Crear]**. Se creará una solicitud nueva que aparecerá en la pantalla Solicitudes de flujo de trabajo.

<table> 
 <tbody> 
  <tr> 
   <td>Campo</td> 
   <td>Descripción</td> 
  </tr> 
  <tr> 
   <td>Título</td> 
   <td>El título se ve en la bandeja de entrada AEM y ayuda a los usuarios a elegir una solicitud. Haga que siga siendo descriptivo. Por ejemplo, la solicitud de apertura de una cuenta de ahorros.<br /> </td> 
  </tr> 
  <tr> 
   <td>Nombre </td> 
   <td>Especifique el nombre de la solicitud. Todos los caracteres que no sean letras, números, guiones o guiones bajos se sustituirán por guiones. </td> 
  </tr> 
  <tr> 
   <td>Descripción</td> 
   <td>La descripción es visible en la bandeja de entrada AEM. Proporcione información detallada sobre la solicitud en los campos de descripción. Por ejemplo, Finalidad de la solicitud.<br /> </td> 
  </tr> 
  <tr> 
   <td>Formulario adaptable</td> 
   <td><p>Especifique la ruta de un formulario adaptable. Cuando un usuario inicia una solicitud, se muestra el formulario adaptable especificado.</p> <p><strong>Nota</strong>: Las solicitudes de flujo de trabajo no admiten formularios ni documentos PDF que tengan más de una página o que requieran desplazamiento en Apple iPad. Cuando se abre una solicitud en Apple iPad y el formulario adaptable o el documento PDF es más largo que una página, se pierden los campos y el contenido del formulario de la segunda página.</p> </td> 
  </tr> 
  <tr> 
   <td>Grupo de acceso</td> 
   <td><p>Seleccionar un grupo. La solicitud solo es visible en la bandeja de entrada AEM para los miembros del grupo seleccionado. La opción de grupo de acceso hace que todos los grupos del grupo del flujo de trabajo de usuarios estén disponibles para seleccionarlos. </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>Servicio de rellenado previo</td> 
   <td>Seleccione un <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">servicio de rellenado previo</a> para el formulario adaptable.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modelo de flujo de trabajo</td> 
   <td>Seleccione un <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">modelo de flujo de trabajo</a> para la solicitud. Un modelo de flujo de trabajo consiste en la lógica y el flujo del proceso empresarial. </td> 
  </tr> 
  <tr> 
   <td>Ruta del archivo de datos</td> 
   <td>Especifique la ruta del archivo de datos en el repositorio crx. La ruta es relativa a la carga útil del formulario adaptable y contiene el nombre del archivo de datos. Incluya siempre el nombre completo del archivo, incluida la extensión, si corresponde. Por ejemplo, [carga útil]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Ruta de archivos adjuntos</td> 
   <td>Especifique la ruta de la carpeta de archivos adjuntos en el repositorio crx. La ruta de acceso de datos adjuntos es relativa a la ubicación de carga útil. Por ejemplo, [carga útil]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Documento de ruta de registro</td> 
   <td>Especifique la ruta del archivo Documento de registro en el repositorio crx. La ruta es relativa a la ubicación de carga útil del formulario adaptable. Incluya siempre el nombre completo del archivo, incluida la extensión, si corresponde. Por ejemplo, [carga útil]/DOR/creditcard.pdf.</td> 
  </tr> 
 </tbody> 
</table>

## Iniciar un flujo de trabajo centrado en Forms en OSGi {#launch}

Puede iniciar o habilitar un flujo de trabajo centrado en Forms mediante:

* [El envío de una solicitud desde la bandeja de entrada AEM](#inbox)
* [Enviar una aplicación desde la aplicación de AEM Forms](#afa)

* [Enviar un formulario adaptable](#af)
* [Usar una carpeta inspeccionada](#watched)

* [El envío de una comunicación interactiva o una carta](#letter)

### El envío de una solicitud desde la bandeja de entrada AEM {#inbox}

La solicitud de flujo de trabajo que ha creado está disponible como solicitud en la bandeja de entrada. Los usuarios que sean miembros del grupo del flujo de trabajo de usuarios pueden rellenar y enviar la solicitud que activa el flujo de trabajo asociado. Para obtener información sobre el uso de la bandeja de entrada de AEM para enviar solicitudes y administrar tareas, consulte [Administrar solicitudes y tareas de Forms en la bandeja de entrada de AEM](/help/forms/using/manage-applications-inbox.md).

### Enviar una aplicación desde la aplicación de AEM Forms {#afa}

La aplicación de AEM Forms se sincroniza con un servidor de AEM Forms y le permite realizar cambios en los datos del formulario, las tareas, las aplicaciones de flujo de trabajo y la información guardada (borradores/plantillas) en su cuenta. Para obtener más información, consulte [aplicación de AEM Forms](/help/forms/using/aem-forms-app.md) y artículos relacionados.

### Enviar un formulario adaptable {#af}

Puede configurar las acciones de envío de un formulario adaptable para iniciar un flujo de trabajo al enviar el formulario adaptable. Los formularios adaptables proporcionan la acción de envío **[!UICONTROL Invocar un flujo de trabajo de AEM]** para iniciar un flujo de trabajo al enviar un formulario adaptable. Para obtener información detallada sobre la acción de envío, consulte [Configurar la acción de envío](/help/forms/using/configuring-submit-actions.md). Para enviar un formulario adaptable a través de la aplicación de AEM Forms, habilite Sincronizar con la aplicación de AEM Forms en las propiedades del formulario adaptable.

Puede configurar un formulario adaptable para sincronizar, enviar y habilitar un flujo de trabajo desde la aplicación de AEM Forms. Para obtener más información, consulte [trabajar con un formulario](/help/forms/using/working-with-form.md).

### Usar una carpeta vigilada {#watched}

Un administrador (un miembro del grupo de administradores de fd) puede configurar una carpeta de red para ejecutar un flujo de trabajo preconfigurado cuando un usuario coloca un archivo (como un archivo PDF) en la carpeta. Una vez finalizado el flujo de trabajo, puede guardar el archivo resultante en una carpeta de salida especificada. Esta carpeta se conoce como [Carpeta vigilada](/help/forms/using/watched-folder-in-aem-forms.md). Realice el siguiente procedimiento para configurar una carpeta vigilada para iniciar un flujo de trabajo:

1. En la instancia de autor de AEM, vaya a ![herramientas](assets/tools.png) **[!UICONTROL Forms > Configurar carpeta vigilada]**. Se mostrará una lista de las carpetas vigiladas ya configuradas.
1. Pulse **[!UICONTROL Nuevo]**. Se mostrará una lista de campos. Especifique un valor para los siguientes campos para configurar una carpeta vigilada para un flujo de trabajo:

<table> 
 <tbody> 
  <tr> 
   <td>Campo</td> 
   <td>Descripción</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Nombre</span></td> 
   <td>Especifique el nombre de la carpeta vigilada. Este campo solo admite caracteres alfanuméricos.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Ruta </span></td> 
   <td>Especifique la ubicación física de la carpeta vigilada. En un entorno agrupado, utilice una carpeta de red compartida a la que se pueda acceder desde el nodo de clúster de AEM.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Procesar archivos mediante</span></td> 
   <td>Seleccione la opción <span class="uicontrol">Flujo de trabajo </span>. </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Modelo de flujo de trabajo</span></td> 
   <td>Seleccione un modelo de flujo de trabajo.<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Patrón de archivo de salida</span></td> 
   <td>Especifique la estructura de directorios para los archivos y directorios de salida. También puede especificar un patrón <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">para archivos y directorios de salida</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. Pulse **[!UICONTROL Avanzadas]**. Especifique un valor para el campo siguiente y toque **[!UICONTROL Crear]**. La carpeta vigilada está configurada para iniciar un flujo de trabajo. Ahora, cada vez que se coloque un archivo en el directorio de entrada de la carpeta vigilada, se activará el flujo de trabajo especificado.

   | Campo | Descripción |
   |---|---|
   | Filtro de asignador de cargas útiles | Cuando se cree una carpeta vigilada, se creará una estructura de carpetas en el repositorio crx. La estructura de carpetas puede servir como carga útil para el flujo de trabajo. Puede escribir un script para asignar un flujo de trabajo de AEM y aceptar entradas de la estructura de carpetas vigilada. Una implementación predeterminada está disponible y se enumera en el filtro asignador de cargas útiles. Si no tiene una implementación personalizada, seleccione la implementación predeterminada. |

   La pestaña Avanzado contiene más campos. La mayoría de estos campos contienen un valor predeterminado. Para obtener más información sobre todos los campos, consulte el artículo [Crear o configurar una carpeta vigilada](/help/forms/using/creating-configure-watched-folder.md).

### Enviar una comunicación interactiva o una carta {#letter}

Puede asociar y ejecutar un flujo de trabajo centrado en Forms en OSGi al enviar una comunicación interactiva o una carta. En Administración de correspondencia, los flujos de trabajo se utilizan para las cartas y las comunicaciones interactivas posteriores al procesamiento. Por ejemplo, enviar por correo electrónico, imprimir, enviar por fax o archivar cartas finales. Para ver los pasos detallados, consulte [Procesamiento posterior de comunicaciones interactivas y cartas](/help/forms/using/submit-letter-topostprocess.md).

## Configuraciones adicionales {#additional-configurations}

### Configurar el servicio de correo electrónico {#configure-email-service}

Puede utilizar los pasos Asignar tarea y Enviar correo electrónico de flujos de trabajo de AEM para enviar un correo electrónico. Realice los siguientes pasos para especificar los servidores de correo electrónico y otras configuraciones necesarias para enviar correo electrónico:

1. Vaya al administrador de configuración de AEM en `https://[server]:[port]/system/console/configMgr`.
1. Abra la configuración de **[!UICONTROL Day CQ Mail Service]**. Especifique un valor para el **[!UICONTROL nombre del host del servidor SMTP]**, **[!UICONTROL el puerto del servidor SMTP]** y **[!UICONTROL los campos de la dirección “Desde”]**. Haga clic en **[!UICONTROL Guardar]**.
1. Abra la configuración de **[!UICONTROL Day CQ Link Externalizer]**. En el campo **[!UICONTROL Dominios]** especifique el nombre del host o la dirección IP real y el número de puerto para las instancias locales, Autor y Publicación. Haga clic en **[!UICONTROL Guardar]**.

### Purgar instancias del flujo de trabajo {#purge-workflow-instances}

Al minimizar el número de instancias del flujo de trabajo, aumenta el rendimiento del motor de flujos de trabajo, por lo que puede depurar con regularidad las instancias del flujo de trabajo completadas o en ejecución desde el repositorio. Para obtener información detallada, consulte [Depuración regular de instancias de flujo de trabajo](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
