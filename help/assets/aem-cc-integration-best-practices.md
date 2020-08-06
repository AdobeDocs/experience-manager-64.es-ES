---
title: Prácticas recomendadas para la integración de AEM y Creative Cloud
description: Prácticas recomendadas para integrar una implementación AEM con Adobe Creative Cloud a fin de optimizar los flujos de trabajo de transferencia de recursos y lograr la máxima eficacia
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1f44950e3e0653df61289e1bd435d13829051365
workflow-type: tm+mt
source-wordcount: '3578'
ht-degree: 17%

---


# Prácticas recomendadas para la integración de AEM y Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets es una solución de administración de recursos digitales (DAM) que se puede integrar con Adobe Creative Cloud para ayudar a los usuarios de DAM a trabajar con equipos creativos, lo que optimiza la colaboración en el proceso de creación de contenido.

Adobe Creative Cloud ofrece a los equipos creativos un ecosistema de soluciones y servicios para ayudarles a crear recursos digitales. Incluye aplicaciones de escritorio y móviles, servicios en la nube como almacenamiento con sincronización de escritorio o experiencia web, así como mercados como Adobe Stock.

Siga leyendo para saber qué integraciones elegir entre el escritorio y el DAM de nivel empresarial en función de su caso de uso y cuáles son las prácticas recomendadas asociadas para los flujos de trabajo de conexión.

>[!NOTE]
>
>El uso compartido de AEM a carpetas de Creative Cloud está obsoleto y ya no se trata en esta guía. Adobe recomienda el uso de funciones más nuevas como [Adobe Asset Link](https://helpx.adobe.com/es/enterprise/using/adobe-asset-link.html) o [AEM aplicación](https://docs.adobe.com/content/help/es-ES/experience-manager-desktop-app/using/introduction.translate.html) de escritorio para proporcionar al usuario creativo acceso a los recursos gestionados en AEM.

## Necesidades de colaboración de creativos, especialistas en mercadotecnia y usuarios de DAM {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Requisitos | Caso de uso | Superficies involucradas |
|---|---|---|
| Simplifique la experiencia para creativos en equipos de escritorio | Racionalice el acceso a los recursos desde un DAM (AEM Assets) para los profesionales creativos o, en términos más generales, para los usuarios de escritorio que trabajan en aplicaciones nativas de creación de recursos. Necesitan una forma sencilla y sencilla de descubrir, utilizar (abrir), editar y guardar los cambios en AEM, así como cargar nuevos archivos. | Win o Mac Desktop; Aplicaciones Creative Cloud |
| Proporcionar recursos listos para usar y de alta calidad de Adobe Stock | Los especialistas en mercadotecnia ayudan a acelerar el proceso de creación de contenido mediante la ayuda en el descubrimiento y el abastecimiento de recursos. Los profesionales creativos utilizan los recursos aprobados directamente desde sus herramientas creativas. | AEM Assets; Adobe Stock Marketplace; campos de metadatos |
| Distribuir y compartir recursos por organizaciones | Los departamentos internos/sucursales locales y los socios, distribuidores y agencias externos utilizan los recursos aprobados compartidos por la organización principal. La organización desea compartir de forma segura y transparente los recursos creados para una reutilización más amplia. | Brand Portal, Asset Share Commons |

## Ofertas de Adobe para apoyar la necesidad de colaboración {#adobe-offerings-to-support-the-collaboration-need}

| Propuesta de valor para las personas involucradas | Oferta de Adobe | Superficies involucradas |
|---|---|---|
| Los usuarios creativos descubren recursos de AEM, los abren y utilizan, editan y cargan cambios en AEM, así como cargan nuevos archivos en AEM sin salir de las aplicaciones Creative Cloud. | [Adobe Asset Link](https://helpx.adobe.com/es/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator y InDesign |
| Los usuarios empresariales simplifican la apertura y el uso de recursos, la edición y la carga de cambios en AEM y la carga de nuevos archivos en AEM desde el entorno de escritorio. Utilizan una integración genérica para abrir cualquier tipo de recurso en la aplicación de escritorio nativa, incluidos los que no son de Adobe. | [Aplicación de escritorio de AEM](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) | AEM aplicación de escritorio en el escritorio de Windows y Mac |
| Los especialistas en marketing y los usuarios empresariales descubren, previsualización, otorgan licencias y guardan y gestionan los recursos de Adobe Stock desde AEM. Los recursos con licencia y guardados proporcionan metadatos de Adobe Stock seleccionados para una mejor gestión. | [Integración de Experience Manager y Adobe Stock](aem-assets-adobe-stock.md) | AEM interfaz web |

Este artículo se centra principalmente en los dos primeros aspectos de las necesidades de colaboración. La distribución y el abastecimiento de activos a escala se mencionan brevemente como un caso de uso. Para estas necesidades, considere Adobe Brand Portal o Asset Share Commons. Alternate solutions such as [Brand Portal](https://helpx.adobe.com/es/experience-manager/brand-portal/user-guide.html), solutions that can be built based on [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) components, [Link Share](/help/assets/link-sharing.md), using [Experience Manager Assets](/help/assets/managing-assets-touch-ui.md) should be reviewed based on specific requirement.

![Conexiones de Creative Cloud para AEM: Decidir qué capacidad utilizar](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with AEM Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### Asignación de casos de uso

| Caso de uso | Aplicación de escritorio de AEM | Uso compartido de carpetas | Otras soluciones |
|---|---|---|---|
| Compartir un número menor (1) de recursos DAM con un usuario creativo | ✔✔ | ✔ |  |
| Compartir un mayor número (2) de recursos DAM con un usuario creativo | ✔✔ | ✘ | [Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) <br> [Uso compartido de recursos](assets-finder-editor.md) |
| Compartir recursos DAM con usuarios que tienen acceso a DAM | ✔✔ | ✔ | [Vínculos compartidos](link-sharing.md) |
| Compartir recursos DAM con usuarios que no tienen acceso a DAM | ✘ | ✔✔ | [Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) <br> [Uso compartido de recursos](assets-finder-editor.md) |
| Guardar un menor número/volumen de recursos en DAM | ✔✔ | ✔ | [Carga de la interfaz de usuario web](managing-assets-touch-ui.md) |
| Guardar un mayor número de recursos en DAM (3) | ✔✔ | ✘ | [Herramienta / script personalizado de carga](managing-assets-touch-ui.md) <br> de interfaz de usuario web |
| Migrar una gran cantidad de recursos a DAM | ✘ | ✘ | [Guía de migración](assets-migration-guide.md) |
| Abrir rápidamente un recurso en el escritorio | ✔✔ | ✘ |  |
| Abra y cambie recursos rápidamente en el escritorio | ✔✔ | ✘ |  |

La leyenda de los símbolos:

* gil ✔: solución preferida
* PEG: solución aceptable
* Archivo: no debe usarse para el caso de uso

Observaciones adicionales:

* (1) Menor número de activos: por ejemplo, un pequeño conjunto de recursos relacionados con un proyecto o una campaña
* 2) Mayor número de activos: por ejemplo, todos los recursos aprobados de la organización
* (3) Uso de AEM función de carpeta de carga de aplicaciones de escritorio

Para admitir casos de uso de distribución de recursos, se deben considerar otras soluciones:

* [Brand Portal](https://helpx.adobe.com/es/experience-manager/brand-portal/user-guide.html) para un complemento SaaS configurable en AEM Assets para publicar recursos.
* Las soluciones personalizadas se crean en función de la base de código de [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) .
* AEM uso compartido [de](/help/assets/link-sharing.md) vínculos para compartir recursos ad hoc mediante vínculos.
* [Interfaz](/help/assets/managing-assets-touch-ui.md) web de AEM Assets con áreas para partes externas aseguradas por AEM configuración de Control de acceso y con los ajustes de configuración de red/TI necesarios, lo que proporciona a estos usuarios externos acceso a AEM.

## Conceptos clave y casos de uso {#key-concepts-and-use-cases}

### Glosario de términos comunes {#glossary-of-common-terms}

* **Trabajo en curso o trabajo en curso creativo (WIP):** Fase del ciclo vital de los recursos en la que sufren varios cambios y, por lo general, no están listos para compartirse con equipos más amplios.
* **Recursos listos para el proceso creativo:** Recursos que están listos para compartirse con un equipo más amplio o que han sido seleccionados o aprobados por el equipo creativo para compartirlos con equipos de marketing o de LOB.
* **Aprobaciones de recursos:** Proceso de aprobación que se ejecuta para los recursos ya cargados en DAM, que generalmente incluye aprobaciones de marca, aprobaciones legales, etc.
* **Recurso final:** Recurso que ha pasado por todas las aprobaciones/etiquetado de metadatos y está listo para que lo utilice el equipo superior. Este recurso se almacena en DAM y se pone a disposición de todos los usuarios (o de todos los interesados). Se puede utilizar en canales de marketing o en equipos creativos para crear diseños.
* **Cambio o actualización menor de recursos:** Un cambio rápido y pequeño en un recurso digital. A menudo se realiza como respuesta a una solicitud de edición, revisión o aprobación de recursos (por ejemplo, cambiar la posición, el tamaño del texto, ajustar la saturación/brillo, el color, etc.).
* **Cambio o actualización de recursos principales:** Un cambio en un recurso digital que requiere un trabajo considerable y que a veces debe hacerse durante un período de tiempo más largo. Generalmente incluye varios cambios. El recurso debe guardarse varias veces mientras se actualiza. Las principales actualizaciones de recursos suelen hacer que el recurso entre en una etapa de trabajo en curso.
* **DAM**: Administración de recursos digitales. En este documento, es sinónimo de AEM Experience Manager Assets, a menos que se mencione específicamente lo contrario.
* **Usuario creativo:** Un profesional creativo que crea recursos digitales mediante las aplicaciones y los servicios de Creative Cloud. En algunos casos, un usuario creativo puede ser miembro de un equipo creativo que puede utilizar Creative Cloud, pero no crea recursos digitales (como un director creativo o un administrador de equipo creativo).
* **Usuario de DAM:** Usuario típico de un sistema DAM. Según la organización, un usuario de DAM puede ser un usuario de marketing o no de marketing, por ejemplo un usuario de línea de negocios (LOB), bibliotecario, vendedor, etc.

### Consideraciones al utilizar la integración de AEM y Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

* Consulte las prácticas recomendadas de la aplicación [de escritorio](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Consulte Integración con [Adobe Stock](aem-assets-adobe-stock.md)
* Consulte Vínculo de recursos de [Adobe](https://helpx.adobe.com/es/enterprise/using/adobe-asset-link.html)

Este es un breve resumen de las prácticas recomendadas para la integración de Experience Manager y Creative Cloud. Lea el resto de este documento para obtener una comprensión detallada de estos.

* **Para usuarios creativos que trabajan con en Photoshop, InDesign o Illustrator:** Adobe Asset Link ofrece la mejor experiencia de usuario, incluida la gestión del trabajo en curso en los recursos extraídos de AEM
* **Para simplificar el acceso a los recursos desde el escritorio para cualquier aplicación o formato de archivo genérico:** Use la aplicación de escritorio de AEM
* **Comprender por qué y cuándo almacenar recursos en DAM:** Actualizaciones que se pondrán a disposición del equipo de la organización al completo
* **Tenga en cuenta el volumen de recursos compartidos:** Si el caso de uso es la distribución de recursos, la administración y la seguridad podrían ser los aspectos más importantes. Considere utilizar herramientas creadas para hacerlo a escala, como Brand Portal.
* **Comprenda el ciclo vital de los recursos:** Conozca cómo los distintos equipos administran los recursos en su organización
* **Gestione los ahorros frecuentes de los recursos con cuidado:** Adobe Asset Link se encarga de ello con PS, AI e ID. Para otras aplicaciones, no realice tareas de trabajo en curso en carpetas asignadas o compartidas a menos que necesite todos los cambios en DAM

### Acceso a los recursos de Adobe Stock desde AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[La integración](/help/assets/aem-assets-adobe-stock.md) de AEM y Adobe Stock ofrece a los usuarios AEM la posibilidad de buscar, previsualización, obtener licencias y guardar recursos de Adobe Stock en AEM. Los recursos de Adobe Stock con licencia y guardados han seleccionado metadatos de almacenamiento, que pueden utilizarse para buscarlos con filtros adicionales.

Algunos puntos importantes sobre esta integración:

* Cuando los recursos de Adobe se guardan en AEM, se convierten en un AEM Assets normal, con el binario guardado en el repositorio de AEM. Algunos metadatos relacionados con Adobe Stock se guardan para el recurso en AEM; de lo contrario, el proceso de inserción tiene el mismo aspecto que para cualquier otro archivo. Por ejemplo, si las etiquetas inteligentes están activas, las etiquetas se agregan a estos recursos al guardarlos.
* El recurso guardado en AEM es una copia, no un vínculo de vuelta a Adobe Stock.

**Trabajar con recursos guardados de Adobe Stock en AEM en Creative Cloud**. Esta integración es independiente de Adobe Asset Link, pero Adobe Asset Link reconoce estos recursos guardados de Stock de esa manera y muestra metadatos adicionales y el icono de almacenamiento en estos recursos en la interfaz de usuario de la extensión de Adobe Asset Link en Photoshop, Illustrator o InDesign. Los archivos están disponibles para su exploración, apertura, etc., ya que son recursos AEM normales cuando se guardan en AEM.
Los usuarios creativos que trabajen en aplicaciones Creative Cloud con la extensión Vínculo de recursos de Adobe presente, además de tener acceso a recursos con licencia de Adobe Stock en AEM, también pueden utilizar el panel Bibliotecas Creative Cloud para buscar, previsualización y obtener licencias de recursos de Adobe Stock.
Los recursos de Adobe Stock con licencia y guardados en AEM estarán disponibles para los equipos más amplios que accedan a la implementación de AEM Assets, mientras que los recursos de licencias de creativos de Adobe Stock mediante el panel de bibliotecas de Creative Cloud solo estarán disponibles de forma predeterminada en su cuenta de Creative Cloud.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Acerca del almacenamiento de recursos en un DAM {#about-storing-assets-in-a-dam}

Para diseñar un flujo de trabajo eficiente entre los equipos creativos y de marketing/línea de negocios (LOB) y elegir las mejores capacidades de soporte, es importante comprender cuándo y por qué los recursos se almacenan en DAM.

### Por qué los recursos se almacenan en DAM {#why-assets-are-stored-in-dam}

El almacenamiento de recursos en DAM hace que sean fácilmente accesibles y asequibles. Garantiza que numerosos usuarios de toda la organización o el ecosistema puedan aprovechar los recursos, lo que incluye socios, clientes, etc.

La mayoría de las organizaciones solo almacenan los recursos que son relevantes para los procesos de mercadotecnia/LOB de flujo descendente (publicándolos en canales como el canal web a través de AEM Sites u otros canales que Adobe Experience Cloud (Marketing Cloud, Advertising Cloud y que Analytics Cloud miden, lo que proporciona a usuarios/socios, etc.). Además, las organizaciones almacenan activos que pueden estar sujetos a un proceso de revisión/aprobación en DAM. De este modo, DAM almacena principalmente activos que tienen altas posibilidades de aprovechar y evita almacenar activos inactivos.

El almacenamiento de recursos también está sujeto a consideraciones técnicas y de utilización de los recursos. DAM proporciona servicios adicionales en torno a los recursos almacenados, como la extracción de metadatos, el control de versiones, la generación de previsualizaciones/transcodificación, la administración de referencias y la adición de información de control de acceso. Estos servicios consumen más tiempo y recursos de infraestructura.

A menudo, no es deseable almacenar todos los recursos y las actualizaciones. Por ejemplo, si las actualizaciones de recursos específicos son de mala calidad y consumen recursos excesivos, es posible que los recursos no se almacenen en DAM.

### Cuando los recursos se almacenan en DAM {#when-assets-are-stored-in-dam}

Los equipos creativos (y las organizaciones) no suelen estar interesados en almacenar recursos en cada etapa del ciclo vital de los recursos. Por ejemplo, evitan almacenar recursos en los siguientes casos:

* Recursos que aún no se han finalizado o que están sujetos a experimentación
* Recursos que no superan el ciclo de revisión creativo/interno del equipo
* En comparación con el activo en cuestión, el equipo tiene mejores candidatos para representar su trabajo en equipos externos

Normalmente, los siguientes recursos de clases se almacenan en DAM:

* Activos que alcanzaron un cierto vencimiento y se consideran listos para compartirse
* Recursos preseleccionados por el equipo creativo
* Formatos de recurso específicos que se pueden utilizar o se solicitan en la mercadotecnia, según un contrato o acuerdo específico (por ejemplo, archivos JPG convertidos a partir de archivos RAW, TIFF/imágenes de originales PSD)

### Cuando las actualizaciones de los recursos se almacenan en DAM {#when-updates-to-assets-are-stored-in-dam}

Como regla general, solo las actualizaciones de los recursos que son relevantes para el conjunto más amplio de usuarios de DAM deben almacenarse en DAM. Garantiza que los usuarios (funciones de marketing y similares) solo vean versiones relevantes en la línea de tiempo de recursos de DAM.

Generalmente, los cambios se relacionan con hitos principales en el ciclo de vida de los recursos. Por ejemplo, el recurso inicial listo para la creación o una actualización oficial basada en una solicitud o revisión proporcionada por el equipo creativo deben almacenarse y crearse en DAM.

La actualización del equipo creativo para su revisión por parte del equipo de marketing tras una solicitud de cambio en el recurso existente en DAM es un ejemplo de una actualización relevante. Debe almacenarse y crearse una versión en DAM para consulta adicional o para volver a la versión anterior.

Los siguientes son ejemplos de actualizaciones que normalmente no son relevantes:

* Versiones iniciales de los recursos cargados antes de que estén listos para la revisión de marketing
* Cambios creativos frecuentes en el recurso en la fase de trabajo en curso antes de que el equipo creativo decida que el recurso está listo

### Acceso del usuario a DAM {#user-access-to-dam}

AEM Assets admite dos tipos de usuarios en función de su acceso a la implementación de AEM Assets. Normalmente, los usuarios dentro de la red empresarial (servidor de seguridad) tienen acceso directo a DAM. Otros usuarios fuera de la red empresarial no tendrían acceso directo. El tipo de usuario determina qué integraciones se pueden utilizar desde el punto de vista técnico.

#### Usuarios creativos con acceso directo a DAM {#creative-users-with-direct-access-to-dam}

Generalmente, los equipos creativos internos o las agencias o los profesionales creativos integrados en la red interna tienen acceso a la instancia de DAM, incluido AEM inicio de sesión.

En estos casos, AEM aplicación de escritorio ayuda a facilitar el acceso a los recursos finales o aprobados y le permite guardar en DAM recursos listos para la creación.

#### Usuarios creativos sin acceso a DAM {#creative-users-without-access-to-dam}

Es posible que las agencias externas y los autónomos que no tienen acceso directo a la instancia de DAM necesiten acceder a los recursos aprobados o deseen añadir sus nuevos diseños al DAM.

En estos casos, puede aprovechar la integración AEM/Creative Cloud para mejorar el flujo de trabajo. El requisito previo es que los usuarios creativos tengan una cuenta de Adobe ID y de Creative Cloud con el servicio de almacenamiento.

Utilice las siguientes estrategias para proporcionar acceso a los activos finales o aprobados:

* Para proporcionar acceso a un gran número de recursos: Utilice [AEM Assets Brand Portal](https://helpx.adobe.com/es/experience-manager/brand-portal/user-guide.html)o la implementación de [Asset Share](assets-finder-editor.md) por parte del cliente en AEM infraestructura de publicación

* Para proporcionar acceso a algunos recursos: AEM uso compartido de carpetas con Adobe Creative Cloud se puede utilizar además de AEM Assets Brand Portal o Asset Share. Tenga en cuenta que existen ciertas limitaciones relacionadas con esta integración, que se explican con más detalle en este artículo.

### Use Cases {#use-cases}

Los siguientes casos de uso describen varios tipos de flujos de trabajo entre DAM y el escritorio del diseñador.

#### Crear nuevos diseños con recursos de DAM {#creating-new-designs-using-assets-from-dam}

El diagrama siguiente ilustra el ciclo de vida de los recursos digitales. Describe cómo los usuarios creativos y los usuarios de DAM (especialistas en marketing, usuarios de LOB) aprovechan los recursos existentes y los utilizan para crear más recursos y enviarlos para su aprobación.

![chlimage_1-301](assets/chlimage_1-301.png)

El ciclo vital de los recursos incluye las siguientes etapas:

1. Compartir recursos aprobados en el escritorio creativo: Los recursos finales de DAM están disponibles para el usuario creativo (en el escritorio)
1. Crear un nuevo diseño (recurso digital creativo): Un nuevo archivo se almacena en el área de trabajo en curso (WIP).
1. Utilizar (colocar) recursos aprobados en un nuevo diseño: El usuario creativo produce un nuevo recurso con los recursos aprobados existentes en las aplicaciones Creative Cloud
1. Actualizaciones de WIP que se guardan con frecuencia: El usuario creativo repite rápidamente y guarda el archivo con frecuencia. En este momento, el usuario creativo puede colaborar con otros, pero las actualizaciones guardadas con frecuencia no suelen ser de interés para los usuarios de DAM.
1. El recurso alcanza el estado listo para el elemento creativo y se guarda en la carpeta Creative Ready
1. Actualización de recursos: Los usuarios de DAM disponen de una actualización de recursos o de un archivo nuevo
1. El activo se somete a la producción: Se trata de un proceso DAM que, según la organización, puede incluir etiquetado, aprobaciones y cambios de controles de acceso. En esta etapa, el recurso se considera definitivo y puede ser utilizado por equipos más amplios que aprovechan DAM. Los usuarios creativos también pueden utilizarla para crear otros recursos.

A continuación se presentan algunas recomendaciones generales sobre cómo administrar los recursos a través de este proceso:

* Utilice un área o sistema de almacenamiento dedicado, como la carpeta sincronizada Adobe Creative Cloud Assets, para los archivos WIP: Las actualizaciones más frecuentes que no son relevantes para los usuarios de DAM son gestionadas mejor por un sistema dedicado, y no desde AEM Assets. Los recursos de WIP se pueden sincronizar con el disco local mediante la aplicación de escritorio de Adobe Creative Cloud, guardar en almacenamiento local, etc.
* Utilice carpetas/recursos compartidos independientes para los recursos finales y los recursos cargados en DAM: para mayor claridad, los recursos finales deben tener su propia carpeta asignada o compartida (ejemplo &quot;final&quot; anterior) y los recursos que se van a cargar de nuevo en DAM deben tener su propia carpeta (&quot;Creative Ready&quot;)

#### Cambiar los recursos existentes administrados en DAM {#changing-existing-assets-managed-in-dam}

En algunos casos, los recursos de DAM pueden requerir cambios. Algunos ejemplos son:

* Solicitud de cambios en los recursos a partir de la revisión y aprobación realizadas en AEM Assets
* Principales actualizaciones de los activos finales existentes
* Ediciones rápidas en un archivo existente (especialmente antes de que se apruebe por fin)

En estos casos, AEM aplicación de escritorio proporciona la forma más sencilla de realizar estas operaciones.

![chlimage_1-302](assets/chlimage_1-302.png)

Este es el flujo de eventos que se ilustran en el diagrama:

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for AEM desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** Comparta el recurso de DAM en el escritorio o ábralo directamente en el escritorio en la aplicación que desee (por ejemplo, Adobe Photoshop, etc.). Se recomienda retirar para bloquear el archivo.
* **2:** Actualización menor: Edite el archivo y guarde los cambios.
* Flujo alternativo al paso 2

   * **A:** Actualización importante: Si el archivo requiere un conjunto detallado de cambios, debe guardarse de forma intermitente y copiarse en una carpeta o área de trabajo en curso.
   * **B:** El trabajo continúa en el archivo de las carpetas WIP. Los cambios guardados no se sincronizan con la versión en DAM
   * **C:** Una vez completadas las actualizaciones, el archivo se copia de nuevo o se guarda en la carpeta asignada

* **3:** Las actualizaciones de recursos se reflejan en DAM. Compruebe el recurso para desbloquearlo.
* **4:** Los activos se ponen en producción.

A continuación se presentan algunas recomendaciones generales sobre cómo administrar los recursos a lo largo de este proceso:

* Evite guardar directamente un archivo que haya abierto desde un recurso compartido de red asignado por AEM aplicación de escritorio, a menos que los cambios realizados en el archivo sean pequeños.
* Copie el archivo en una carpeta WIP independiente si desea realizar cambios adicionales en él, guardarlo de forma intermitente o colaborar con el equipo creativo.

#### Carga masiva a DAM {#bulk-upload-to-dam}

Es posible que tenga que cargar simultáneamente un número mayor de archivos en DAM en algunos casos, por ejemplo:

* Carga de resultados de fotografías o proyectos más grandes
* Carga de recursos proporcionados por agencias creativas
* Carga de recursos seleccionados de un conjunto más grande si la selección se realiza fuera de DAM

Tenga en cuenta que esta descripción se refiere a la carga operativa de archivos (por ejemplo, cada semana o con cada sesión fotográfica, etc.) como parte normal del flujo de trabajo del usuario del escritorio. Las migraciones de recursos grandes no se cubren aquí.

Puede aprovechar las siguientes funciones si desea cargar recursos de forma masiva:

* Para cargar carpetas grandes o jerárquicas, utilice AEM aplicación de escritorio, que proporciona una función de carga [de carpetas](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) . También puede cargar estructuras de carpetas jerárquicas. Los recursos se cargan en segundo plano y, por lo tanto, no están vinculados a una sesión de explorador Web
* Si desea cargar algunos archivos desde una sola carpeta, arrástrelos directamente desde el escritorio a la interfaz de usuario web o utilice la opción Crear en la interfaz de usuario web de AEM Assets.

>[!NOTE]
>
>Según los requisitos comerciales, también puede utilizar el cargador personalizado.

#### Administrar recursos digitales directamente desde el escritorio {#managing-digital-assets-directly-from-desktop}

Si utiliza Compartidos de archivos de red para administrar recursos digitales, el uso del recurso compartido de red asignado por AEM aplicación de escritorio podría considerarse un sustituto conveniente. Al realizar la transición desde los recursos compartidos de archivos de red, recuerde que AEM interfaz de usuario web proporciona un completo conjunto de funciones de administración de recursos digitales que van mucho más allá de lo posible en un recurso compartido de red (búsqueda, colecciones, metadatos, colaboración, previsualizaciones, etc.) y AEM aplicación de escritorio proporciona un vínculo práctico para conectar el repositorio DAM del lado del servidor con el trabajo en el escritorio.

Evite utilizar AEM aplicación de escritorio para administrar recursos directamente en el recurso compartido de red de AEM Assets. Por ejemplo, evite utilizar AEM aplicación de escritorio para mover o copiar varios archivos. En su lugar, utilice la interfaz de usuario web de AEM Assets para arrastrar carpetas desde Finder/Explorer al recurso compartido de red o utilice la función de carga de carpetas de AEM Assets.

#### Migración de recursos {#asset-migration}

Para planificar y ejecutar migraciones de recursos desde un sistema existente a un nuevo sistema o migración de grandes volúmenes de recursos almacenados en servidores, consulte la Guía [](/help/assets/assets-migration-guide.md)de migración. AEM aplicación de escritorio y AEM a integraciones de Creative Cloud no admiten estas migraciones. Debido a los grandes volúmenes de recursos que se van a ingerir y a los requisitos adicionales en cuanto a la asignación, transformación e ingesta de metadatos, las migraciones deben gestionarse con diferentes herramientas y enfoques.

>[!MORELIKETHIS]
>
>* [Adobe Asset Link](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [Prácticas recomendadas para aplicaciones de escritorio AEM](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [Integración de AEM y Adobe Stock](aem-assets-adobe-stock.md)

