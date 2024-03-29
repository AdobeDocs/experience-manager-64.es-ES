---
title: Referencia de esquemas de metadatos
description: Obtenga información sobre las convenciones estándar para describir metadatos de recursos, incluidos Dublin Core, IPTC y otros esquemas de metadatos.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 4%

---

# Referencia de esquemas de metadatos {#metadata-schemata-reference}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La siguiente referencia incluye información sobre esquemas de metadatos específicos (en orden alfabético), así como una lista de propiedades y sus definiciones.

## Dublin Core {#dublin-core}

Los metadatos principales de Dublín proporcionan un conjunto estandarizado de convenciones para describir los activos y facilitar su búsqueda. En [!DNL Experience Manager] Assets, the Dublin Core describe los recursos digitales, incluidos vídeo, sonido, imágenes y documentos.

El sencillo conjunto de elementos de metadatos principales de Dublín (DCMES) contiene 15 elementos de metadatos enumerados en la siguiente tabla. Cada elemento principal de Dublín es opcional y se puede repetir. Puede añadir o eliminar la información de metadatos de Dublin Core, como lo haría con los metadatos específicos de tipo de medio.

Además del DCMES, existen otros elementos de metadatos creados por la Iniciativa Principal de Dublín. Consulte la [Iniciativa principal de Dublín](https://dublincore.org/) para obtener más información.

| Propiedad | Descripción |
|---|---|
| colaborador | La persona o empresa responsable de contribuir al contenido. |
| cobertura | Ubicación geográfica o período de tiempo que abarca el recurso. |
| creador | La persona o empresa responsable de la creación del contenido. |
| fecha | Fecha o período de tiempo asociado al recurso. |
| description | Más información sobre el recurso. |
| format | El formato de archivo, el medio físico o las dimensiones del recurso. [!DNL Experience Manager] utiliza dc:format para denotar el tipo mime del recurso. |
| identifier | Una referencia única al recurso. |
| language | El idioma del recurso (por ejemplo, en para inglés). |
| publisher | La persona o empresa responsable de poner el recurso a disposición. |
| relation | Un recurso relacionado. |
| derechos | Información sobre quién tiene los derechos de este recurso. |
| origen | Recurso relacionado del que se deriva el recurso. |
| subject | El tema del recurso. |
| título | Un nombre para el recurso. |
| type | La naturaleza o el género del recurso. |

## IPTC {#iptc}

El Consejo Internacional de Telecomunicaciones de Prensa (IPTC, por sus siglas en inglés) es un consorcio de agencias de noticias alrededor del mundo - uno de sus objetivos es desarrollar y mantener estándares técnicos. El IPTC definió un conjunto de estándares de metadatos de fotos para imágenes que es aceptado casi universalmente entre los fotógrafos. Estas normas de metadatos formaban parte del estándar más amplio conocido como el Modelo de intercambio de información IPTC (IIM) creado en los años 90.

Aunque la información del encabezado IPTC se ha reemplazado por XMP, un esquema principal IPTC y un esquema de extensión están disponibles para XMP. En los programas de imágenes, se sincronizan las propiedades XMP e IPTC.
