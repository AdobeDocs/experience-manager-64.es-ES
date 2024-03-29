---
title: Usuarios de servicio en AEM
seo-title: Service Users in AEM
description: Obtenga información sobre los usuarios de servicios en AEM.
feature: Security
seo-description: Learn about Service Users in AEM.
uuid: 4efab5fb-ba11-4922-bd68-43ccde4eb355
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 9cfe5f11-8a0e-4a27-9681-a8d50835c864
exl-id: b6e77f61-5c7b-4e40-881c-057177e7ea6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1814'
ht-degree: 1%

---

# Usuarios de servicio en AEM{#service-users-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

La forma principal de obtener una sesión administrativa o resolución de recursos en AEM era usar la variable `SlingRepository.loginAdministrative()` y `ResourceResolverFactory.getAdministrativeResourceResolver()` métodos proporcionados por Sling.

Sin embargo, ninguno de estos métodos se diseñó en torno a la variable [principio del menor privilegio](https://en.wikipedia.org/wiki/Principle_of_least_privilege) y facilitar a un desarrollador no planificar una estructura adecuada y los niveles de control de acceso (ACL) correspondientes para su contenido de forma temprana. Si una vulnerabilidad está presente en un servicio de este tipo, a menudo conduce a escalaciones de privilegios a la variable `admin` incluso si el código en sí no necesita privilegios administrativos para funcionar.

## Cómo eliminar sesiones de administración {#how-to-phase-out-admin-sessions}

### Prioridad 0: ¿La función está activa/es necesaria/no se selecciona? {#priority-is-the-feature-active-needed-derelict}

Puede haber casos en los que la sesión de administración no se utilice o la función esté deshabilitada por completo. Si este es el caso de la implementación, asegúrese de eliminar la función por completo o de adaptarla a [Código NOP](https://en.wikipedia.org/wiki/NOP).

### Prioridad 1: Uso De La Sesión De Solicitud {#priority-use-the-request-session}

Siempre que sea posible, refactorice su función para que la sesión de solicitud determinada y autenticada se pueda utilizar para leer o escribir contenido. Si esto no es factible, a menudo se puede lograr aplicando las prioridades que se indican a continuación.

### Prioridad 2: Reestructurar contenido {#priority-restructure-content}

Se pueden resolver muchos problemas reestructurando el contenido. Tenga en cuenta estas reglas sencillas al realizar la reestructuración:

* **Cambiar control de acceso**

   * Asegúrese de que los usuarios o grupos a los que realmente se necesita acceder tengan acceso;

* **Ajustar la estructura de contenido**

   * Moverla a otras ubicaciones, por ejemplo, donde el control de acceso coincida con las sesiones de solicitud disponibles;
   * Cambiar la granularidad del contenido;

* **Refactorizar el código para que sea un servicio adecuado**

   * Mueva la lógica empresarial del código JSP al servicio. Esto permite realizar modelos de contenido diferentes.

Además, asegúrese de que cualquier función nueva que desarrolle cumpla estos principios:

* **Los requisitos de seguridad deben dirigir la estructura de contenido**

   * La gestión del control de acceso debería ser natural
   * El control de acceso debe ser reforzado por el repositorio, no por la aplicación

* **Usar nodos**

   * Restringir el conjunto de propiedades que se pueden establecer

* **Respetar la configuración de privacidad**

   * En el caso de los perfiles privados, un ejemplo sería no exponer la imagen de perfil, el correo electrónico o el nombre completo que se encuentra en el privado `/profile` nodo .

## Control de acceso estricto {#strict-access-control}

Tanto si aplica el control de acceso durante la reestructuración de contenido como cuando lo hace para un nuevo usuario de servicio, debe aplicar las ACL más estrictas posibles. Utilice todas las instalaciones posibles de control de acceso:

* Por ejemplo, en lugar de aplicar `jcr:read` en `/apps`, aplique únicamente a `/apps/*/components/*/analytics`

* Uso [restricciones](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html)

* Aplicar ACL para tipos de nodos
* Límite de permisos

   * por ejemplo, cuando solo necesite escribir propiedades, no asigne la variable `jcr:write` permiso; use `jcr:modifyProperties` en lugar de

## Usuarios y asignaciones de servicio {#service-users-and-mappings}

Si lo anterior falla, Sling 7 ofrece un servicio de Asignación de usuarios de servicio, que permite configurar una asignación entre paquetes y usuarios y dos métodos de API correspondientes: ` [SlingRepository.loginService()](https://sling.apache.org/apidocs/sling7/org/apache/sling/jcr/api/SlingRepository.html#loginService-java.lang.String-java.lang.String-)` y ` [ResourceResolverFactory.getServiceResourceResolver()](https://sling.apache.org/apidocs/sling7/org/apache/sling/api/resource/ResourceResolverFactory.html#getServiceResourceResolver-java.util.Map-)` que devuelven una resolución de sesión/recurso con los privilegios de un usuario configurado únicamente. Estos métodos tienen las siguientes características:

* Permiten asignar servicios a los usuarios
* Permiten definir usuarios de subservicios
* El punto de configuración central es: `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl`
* `service-id` = `service-name` [ &quot;:&quot; subservice-name ]

* `service-id` está asignado a un solucionador de recursos o a un ID de usuario del repositorio JCR para la autenticación
* `service-name` es el nombre simbólico del paquete que proporciona el servicio

## Otros Recommendations {#other-recommendations}

### Reemplazar la sesión de administración por un usuario de servicio {#replacing-the-admin-session-with-a-service-user}

Un usuario de servicio es un usuario JCR sin contraseña establecida y con un conjunto mínimo de privilegios necesarios para realizar una tarea específica. Si no se ha establecido ninguna contraseña, no será posible iniciar sesión con un usuario de servicio.

Una forma de eliminar una sesión administrativa es reemplazarla por sesiones de usuario de servicio. También se puede sustituir por varios usuarios de subservicio si es necesario.

Para reemplazar la sesión de administrador por un usuario de servicio, debe realizar los siguientes pasos:

1. Identifique los permisos necesarios para su servicio, teniendo en cuenta el principio de mínimo permiso.
1. Compruebe si ya hay un usuario disponible con exactamente la configuración de permisos que necesita. Cree un nuevo usuario de servicio del sistema si ningún usuario existente coincide con sus necesidades. RTC es necesario para crear un nuevo usuario de servicio. A veces, tiene sentido crear varios usuarios de subservicios (por ejemplo, uno para escribir y otro para leer) para compartimentar el acceso aún más.
1. Configure y pruebe los ACE para su usuario.
1. Agregue un `service-user` asignación para su servicio y para `user/sub-users`

1. Haga que la función sling del usuario del servicio esté disponible para su paquete: actualización a la versión más reciente de `org.apache.sling.api`.

1. Sustituya el `admin-session` en su código con la variable `loginService` o `getServiceResourceResolver` API.

## Creación de un nuevo usuario de servicio {#creating-a-new-service-user}

Después de comprobar que ningún usuario de la lista de usuarios de AEM servicio es aplicable para su caso de uso y de aprobar los problemas correspondientes de RTC, puede continuar y agregar el nuevo usuario al contenido predeterminado.

El método recomendado es crear un usuario de servicio para utilizar el explorador de repositorios en *https://&lt;server>:&lt;port>/crx/explorer/index.jsp*

El objetivo es obtener una `jcr:uuid` que es obligatoria para crear el usuario a través de una instalación de paquete de contenido.

Puede crear usuarios de servicios mediante:

1. Ir al explorador del repositorio en *https://&lt;server>:&lt;port>/crx/explorer/index.jsp*
1. Inicie sesión como administrador pulsando el botón **Iniciar sesión** en la esquina superior izquierda de la pantalla.
1. A continuación, cree y asigne un nombre al usuario del sistema. Para crear el usuario como un sistema, establezca la ruta intermedia como `system` y agregue subcarpetas opcionales según sus necesidades:

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. Compruebe que el nodo de usuario del sistema tenga el siguiente aspecto:

   ![chlimage_1-103](assets/chlimage_1-103.png)

   >[!NOTE]
   >
   >Tenga en cuenta que no hay tipos de mezcla asociados con los usuarios de servicios. Esto significa que no habrá políticas de control de acceso para los usuarios del sistema.

Al añadir el .content.xml correspondiente al contenido de su paquete, asegúrese de haber configurado la variable `rep:authorizableId` y que el tipo principal es `rep:SystemUser`. Debería tener este aspecto:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:rep="internal"
    jcr:primaryType="rep:SystemUser"
    jcr:uuid="4917dd68-a0c1-3021-b5b7-435d0044b0dd"
    rep:principalName="authentication-service"
    rep:authorizableId="authentication-service"/>
```

## Adición de una modificación de configuración a la configuración de ServiceUserMapper {#adding-a-configuration-amendment-to-the-serviceusermapper-configuration}

Para añadir una asignación desde el servicio a los usuarios del sistema correspondientes, debe crear una configuración de fábrica para el ` [ServiceUserMapper](https://sling.apache.org/apidocs/sling7/org/apache/sling/serviceusermapping/ServiceUserMapper.html)` servicio. Para mantener este modular, estas configuraciones se pueden proporcionar utilizando la variable [Mecanismo de modificación de Sling](https://issues.apache.org/jira/browse/SLING-3578). La forma recomendada de instalar estas configuraciones con su paquete es mediante [Carga inicial de contenido de Sling](https://sling.apache.org/documentation/bundles/content-loading-jcr-contentloader.html):

1. Cree una subcarpeta SLING-INF/content debajo de la carpeta src/main/resources del paquete
1. En esta carpeta, cree un archivo llamado org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.modified-&lt;some unique=&quot;&quot; name=&quot;&quot; for=&quot;&quot; your=&quot;&quot; factory=&quot;&quot; configuration=&quot;&quot;>.xml con el contenido de la configuración de fábrica (incluidas todas las asignaciones de usuario de subservicio). Ejemplo:

1. Cree un `SLING-INF/content` carpeta debajo de `src/main/resources` carpeta del paquete;
1. En esta carpeta, cree un archivo `named org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-<a unique name for your factory configuration>.xml` con el contenido de la configuración de fábrica, incluidas todas las asignaciones de usuario de subservicio.

   Para fines ilustrativos, tome un archivo llamado `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-com.adobe.granite.auth.saml.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <node>
       <primaryNodeType>sling:OsgiConfig</primaryNodeType>
       <property>
           <name>user.default</name>
           <value></value>
       </property>
       <property>
           <name>user.mapping</name>
           <values>
               <value>com.adobe.granite.auth.saml=authentication-service</value>
           </values>
       </property>
   </node>
   ```

1. Haga referencia al contenido inicial de Sling en la configuración del `maven-bundle-plugin` en el `pom.xml` de su paquete. Ejemplo:

   ```xml
   <Sling-Initial-Content>
      SLING-INF/content;path:=/libs/system/config;overwrite:=true;
   </Sling-Initial-Content>
   ```

1. Instale el paquete y asegúrese de que la configuración de fábrica se ha instalado. Para ello:

   * Ir a la consola web en *https://serverhost:serveraddress/system/console/configMgr*
   * Buscar **Modificación del servicio del asignador de usuarios del servicio Apache Sling**
   * Haga clic en el vínculo para ver si se ha configurado correctamente.

## Cómo tratar las sesiones compartidas en los servicios {#dealing-with-shared-sessions-in-services}

Llamadas a `loginAdministrative()` a menudo aparecen junto con sesiones compartidas. Estas sesiones se adquieren al activar el servicio y solo se cerran tras detener el servicio. Aunque esta es una práctica común, conduce a dos problemas:

* **Seguridad:** Estas sesiones de administración se utilizan para almacenar en caché y devolver recursos u otros objetos enlazados a la sesión compartida. Más adelante en la pila de llamadas, estos objetos podrían adaptarse a las sesiones o a los solucionadores de recursos con privilegios elevados y, a menudo, el llamador no tiene claro que sea una sesión de administrador con la que esté operando.
* **Rendimiento:** En las sesiones compartidas de Oak pueden causar problemas de rendimiento y actualmente no se recomienda usarlos.

La solución más obvia para el riesgo de seguridad es simplemente reemplazar la variable `loginAdministrative()` llamada con un `loginService()` uno a un usuario con privilegios restringidos. Sin embargo, esto no tendrá ningún impacto en ninguna posible degradación del rendimiento. Una posibilidad de mitigar esto es envolver toda la información solicitada en un objeto que no esté asociado con la sesión. A continuación, cree (o destruya) la sesión bajo demanda.

El método recomendado es refactorizar la API del servicio para proporcionar al llamador control sobre la creación/destrucción de la sesión.

## Sesiones administrativas en JSP {#administrative-sessions-in-jsps}

Los JSP no pueden utilizar `loginService()`, ya que no hay ningún servicio asociado. Sin embargo, las sesiones administrativas en los JSP suelen ser una señal de violación del paradigma de MVC.

Esto se puede corregir de dos maneras:

1. Reestructurar el contenido de manera que permita manipularlo con la sesión del usuario;
1. Extracción de la lógica a un servicio que proporcione una API que luego JSP pueda usar.

El primer método es el preferido.

## Eventos de procesamiento, preprocesadores de replicación y trabajos {#processing-events-replication-preprocessors-and-jobs}

Al procesar eventos o trabajos, y en algunos casos flujos de trabajo, la sesión correspondiente que activó el evento generalmente se pierde. Esto lleva a que los administradores de eventos y los procesadores de trabajos a menudo utilicen sesiones administrativas para realizar su trabajo. Hay diferentes enfoques concebibles para resolver este problema, cada uno con sus ventajas y desventajas:

1. Pase el `user-id` en la carga útil de evento y utilice la suplantación.

   **Ventajas:** Fácil de usar.

   **Desventajas:** Todavía utiliza `loginAdministrative()`. Vuelve a autenticar una solicitud que ya se ha autenticado.

1. Cree o reutilice un usuario de servicio que tenga acceso a los datos.

   **Ventajas:** Coherente con el diseño actual. Necesita un cambio mínimo.

   **Desventajas:** Necesita usuarios de servicio muy poderosos para ser flexibles, lo que puede conducir fácilmente a escalaciones de privilegios. Elude el modelo de seguridad.

1. Pase una serialización de `Subject` en la carga útil de evento y cree un `ResourceResolver` basado en ese tema. Un ejemplo sería el uso de JAAS `doAsPrivileged` en el `ResourceResolverFactory`.

   **Ventajas:** Implementación limpia desde un punto de vista de seguridad. Evita la reautenticación y funciona con los privilegios originales. El código relevante para la seguridad es transparente para el consumidor del evento.

   **Desventajas:** Necesita refactorización. El hecho de que el código relevante para la seguridad sea transparente para el consumidor del evento también podría causar problemas.

El tercer método es actualmente la técnica de procesamiento preferida.

## Procesos de flujo de trabajo {#workflow-processes}

En implementaciones de procesos de flujo de trabajo, la sesión de usuario correspondiente que activó el flujo de trabajo generalmente se pierde. Esto lleva a que los procesos de flujo de trabajo a menudo utilicen sesiones administrativas para realizar su trabajo.

Para solucionar estos problemas, se recomienda que se sigan los mismos enfoques mencionados en [Eventos de procesamiento, preprocesadores de replicación y trabajos](/help/sites-administering/security-service-users.md#processing-events-replication-preprocessors-and-jobs) se utilizará.

## Procesadores de POST de Sling y páginas eliminadas {#sling-post-processors-and-deleted-pages}

Hay un par de sesiones administrativas que se utilizan en las implementaciones de procesador de sling POST. Normalmente, las sesiones administrativas se utilizan para acceder a los nodos que están pendientes de eliminación dentro del POST que se está procesando. Por lo tanto, ya no están disponibles a través de la sesión de solicitud. Se puede acceder a un nodo pendiente de eliminación para revelar a metada que de otra manera no debería ser accesible.
