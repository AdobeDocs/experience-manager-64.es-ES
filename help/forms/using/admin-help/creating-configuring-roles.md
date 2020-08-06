---
title: Creación y configuración de funciones
seo-title: Creación y configuración de funciones
description: Obtenga información sobre cómo asociar usuarios y grupos con funciones que ya forman parte de la base de datos de Administración de usuarios. También puede crear, editar y eliminar funciones.
seo-description: Obtenga información sobre cómo asociar usuarios y grupos con funciones que ya forman parte de la base de datos de Administración de usuarios. También puede crear, editar y eliminar funciones.
uuid: e8e4331d-48e1-4fa9-8f44-f885f4ab1a54
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 737fb4d1-adef-47e1-9a0d-8cddd13132cb
translation-type: tm+mt
source-git-commit: ba04fe705a91717f1d9658d436056ebddda6be3a
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 0%

---


# Creación y configuración de funciones{#creating-and-configuring-roles}

Mediante las páginas web de Administración de usuarios, puede asociar usuarios y grupos con funciones que ya forman parte de la base de datos de Administración de usuarios. También puede crear, editar y eliminar funciones.

La Administración de usuarios tiene dos tipos de funciones:

**Funciones mutables:** Este tipo de rol se puede editar y eliminar, y los permisos de rol se pueden agregar y eliminar de estos tipos de rol. Cualquier función que cree se considerará una función mutable. Puede agregar o quitar usuarios y grupos asignados a funciones múltiples.

**Funciones inmutables:** Las funciones predeterminadas que se incluyen con Administración de usuarios son funciones inmutables. Estas funciones no se pueden editar ni eliminar. Sin embargo, puede agregar o eliminar usuarios y grupos asignados a funciones inmutables.

También se pueden crear funciones mutables e inmutables a través de las API de formularios AEM.

## Funciones predeterminadas {#default-roles}

Las siguientes funciones predeterminadas se incluyen en la base de datos de Administración de usuarios.

**usuario de la consola de administración:** Puede acceder a la consola de administración.

**Administrador de aplicaciones:** Puede utilizar todas las funciones de Workbench. Puede utilizar las páginas Aplicaciones y Servicios de la consola de administración para configurar propiedades, extremos y seguridad en tiempo de ejecución del servicio.

**Administrador de formularios AEM:** Puede realizar todas las tareas para todos los servicios instalados.

**Administrador de seguridad:** Controla la configuración de Administración de usuarios y administra los usuarios y grupos asociados a cualquier dominio del Administrador de usuarios

**Usuario de servicios:** Puede realizar vistas e invocar cualquier servicio

**Superadministrador:** Tiene acceso a toda la funcionalidad administrativa del sistema, incluidos los servicios

**Administrador de confianza:** Puede administrar la configuración de confianza PKI y las credenciales PKI que se administran desde la página Administración de almacén de confianza en la consola de administración

### Funciones predeterminadas adicionales {#additional-default-roles}

Se pueden incluir las siguientes funciones predeterminadas adicionales, según los componentes de formularios AEM que haya instalado

**Usuario de la aplicación de carga de Documento:** Puede cargar documentos con Flex Remoting.

**Administrador de Forms:** Puede realizar vistas y modificar la configuración desde la página de Forms en la Consola de administración

**Administrador de Contentspace de AEM formularios:** Puede vista y modificación de la configuración desde la página Content Services (obsoleto) en la consola de administración

**AEM formularios Contentspace User:** Puede iniciar sesión en las páginas web de ContentSpace (obsoleto)

**Administrador de Documentum Connector:** Puede vista y modificación de la configuración desde la página Connector for EMC Documentum en la consola de administración

**Administrador del conector de FileNet de formularios AEM:** Puede vista y modificación de la configuración desde la página Connector for IBM FileNet en la consola de administración

**AEM formularios de administrador de conector de IBM CM:** Puede vista y modificación de la configuración desde la página Connector for IBM Content Manager en la consola de administración

**Rights Management Administrador:** Realiza todas las tareas necesarias para todas las configuraciones de servidor en las páginas de Rights Management relevantes

**Usuario final Rights Management:** Puede acceder a las páginas web del usuario final Rights Management

**Usuario de invitación de Rights Management:** Puede invitar a usuarios

**Rights Management Administrar usuarios invitados y locales:** Puede realizar tareas necesarias para administrar todos los usuarios invitados y locales en las páginas de Rights Management relevantes

**Administrador de conjuntos de directivas de Rights Management:** Realiza todas las tareas necesarias para todos los conjuntos de políticas en las páginas de Rights Management relevantes

**Rights Management Super Administrator:** Realiza todas las tareas necesarias desde la página Rights Management

**Administrador de área de trabajo de formularios AEM:** Puede vista y modificación de la configuración desde la página Espacio de trabajo de la Consola de administración

***nota **: Flex Workspace está obsoleto para AEM versión de formularios.*

**Usuario de Workspace:** Puede iniciar sesión en la aplicación de usuario final de Workspace

**Administrador de salida:** Puede vista y modificación de la configuración desde la página Salida de la Consola de administración

**Administrador de PDFG:** Puede vista y modificación de la configuración desde la página Generador de archivos PDF en la consola de administración

**Usuario de PDFG:** Puede acceder a todas las funciones no administrativas de PDF Generator

**Aplicación web de extensiones de Acrobat Reader DC:** Puede utilizar la aplicación web de extensiones de Acrobat Reader DC

>[!NOTE]
>
>Los usuarios con determinados tipos de privilegios de administrador no pueden acceder a las páginas web del usuario final de Workspace por motivos de seguridad. Dado que estas páginas pueden existir fuera de un servidor de seguridad, permitir tareas de nivel de administración podría suponer un riesgo para la seguridad. Solo los usuarios que tengan los privilegios de administrador de Workspace o de usuario de AEM formularios de AEM pueden acceder a las páginas web del usuario final de Workspace.

>[!NOTE]
>
>Flex Workspace está obsoleto para AEM versión de formularios.

## Crear una función {#create-a-role}

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Administración de funciones y, a continuación, haga clic en Nueva función.
1. En el cuadro Nombre de rol, escriba un nombre para la función y, opcionalmente, escriba una descripción de la función y, a continuación, haga clic en Siguiente.

   >[!NOTE]
   >
   >Cuando se utiliza MySQL, no se pueden crear dos roles que tengan el mismo nombre pero que difieran en el uso de caracteres extendidos. Por ejemplo, intentar crear una función denominada &quot;abcde&quot; cuando ya existe una llamada &quot;âbcdè&quot; resulta en un error.

1. Haga clic en Buscar permisos y seleccione los permisos que desee agregar a la función.
1. Haga clic en Aceptar y, a continuación, en Siguiente.
1. Asignar esta función a usuarios y grupos:

   * Haga clic en Buscar usuarios/grupos.
   * En el cuadro Buscar, escriba los criterios de búsqueda.
   * Seleccione Nombre, Correo electrónico o ID de usuario y, a continuación, seleccione Usuarios, Grupos o Usuarios y grupos.
   * Seleccione el dominio, seleccione el número de resultados que desea mostrar y haga clic en Buscar.
   * Seleccione las casillas de verificación de los usuarios y grupos a los que asignar esta función y haga clic en Aceptar.

1. Para vista de detalles de usuarios y grupos, seleccione la entidad.
1. Haga clic en Aceptar y, a continuación, en Finalizar.

## Editar una función {#edit-a-role}

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Administración de funciones y, a continuación, haga clic en Nombre de función.

   De forma predeterminada, la página Administración de roles muestra todas las funciones de la base de datos de Administración de usuarios. Si la lista de roles es grande, utilice el área Buscar en la parte superior de la página para buscar un nombre de rol específico.

1. Haga clic en la función que desea editar, edite la configuración general y haga clic en Guardar.
1. Para editar los permisos de las funciones, haga clic en la ficha Permisos y lleve a cabo las siguientes tareas:

   * Para agregar nuevos permisos, haga clic en Buscar permisos, seleccione las casillas de verificación de los permisos que desee agregar, haga clic en Aceptar y, a continuación, haga clic en Guardar.
   * Para eliminar un permiso de la función, seleccione la casilla de verificación del permiso, haga clic en Eliminar y, a continuación, haga clic en Guardar.

1. Para administrar a quién está asignada la función, haga clic en la ficha Usuarios de rol y realice las siguientes tareas:

   * Para asignar la función a nuevos usuarios y grupos, haga clic en Buscar usuarios/grupos y complete la información de búsqueda. Seleccione la casilla de verificación de cada usuario y grupo al que asignar esta función, haga clic en Aceptar y, a continuación, en Guardar.
   * Para quitar la función, seleccione la casilla de verificación de los usuarios o del grupo, haga clic en Cancelar asignación y, a continuación, haga clic en Guardar.

## Eliminar una función {#delete-a-role}

Puede eliminar cualquiera de las funciones que haya creado, pero no las funciones AEM formularios predeterminadas que se incluyen en el producto.

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Administración de funciones y, a continuación, haga clic en Nombre de función.

   De forma predeterminada, la página Administración de roles muestra todas las funciones de la base de datos de Administración de usuarios. Si la lista de roles es grande, utilice el área Buscar en la parte superior de la página para buscar un nombre de rol específico.

1. Seleccione la casilla de verificación de la función que desea eliminar, haga clic en Eliminar y, a continuación, haga clic en Aceptar.

## Asignación de una función a usuarios y grupos {#assign-a-role-to-users-and-groups}

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Usuarios y grupos.
1. Especifique la información para limitar la búsqueda y haga clic en Buscar. Los resultados de la búsqueda se enumeran en la parte inferior de la página. Puede ordenar la lista haciendo clic en cualquiera de los encabezados de columna.
1. Seleccione las casillas de verificación situadas junto a los usuarios y grupos con los que desea asociar una función y haga clic en Asignar función.
1. Seleccione la función que desea asignar al usuario o grupo y haga clic en Aceptar.

También puede asignar funciones mediante la página Administración de funciones.

## Determinar quién está asignado a una función {#determine-who-is-assigned-to-a-role}

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Administración de funciones y, a continuación, haga clic en Nombre de función.

   De forma predeterminada, la página Administración de roles muestra todas las funciones de la base de datos de Administración de usuarios. Si la lista de roles es grande, utilice el área Buscar en la parte superior de la página para buscar un nombre de rol específico.

1. En la página Detalle de función, haga clic en la ficha Usuarios de rol. Se muestra una lista de usuarios y grupos que están directamente asociados con la función.

## Cambiar permisos de funciones {#change-role-permissions}

Puede cambiar los permisos de cualquiera de las funciones que ha creado. No se pueden cambiar los permisos para las funciones de formularios AEM predeterminadas que se incluyen en el producto.

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Administración de funciones y, a continuación, haga clic en Nombre de función.

   De forma predeterminada, la página Administración de roles muestra todas las funciones de la base de datos de Administración de usuarios. Si la lista de roles es grande, utilice el área Buscar en la parte superior de la página para buscar un nombre de rol específico.

1. Seleccione la función para la que desea asignar permisos de vista y haga clic en la ficha Permisos.
1. Para cambiar estos permisos, haga clic en Buscar permisos, seleccione las casillas de verificación de los permisos que desea agregar a la función, haga clic en Aceptar y, a continuación, en Guardar.
1. Para eliminar un permiso, selecciónelo, haga clic en Eliminar y, a continuación, en Guardar.

### Permisos de formularios AEM {#aem-forms-permissions}

**AÑADIR_REMOVE_ENDPOINT_PERM:** Añadir, eliminar y modificar los extremos de un servicio

**Inicio de sesión de Admin Console:** Vista de la consola de administración

**Modificación de certificado:** Modificar la configuración de confianza de cualquier certificado del almacén de confianza

**Lectura del certificado:** Leer cualquier certificado del almacén de confianza

**Escritura de certificado:** Añadir un certificado al almacén de confianza

**Añadir componente:** Instalar un componente nuevo en el sistema

**Eliminación de componentes:** Eliminar cualquier componente del sistema

**Lectura del componente:** Leer cualquier componente del sistema

**Administrador de Contentspace:** Permiso para administrador de ContentSpace (obsoleto)

**Inicio de sesión en la consola de Contentspace:** Permiso para el inicio de sesión en la consola de ContentSpace (obsoleto)

**Control de configuración principal:** Administrar la configuración en la página Configuración del sistema principal de la Consola de administración

**CREATE_VERSION_PERM:** Crear una nueva versión de un servicio

**Modificación de credenciales:** Modificar cualquier credencial de firma en el almacén de confianza

**Lectura de credencial:** Leer las credenciales de firma en el almacén de confianza

**Escritura de credenciales:** Añadir una credencial de firma en el almacén de confianza

**Modificación de CRL:** Modificar cualquier CRL (Lista de revocación de certificados) en el almacén de confianza

**Lectura de CRL:** Leer cualquier CRL en el almacén de confianza

**Escritura CRL:** Añadir una CRL al almacén de confianza

**Delegado:** Establecer una ACL en un recurso

**DELETE_VERSION_PERM:** Eliminar una versión de un servicio

**Carga de Documento:** Cargar documentos en formularios AEM

**Control de dominio:** Crear, eliminar o modificar la configuración de cualquier dominio de Administración de usuarios, incluidos sus proveedores de autenticación y directorio

**Edición de Tipo de evento:** Editar en tipos de evento

**Control de suplantación de identidad:** Suplantar identidad en el Administrador de usuarios

**INVOKE_PERM:** Invocar todas las operaciones en un servicio

**Control del modelo de datos LCDS:** Leer e implementar modelos de datos en Servicios de datos

**Actualización del Administrador de licencias:** Actualizar información de licencia

**MODIFY_CONFIG_PERM:** Modificar la configuración de un servicio

**TÉRMINO** Modificación de la versión de un servicio

**PDFGAdminPermission:** Administrador de PDFG

**PDFGUserPermission:** Usuario de PDFG

**PERM_DCTM_ADMIN:** Administrador de Documentum Connector

**PERM_FILENET_ADMIN:** Administrador del conector FileNet

**PERM_FORMS_ADMIN:** Administrador de Forms

**PERM_IBMCM_ADMIN:** Administrador de conector de IBM CM

**PERM_OUTPUT_ADMIN:** Administrador de salida

**PERM_READER_EXTENSIONS_WEB_APPLICATION:** Uso de la aplicación web de extensiones de Acrobat Reader DC

**PERM_SP_ADMIN:** Administrar la configuración del conector de SharePoint

**PERM_WORKSPACE_ADMIN:** Administrar la configuración del espacio de trabajo

**PERM_WORKSPACE_USER:** Inicie sesión en la aplicación de usuario final de Workspace

**Control principal:** Administre usuarios y grupos para cualquier dominio y administre asignaciones de funciones para todos los usuarios y grupos de cualquier dominio

**Proceso de grabación de lectura/eliminación:** Lista y recuperación de instancias de auditoría de flujo de trabajo

**PROCESS_OWNER_PERM:** Vista de datos de tendencia y realización de acciones administrativas en un servicio creado a partir de un proceso

**Lea:** Leer el contenido de un recurso

**READ_PERM:** Leer o vista de un servicio

**Renovar afirmación:** Renovar aserciones en Administración de usuarios

**Delegado de repositorio:** Establecer una ACL en un recurso

**Lectura del repositorio:** Leer el contenido de un recurso

**Ruta del repositorio:** Incluir un recurso en una solicitud de recursos de lista o leer los metadatos de un recurso

**Escritura del repositorio:** Escribir metadatos y contenido del repositorio

**Propietario de directiva de cambio de Rights Management:** Cambiar propietario de directiva

**Inicio de sesión en la consola de usuario final de Rights Management:** Inicio de sesión en la interfaz de usuario del usuario final del Rights Management

**Rights Management Administrar configuración:** Administrar la configuración del servidor

**Rights Management Administrar usuarios invitados y locales:** Administrar usuarios invitados y locales

**Administrar conjuntos de directivas de Rights Management:** Administrar todas las directivas y documentos dentro de cualquier conjunto de directivas

**Coordinador de Añadir conjunto de directivas de Rights Management:** Añadir, eliminar y cambiar permisos para coordinadores de conjuntos de directivas

**Política de creación de conjunto de directivas de Rights Management:** Crear una nueva directiva para un conjunto de directivas

**Directiva de eliminación de conjunto de directivas de Rights Management:** Quitar una directiva de un conjunto de directivas

**Directiva de edición de conjunto de directivas de Rights Management:** Editar una directiva en un conjunto de directivas

**Editor de Documentos de Administrar conjunto de directivas de Rights Management:** Al crear conjuntos de políticas, se asigna a los usuarios la función de publicador de documento. El editor de documento es el usuario que protege el documento con una política.

**Coordinador de eliminación de conjunto de directivas de Rights Management:** Quitar un coordinador de conjuntos de directivas de un conjunto de directivas

**Documento de anulación de conjunto de directivas de Rights Management:** Revocar el acceso a documentos en un conjunto de directivas

**Directiva de cambio de conjunto de directivas de Rights Management:** Cambiar directivas para un documento

**Documento Unrevoke de conjunto de directivas de Rights Management:** Anular la revocación de un documento

**Evento de Vista de conjunto de directivas Rights Management:** eventos de política de Vista y documento para cualquier política o documento dentro de un conjunto de políticas

**Eventos del servidor de Vista Rights Management:** Buscar y vista de todos los eventos de auditoría

**Control de funciones:** Crear, eliminar y modificar funciones en Administración de usuarios

**Activación del servicio:** Inicio de cualquier servicio, poniéndolo a disposición para la invocación

**Añadir servicio:** Implemente un nuevo servicio en el Registro de servicios. Esto incluye agregar nuevos procesos y variantes de proceso

**Desactivación del servicio:** Detener cualquier servicio del sistema

**Eliminación del servicio:** Eliminar cualquier servicio del sistema, incluidos los procesos y las variantes de proceso

**Invocación de servicio:** Invocar cualquier servicio del Registro de servicios disponible en tiempo de ejecución

**Modificación del servicio:** Modifique las propiedades de configuración de cualquier servicio del sistema. Esto incluye bloquear y desbloquear un servicio en el IDE, y agregar o quitar puntos finales de un servicio

**Lectura del servicio:** Lea los servicios del sistema. Esto incluye todos los procesos y variantes de proceso

**SERVICE_AGENT_PERM:** Vista de datos e interacción con instancias de proceso para un servicio creado a partir de un proceso

**SERVICE_MANAGER_PERM:** Realizar balance de carga y otras acciones administrativas en un servicio creado a partir de un proceso

**INICIO_STOP_PERM:** Inicio o parada de un servicio

**SUPERVISOR_PERM:** Datos de instancia de proceso de Vista para un servicio creado a partir de un proceso

**Travesía:** Incluir un recurso en una solicitud de recursos de lista o leer los metadatos de un recurso

**Escribir:** Escribir metadatos y contenido del repositorio

**Apertura de archivos en Workbench**

Para vista del contenido de la vista Recursos en Workbench y abrir archivos para su visualización, un usuario necesita los siguientes permisos:

* Lectura del repositorio
* Travesía del repositorio
* Invocación de servicio
* Lectura del servicio

## Quitar un usuario o grupo de una función {#remove-a-user-or-group-from-a-role}

Utilice la página Administración de roles para eliminar usuarios y grupos de una función en particular. Si el usuario o grupo heredó la asignación de funciones, no podrá quitar la función a nivel de usuario o grupo. Elimine el usuario o grupo del árbol de herencia o quite la función del elemento principal.

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Administración de funciones y, a continuación, haga clic en Nombre de función.

   De forma predeterminada, la página Administración de roles muestra todas las funciones de la base de datos de Administración de usuarios. Si la lista de roles es grande, utilice el área Buscar en la parte superior de la página para buscar un nombre de rol específico.

1. En la lista de funciones, haga clic en el nombre de la función que desea actualizar y, a continuación, haga clic en la ficha Usuarios de rol. Se muestra una lista de usuarios y grupos asociados a la función.
1. Seleccione las casillas de verificación de los usuarios y grupos que desea quitar de la función y haga clic en Cancelar asignación.
1. Haga clic en Guardar y, a continuación, en Aceptar.

