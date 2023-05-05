---
title: Archivos de registro
seo-title: Log files
description: Eventos como errores de inicio o en tiempo de ejecución se registran en los archivos de registro del servidor de aplicaciones, que se pueden abrir con cualquier editor de texto.
seo-description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
exl-id: acce13aa-864c-4999-be5c-6d49b99d5459
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 6%

---

# Archivos de registro {#log-files}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Eventos como errores de inicio o en tiempo de ejecución se registran en los archivos de registro del servidor de aplicaciones. Si tiene problemas de implementación en el servidor de aplicaciones, puede utilizar los archivos de registro para ayudarle a encontrar el problema. Puede abrir los archivos de registro con cualquier editor de texto.

(JBoss) Los siguientes archivos de registro se encuentran en la `*[appserver root]*/server/*[server]*/log` directorio:

* boot.log
* server.log.*[aaaa-mm-dd]*
* server.log

(WebLogic) Los archivos de registro de dominio se encuentran en el *[appserverdomain]* y los archivos de registro del servidor se encuentran en el directorio *[appserverdomain]/servers/[nombre del servidor de aplicaciones]/logs *directorio:

* access.log
* *[nombre del servidor de aplicaciones]*.log
* *[nombre del servidor de aplicaciones]*.out.*[número incremental]*

(WebSphere) Los siguientes archivos de registro se encuentran en la *[raíz de appserver]*/profiles/default/logs/*[nombre del servidor de aplicaciones]* directorio:

* SystemErr.log
* SystemOut.log
* StartServer.log
