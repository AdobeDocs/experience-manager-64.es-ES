---
title: Configurar valores de tiempo de espera para usarlos con extensiones de Acrobat Reader DC
seo-title: Setting timeout values for use with Acrobat Reader DC extensions
description: Obtenga información sobre cómo establecer valores de tiempo de espera para su uso con extensiones de Acrobat Reader DC.
seo-description: Learn how to set timeout values for use with Acrobat Reader DC extensions.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
exl-id: e7de9971-3eac-4248-8709-0da7dd709d1b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 13%

---

# Configurar valores de tiempo de espera para usarlos con extensiones de Acrobat Reader DC  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cuando trabaje en muchos archivos de PDF en extensiones de Acrobat Reader DC, asegúrese de que los siguientes valores de tiempo de espera estén correctamente configurados para evitar que los trabajos finalicen y fallen:

**Tiempo de espera de eliminación de documentos**

Este valor se puede establecer en la consola de administración. Haga clic en Configuración > Configuración del sistema principal > Configuraciones y especifique un valor para el tiempo de espera de eliminación de documentos predeterminado.

**Tiempo de espera de AEM de formularios del administrador de usuarios:** Este valor se puede configurar editando el archivo config.xml. En la consola de administración, haga clic en Configuración > Administración de usuarios > Configuración > Importar y exportar archivos de configuración y, a continuación, haga clic en Exportar. Abra el archivo config.xml exportado y edite las siguientes líneas:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Guarde y luego importe el archivo config.xml de nuevo en la consola de administración.

**Tiempo de espera de sesión del servidor de aplicaciones:** Este valor se puede establecer en el servidor de aplicaciones. Para obtener más información, consulte la documentación proporcionada con el servidor de aplicaciones.
