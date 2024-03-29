---
title: "Reutilización del contenido: administrador de varios sitios y Live Copy"
seo-title: "Reusing Content: Multi Site Manager and Live Copy"
description: Obtenga información sobre cómo reutilizar contenido con Live Copies y Multi Site Manager.
seo-description: Learn about reusing content with Live Copies and the Multi Site Manager.
uuid: 9f955226-8fc9-4357-b90c-c6896b0dc4b4
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c21debc3-ecf4-4aa9-ab5a-18ddd5cf2fff
exl-id: 96e75d9c-f091-4ca1-afd3-6309a08de525
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2700'
ht-degree: 33%

---

# Reutilización del contenido: administrador de varios sitios y Live Copy{#reusing-content-multi-site-manager-and-live-copy}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Multi Site Manager (MSM) le permite usar el mismo contenido del sitio en varias ubicaciones. MSM utiliza su funcionalidad de Live Copy para conseguirlo:

* Con MSM puede lograr lo siguiente:

   * Crear contenido una vez y después
   * Copie este contenido en otras áreas y reutilice este contenido en ([Live Copies](#live-copies)) del mismo sitio u otros sitios.

* A continuación, MSM mantiene las relaciones (activas) entre el contenido de origen y sus Live Copies, de modo que:

   * Cuando se realizan cambios en el contenido de origen, el origen y las Live Copies se sincronizan (para aplicar estos cambios también a las Live Copies).
   * Puede realizar ajustes en el contenido de las Live Copies desconectando la relación activa para subpáginas o componentes individuales. Al hacer esto, los cambios en el origen ya no se aplicarán a la Live Copy.

Esta y las siguientes páginas tratan los problemas relacionados:

* [Creación y sincronización de Live Copies](/help/sites-administering/msm-livecopy.md)
* [Información general de Live Copy](/help/sites-administering/msm-livecopy-overview.md)
* [Configuración de la sincronización de Live Copy](/help/sites-administering/msm-sync.md)
* [Conflictos de despliegue de MSM](/help/sites-administering/msm-rollout-conflicts.md)
* [Prácticas recomendadas de MSM](/help/sites-administering/msm-best-practices.md)

## Posibles escenarios {#possible-scenarios}

Hay muchos casos de uso para MSM y Live Copies, algunos escenarios incluyen:

* **Multinacionales: empresa global a local**

   Un caso de uso típico que admite MSM es reutilizar contenido en varios sitios multinacionales en el mismo idioma. Esto permite reutilizar el contenido principal, a la vez que permite variaciones nacionales.

   Por ejemplo, la sección en inglés del ejemplo del sitio de referencia de We.Retail se crea para los clientes de EE. UU. La mayoría del contenido de este sitio también puede utilizarse para otros sitios de We.Retail que se ocupan de clientes de habla inglesa de diferentes países y culturas. El contenido principal sigue siendo el mismo en todos los sitios, mientras que se pueden llevar a cabo ajustes regionales.

   La siguiente estructura se puede utilizar para sitios para Estados Unidos, Reino Unido, Canadá y Australia:

   ```xml
   /content
       |- we.retail
           |- language-masters
               |- en
       |- we.retail
           |- us
               |- en
       |- we.retail
           |- gb
               |- en
       |- we.retail
           |- ca
               |- en
       |- we.retail
           |- au
               |- en
   ```

   >[!NOTE]
   >
   >MSM no traduce el contenido. Se utiliza para crear la estructura necesaria e implementar el contenido.
   >
   >
   >Consulte [Traducción de contenido para sitios multilingües](/help/sites-administering/translation.md) si desea ampliar este ejemplo.

* **Nacional: de la sede central a las subdivisiones regionales**

   Alternativamente, una empresa con una red de distribuidores podría querer sitios web separados para sus concesionarios individuales, siendo cada uno una variación del sitio principal proporcionado por la sede central. Esto podría ser para una sola empresa con múltiples oficinas regionales, o un sistema nacional de franquicias compuesto por un franquiciador central y múltiples franquicias locales.

   La sede central puede proporcionar la información básica, mientras que las entidades regionales pueden añadir información local, como detalles de contacto, horarios de apertura y eventos.

   ```xml
   /content
       |- head-office-Berlin
       |- branch-Hamburg
       |- branch-Stuttgart
       |- branch-Munich
       |- branch-Frankfurt
   ```

* **Varias versiones**

   O puede utilizar MSM para crear versiones de una subrama específica; por ejemplo, un subsitio de asistencia que contiene detalles de las distintas versiones de un producto específico, donde la información base permanece constante y solo es necesario cambiar las funciones actualizadas:

   ```xml
   /content
       |- support
           |- product X
               |- v5.0
               |- v4.0
               |- v3.0
               |- v2.0
               |- v1.0
   ```

   >[!NOTE]
   >
   >En tal escenario siempre está la cuestión de si hacer una copia directa o utilizar Live Copies.
   >
   >Hay un equilibrio entre:
   >
   >  * La cantidad de contenido principal que necesitará actualizarse en las distintas versiones.
   >
   >Frente a:
   >
   >  * La cantidad de copias individuales deberá ajustarse.


## MSM desde la IU {#msm-from-the-ui}

Se puede acceder directamente a MSM desde la IU mediante diversas opciones desde la consola adecuada. Para proporcionar una introducción, a continuación se enumeran las ubicaciones principales:

* **Crear sitio** (**Sitios**)

   * MSM le ayuda a administrar varios sitios web que comparten contenido común; por ejemplo, los sitios web se proporcionan a menudo para audiencias internacionales, de modo que la mayoría del contenido es común en todos los países, con un subconjunto del contenido específico de cada país individual. MSM le permite [crear Live Copies que actualicen automáticamente uno o varios sitios en función del sitio de origen](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Esto también le ayuda a aplicar una estructura base común, utilizar el contenido general en varios sitios, mantener un aspecto y un enfoque comunes y enfocar los esfuerzos en administrar el contenido que difiere entre los sitios.
   * Requiere una configuración de modelo predefinida para especificar el origen.
   * Crea una Live Copy del origen (predefinido).
   * Proporciona al usuario el botón **Despliegue**.

* **Creación de Live Copy** (**Sites**)

   * MSM le permite [crear una Live Copy ad-hoc (única) de una página o rama individual de un sitio web](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page); por ejemplo, duplicar una subrama para proporcionar información sobre una versión nueva o actualizada de un producto.
   * Crea una Live Copy ad-hoc (no se requiere configuración de modelo).
   * Se puede utilizar para crear (inmediatamente) una Live Copy de cualquier página o rama.
   * Requiere **Sincronizar** (no proporciona el botón **Despliegue**).

* **Ver propiedades** (**Sitios**)

   * Si corresponde, esta opción le ayuda a [supervisar la Live Copy](/help/sites-administering/msm-livecopy.md#monitoring-your-live-copy) proporcionando información sobre las **Live Cop** y o **Modelo**.

* **Referencias** (**Sitios**)

   * El carril [Referencias](/help/sites-authoring/basic-handling.md#references) proporciona información sobre **Live Copies** junto con el acceso a las acciones adecuadas.

* **Información general de Live Copy** (**Sites**)

   * Esta consola le permite [ver y administrar su modelo y sus Live Copies](/help/sites-administering/msm-livecopy-overview.md).

* **Modelos** (**Herramientas** - **Sites**)

   * Esta consola le permite [crear y administrar las configuraciones de modelo](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

>[!NOTE]
>
>Los aspectos de la funcionalidad de MSM se utilizan en varias otras funciones de AEM (por ejemplo, Lanzamientos, Catálogo); en estos casos, esa función administra la Live Copy.

### Términos utilizados {#terms-used}

Como introducción, la siguiente tabla proporciona una visión general de los términos principales utilizados con MSM; se tratarán en más detalles en las secciones y páginas siguientes:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Término</strong></td> 
   <td><strong>Definición</strong></td> 
   <td><strong>Más detalles</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Origen</strong></td> 
   <td>Las páginas originales.</td> 
   <td>Sinónimo de páginas de modelos o modelos.</td> 
  </tr> 
  <tr> 
   <td><strong>Live Copy   </strong></td> 
   <td>La copia (del origen), mantenida mediante acciones de sincronización definidas según las configuraciones de despliegue. </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Configuración de Live Copy</strong></td> 
   <td>Definición de los detalles de configuración de una Live Copy.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Relación activa</strong><br /> </td> 
   <td>Definición efectiva de la herencia de un recurso determinado; las conexiones entre el origen y las Live Copies.<br /> </td> 
   <td>Garantiza que los cambios en el origen se puedan sincronizar con la Live Copy.</td> 
  </tr> 
  <tr> 
   <td><strong>Modelo</strong></td> 
   <td>Sinónimo de origen.</td> 
   <td>Se puede definir mediante una configuración de modelo.</td> 
  </tr> 
  <tr> 
   <td><strong>Configuración del modelo</strong></td> 
   <td>Configuración predefinida que especifica una ruta de origen.</td> 
   <td>Cuando se hace referencia a una página de modelo en una configuración de modelo, el comando Despliegue está disponible.</td> 
  </tr> 
  <tr> 
   <td><strong>Sincronización</strong></td> 
   <td>Término genérico para la sincronización de contenido entre el origen y las Live Copies (por <strong>Despliegue</strong> y <strong>Sincronizar</strong>).</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Despliegue</strong><br /> </td> 
   <td>Sincroniza desde el origen con la Live Copy.<br /> Se puede activar mediante un autor (en una página de modelo) o mediante un evento del sistema (tal como se define en la configuración de despliegue).</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Configuración de despliegue</strong></td> 
   <td>Reglas que determinan qué propiedades se sincronizarán, cómo y cuándo.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Sincronizar</strong></td> 
   <td>Solicitud manual de sincronización, realizada desde las páginas de Live Copy.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Herencia</strong></td> 
   <td>Una página o componente de Live Copy hereda el contenido de su página o componente de origen cuando se produce la sincronización.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Suspender</strong></td> 
   <td>Elimina temporalmente la relación activa entre una Live Copy y su página de modelo.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Desasociar</strong></td> 
   <td>Elimina permanentemente la relación activa entre una Live Copy y su página de modelo.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Restablecer</strong></td> 
   <td><p>Restaurar una página de Live Copy a:</p> 
    <ul> 
     <li>Quite todas las cancelaciones de herencia y<br /> </li> 
     <li>Devuelva la página al mismo estado que la página de origen.</li> 
    </ul> <p>Restablecer afecta a cualquier cambio que haya realizado en las propiedades de la página, el sistema de párrafos y los componentes.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Superficial</strong></td> 
   <td>Copia activa de una sola página.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><strong>Profundo</strong></td> 
   <td>Copia activa de una página, junto con sus páginas secundarias.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Consulte [Información general sobre la API de Java](/help/sites-developing/extending-msm.md#overview-of-the-java-api) para los nombres de objeto.

## Live Copies {#live-copies}

Una Live Copy MSM es una copia de contenido específico del sitio para el que se mantiene una relación activa con el origen:

* La Live Copy hereda el contenido de su origen.
* La sincronización realiza la transferencia real de contenido cuando se realizan cambios en el origen.
* Una Live Copy puede considerarse como:

   * Superficial: una sola página
   * Profundo: la página, junto con sus páginas secundarias

* Las reglas de sincronización, llamadas configuraciones de implementación, determinan qué propiedades se sincronizan y cuándo se produce la sincronización.

En el ejemplo anterior, `/content/we-retail/language-masters/en` es la ubicación maestra global en inglés. Para reutilizar el contenido de este sitio, se crean Live Copies de MSM:

* El contenido siguiente `/content/we-retail/language-masters/en` es el origen.

* El contenido siguiente `/content/we-retail/language-masters/en` se copia debajo de `/content/we-retail/us/en/`, `/content/we-retail/gb/en`, `/content/we-retail/ca/en`y `/content/we-retail/au/en` nodos. Estas son las Live Copies.

* Los autores realizan cambios en las páginas siguientes `/content/we-retail/language-masters/en`.
* Cuando se activa, MSM sincroniza estos cambios con las Live Copies.

### Live Copies: composición {#live-copies-composition}

>[!NOTE]
>
>Los diagramas y las descripciones de esta sección representan instantáneas de posibles copias en vivo. No son exhaustivas, pero ofrecen una descripción general para resaltar características específicas.

Cuando crea una Live Copy por primera vez, las páginas de origen seleccionadas se reflejan en 1:1 en la Live Copy. Después de esto, también se pueden crear nuevos recursos (páginas o párrafos) directamente en la Live Copy, por lo que es útil tener en cuenta estas variaciones y cómo afectan a la sincronización. Las posibles composiciones incluyen las siguientes:

* [Live Copy con páginas que no sean de Live Copy](#live-copy-with-non-live-copy-pages)
* [Live Copies anidadas](#nested-live-copies)

La forma básica de Live Copy es:

* Live Copy páginas que reflejen las páginas de origen seleccionadas de forma individual.
* Una definición de configuración.
* Una relación activa definida para cada recurso:

   * Vincule el recurso de Live Copy con su modelo o origen.
   * Se utilizan para realizar la herencia y el despliegue.

* Los cambios se pueden [sincronizar](/help/sites-administering/msm-livecopy.md#synchronizing-your-live-copy) según los requisitos.

![chlimage_1-367](assets/chlimage_1-367.png)

#### Live Copy con páginas que no sean de Live Copy {#live-copy-with-non-live-copy-pages}

Cuando crea una Live Copy en AEM, puede ver y navegar por la rama de Live Copy y utilizar la funcionalidad de AEM normal en la rama de Live Copy. Esto significa que usted (o un proceso) puede crear nuevos recursos (páginas o párrafos) dentro de la rama de Live Copy (p. ej. `myCanadaOnlyProduct`).

* Estos recursos no tienen relación activa con las páginas de origen/modelo y no se sincronizan.
* Pueden producirse escenarios que MSM gestione como casos especiales. Por ejemplo, cuando crea (o un proceso) una página con la misma posición y nombre en las ramas de origen/modelo y Live Copy. Para estas situaciones, consulte [Conflictos de despliegue de MSM](/help/sites-administering/msm-rollout-conflicts.md) para obtener más información.

![chlimage_1-368](assets/chlimage_1-368.png)

#### Live Copies anidadas {#nested-live-copies}

Al crear (o un proceso) un [nueva página dentro de una Live Copy existente](#live-copy-with-non-live-copy-pages) esta nueva página también se puede configurar como una Live Copy de un modelo diferente. Esto se conoce como Live Copy anidado, donde el comportamiento de la segunda Live Copy (interna) se ve afectado por la primera Live Copy (externa) de la siguiente manera:

* Se puede continuar con un despliegue profundo activado para la Live Copy de nivel superior en la Live Copy anidada (por ejemplo, si el déclencheur coincide).
* Cualquier vínculo entre las fuentes se reescribirá dentro de las Live Copies.

   Por ejemplo, los vínculos del segundo al primer modelo se reescribirán como vínculos desde la Live Copy anidada/segunda a la primera Live Copy.

![chlimage_1-369](assets/chlimage_1-369.png)

>[!NOTE]
>
>Si mueve o cambia el nombre de una página dentro de la rama de Live Copy, esto se tratará (internamente) como una Live Copy anidada para permitir que el AEM rastree las relaciones.

#### Copias activas apiladas {#stacked-live-copies}

Una Live Copy se conoce como Live Copy apilada cuando se crea como el elemento secundario de una Live Copy superficial. Se comporta de la misma manera que una [Live Copy anidada](#nested-live-copies).

### Fuentes, modelos y configuraciones de modelo {#source-blueprints-and-blueprint-configurations}

Cualquier página o rama de páginas puede utilizarse como fuente de una Live Copy.

Sin embargo, MSM también le permite definir una configuración de modelo que especifica una ruta de origen. Los beneficios de utilizar una configuración de modelo son los siguientes:

* Permita que el autor use el **Despliegue** en un modelo: para insertar (explícitamente) modificaciones en Live Copies que heredan de este modelo.
* Permita que el autor utilice **Crear sitio**; esto permite al usuario seleccionar fácilmente idiomas y configurar la estructura de la Live Copy.
* Defina una configuración de lanzamiento predeterminada para Live Copies que tengan una relación con el modelo.

El origen de una Live Copy puede ser páginas normales o páginas incluidas en una configuración de modelo; ambos son casos de uso válidos.

El origen forma el modelo para la Live Copy. El modelo se define al:

* [Crear una configuración de modelo](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration)

   La configuración define (con antelación) las páginas que se utilizarán para crear la Live Copy.

* [Crear una Live Copy de una página](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   Las páginas utilizadas para crear la Live Copy (las páginas de origen) son las páginas de modelo.

   Se puede hacer referencia a la página de origen mediante una configuración de modelo, o no.

### Desplegar y sincronizar {#rollout-and-synchronize}

Un despliegue es la acción MSM central que sincroniza Live Copies con su origen. Puede realizar despliegues manualmente o automáticamente:

* Una [configuración de despliegue](#rollout-configurations) puede definirse de modo que [eventos](/help/sites-administering/msm-sync.md#rollout-triggers) específicos puedan provocar un despliegue automáticamente.
* Al crear una página de modelo, puede usar la variable [Despliegue](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) para insertar cambios en la Live Copy.

   **El comando Despliegue** está disponible en una página de modelo a la que se hace referencia mediante una configuración de modelo.

   ![chlimage_1-370](assets/chlimage_1-370.png)

* Al crear una página de Live Copy, puede utilizar la variable [Sincronizar](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) para extraer cambios del origen a la Live Copy.

   La variable **Sincronizar** siempre está disponible en la página de Live Copy (independientemente de si la página de origen/modelo está incluida en una configuración de modelo).

   ![chlimage_1-371](assets/chlimage_1-371.png)

### Opciones de configuración del lanzamiento {#rollout-configurations}

Una configuración de lanzamiento define cuándo y cómo se sincroniza una Live Copy con el contenido de origen. Una configuración de despliegue consta de un activador y una o más acciones de sincronización:

* **Activador**

   Un déclencheur es un evento que hace que se produzca la sincronización de la acción activa, como la activación de una página de origen. MSM define los activadores que puede utilizar.

* **Acciones de sincronización**

   Se realizan en la Live Copy para sincronizarla con el origen. Las acciones de ejemplo son copiar contenido, ordenar nodos secundarios y activar la página de Live Copy. MSM proporciona una serie de acciones de sincronización.

   >[!NOTE]
   >
   >Puede crear acciones personalizadas para su instancia mediante la API de Java.

Las configuraciones de lanzamiento se pueden reutilizar, de modo que más de una Live Copy pueda utilizar la misma configuración de lanzamiento. Varias [configuraciones de despliegue](/help/sites-administering/msm-sync.md#installed-rollout-configurations) se incluyen en una instalación estándar.

### Despliegue de conflictos {#rollout-conflicts}

Los lanzamientos pueden resultar complicados, especialmente cuando los autores editan contenido tanto en el origen como en la Live Copy, por lo que es útil tener en cuenta cómo AEM gestiona los [conflictos que podrían producirse durante la implementación](/help/sites-administering/msm-rollout-conflicts.md).

### Suspender y cancelar la herencia y sincronización {#suspending-and-cancelling-inheritance-and-synchronization}

Cada página y componente de una Live Copy está asociado con su página de origen y componente a través de una relación activa. La relación activa configura la sincronización del contenido de Live Copy desde el origen.

Puede **Suspender** la herencia de Live Copy de una página de Live Copy para que pueda cambiar las propiedades y los componentes de la página. Al suspender la herencia, las propiedades y los componentes de la página ya no se sincronizan con el origen.

Al editar una página individual, los autores pueden **Cancelar la herencia** de un componente. Cuando se cancela la herencia, la relación dinámica se suspende y la sincronización no se lleva a cabo para ese componente. Cancelar la herencia y sincronizar resulta útil cuando es necesario personalizar las secciones secundarias del contenido.

### Desasociación de una Live Copy {#detaching-a-live-copy}

También puede [separar una Live Copy](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy) de su modelo para eliminar todas las conexiones.

>[!CAUTION]
>
>La acción Desasociar es permanente e irreversible.

Separar de forma permanente elimina la relación activa entre una Live Copy y su página de modelo. Todas las propiedades relevantes para MSM se eliminan de la Live Copy y las páginas de Live Copy se convierten en una copia independiente.

>[!NOTE]
>
>Consulte [Desasociar una Live Copy](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy) para obtener detalles completos; incluyendo el impacto relacionado en las páginas secundarias y principales.

## Pasos estándar para usar MSM {#standard-steps-for-using-msm}

Los siguientes pasos describen el procedimiento estándar para utilizar MSM para reutilizar contenido y sincronizar cambios en Live Copies.

1. Desarrollar el contenido del sitio de origen.
1. Determine la configuración de despliegue que desea utilizar.

   1. MSM [instala varias configuraciones de despliegue](/help/sites-administering/msm-sync.md#installed-rollout-configurations) que pueden satisfacer varios casos de uso.
   1. Opcionalmente, puede [crear una configuración de despliegue](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) si es necesario.

1. Determine dónde debe [especificar las configuraciones de despliegue que se van a utilizar](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) y configúrelas según sea necesario.
1. Si es necesario, [crear una configuración de modelo](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration) que identifica el contenido de origen de la Live Copy.
1. [Crear una Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy).
1. Realice los cambios necesarios en el contenido de origen. Debe utilizar el proceso normal de revisión y aprobación de contenido que ha establecido su organización.
1. [Desplegar](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) el modelo, o [sincronizar la Live Copy](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) con los cambios.

## Personalización de MSM {#customizing-msm}

MSM proporciona herramientas para que su implementación se pueda adaptar a las complejidades excepcionales que puedan existir al compartir contenido:

* **Configuraciones de lanzamiento personalizadas**
   [Crear una configuración de lanzamiento](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) cuando las configuraciones de lanzamiento instaladas no cumplan con sus requisitos. Puede utilizar cualquier activador de despliegue y acción de sincronización disponible.

* **Acciones de sincronización personalizadas**
   [Crear una acción de sincronización personalizada](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) cuando las acciones instaladas no cumplen los requisitos específicos de la aplicación. MSM proporciona una API de Java para crear acciones de sincronización personalizadas.

## Prácticas recomendadas   {#best-practices}

La página [Prácticas recomendadas de MSM](/help/sites-administering/msm-best-practices.md) contiene información importante sobre la implementación.
