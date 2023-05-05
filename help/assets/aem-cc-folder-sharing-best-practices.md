---
title: Uso compartido de carpetas de Experience Manager Assets con Creative Cloud
description: Configuración y prácticas recomendadas para permitir a los usuarios de Adobe Experience Manager Assets intercambiar carpetas de recursos con usuarios de Adobe Creative Cloud.
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 1%

---

# [!DNL Experience Manager] a [!DNL Creative Cloud] prácticas recomendadas para compartir carpetas {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>La función Experience Manager al uso compartido de carpetas del Creative Cloud está en desuso. Adobe recomienda encarecidamente utilizar funciones más nuevas, como [Vínculo de recurso de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) o [aplicación de escritorio de Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Obtenga más información en [Prácticas recomendadas para la integración de Experience Manager y Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager se puede configurar para permitir que los usuarios de Experience Manager Assets compartan carpetas con usuarios de Creative Cloud, de modo que estén disponibles como carpetas compartidas en el servicio Creative Cloud Assets. La función se puede utilizar para intercambiar archivos entre equipos creativos y usuarios de Experience Manager Assets, especialmente cuando los usuarios creativos no tienen acceso a la instancia de Experience Manager Assets (no están en la red empresarial).

Este tipo de integración se puede utilizar en ambos casos de uso, especialmente cuando se trabaja con usuarios que no tienen acceso directo a Experience Manager Assets:

* Uso compartido de un conjunto de recursos específicos de Experience Manager Assets con usuarios de archivos de Creative Cloud (por ejemplo, un resumen creativo y un conjunto de recursos aprobados para el trabajo de diseño para una nueva actividad de marketing)
* Recibir nuevos archivos de usuarios de Creative Cloud.

>[!NOTE]
>
>Antes de leer este documento, puede revisar el [Prácticas recomendadas para la integración de Experience Manager y Creative Cloud](aem-cc-integration-best-practices.md) para obtener una descripción general de nivel superior del tema.

## Información general {#overview}

El uso compartido de Experience Manager a Creative Cloud depende del uso compartido de carpetas y archivos en el lado del servidor entre cuentas de Experience Manager Assets y Creative Cloud. Los profesionales creativos, que utilizan la aplicación de escritorio de Creative Cloud en sus escritorios, también pueden hacer que las carpetas compartidas estén disponibles directamente en sus discos mediante la tecnología Adobe CreativeSync.

El diagrama siguiente proporciona una descripción general de la integración.

![chlimage_1-406](assets/chlimage_1-406.png)

La integración incluye los siguientes elementos:

* **[!DNL Assets]server** implementado en la red empresarial (servicios administrados o locales): El uso compartido de carpetas se inicia aquí.
* **Servicio principal de Adobe Marketing Cloud Assets**: Actúa como intermediario entre los servicios de almacenamiento de información del Experience Manager y del Creative Cloud. El administrador de la empresa que utiliza la integración debe establecer una relación de confianza entre la organización de Marketing Cloud y la instancia de Experience Manager Assets. También [definir una lista de colaboradores del Creative Cloud aprobados](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets), que los usuarios de Assets también pueden compartir carpetas para obtener más seguridad.
* **Servicios web de Creative Cloud Assets** (IU web de archivos de almacenamiento y Creative Cloud): Aquí es donde los usuarios de Creative Cloud específicos, con los que se ha compartido una carpeta de Assets, podrían aceptar la invitación y ver la carpeta en su almacenamiento de cuentas de Creative Cloud.
* **aplicación de escritorio de Creative Cloud**: (Opcional) Permite el acceso directo a carpetas compartidas o archivos desde el escritorio del usuario creativo mediante la sincronización con el almacenamiento de recursos de Creative Cloud.

## Características y limitaciones {#characteristics-and-limitations}

* **Propagación unidireccional de cambios:** Los cambios en los archivos se propagan solo en una dirección, desde el sistema (recursos de Experience Manager o Creative Cloud), donde el recurso se creó originalmente (se cargó). La integración no proporciona una sincronización bidireccional completamente automatizada entre los dos sistemas.

* **Versiones:**

   * Experience Manager solo crea versiones de un recurso en actualizaciones si el archivo se originó en el Experience Manager y se actualiza en él.
   * Recursos de Creative Cloud proporciona su propio [función de versiones](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) que está dirigido a las actualizaciones de Work in Progress (básicamente, almacena actualizaciones durante un máximo de 10 días)

* **Limitaciones de espacio:** Los tamaños y volúmenes de archivos intercambiados están limitados por el [Cuota de recursos del Creative Cloud](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) para usuarios creativos (depende del nivel de suscripción) y una limitación de 5 GB de tamaño máximo de archivo. El espacio está limitado además por la cuota de recursos que la organización tiene en el servicio principal Adobe Marketing Cloud Assets.

* **Requisitos de espacio:** Los archivos de las carpetas compartidas también deben almacenarse físicamente en el Experience Manager y, a continuación, en la cuenta del Creative Cloud, con una copia en caché en el servicio principal de Recursos de Marketing Cloud.
* **Redes y ancho de banda:** Los archivos de carpetas compartidas y todas las actualizaciones deben transportarse a través de la red entre los sistemas. Debe asegurarse de que solo se compartan los archivos y las actualizaciones relevantes.
* **Tipo de carpeta**: Uso compartido de una carpeta de recursos del tipo `sling:OrderedFolder`, no es compatible. Si desea compartir una carpeta, al crearla en Experience Manager Assets, no seleccione la opción Pedido .

## Prácticas recomendadas {#best-practices}

Entre las prácticas recomendadas para aprovechar el uso compartido de Experience Manager en Creative Cloud se incluyen:

* **Consideraciones sobre el volumen:** Experience Manager, Creative Cloud de uso compartido de carpetas debe usarse para compartir un número menor de archivos, por ejemplo, relevantes para una campaña o actividad específica. Para compartir conjuntos más grandes de recursos, como todos los recursos aprobados de la organización, utilice otros métodos de distribución (por ejemplo, Experience Manager Assets Brand Portal) o la aplicación de escritorio de Experience Manager.
* **Evite compartir jerarquías profundas:** El uso compartido funciona de forma recursiva y no permite la interrupción selectiva del uso compartido. Normalmente, solo las carpetas sin subcarpetas o con una jerarquía muy superficial, como el nivel de subcarpeta 1, deben considerarse para el uso compartido.
* **Separe las carpetas para un uso compartido unidireccional:** Las carpetas independientes deben usarse para compartir recursos finales de Experience Manager Assets en archivos de Creative Cloud y para volver a compartir recursos listos para la creación de archivos de Creative Cloud en [!DNL Assets]. Junto con una buena convención de nombres para estas carpetas, crea un entorno de trabajo más fácil de entender para los usuarios de Experience Manager Assets y los Creative Cloud.
* **Evite WIP en la carpeta compartida:** La carpeta compartida no debe utilizarse para el trabajo en curso (utilice una carpeta independiente en los archivos de Creative Cloud para llevar a cabo un trabajo que requiera cambios frecuentes en el archivo).
* **Inicie un nuevo trabajo fuera de la carpeta compartida:** Los nuevos diseños (archivos creativos) deben iniciarse en la carpeta WIP independiente de los archivos Creative Cloud y, cuando estén listos para compartirse con los usuarios de Experience Manager Assets, deben moverse o guardarse en la carpeta compartida.
* **Simplifique la estructura de uso compartido:** Para una configuración operativa más manejable, piense en simplificar la estructura de uso compartido. En lugar de compartir con todos los usuarios creativos, las carpetas de Experience Manager Assets deben compartirse únicamente con los representantes del equipo, como un director creativo o un administrador de equipos. El administrador del lado creativo recibiría los recursos finales, decidiría las asignaciones de trabajo y, a continuación, permitiría a los diseñadores trabajar en sus propias cuentas de Creative Cloud en los recursos de trabajo en curso. Pueden utilizar funciones de colaboración de Creative Cloud para coordinar el trabajo y, finalmente, seleccionar y colocar recursos listos para compartir en Experience Manager Assets en su carpeta compartida lista para la creación.

En el diagrama siguiente se ilustra un ejemplo de configuración para crear nuevos diseños basado en los recursos finales existentes de Experience Manager Assets.

![chlimage_1-407](assets/chlimage_1-407.png)
