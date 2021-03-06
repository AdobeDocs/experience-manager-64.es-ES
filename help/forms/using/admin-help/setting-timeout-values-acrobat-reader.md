---
title: 'Configuración de valores de tiempo de espera para su uso con extensiones de Acrobat Reader DC '
seo-title: 'Configuración de valores de tiempo de espera para su uso con extensiones de Acrobat Reader DC '
description: Obtenga información sobre cómo establecer valores de tiempo de espera para su uso con extensiones de Acrobat Reader DC.
seo-description: Obtenga información sobre cómo establecer valores de tiempo de espera para su uso con extensiones de Acrobat Reader DC.
uuid: d6d072a0-0a30-417a-98b1-df8b4ff8f911
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a9aeeb89-45e9-4d5d-aa25-8145c89b64f2
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Configuración de valores de tiempo de espera para su uso con extensiones de Acrobat Reader DC {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

Al trabajar con muchos archivos PDF en extensiones de Acrobat Reader DC, asegúrese de que los siguientes valores de tiempo de espera estén correctamente configurados para evitar que los trabajos se agote o falle:

**Tiempo de espera de eliminación de documentos**

Este valor se puede establecer en la consola de administración. Haga clic en Configuración > Configuración del sistema principal > Configuraciones y especifique un valor para Tiempo de espera de eliminación de Documentos predeterminado.

**Tiempo de espera AEM formularios del Administrador de usuarios:** este valor se puede establecer editando el archivo config.xml. En la consola de administración, haga clic en Configuración > Administración de usuarios > Configuración > Importar y exportar archivos de configuración y, a continuación, haga clic en Exportar. Abra el archivo config.xml exportado y edite las siguientes líneas:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot; />

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot; />

Guarde y, a continuación, importe el archivo config.xml de nuevo en la consola de administración.

**Tiempo de espera de sesión de Application Server:** este valor se puede establecer en el servidor de aplicaciones. Para obtener más información, consulte la documentación proporcionada con el servidor de aplicaciones.
