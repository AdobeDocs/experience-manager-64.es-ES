---
title: Compartir carpetas de AEM Assets con Creative Cloud
description: Configuración y prácticas recomendadas para permitir a los usuarios de Recursos Adobe Experience Manager intercambiar carpetas de recursos con usuarios de Adobe Creative Cloud.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '1057'
ht-degree: 0%

---


# Prácticas recomendadas para compartir carpetas de AEM con Creative Cloud {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>La función AEM to Creative Cloud Folder Sharing está en desuso. Adobe recomienda encarecidamente el uso de nuevas funciones como [Adobe Asset Link](https://helpx.adobe.com/es/enterprise/using/adobe-asset-link.html) o la aplicación [de escritorio](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)AEM. Obtenga más información sobre las prácticas recomendadas [](/help/assets/aem-cc-integration-best-practices.md)de integración de AEM y Creative Cloud.

Adobe Experience Manager (AEM) se puede configurar para permitir que los usuarios en AEM Assets compartan carpetas con usuarios de Creative Cloud, de modo que estén disponibles como carpetas compartidas en el servicio Creative Cloud Assets. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios AEM Assets, especialmente cuando los usuarios creativos no tienen acceso a la instancia de AEM Assets (no están en la red empresarial).

Este tipo de integración se puede utilizar en ambos casos de uso, especialmente cuando se trabaja con usuarios que no tienen acceso directo a AEM Assets:

* Uso compartido de un conjunto de recursos específicos de AEM Assets con usuarios de Creative Cloud Files (por ejemplo, un resumen creativo y un conjunto de recursos aprobados para el trabajo de diseño de una nueva actividad de marketing)
* Recibir nuevos archivos de usuarios de Creative Cloud.

>[!NOTE]
>
>Antes de leer este documento, puede consultar las prácticas recomendadas [generales de integración de](aem-cc-integration-best-practices.md) AEM y Creative Cloud para obtener una descripción general de nivel superior del tema.

## Información general {#overview}

El uso compartido de carpetas de AEM a Creative Cloud depende del uso compartido de carpetas y archivos por parte del servidor entre AEM Assets y cuentas de Creative Cloud. Los profesionales creativos, que utilizan la aplicación de escritorio Creative Cloud en sus equipos de escritorio, pueden además hacer que las carpetas compartidas estén disponibles directamente en sus discos mediante la tecnología Adobe CreativeSync.

En el diagrama siguiente se proporciona una descripción general de la integración.

![chlimage_1-406](assets/chlimage_1-406.png)

La integración incluye los siguientes elementos:

* **Servidor** AEM Assets implementado en la red empresarial (servicios administrados o in situ): El uso compartido de carpetas se inicia aquí.
* **Servicio** principal de Recursos Adobe Marketing Cloud: Actúa como intermediario entre los servicios de almacenamiento de AEM y Creative Cloud. El administrador de la compañía que utiliza la integración necesita establecer una relación de confianza entre la organización de Marketing Cloud y la instancia de AEM Assets. También [definen una lista de colaboradores](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html)aprobados de Creative Cloud, que los usuarios de AEM Assets también pueden compartir carpetas para mayor seguridad.
* **Servicios** web de Creative Cloud Assets (interfaz de usuario web de almacenamiento y Creative Cloud Files): Aquí es donde usuarios específicos de Creative Cloud, con los que se ha compartido una carpeta de AEM Assets, pueden aceptar la invitación y ver la carpeta en el almacenamiento de su cuenta de Creative Cloud.
* **Aplicación** de escritorio de Creative Cloud: (Opcional) Permite el acceso directo a las carpetas o archivos compartidos desde el escritorio del usuario creativo mediante la sincronización con el almacenamiento de Creative Cloud Assets.

## Características y limitaciones {#characteristics-and-limitations}

* **Propagación unidireccional de cambios:** Los cambios en los archivos se propagan en una sola dirección, desde el sistema (AEM o Creative Cloud Assets), donde el recurso se creó originalmente (se cargó). La integración no proporciona una sincronización bidireccional completamente automatizada entre los dos sistemas.

* **Versiones:**

   * AEM solo crea versiones de un recurso al actualizar si el archivo se originó en AEM y se actualiza en él.
   * Creative Cloud Assets ofrece su propia función [de](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) control de versiones que está dirigida a las actualizaciones de Work in Progress (básicamente, almacena actualizaciones durante un máximo de 10 días)

* **Limitaciones de espacio:** Los tamaños y volúmenes de archivos intercambiados están limitados por la cuota [específica de](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud Assets para usuarios creativos (depende del nivel de suscripción) y una limitación de 5 GB de tamaño máximo de archivo. El espacio está limitado además por la cuota de recursos que la organización tiene en el servicio principal de Recursos de Adobe Marketing Cloud.

* **Requisitos de espacio:** Los archivos de las carpetas compartidas también deben almacenarse físicamente en AEM y, a continuación, en la cuenta de Creative Cloud, con una copia en caché en el servicio principal de Marketing Cloud Assets.
* **Redes y ancho de banda:** Los archivos de las carpetas compartidas y todas las actualizaciones deben trasladarse a través de la red entre los sistemas. Debe asegurarse de que solo se comparten los archivos y las actualizaciones relevantes.
* **Tipo** de carpeta: No se puede compartir una carpeta de recursos del tipo `sling:OrderedFolder`. Si desea compartir una carpeta, al crearla en AEM Assets, no seleccione la opción Pedido.

## Best practices {#best-practices}

Entre las prácticas recomendadas para aprovechar AEM para compartir carpetas de Creative Cloud se incluyen:

* **Consideraciones sobre el volumen:** El uso compartido de carpetas de AEM/Creative Cloud debe utilizarse para compartir un número menor de archivos, por ejemplo, relevantes para una campaña o actividad específica. Para compartir conjuntos más grandes de recursos, como todos los recursos aprobados en la organización, utilice otros métodos de distribución (por ejemplo, AEM Assets Brand Portal) o la aplicación de escritorio AEM.
* **Evite compartir jerarquías profundas:** El uso compartido funciona de forma recursiva y no permite la desdistribución selectiva. Normalmente, solo las carpetas sin subcarpetas o con una jerarquía muy superficial, como el nivel de subcarpeta 1, deben considerarse para uso compartido.
* **Separe las carpetas para compartir en un solo sentido:** Se deben utilizar carpetas independientes para compartir recursos finales de AEM Assets a archivos de Creative Cloud, así como para compartir recursos listos para la creación desde archivos de Creative Cloud a AEM Assets. Junto con una buena convención de nombres para estas carpetas, crea un entorno de trabajo más fácil de entender tanto para los AEM Assets como para los usuarios de Creative Cloud.
* **Evite WIP en la carpeta compartida:** La carpeta compartida no debe utilizarse para el trabajo en curso; utilice una carpeta independiente en Creative Cloud Files para realizar un trabajo que requiera cambios frecuentes en el archivo.
* **Inicio del nuevo trabajo fuera de la carpeta compartida:** Los nuevos diseños (archivos creativos) deben iniciarse en la carpeta WIP independiente de Creative Cloud Files y, cuando estén listos para compartirse con los usuarios de AEM Assets, se deben mover o guardar en la carpeta compartida.
* **Simplifique la estructura de uso compartido:** Para una configuración operativa más manejable, piense en simplificar la estructura de uso compartido. En lugar de compartir con todos los usuarios creativos, las carpetas de AEM Assets solo deben compartirse con los representantes del equipo, como un director creativo o un administrador de equipos. El administrador del lado creativo recibiría los recursos finales, decidiría las asignaciones de trabajo y, a continuación, dejaría que los diseñadores trabajaran en sus propias cuentas de Creative Cloud en los recursos de trabajo en curso. Pueden utilizar las funciones de colaboración de Creative Cloud para coordinar el trabajo y, por último, seleccionar y colocar los recursos listos para compartir con los AEM Assets en su carpeta compartida lista para creativos.

El diagrama siguiente ilustra una configuración de ejemplo para crear nuevos diseños en función de los recursos finales existentes de los AEM Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
