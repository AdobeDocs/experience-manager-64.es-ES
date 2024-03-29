---
title: Especificar ubicaciones de archivos para la salida
seo-title: Specify file locations for Output
description: Obtenga información sobre cómo especificar ubicaciones de archivos para Output.
seo-description: Learn how to specify file locations for Output.
uuid: 3287274f-85b5-4811-8abb-d347a9b80947
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 460bbb31-8187-469c-8102-b310093b6c03
exl-id: 5b8f04dd-6781-4126-8bb2-5d8b7a2f19c8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 7%

---

# Especificar ubicaciones de archivos para la salida {#specify-file-locations-for-output}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Puede especificar las ubicaciones en las que Output busca ciertos tipos de archivos que requiere.

1. En la consola de administración, haga clic en Servicios > salida.
1. En Ubicaciones, especifique las opciones adecuadas.
1. Haga clic en Guardar.

## Configuración de ubicaciones {#locations-settings}

**URI raíz de contenido:** URI o ubicación absoluta del repositorio desde el que se recuperan los formularios. Este valor se combina con el parámetro sForm, especificado a través de la API, para construir la ruta absoluta al formulario que se recupera. Este valor puede hacer referencia a un directorio o a una ubicación web a la que se puede acceder mediante HTTP.

El valor predeterminado es una cadena vacía.

**Archivo de configuración XCI:** Ubicación relativa o absoluta del archivo de configuración XCI que utiliza el servicio Output para la renderización. Para un valor relativo, se supone que el archivo XCI reside en el archivo EAR implementable de AEM formularios.

El valor predeterminado es `com/adobe/formServer/PA/pa_output.xci`.

**Ubicación de caché:** Especifica la ubicación de la caché de disco de salida. Al cambiar esta configuración, se restablece toda la información de caché existente de la ubicación actual y se crea una nueva caché en la nueva ubicación. Seleccione una de las siguientes opciones:

**Ubicación predeterminada:** Esta es la selección predeterminada. Cuando se selecciona esta opción, la caché se crea en una ubicación que depende del servidor de aplicaciones que esté utilizando:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[forms server name]\Output\Cache`
* **WebSphere:** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**Directorio temporal LC:** La caché se crea en un subdirectorio del directorio temporal de formularios AEM, que se especifica en la consola de administración en Configuración > Configuración del sistema principal > Configuraciones > Ubicación del directorio temporal. El nombre del subdirectorio es `adobeoutput_[servername]`.

>[!NOTE]
>
>Si utiliza una utilidad de limpieza temporal, tenga en cuenta que, aunque la eliminación de estos directorios no afecta a la funcionalidad, puede afectar significativamente al rendimiento durante un breve periodo, hasta que se cree la nueva caché. Para evitar este problema, no elimine estos directorios mientras borra el directorio temporal de formularios AEM.
