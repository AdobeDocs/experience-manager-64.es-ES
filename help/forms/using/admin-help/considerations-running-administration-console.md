---
title: Consideraciones al ejecutar la AdministrationConsole
seo-title: Considerations when running AdministrationConsole
description: Este documento enumera algunos puntos a tener en cuenta al ejecutar la Consola de administración.
seo-description: This document lists a few points to consider when running Administration Console.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 7%

---

# Consideraciones al ejecutar la Consola de administración {#considerations-when-running-administrationconsole}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Estas son algunas cosas que hay que tener en cuenta al ejecutar la Consola de administración:

* Si accede a la consola de administración mediante la dirección URL `https://*[hostname]*:*[port]*/adminui`, el nombre de host especificado no puede contener caracteres subrayados. De lo contrario, es posible que los vínculos a algunas áreas de la consola de administración no funcionen correctamente.
* Si ejecuta la consola de administración en el Explorador de Windows en un sistema operativo japonés, puede encontrar estos problemas:

   * Al hacer clic en un vínculo, volverá a la página de inicio de sesión en lugar de al vínculo esperado.
   * Al hacer clic en un vínculo, aparece un error de permiso.

   Una práctica recomendada es ejecutar la consola de administración desde otro navegador, como Mozilla Firefox, para garantizar que no se produzca ningún error en los vínculos.

* No utilice caracteres de barra invertida () al realizar búsquedas en la consola de administración.
