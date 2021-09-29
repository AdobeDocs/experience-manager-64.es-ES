---
title: Compartir carpetas de recursos de Experience Manager con Creative Cloud
description: Configuración y prácticas recomendadas para permitir a los usuarios de Adobe Experience Manager Assets intercambiar carpetas de recursos con usuarios de Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---

# [!DNL Experience Manager] prácticas recomendadas para compartir  [!DNL Creative Cloud] carpetas {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>La función Experience Manager al uso compartido de carpetas del Creative Cloud está en desuso. Adobe recomienda encarecidamente utilizar funciones más nuevas, como [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) o [Experience Manager desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Obtenga más información en [Prácticas recomendadas para la integración de Experience Manager y Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager se puede configurar para permitir que los usuarios de Recursos de Experience Manager compartan carpetas con usuarios de Creative Cloud, de modo que estén disponibles como carpetas compartidas en el servicio Recursos de Creative Cloud. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios de Recursos de Experience Manager, especialmente cuando los usuarios creativos no tienen acceso a la instancia de Recursos de Experience Manager (no están en la red empresarial).

Este tipo de integración se puede utilizar en ambos casos de uso, especialmente cuando se trabaja con usuarios que no tienen acceso directo a Recursos de Experience Manager:

* Uso compartido de un conjunto de recursos específicos desde recursos de Experience Manager con usuarios de archivos de Creative Cloud (por ejemplo, un resumen creativo y un conjunto de recursos aprobados para trabajo de diseño para una nueva actividad de marketing)
* Recibir nuevos archivos de usuarios de Creative Cloud.

>[!NOTE]
>
>Antes de leer este documento, puede revisar las [prácticas recomendadas generales de integración de Experience Manager y Creative Cloud](aem-cc-integration-best-practices.md) para obtener información general de más alto nivel sobre el tema.

## Información general {#overview}

El uso compartido de Experience Manager a Creative Cloud depende del uso compartido de carpetas y archivos en el servidor entre Experience Manager Assets y cuentas de Creative Cloud. Los profesionales creativos, que utilizan la aplicación de escritorio de Creative Cloud en sus escritorios, también pueden hacer que las carpetas compartidas estén disponibles directamente en sus discos mediante la tecnología Adobe CreativeSync.

El diagrama siguiente proporciona una descripción general de la integración.

![chlimage_1-406](assets/chlimage_1-406.png)

La integración incluye los siguientes elementos:

* **[!DNL Assets]** Servidor implementado en la red empresarial (servicios administrados o locales): El uso compartido de carpetas se inicia aquí.
* **Servicio principal de Adobe Marketing Cloud Assets**: Actúa como intermediario entre los servicios de almacenamiento de información del Experience Manager y del Creative Cloud. El administrador de la empresa que utiliza la integración debe establecer una relación de confianza entre la organización de Marketing Cloud y la instancia de Experience Manager Assets. También [definen una lista de colaboradores del Creative Cloud aprobados](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets), que los usuarios de Assets también pueden compartir carpetas para obtener más seguridad.
* **Servicios web de Creative Cloud Assets**  (interfaz de usuario web de almacenamiento y archivos de Creative Cloud): Aquí es donde los usuarios Creative Cloud específicos, con los que se ha compartido una carpeta de Assets, podrían aceptar la invitación y ver la carpeta en su almacenamiento de cuentas de Creative Cloud.
* **aplicación** de escritorio de Creative Cloud: (Opcional) Permite el acceso directo a carpetas compartidas o archivos desde el escritorio del usuario creativo mediante la sincronización con el almacenamiento de recursos de Creative Cloud.

## Características y limitaciones {#characteristics-and-limitations}

* **Propagación unidireccional de cambios:**  los cambios de archivos se propagan en una sola dirección, desde el sistema (recursos del Experience Manager o del Creative Cloud), donde el recurso se creó originalmente (se cargó). La integración no proporciona una sincronización bidireccional completamente automatizada entre los dos sistemas.

* **Versiones:**

   * Experience Manager solo crea versiones de un recurso en actualizaciones si el archivo se originó en el Experience Manager y se actualiza en él.
   * Creative Cloud Assets proporciona su propia [función de versiones](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) dirigida a las actualizaciones de Work in Progress (básicamente, almacena actualizaciones durante un máximo de 10 días)

* **Limitaciones de espacio:** los tamaños y volúmenes de archivos intercambiados están limitados por la cuota específica de  [Creative Cloud Assets ](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) para usuarios creativos (depende del nivel de suscripción) y una limitación de 5 GB de tamaño máximo de archivo. El espacio está limitado además por la cuota de recursos que la organización tiene en el servicio principal Adobe Marketing Cloud Assets.

* **Requisitos de espacio:** Los archivos de carpetas compartidas también deben almacenarse físicamente en el Experience Manager y, a continuación, en la cuenta del Creative Cloud, con una copia en caché en el servicio principal de Recursos de Marketing Cloud.
* **Redes y ancho de banda:**  Los archivos de carpetas compartidas y todas las actualizaciones deben transportarse a través de la red entre los sistemas. Debe asegurarse de que solo se compartan los archivos y las actualizaciones relevantes.
* **Tipo** de carpeta: No se admite el uso compartido de una carpeta de recursos del tipo  `sling:OrderedFolder`. Si desea compartir una carpeta, al crearla en Recursos de Experience Manager, no seleccione la opción Pedido .

## Prácticas recomendadas {#best-practices}

Entre las prácticas recomendadas para aprovechar el uso compartido de Experience Manager en Creative Cloud se incluyen:

* **Consideraciones sobre el volumen: el Experience Manager de** , el uso compartido de carpetas de Creative Cloud deben utilizarse para compartir un número menor de archivos, por ejemplo, relevantes para una campaña o actividad específica. Para compartir conjuntos más grandes de recursos, como todos los recursos aprobados de la organización, utilice otros métodos de distribución (por ejemplo, Experience Manager Assets Brand Portal) o la aplicación de escritorio de Experience Manager.
* **Evite compartir jerarquías profundas:** El uso compartido funciona de forma recursiva y no permite el uso compartido selectivo. Normalmente, solo las carpetas sin subcarpetas o con una jerarquía muy superficial, como el nivel de subcarpeta 1, deben considerarse para el uso compartido.
* **Carpetas independientes para el uso compartido unidireccional:** Las carpetas independientes deben usarse para compartir recursos finales desde recursos Experience Manager a archivos Creative Cloud y para compartir recursos listos para la creación de archivos Creative Cloud a  [!DNL Assets]. Junto con una buena convención de nombres para estas carpetas, crea un entorno de trabajo más fácil de entender para los usuarios de Recursos Experience Manager y Creative Cloud.
* **Evitar WIP en la carpeta compartida:**  La carpeta compartida no debe utilizarse para el trabajo en curso. Utilice una carpeta independiente en los archivos de Creative Cloud para realizar trabajos que requieran cambios frecuentes en el archivo.
* **Iniciar nuevo trabajo fuera de la carpeta compartida:**  Los nuevos diseños (archivos creativos) deben iniciarse en la carpeta WIP independiente de los archivos Creative Cloud y, cuando estén listos para compartirse con los usuarios de Recursos Experience Manager, deben moverse o guardarse en la carpeta compartida.
* **Simplificar la estructura de uso compartido:** para una configuración operativa más manejable, piense en simplificar la estructura de uso compartido. En lugar de compartir con todos los usuarios creativos, las carpetas de Recursos de Experience Manager solo deben compartirse con los representantes del equipo, como un director creativo o un administrador de equipos. El administrador del lado creativo recibiría los recursos finales, decidiría las asignaciones de trabajo y, a continuación, permitiría a los diseñadores trabajar en sus propias cuentas de Creative Cloud en los recursos de trabajo en curso. Pueden utilizar funciones de colaboración de Creative Cloud para coordinar el trabajo y, por último, seleccionar y colocar los recursos listos para compartir con los recursos de Experience Manager en su carpeta compartida lista para la creación.

El diagrama siguiente ilustra una configuración de ejemplo para crear nuevos diseños basada en los recursos finales existentes de Recursos Experience Manager.

![chlimage_1-407](assets/chlimage_1-407.png)
