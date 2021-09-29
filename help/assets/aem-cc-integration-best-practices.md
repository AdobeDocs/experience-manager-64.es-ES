---
title: Prácticas recomendadas para la integración de Experience Manager y Creative Cloud
description: Prácticas recomendadas para integrar una implementación [!DNL Experience Manager] con Adobe Creative Cloud con el fin de optimizar los flujos de trabajo de transferencia de recursos y lograr la máxima eficacia
contentOwner: AG
feature: Collaboration,Adobe Asset Link,Desktop App
role: User,Admin
exl-id: cb9bea05-3359-4fb4-b935-59e522a5f387
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '3488'
ht-degree: 16%

---

# [!DNL Experience Manager] y prácticas recomendadas de  [!DNL Creative Cloud] integración {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets es una solución de administración de recursos digitales (DAM) que se puede integrar con Adobe Creative Cloud para ayudar a los usuarios de DAM a trabajar con equipos creativos, lo que optimiza la colaboración en el proceso de creación de contenido.

Adobe Creative Cloud proporciona a los equipos creativos un ecosistema de soluciones y servicios que les ayudan a crear recursos digitales. Incluye aplicaciones de escritorio y móviles, servicios en la nube como almacenamiento con sincronización de escritorio o experiencia web, así como mercados como Adobe Stock.

Siga leyendo para saber qué integraciones escoger entre el escritorio y el DAM de nivel empresarial en función de su caso de uso y cuáles son las prácticas recomendadas asociadas para los flujos de trabajo de conexión.

>[!NOTE]
>
>El uso compartido de carpetas de [!DNL Experience Manager] a Creative Cloud está obsoleto y ya no se explica en esta guía. Adobe recomienda utilizar funciones más nuevas, como [Adobe Asset Link](https://helpx.adobe.com/es/enterprise/using/adobe-asset-link.html) o [[!DNL Experience Manager] aplicación de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html), para proporcionar al usuario creativo acceso a los recursos administrados en [!DNL Experience Manager].

## Necesidades de colaboración de creativos, especialistas en marketing y usuarios de DAM {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Requisitos | Caso de uso | Superficies implicadas |
|---|---|---|
| Simplificar la experiencia para creativos en equipos de escritorio | Optimice el acceso a los recursos desde un DAM ([!DNL Assets]) para los profesionales creativos o, en términos más generales, para los usuarios de escritorio que trabajen en aplicaciones nativas de creación de recursos. Necesitan una forma sencilla y sencilla de descubrir, utilizar (abrir), editar y guardar cambios en [!DNL Experience Manager], así como cargar nuevos archivos. | escritorio Win o Mac; aplicaciones Creative Cloud |
| Proporcionar recursos listos para usar de Adobe Stock de alta calidad | Los especialistas en marketing ayudan a acelerar el proceso de creación de contenido mediante la asistencia en el abastecimiento y descubrimiento de recursos. Los profesionales creativos utilizan los recursos aprobados directamente desde sus herramientas creativas. | [!DNL Assets]; Adobe Stock Marketplace; campos de metadatos |
| Distribuir y compartir recursos por organizaciones | Los departamentos internos/las sucursales locales y los socios, distribuidores y agencias externos utilizan los recursos aprobados compartidos por la organización principal. La organización desea compartir de forma segura y transparente los recursos creados para una reutilización más amplia. | Brand Portal, Asset Share Commons |

## Ofertas de Adobe para apoyar la necesidad de colaboración {#adobe-offerings-to-support-the-collaboration-need}

| Propuesta de valor para las personas implicadas | oferta de Adobe | Superficies implicadas |
|---|---|---|
| Los usuarios creativos descubren recursos de [!DNL Experience Manager], los abren y usan, editan y cargan cambios en [!DNL Experience Manager], así como cargan nuevos archivos en [!DNL Experience Manager], sin salir de las aplicaciones Creative Cloud. | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator y InDesign |
| Los usuarios empresariales simplifican la apertura y el uso de recursos, editan y cargan cambios en [!DNL Experience Manager] y cargan nuevos archivos en [!DNL Experience Manager] desde el entorno de escritorio. Utilizan una integración genérica para abrir cualquier tipo de recurso en la aplicación de escritorio nativa, incluidos los que no sean de Adobe. | Aplicación de escritorio de [[!DNL Experience Manager]  ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] aplicación de escritorio en escritorio Win y Mac |
| Los especialistas en marketing y los usuarios empresariales descubren, previsualizan, otorgan licencias y guardan y administran los recursos de Adobe Stock desde [!DNL Experience Manager]. Los recursos con licencia y guardados proporcionan metadatos de Adobe Stock seleccionados para un mejor gobierno. | [Integración de Experience Manager y Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] interfaz web |

Este artículo se centra principalmente en los dos primeros aspectos de las necesidades de colaboración. La distribución y el abastecimiento de activos a escala se mencionan brevemente como un caso de uso. Para estas necesidades, considere Adobe Brand Portal o Asset Share Commons. Las soluciones alternativas como [Brand Portal](https://helpx.adobe.com/es/experience-manager/brand-portal/user-guide.html), las soluciones que se pueden crear en función de los componentes de [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/), [Link Share](/help/assets/link-sharing.md), utilizando [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) deben revisarse en función de requisitos específicos.

![conexiones de Creative Cloud para  [!DNL Experience Manager]: Decidir qué capacidad utilizar](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### Asignación de casos de uso

| Caso de uso | Aplicación de escritorio de [!DNL Experience Manager] | Uso compartido de carpetas | Otras soluciones |
|---|---|---|---|
| Compartir un número menor de activos DAM (1) con un usuario creativo | ✔ | š |  |
| Compartir un mayor número (2) de activos DAM con un usuario creativo | ✔ | ü | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Uso compartido de recursos](assets-finder-editor.md) |
| Compartir recursos DAM con usuarios que tienen acceso a DAM | ✔ | š | [Vínculos compartidos](link-sharing.md) |
| Compartir recursos DAM con usuarios que no tienen acceso a DAM | ü | ✔ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [Uso compartido de recursos](assets-finder-editor.md) |
| Guardar un número/volumen menor de recursos en DAM | ✔ | š | [Carga de la interfaz de usuario web](managing-assets-touch-ui.md) |
| Guardar un mayor número de activos en DAM (3) | ✔ | ü | [Herramienta/script ](managing-assets-touch-ui.md) <br> UploadCustom de la interfaz de usuario web |
| Migración de una gran cantidad de activos a DAM | ü | ü | [Guía de migración](assets-migration-guide.md) |
| Abrir rápidamente un recurso en el escritorio | ✔ | ü |  |
| Abrir y cambiar recursos rápidamente en el escritorio | ✔ | ü |  |

La leyenda de los símbolos:

* š ✔: solución preferida
* š: solución aceptable
* ü no debería usarse para el caso de uso

Observaciones adicionales:

* 1) Menor número de activos: por ejemplo, un pequeño conjunto de activos relacionados con un proyecto o una campaña
* (2) Mayor número de activos: por ejemplo, todos los recursos aprobados de la organización
* (3) Utilizar la función [!DNL Experience Manager] carpeta de carga de aplicaciones de escritorio

Para admitir casos de uso de distribución de recursos, se deben considerar otras soluciones:

* [Brand ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) Portal para un complemento configurable de SaaS a  [!DNL Experience Manager] Assets para publicar recursos.
* Las soluciones personalizadas se crean en función del código [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/).
* [!DNL Experience Manager] [vincular ](/help/assets/link-sharing.md) compartir para compartir recursos ad hoc mediante vínculos.
* [[!DNL Experience Manager] Interfaz web de activos ](/help/assets/managing-assets-touch-ui.md) con áreas para partes externas garantizadas por la configuración de Control de  [!DNL Experience Manager] acceso y con los ajustes de configuración de red/TI necesarios, lo que proporciona acceso a estos usuarios externos a  [!DNL Experience Manager].

## Conceptos clave y casos de uso {#key-concepts-and-use-cases}

### Glosario de términos comunes {#glossary-of-common-terms}

* **Trabajo en curso o trabajo en curso creativo (WIP):** Fase del ciclo vital de los recursos en la que sufren varios cambios y, por lo general, no están listos para compartirse con equipos más amplios.
* **Recursos listos para el proceso creativo:** Recursos que están listos para compartirse con un equipo más amplio o que han sido seleccionados o aprobados por el equipo creativo para compartirlos con equipos de marketing o de LOB.
* **Aprobaciones de recursos:** Proceso de aprobación que se ejecuta para los recursos ya cargados en DAM, que generalmente incluye aprobaciones de marca, aprobaciones legales, etc.
* **Recurso final:** Recurso que ha pasado por todas las aprobaciones/etiquetado de metadatos y está listo para que lo utilice el equipo superior. Este recurso se almacena en DAM y se pone a disposición de todos los usuarios (o de todos los interesados). Se puede utilizar en canales de marketing o en equipos creativos para crear diseños.
* **Cambio o actualización menor de recursos:** Un cambio rápido y pequeño en un recurso digital. A menudo se realiza como respuesta a una solicitud de edición, revisión o aprobación de recursos (por ejemplo, cambiar la posición, el tamaño del texto, ajustar la saturación/brillo, el color, etc.).
* **Cambio o actualización de recursos principales:** Un cambio en un recurso digital que requiere un trabajo considerable y que a veces debe hacerse durante un período de tiempo más largo. Generalmente incluye varios cambios. El recurso debe guardarse varias veces mientras se actualiza. Las principales actualizaciones de recursos suelen hacer que el recurso entre en una etapa de trabajo en curso.
* **DAM**: Administración de recursos digitales. En este documento, es sinónimo de [!DNL Experience Manager Assets], a menos que se mencione específicamente lo contrario.
* **Usuario creativo:** Un profesional creativo que crea recursos digitales mediante las aplicaciones y los servicios de Creative Cloud. En algunos casos, un usuario creativo puede ser miembro de un equipo creativo que puede utilizar Creative Cloud, pero no crea recursos digitales (como un director creativo o un administrador de equipo creativo).
* **Usuario de DAM:** Usuario típico de un sistema DAM. Según la organización, un usuario de DAM puede ser un usuario de marketing o no de marketing, por ejemplo un usuario de línea de negocios (LOB), bibliotecario, vendedor, etc.

### Consideraciones al utilizar [!DNL Experience Manager] e integración con el Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

* Consulte [prácticas recomendadas de la aplicación de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Consulte [Integración con Adobe Stock](aem-assets-adobe-stock.md)
* Consulte [Vínculo de recursos de Adobe](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Este es un breve resumen de las prácticas recomendadas para la integración de Experience Manager y Creative Cloud. Lea el resto de este documento para conocer en detalle estos aspectos.

* **Para usuarios creativos que trabajan con en Photoshop, InDesign o Illustrator:** Adobe Asset Link ofrece la mejor experiencia de usuario, incluida la gestión del trabajo en curso en los recursos extraídos de [!DNL Experience Manager]
* **Para simplificar el acceso a los recursos desde el escritorio para cualquier aplicación o formato de archivo genérico:**[!DNL Experience Manager] Use la aplicación de escritorio de 
* **Comprender por qué y cuándo almacenar recursos en DAM:** Actualizaciones que se pondrán a disposición del equipo de la organización al completo
* **Tenga en cuenta el volumen de recursos compartidos:** Si el caso de uso es la distribución de recursos, la administración y la seguridad podrían ser los aspectos más importantes. Considere utilizar herramientas creadas para hacerlo a escala, como Brand Portal.
* **Comprenda el ciclo vital de los recursos:** Conozca cómo los distintos equipos administran los recursos en su organización
* **Gestione los ahorros frecuentes de los recursos con cuidado:** Adobe Asset Link se encarga de ello con PS, AI e ID. Para otras aplicaciones, no realice tareas de trabajo en curso en carpetas asignadas o compartidas a menos que necesite todos los cambios en DAM

### Acceso a los recursos de Adobe Stock desde [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[[!DNL Experience Manager] e ](/help/assets/aem-assets-adobe-stock.md) integración con Adobe Stock ofrecen a los  [!DNL Experience Manager] usuarios la posibilidad de buscar, previsualizar, obtener licencias y guardar recursos de Adobe Stock en  [!DNL Experience Manager]. Los recursos de Adobe Stock con licencia y guardados han seleccionado metadatos de Stock, que pueden utilizarse para buscarlos con filtros adicionales.

Algunos puntos importantes sobre esta integración:

* Cuando los recursos de existencias de Adobe se guardan en [!DNL Experience Manager], se convierten en [!DNL Experience Manager] Assets normales, con el binario guardado en el repositorio [!DNL Experience Manager]. Algunos metadatos relacionados con Adobe Stock se guardan para el recurso en [!DNL Experience Manager]; de lo contrario, el proceso de ingesta tiene el mismo aspecto que para cualquier otro archivo. Por ejemplo, si las etiquetas inteligentes están activas, estas se añaden a estos recursos al guardarlos.
* El recurso guardado en [!DNL Experience Manager] es una copia, no un vínculo de nuevo en Adobe Stock.

**Uso de recursos guardados desde Adobe Stock en  [!DNL Experience Manager] Creative Cloud**. Esta integración es independiente de Asset Link de Adobe, pero Asset Link de Adobe reconoce estos recursos guardados de Stock de esa manera y muestra metadatos adicionales y el icono Stock de estos recursos en la interfaz de usuario de la extensión Asset Link de Adobe en Photoshop, Illustrator o InDesign. Los archivos están disponibles para explorar, abrir, etc. porque son [!DNL Experience Manager] recursos normales cuando se guardan en [!DNL Experience Manager].
Los usuarios creativos que trabajen en aplicaciones de Creative Cloud con la extensión de Adobe Asset Link presente, además de tener acceso a recursos ya licenciados de Adobe Stock en [!DNL Experience Manager], también pueden utilizar el panel Bibliotecas de Creative Cloud para buscar, previsualizar y obtener licencias para recursos de Adobe Stock.
Los recursos de Adobe Stock con licencia y guardados en [!DNL Experience Manager] quedan disponibles para los equipos más amplios que acceden a la implementación de [!DNL Experience Manager] Assets, mientras que los recursos de licencia de creativos de Adobe Stock mediante el panel Bibliotecas de Creative Cloud solo se ponen a disposición de los usuarios de forma predeterminada en su cuenta de Creative Cloud.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Acerca del almacenamiento de recursos en un DAM {#about-storing-assets-in-a-dam}

Para diseñar un flujo de trabajo eficiente entre los equipos creativos y los equipos de marketing/línea de negocios (LOB) y elegir las mejores capacidades de asistencia, es importante comprender cuándo y por qué los recursos se almacenan en DAM.

### Por qué los recursos se almacenan en DAM {#why-assets-are-stored-in-dam}

El almacenamiento de recursos en DAM los hace fácilmente accesibles y asequibles. Garantiza que numerosos usuarios de toda la organización o el ecosistema puedan aprovechar los recursos, lo que incluye socios, clientes, etc.

La mayoría de las organizaciones solo almacenan recursos que son relevantes para los procesos de marketing/LOB descendentes (publicándolos en canales como el canal web a través de [!DNL Experience Manager] Sitios u otros canales servidos por Adobe Experience Cloud, Advertising Cloud y medidos por Analytics Cloud, proporcionándolos a usuarios/socios, etc.). Además, las organizaciones almacenan activos que pueden estar sujetos a un proceso de revisión/aprobación en DAM. De esta manera, DAM almacena principalmente activos que tienen altas posibilidades de ser aprovechados y evita almacenar activos inactivos.

El almacenamiento de recursos también está sujeto a consideraciones técnicas y de utilización de recursos. DAM proporciona servicios adicionales en torno a los recursos almacenados, incluida la extracción de metadatos, el control de versiones, la generación de vistas previas/transcodificación, la administración de referencias y la adición de información de control de acceso. Estos servicios consumen tiempo y recursos de infraestructura adicionales.

A menudo, no es deseable almacenar todos los recursos y actualizaciones. Por ejemplo, si las actualizaciones de recursos específicos son de mala calidad y consumen recursos excesivos, es posible que los recursos no se almacenen en DAM.

### Cuando los recursos se almacenan en DAM {#when-assets-are-stored-in-dam}

Los equipos creativos (y las organizaciones) no suelen estar interesados en almacenar recursos en cada etapa del ciclo de vida de los recursos. Por ejemplo, evitan almacenar recursos en los siguientes casos:

* Activos que aún no se han finalizado o que están sujetos a experimentación
* Recursos que no superan el ciclo de revisión del equipo creativo/interno
* En comparación con el recurso en cuestión, el equipo tiene mejores candidatos para representar su trabajo en equipos externos

Normalmente, las siguientes clases de activos se almacenan en DAM:

* Activos que han alcanzado un cierto vencimiento y que se consideran listos para compartirse
* Recursos preseleccionados por el equipo creativo
* Formatos de recurso específicos que el marketing puede utilizar o solicitar, según un contrato o acuerdo específico (por ejemplo, archivos JPG convertidos a partir de archivos RAW, TIFF/imágenes de originales PSD)

### Cuando las actualizaciones de los recursos se almacenan en DAM {#when-updates-to-assets-are-stored-in-dam}

Como regla, solo las actualizaciones de los recursos que sean relevantes para el conjunto más amplio de usuarios de DAM deben almacenarse en DAM. Garantiza que los usuarios (funciones de marketing y similares) solo vean versiones relevantes en la cronología de recursos de DAM.

Normalmente, los cambios se relacionan con hitos importantes del ciclo vital de los recursos. Por ejemplo, el recurso listo para la creación inicial o una actualización oficial basada en una solicitud o revisión proporcionada por el equipo creativo deben almacenarse y crearse versiones en DAM.

La actualización del equipo creativo para que la revise el equipo de marketing después de una solicitud de cambio en el recurso existente en DAM es un ejemplo de una actualización relevante. Debe almacenarse y crearse una versión en DAM para su posterior referencia o para volver a la versión anterior.

Los siguientes son ejemplos de actualizaciones que normalmente no son relevantes:

* Versiones anteriores de recursos cargados antes de que estén listos para su revisión de marketing
* Cambios creativos frecuentes en el recurso en la fase de trabajo en curso antes de que el equipo creativo decida que el recurso está listo

### Acceso de usuario a DAM {#user-access-to-dam}

[!DNL Experience Manager] Assets es compatible con dos tipos de usuarios en función de su acceso a la implementación de  [!DNL Experience Manager] Assets. Normalmente, los usuarios de la red empresarial (firewall) tienen acceso directo a DAM. Otros usuarios fuera de la red empresarial no tendrían acceso directo. El tipo de usuario determina qué integraciones se pueden utilizar desde el punto de vista técnico.

#### Usuarios creativos con acceso directo a DAM {#creative-users-with-direct-access-to-dam}

Normalmente, los equipos creativos o agencias/profesionales creativos internos incorporados a la red interna tienen acceso a la instancia de DAM, incluido el inicio de sesión [!DNL Experience Manager].

En estos casos, la aplicación de escritorio [!DNL Experience Manager] ayuda a proporcionar un acceso fácil a los recursos finales/aprobados y le permite guardar en DAM recursos listos para la creación.

#### Usuarios creativos sin acceso a DAM {#creative-users-without-access-to-dam}

Las agencias externas y los trabajadores independientes sin acceso directo a la instancia de DAM pueden requerir acceso a los recursos aprobados o desean añadir sus nuevos diseños a DAM.

En estos casos, puede aprovechar la integración [!DNL Experience Manager]/Creative Cloud para mejorar el flujo de trabajo. El requisito previo es que los usuarios creativos tengan una Adobe ID y una cuenta de Creative Cloud con servicio de almacenamiento.

Utilice las siguientes estrategias para proporcionar acceso a los recursos finales/aprobados:

* Para proporcionar acceso a un gran número de recursos: Utilice [[!DNL Experience Manager] Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) o la implementación de [Asset Share](assets-finder-editor.md) por parte del cliente en la [!DNL Experience Manager] infraestructura de publicación

* Para proporcionar acceso a algunos recursos: El uso compartido de carpetas [!DNL Experience Manager] con Adobe Creative Cloud se puede usar además de [!DNL Experience Manager] Assets Brand Portal o Asset Share. Tenga en cuenta que existen ciertas limitaciones relacionadas con esta integración, que se explican con más detalle en este artículo.

### Casos de uso {#use-cases}

Los siguientes casos de uso describen varios tipos de flujos de trabajo entre DAM y el escritorio de designer.

#### Crear nuevos diseños con recursos de DAM {#creating-new-designs-using-assets-from-dam}

El diagrama siguiente ilustra el ciclo vital de los recursos digitales. Describe cómo los usuarios creativos y los usuarios de DAM (especialistas en marketing, usuarios de LOB) aprovechan los recursos existentes y los utilizan para crear más recursos y enviarlos para su aprobación.

![chlimage_1-301](assets/chlimage_1-301.png)

El ciclo de vida de los recursos incluye las siguientes etapas:

1. Comparta los recursos aprobados en creative desktop: Los recursos finales de DAM están disponibles para el usuario creativo (en el escritorio)
1. Cree un nuevo diseño (recurso digital creativo): Un nuevo archivo se almacena en el área de trabajo en curso (WIP).
1. Utilice los recursos aprobados (colóquelos) en un nuevo diseño: El usuario creativo produce un nuevo recurso mediante los recursos aprobados existentes en las aplicaciones de Creative Cloud
1. Guardar con frecuencia las actualizaciones de WIP: El usuario creativo se repite rápidamente y guarda el archivo con frecuencia. En este momento, el usuario creativo puede colaborar con otros, pero las actualizaciones guardadas con frecuencia no suelen ser de interés para los usuarios de DAM.
1. El recurso alcanza el estado listo para el creativo y se guarda en la carpeta Creative Ready.
1. Actualización de recursos : Los usuarios de DAM disponen de una actualización de recursos o de un nuevo archivo
1. El recurso se pone en producción: Se trata de un proceso DAM que, según la organización, puede incluir etiquetado, aprobaciones y cambios en el control de acceso. En esta fase, el recurso se considera definitivo y puede ser utilizado por equipos más amplios que aprovechen DAM. También pueden utilizarla usuarios creativos para crear otros recursos.

A continuación se presentan algunas recomendaciones generales sobre cómo administrar recursos a través de este proceso:

* Utilice un sistema o área de almacenamiento dedicada, como la carpeta sincronizada Adobe Creative Cloud Assets, para los archivos WIP: Las actualizaciones frecuentes que no son relevantes para los usuarios de DAM son mejor gestionadas por un sistema dedicado y no desde [!DNL Experience Manager] Assets. Los recursos de WIP se pueden sincronizar con el disco local mediante la aplicación de escritorio de Adobe Creative Cloud, guardarse en almacenamiento local, etc.
* Utilice carpetas/recursos compartidos independientes para los recursos finales y los recursos cargados en DAM: para una mayor claridad, los recursos finales deben tener su propia carpeta asignada/compartida (ejemplo &quot;final&quot; anterior), y los recursos que se van a cargar de nuevo en DAM deben tener los suyos propios (&quot;Creative Ready&quot;)

#### Cambiar recursos existentes administrados en DAM {#changing-existing-assets-managed-in-dam}

En algunos casos, los recursos de DAM pueden requerir cambios. Algunos ejemplos son:

* Solicitud de cambios en los recursos procedentes de la revisión y aprobación realizadas en [!DNL Experience Manager] Assets
* Principales actualizaciones de los recursos finales existentes
* Ediciones rápidas en un archivo existente (especialmente antes de que se apruebe por fin)

En estos casos, la aplicación de escritorio [!DNL Experience Manager] proporciona la forma más sencilla de realizar estas operaciones.

![chlimage_1-302](assets/chlimage_1-302.png)

Este es el flujo de eventos que se muestran en el diagrama:

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for [!DNL Experience Manager] desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** Comparta el recurso de DAM a escritorio o ábralo directamente en el escritorio en la aplicación que desee (por ejemplo, Adobe Photoshop, etc.). Se recomienda desproteger para bloquear el archivo.
* **2:** Actualización menor: Edite el archivo y guarde los cambios.
* Flujo alternativo al paso 2

   * **R:** Actualización principal: Si el archivo requiere un conjunto detallado de cambios, debe guardarse de forma intermitente y copiarse en una carpeta o área de trabajo en curso.
   * **B:** El trabajo continúa en el archivo de las carpetas WIP. Los cambios guardados no se sincronizan con la versión en DAM
   * **C:**  Una vez completadas las actualizaciones, el archivo se copia de nuevo o se guarda en la carpeta asignada

* **3:** Las actualizaciones de recursos se reflejan en DAM. Marque el recurso para desbloquearlo.
* **4:** El recurso se pone en producción.

A continuación se presentan algunas recomendaciones generales sobre cómo administrar recursos a lo largo de este proceso:

* Evite guardar directamente un archivo que haya abierto desde un recurso compartido de red asignado por la aplicación de escritorio [!DNL Experience Manager] a menos que los cambios realizados en el archivo sean pequeños.
* Copie el archivo en una carpeta de trabajo en curso independiente si desea realizar cambios adicionales, guardarlo de forma intermitente o colaborar con el equipo creativo.

#### Carga masiva a DAM {#bulk-upload-to-dam}

Puede que tenga que cargar simultáneamente un mayor número de archivos en DAM en algunos casos, por ejemplo:

* Carga de resultados de fotos o proyectos más grandes
* Carga de recursos proporcionados por agencias creativas
* Carga de recursos seleccionados de un conjunto mayor si la selección se realiza fuera de DAM

Tenga en cuenta que esta descripción se refiere a la carga de archivos operacionalmente (por ejemplo, cada semana o con cada sesión fotográfica , etc.), como parte normal del flujo de trabajo del usuario del escritorio. Las migraciones de recursos grandes no se tratan aquí.

Puede aprovechar las siguientes capacidades si desea cargar recursos de forma masiva:

* Para cargar carpetas grandes/jerárquicas, utilice la aplicación de escritorio [!DNL Experience Manager], que proporciona la función [Carga de carpetas](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload). También puede cargar estructuras de carpetas jerárquicas. Los recursos se cargan en segundo plano y, por lo tanto, no están vinculados a una sesión del explorador web
* Si desea cargar algunos archivos de una sola carpeta, arrástrelos directamente desde el escritorio a la interfaz de usuario web o utilice la opción Crear en la interfaz de usuario web de [!DNL Experience Manager] Assets.

>[!NOTE]
>
>Según los requisitos empresariales, también puede utilizar el cargador personalizado.

#### Administrar recursos digitales directamente desde el escritorio {#managing-digital-assets-directly-from-desktop}

Si utiliza Recursos compartidos de archivos de red para administrar recursos digitales, el uso del recurso compartido de red asignado por la aplicación de escritorio [!DNL Experience Manager] podría considerarse un sustituto conveniente. Al realizar la transición de archivos compartidos de red, recuerde que la [!DNL Experience Manager] interfaz de usuario web proporciona un completo conjunto de funcionalidades de administración de recursos digitales que van mucho más allá de lo posible en un recurso compartido de red (búsqueda, colecciones, metadatos, colaboración, previsualizaciones, etc.) y la aplicación de escritorio [!DNL Experience Manager] proporciona un práctico vínculo para conectar el repositorio DAM del lado del servidor con el trabajo en el escritorio.

Evite utilizar la aplicación de escritorio [!DNL Experience Manager] para administrar recursos directamente en la red compartida de [!DNL Experience Manager] Assets. Por ejemplo, evite utilizar la aplicación de escritorio [!DNL Experience Manager] para mover/copiar varios archivos. En su lugar, utilice la interfaz de usuario web de [!DNL Experience Manager] Assets para arrastrar carpetas desde Finder/Explorer al recurso compartido de red o utilice la función [!DNL Experience Manager] Carga de carpetas de recursos .

#### Migración de recursos {#asset-migration}

Para planificar y ejecutar las migraciones de recursos desde un sistema existente a un nuevo sistema o la migración de un gran volumen de recursos almacenados en servidores, consulte la [Guía de migración](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] las integraciones de aplicaciones de escritorio y  [!DNL Experience Manager] de Creative Cloud no admiten estas migraciones. Debido a los grandes volúmenes de recursos que se van a ingerir, y a los requisitos adicionales en torno a la asignación, transformación e ingesta de metadatos, las migraciones deben manejarse con diferentes herramientas y enfoques.

>[!MORELIKETHIS]
>
>* [Vínculo de recurso de Adobe](https://helpx.adobe.com/in/enterprise/admin-guide.html/in/enterprise/using/adobe-asset-link.ug.html)
>* [[!DNL Experience Manager] prácticas recomendadas para las aplicaciones de escritorio](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [[!DNL Experience Manager] Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [[!DNL Experience Manager] Integración con Adobe Stock](aem-assets-adobe-stock.md)

