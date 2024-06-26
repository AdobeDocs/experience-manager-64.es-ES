---
title: Creación de modelos de flujo de trabajo
seo-title: Creating Workflow Models
description: Puede crear un modelo de flujo de trabajo para definir la serie de pasos que se ejecutan cuando un usuario inicia el flujo de trabajo.
seo-description: You create a workflow model to define the series of steps executed when a user starts the workflow.
uuid: 53d94176-4d5f-4ab3-9628-6b7d44f81139
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 9d2dba11-0d2d-4aed-b941-c8ade9bb7bfa
exl-id: d9c9db5f-9788-460f-ac09-88dd3c911edd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 4%

---

# Creación de modelos de flujo de trabajo{#creating-workflow-models}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Para usar la IU clásica, consulte la [Documentación de AEM 6.3](https://helpx.adobe.com/experience-manager/6-3/sites-developing/workflows-models.html) como referencia.

Puede crear un [modelo de flujo de trabajo](/help/sites-developing/workflows.md#model) para definir la serie de pasos que se ejecutan cuando un usuario inicia el flujo de trabajo. También puede definir propiedades del modelo, como si el flujo de trabajo es transitorio o utiliza varios recursos.

Cuando un usuario inicia un flujo de trabajo, se inicia una instancia; este es el modelo de tiempo de ejecución correspondiente, creado al [Sincronización](#sync-your-workflow-generate-a-runtime-model) los cambios.

## Creación de un nuevo flujo de trabajo {#creating-a-new-workflow}

La primera vez que se crea un nuevo modelo de flujo de trabajo contiene:

* Los pasos, **[!UICONTROL Inicio de flujo]** y **[!UICONTROL Fin del flujo]**.

   Representan el principio y el final del flujo de trabajo. Estos pasos son obligatorios y no se pueden editar ni eliminar.

* Un ejemplo **Participante** step named **Paso 1**.

   Este paso está configurado para asignar un elemento de trabajo al iniciador del flujo de trabajo. Edite o elimine este paso y añada los pasos necesarios.

Para crear un nuevo flujo de trabajo con el editor:

1. Abra el **[!UICONTROL Modelos de flujo de trabajo]** consola; mediante **[!UICONTROL Herramientas]**, **[!UICONTROL Flujo de trabajo]**, **[!UICONTROL Modelos]** o, por ejemplo:

   [http://localhost:4502/aem/workflow](http://localhost:4502/aem/workflow)

1. Seleccione **[!UICONTROL Crear]** y, a continuación, **[!UICONTROL Crear modelo]**.
1. La variable **[!UICONTROL Agregar modelo de flujo de trabajo]** aparece en el cuadro de diálogo. Introduzca la variable **[!UICONTROL Título]** y **[!UICONTROL Nombre]** (opcional) antes de seleccionar **[!UICONTROL Listo]**.
1. El nuevo modelo se enumera en la **[!UICONTROL Modelos de flujo de trabajo]** consola.
1. Seleccione el nuevo flujo de trabajo y, a continuación, utilice [**[!UICONTROL Editar ]**para abrirlo y configurarlo](#editing-a-workflow):

   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>Si crea modelos mediante programación (utilizando un paquete crx), también puede crear una subcarpeta dentro de:
>
>`/var/workflow/models`
>
>Por ejemplo, `/var/workflow/models/prototypes`. 
>
>Esta carpeta se puede usar para [administrar el acceso a los modelos de esa carpeta](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that).

## Edición de un flujo de trabajo {#editing-a-workflow}

Puede editar cualquier modelo de flujo de trabajo existente para:

* [definir pasos](#adding-a-step-to-a-model) y [parámetros](#configuring-a-workflow-step)

* configurar las propiedades del flujo de trabajo, incluyendo [fases](#configuring-workflow-stages-that-show-workflow-progress), [si el flujo de trabajo es transitorio](#creating-a-transient-workflow) y/o [utiliza varios recursos](#configuring-a-workflow-for-multi-resource-support)

Edición de un [**Predeterminado o Heredado** flujo de trabajo (predeterminado)](#editing-a-default-or-legacy-workflow-for-the-first-time) tiene un paso adicional para garantizar que [copia segura](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) se toma antes de realizar los cambios.

Cuando se hayan completado las actualizaciones del flujo de trabajo, debe utilizar **[!UICONTROL Sincronización]** a **[!UICONTROL Generar un modelo de tiempo de ejecución]**. Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

### Sincronizar el flujo de trabajo: generar un modelo de tiempo de ejecución {#sync-your-workflow-generate-a-runtime-model}

**Sincronización** (derecha en la barra de herramientas del editor) genera un [modelo runtime](/help/sites-developing/workflows.md#runtime-model). El modelo de tiempo de ejecución es el modelo que se utiliza realmente cuando un usuario inicia un flujo de trabajo. Si no **[!UICONTROL Sincronización]** Los cambios no estarán disponibles durante la ejecución.

Cuando usted (o cualquier otro usuario) realicen cambios en el flujo de trabajo, debe utilizar **[!UICONTROL Sincronización]** para generar un modelo de tiempo de ejecución, incluso cuando los cuadros de diálogo individuales (por ejemplo, para los pasos) tienen sus propias opciones de guardado.

Cuando los cambios se sincronizan con el modelo de tiempo de ejecución (guardado), **[!UICONTROL Sincronizado]** se muestra en su lugar.

Algunos pasos tienen campos obligatorios o una validación integrada. Cuando no se cumplan estas condiciones, se mostrará un error cuando intente **[!UICONTROL Sincronización]** el modelo. Por ejemplo, cuando no se ha definido ningún participante para un **[!UICONTROL Participante]** paso:

![wf-21](assets/wf-21.png)

### Edición de un flujo de trabajo predeterminado o heredado por primera vez {#editing-a-default-or-legacy-workflow-for-the-first-time}

Cuando abra un [Modelo predeterminado y/o heredado](/help/sites-developing/workflows.md#workflow-types) para edición:

* La variable **[!UICONTROL Pasos]** El explorador no está disponible (lado izquierdo).
* Hay un **[!UICONTROL Editar]** acción disponible en la barra de herramientas (lado derecho).
* Inicialmente, el modelo y sus propiedades se presentan en modo de solo lectura como:

   * Los flujos de trabajo predeterminados se encuentran en `/libs`
   * Los flujos de trabajo heredados se encuentran en `/etc`

Selección **[!UICONTROL Editar]** será:

* llevar una copia del flujo de trabajo a `/conf`
* haga que la variable **[!UICONTROL Pasos]** explorador disponible
* permite realizar cambios

>[!NOTE]
>
>Consulte [Ubicaciones de los modelos de flujo de trabajo](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) para obtener más información.

![wf-22](assets/wf-22.png)

### Adición de un paso a un modelo {#adding-a-step-to-a-model}

Deberá añadir pasos al modelo para representar la actividad que se va a realizar: cada paso realiza una actividad específica. Hay una selección de componentes de paso disponibles en una instancia de AEM estándar.

Al editar un modelo, los pasos disponibles aparecen en los distintos grupos de la variable **[!UICONTROL Pasos]** explorador. Por ejemplo:

![wf-10](assets/wf-10.png)

>[!NOTE]
>
>Para obtener información sobre los componentes del paso principal instalados con AEM, consulte [Referencia de pasos del flujo de trabajo](/help/sites-developing/workflows-step-ref.md).

**Adición de un paso a un modelo**:

1. Abra un modelo de flujo de trabajo existente para editarlo. En el **[!UICONTROL Modelo de flujos de trabajo]** consola, seleccione el modelo requerido y, a continuación, **[!UICONTROL Editar]**.
1. Abra el **[!UICONTROL Pasos]** explorador; using **[!UICONTROL Alternar panel lateral]**, en el extremo izquierdo de la barra de herramientas superior. Aquí puede hacer lo siguiente:

   * **[!UICONTROL Filtro]** para pasos específicos.
   * Utilice el selector desplegable para limitar la selección a un grupo específico de pasos.
   * Seleccione el icono Mostrar descripción ![wf-step-icon](assets/wf-stepinfo-icon.png) para mostrar más detalles sobre el paso adecuado.

   ![wf-02](assets/wf-02.png)

1. Arrastre los pasos correspondientes a la ubicación requerida en el modelo.

   Por ejemplo, una **[!UICONTROL Etapa de participante]**.

   Después de añadirlo al flujo, puede [configurar el paso](#configuring-a-workflow-step).

   ![wf-03](assets/wf-03.png)

1. Agregue tantos pasos u otras actualizaciones como sea necesario.

   En tiempo de ejecución, los pasos se ejecutan en el orden en que aparecen en el modelo. Después de agregar componentes de paso, puede arrastrarlos a una ubicación diferente del modelo.

   También puede copiar, cortar, pegar, agrupar o eliminar pasos existentes; como con el [editor de páginas.](/help/sites-authoring/editing-content.md)

   Los pasos divididos también se pueden contraer o expandir con la opción de la barra de herramientas: ![wf-contraseexpand-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png)

1. Confirme los cambios con **[!UICONTROL Sincronización]** (barra de herramientas del editor) para generar el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

### Configuración de un paso de flujo de trabajo {#configuring-a-workflow-step}

Puede **Configurar** y personalizar el comportamiento de un paso de flujo de trabajo mediante el **[!UICONTROL Propiedades de los pasos]** para abrir el Navegador.

1. Para abrir el **[!UICONTROL Propiedades de los pasos]** para un paso:

   * Pulse el paso en el modelo de flujo de trabajo y seleccione **[!UICONTROL Configurar]** en la barra de herramientas de componentes.
   * Haga doble clic en el paso .

   >[!NOTE]
   >
   >Para obtener información sobre los componentes del paso principal instalados con AEM, consulte [Referencia de pasos del flujo de trabajo](/help/sites-developing/workflows-step-ref.md).

1. Configure las variables **[!UICONTROL Propiedades de los pasos]** según sea necesario; las propiedades disponibles dependen del tipo de paso; también pueden haber varias pestañas disponibles. Por ejemplo, el valor predeterminado **[!UICONTROL Etapa de participante]**, presente en un nuevo flujo de trabajo como `Step 1`:

   ![wf-11](assets/wf-11.png)

1. Confirme sus actualizaciones con el visto.
1. Confirme los cambios con **[!UICONTROL Sincronización]** (barra de herramientas del editor) para generar el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

### Creación de un flujo de trabajo transitorio {#creating-a-transient-workflow}

Puede crear un [Transitorio](/help/sites-developing/workflows.md#transient-workflows) modelo de flujo de trabajo al crear un nuevo modelo o al editar uno existente:

1. Abra el modelo de flujo de trabajo para [editar](#editing-a-workflow).
1. Select **[!UICONTROL Propiedades del modelo de flujo de trabajo]** en la barra de herramientas.
1. En el cuadro de diálogo, active **[!UICONTROL Flujo de trabajo transitorio]** (o desactivar si es necesario):

   ![wf-07](assets/wf-07.png)

1. Confirme el cambio con **[!UICONTROL Guardar y cerrar]**; seguido de **[!UICONTROL Sincronización]** (barra de herramientas del editor) para generar el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

>[!NOTE]
>
>Al ejecutar un flujo de trabajo en [transient](/help/sites-developing/workflows.md#transient-workflows) modo AEM no almacena ningún historial de flujo de trabajo. Por lo tanto, [Cronología](/help/sites-authoring/basic-handling.md#timeline) no muestra ninguna información relacionada con ese flujo de trabajo. [](/help/sites-authoring/basic-handling.md#timeline)

### Hacer que los modelos de flujo de trabajo estén disponibles en la interfaz de usuario táctil {#make-workflow-models-available-in-touchui}

Si hay un modelo de flujo de trabajo en la IU clásica, pero falta en el menú emergente de selección en la **[!UICONTROL Cronología]** de la interfaz de usuario táctil y, a continuación, siga la configuración para que esté disponible. Los siguientes pasos ilustran el uso del modelo de flujo de trabajo llamado **[!UICONTROL Solicitud de activación]**.

1. Confirme que el modelo no está disponible en la IU táctil. Acceder a un recurso mediante `/assets.html/content/dam` ruta. Seleccione un recurso. Apertura **[!UICONTROL Cronología]** en el carril izquierdo. Haga clic en **[!UICONTROL Iniciar flujo de trabajo]** y confirme que **[!UICONTROL Solicitud de activación]** no está presente en la lista emergente.

1. Navegar por **[!UICONTROL Herramientas > General > Etiquetado]**. Select **[!UICONTROL Flujo de trabajo]**.

1. Select **[!UICONTROL Crear > Crear etiqueta]**. Establezca **[!UICONTROL Título]** como `DAM` y **[!UICONTROL Nombre]** como `dam`. Seleccione **[!UICONTROL Enviar]**.
   ![Creación de una etiqueta en el modelo de flujo de trabajo](assets/workflow_create_tag.png)

1. Navegue hasta **[!UICONTROL Herramientas > Flujo de trabajo > Modelos]**. Select **[!UICONTROL Solicitud de activación]** y, a continuación, seleccione **[!UICONTROL Editar]**.

1. Select **[!UICONTROL Editar]** y, a continuación, abra **[!UICONTROL Propiedades del modelo de flujo de trabajo]**. Vaya a la **[!UICONTROL Básico]** pestaña .

1. Agregar `Workflow : DAM` a **[!UICONTROL Etiquetas]** campo . Confirme la selección con la marca de verificación (visto).

1. Confirme la adición de la etiqueta con **[!UICONTROL Guardar y cerrar]**.
   ![Editar propiedades de página del modelo](assets/workflow_model_edit_activation1.png)

1. Complete el proceso con **[!UICONTROL Sincronización]**. El flujo de trabajo ya está disponible en la IU táctil.

### Configuración de un flujo de trabajo para compatibilidad con varios recursos {#configuring-a-workflow-for-multi-resource-support}

Puede configurar un modelo de flujo de trabajo para [Compatibilidad con varios recursos](/help/sites-developing/workflows.md#multi-resource-support) al crear un modelo nuevo o al editar uno existente:

1. Abra el modelo de flujo de trabajo para [editar](#editing-a-workflow).
1. Select **[!UICONTROL Propiedades del modelo de flujo de trabajo]** en la barra de herramientas.

1. En el cuadro de diálogo, active **[!UICONTROL Compatibilidad con varios recursos]** (o desactivar si es necesario):

   ![wf-08](assets/wf-08.png)

1. Confirme el cambio con **[!UICONTROL Guardar y cerrar]**; seguido de **[!UICONTROL Sincronización]** (barra de herramientas del editor) para generar el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

### Configuración de etapas de flujo de trabajo (que muestran el progreso del flujo de trabajo) {#configuring-workflow-stages-that-show-workflow-progress}

[Etapas del flujo de trabajo](/help/sites-developing/workflows.md#workflow-stages) ayuda a visualizar el progreso de un flujo de trabajo al administrar tareas.

>[!CAUTION]
>
>Si las etapas del flujo de trabajo se definen en **[!UICONTROL Propiedades de página]**, pero no se utiliza para ninguno de los pasos del flujo de trabajo, la barra de progreso no muestra ningún progreso (independientemente del paso actual del flujo de trabajo).

Las etapas que estarán disponibles se definen en los modelos de flujo de trabajo; los modelos de flujo de trabajo existentes se pueden actualizar para incluir definiciones de escenario. Puede definir cualquier número de etapas para el modelo de flujo de trabajo.

Para definir **[!UICONTROL Etapas]** para el flujo de trabajo:

1. Abra el modelo de flujo de trabajo para editarlo.
1. Select **[!UICONTROL Propiedades del modelo de flujo de trabajo]** en la barra de herramientas. A continuación, abra el **[!UICONTROL Etapas]** pestaña .
1. Añada (y posicione) su **[!UICONTROL Etapas]**. Puede definir cualquier número de etapas para el modelo de flujo de trabajo.

   Por ejemplo:

   ![wf-08-1](assets/wf-08-1.png)

1. Haga clic en **[!UICONTROL Guardar y cerrar]** para guardar las propiedades.
1. Asigne un escenario a cada uno de los pasos del modelo de flujo de trabajo. Por ejemplo:

   ![wf-09](assets/wf-09.png)

   Se puede asignar un escenario a más de un paso. Por ejemplo:

   | **Paso** | **Escenario** |
   |---|---|
   | Etapa 1 | Crear |
   | Etapa 2 | Crear |
   | Etapa 3 | Revisión |
   | Etapa 4 | Aprobar |
   | Etapa 5 | Aprobar |
   | Etapa 6 | Completar |

1. Confirme los cambios con **[!UICONTROL Sincronización]** (barra de herramientas del editor) para generar el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

## Exportación de un modelo de flujo de trabajo en un paquete {#exporting-a-workflow-model-in-a-package}

1. Cree un nuevo paquete utilizando la variable [Administrador de paquetes](/help/sites-administering/package-manager.md#package-manager):

   1. Vaya al Administrador de paquetes mediante **[!UICONTROL Herramientas]**, **[!UICONTROL Implementación]**, **[!UICONTROL Paquetes]**.
   1. Haga clic en **[!UICONTROL Crear paquete]**.
   1. Especifique la variable **[!UICONTROL Nombre del paquete]**, y cualquier otro detalle según sea necesario.
   1. Haga clic en **[!UICONTROL Aceptar]**.

1. Haga clic en **[!UICONTROL Editar]** en la barra de herramientas del nuevo paquete.

1. Abra el **[!UICONTROL Filtros]** pestaña .

1. Select **[!UICONTROL Agregar filtro]** y especifique la ruta del modelo de flujo de trabajo *diseño*:

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   Haga clic en **[!UICONTROL Listo]**.

1. Select **[!UICONTROL Agregar filtro]** y especifique la ruta de *tiempo de ejecución* modelo de flujo de trabajo:

   `/var/workflow/models/<*your-model-name*>`

   Haga clic en **[!UICONTROL Listo]**.

1. Añada filtros adicionales para cualquier secuencia de comandos personalizada que utilice el modelo.
1. Haga clic en **[!UICONTROL Guardar]** para confirmar las definiciones del filtro.
1. Select **[!UICONTROL Generar]** de la barra de herramientas de la definición del paquete.
1. Select **[!UICONTROL Descargar]** en la barra de herramientas del paquete.

## Uso de flujos de trabajo para procesar envíos de formularios {#using-workflows-to-process-form-submissions}

Puede configurar un formulario para que lo procese el flujo de trabajo seleccionado. Cuando los usuarios envían el formulario, se crea una nueva instancia de flujo de trabajo con los datos del envío del formulario como carga útil.

Para configurar el flujo de trabajo que se utilizará con el formulario:

1. Cree una nueva página y ábrala para editarla.
1. Agregue un **[!UICONTROL Formulario]** a la página.
1. Configure las variables **[!UICONTROL Inicio del formulario]** que apareció en la página.
1. Uso **[!UICONTROL Iniciar flujo de trabajo]** para seleccionar el flujo de trabajo deseado de los disponibles:

   ![wf-12](assets/wf-12.png)

1. Confirme la nueva configuración de formulario con la marca de verificación.

## Flujos de trabajo de prueba {#testing-workflows}

Es una buena práctica a la hora de probar un flujo de trabajo utilizar una variedad de tipos de carga útil; incluyendo tipos diferentes de los para los que se ha desarrollado. Por ejemplo, si tiene intención de que el flujo de trabajo trate con Assets, pruébelo configurando una página como carga útil y asegúrese de que no arroja errores.

Por ejemplo, pruebe el nuevo flujo de trabajo de la siguiente manera:

1. [Inicio del modelo de flujo de trabajo](/help/sites-administering/workflows-starting.md) desde la consola.
1. Defina el **[!UICONTROL Carga útil]** y confirme.

1. Realice las acciones necesarias para que se ejecute el flujo de trabajo.
1. Monitorice los archivos de registro mientras se ejecuta el flujo de trabajo.

También puede configurar AEM para mostrar **[!UICONTROL DEBUG]** en los archivos de registro. Consulte [Registro](/help/sites-deploying/configure-logging.md) para obtener más información y cuando finalice el desarrollo, establezca la variable **[!UICONTROL Nivel de registro]** volver a **[!UICONTROL Información]**.

## Ejemplos {#examples}

### Ejemplo: Creación de un flujo de trabajo (simple) para aceptar o rechazar una solicitud de publicación {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

Para ilustrar algunas de las posibilidades de creación de un flujo de trabajo, el siguiente ejemplo crea una variación de la variable `Publish Example` flujo de trabajo.

1. [Creación de un nuevo modelo de flujo de trabajo](#creating-a-new-workflow).

   El nuevo flujo de trabajo contiene:

   * **[!UICONTROL Inicio de flujo]**
   * `Step 1`
   * **[!UICONTROL Fin de flujo]**

1. Eliminar `Step 1` (ya que es el tipo de paso incorrecto para este ejemplo):

   * Haga clic en el paso y seleccione **[!UICONTROL Eliminar]** en la barra de herramientas de componentes. Confirme la acción.

1. En el **[!UICONTROL Flujo de trabajo]** selección del navegador de pasos, arrastre un **[!UICONTROL Etapa de participante]** en el flujo de trabajo y colóquelo entre **[!UICONTROL Inicio de flujo]** y **[!UICONTROL Fin de flujo*]*.
1. Para abrir el cuadro de diálogo de propiedades:

   * Haga clic en el paso del participante y seleccione **[!UICONTROL Configurar]** en la barra de herramientas de componentes.
   * Haga doble clic en el paso del participante.

1. En el **[!UICONTROL Frecuentes]** tab enter `Validate Content` para ambas **[!UICONTROL Título]** y **[!UICONTROL Descripción]**.
1. Abra el **[!UICONTROL Usuario/Grupo]** pestaña:

   * Activar **[!UICONTROL Notificar al usuario por correo electrónico]**.
   * Select `Administrator` ( `admin`) para la variable **[!UICONTROL Usuario/Grupo]** campo .

   >[!NOTE]
   >
   >Para enviar correos electrónicos, [es necesario configurar el servicio de correo y los detalles de la cuenta de usuario](/help/sites-administering/notification.md).

1. Confirme las actualizaciones con la marca de verificación.

   Se le devolverá a la descripción general del modelo de flujo de trabajo, donde se habrá cambiado el nombre del paso del participante a `Validate Content`.

1. Arrastre un **[!UICONTROL División O]** en el flujo de trabajo y colóquelo entre `Validate Content` y **[!UICONTROL Fin del flujo]**.
1. Abra el **[!UICONTROL División O]** para la configuración.
1. Configuración de:

   * **[!UICONTROL Frecuentes]**: select **[!UICONTROL 2 ramas]**
   * **[!UICONTROL Rama 1]**: select **[!UICONTROL Ruta predeterminada]**.
   * **[!UICONTROL Rama 2]**: garantizar **[!UICONTROL Ruta predeterminada]** no está seleccionado.

1. Confirme las actualizaciones a la **[!UICONTROL División OR]**.
1. Arrastre un **[!UICONTROL Etapa de participante]** en la rama izquierda, abra las propiedades, especifique los siguientes valores y confirme los cambios:

   * **[!UICONTROL Título]**: `Reject Publish Request`
   * **[!UICONTROL Usuario/Grupo]**: por ejemplo, `projects-administrators`
   * **[!UICONTROL Notificar al usuario por correo electrónico]**: Active esta opción para que el usuario reciba una notificación por correo electrónico.

1. Arrastre un **[!UICONTROL Paso de proceso]** en la rama derecha, abra las propiedades, especifique los siguientes valores y confirme los cambios:

   * **[!UICONTROL Título]**: `Publish Page as Requested`
   * **[!UICONTROL Proceso]**: select `Activate Page`. Este proceso publica la página seleccionada en las instancias del editor.

1. Haga clic en **[!UICONTROL Sincronización]** (barra de herramientas del editor) para generar el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

   El nuevo modelo de flujo de trabajo tendrá el siguiente aspecto:

   ![wf-13](assets/wf-13.png)

1. Aplique este flujo de trabajo a su página, de modo que cuando el usuario se mueva a **[!UICONTROL Completar]** el **[!UICONTROL Validar contenido]** , pueden seleccionar si desean **[!UICONTROL Publicar página como se solicitó]** o **[!UICONTROL Rechazar solicitud de publicación]**.

   ![chlimage_1-182](assets/chlimage_1-182.png)

### Ejemplo: Definición de una regla para una división OR {#example-defining-a-rule-for-an-or-split}

**[!UICONTROL División OR]** los pasos le permiten introducir rutas de procesamiento condicionales en el flujo de trabajo.

Para definir una regla O:

1. Cree dos secuencias de comandos y guárdelas en el repositorio, por ejemplo, en:

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   >
   >Las secuencias de comandos deben tener un [function `check()`](#function-check) que devuelve un valor booleano.

1. Edite el flujo de trabajo y añada la variable **[!UICONTROL División OR]** al modelo.
1. Editar las propiedades de **[!UICONTROL Rama 1]** del **[!UICONTROL División OR]**:

   * Defina esto como la variable **[!UICONTROL Ruta predeterminada]** configurando la variable **[!UICONTROL Valor]** a `true`.
   * Como **[!UICONTROL Regla]**, establezca la ruta en la secuencia de comandos. Por ejemplo:

      `/apps/myapp/workflow/scripts/myscript1.ecma`
   >[!NOTE]
   >
   >Si es necesario, puede cambiar el orden de las ramas.

1. Edite las propiedades del **[!UICONTROL Rama 2]** del **[!UICONTROL División OR]**.

   * Como **[!UICONTROL Regla]**, establezca la ruta en la otra secuencia de comandos. Por ejemplo:

      `/apps/myapp/workflow/scripts/myscript2.ecma`

1. Defina las propiedades de los pasos individuales de cada rama. Asegúrese de que la variable **[!UICONTROL Usuario/Grupo]** está configurado.
1. Haga clic en **Sincronización** (barra de herramientas del editor) para mantener los cambios en el modelo de tiempo de ejecución.

   Consulte [Sincronizar el flujo de trabajo](#sync-your-workflow-generate-a-runtime-model) para obtener más información.

#### Función Check() {#function-check}

>[!NOTE]
>
>Consulte [Uso de ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).

El siguiente script de ejemplo devuelve `true` si el nodo es un `JCR_PATH` ubicado bajo `/content/we-retail/us/en`:

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      } 
     } else {
      return false;
     }
}
```

### Ejemplo: Solicitud de activación personalizada {#example-customized-request-for-activation}

Puede personalizar cualquiera de los flujos de trabajo predeterminados. Para tener un comportamiento personalizado, superponga los detalles del flujo de trabajo adecuado.

Por ejemplo, **[!UICONTROL Solicitud de activación]**. Este flujo de trabajo se utiliza para publicar páginas en **[!UICONTROL Sitios]** y se activa automáticamente cuando un autor de contenido no tiene los derechos de replicación adecuados. Consulte [Personalización de la creación de páginas: personalización del flujo de trabajo de solicitud de activación](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow) para obtener más información.
