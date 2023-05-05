---
title: Revisar información del uso de credenciales
seo-title: Review credential use information
description: Obtenga información sobre cómo revisar la información de uso de credenciales.
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 8%

---

# Revisar información del uso de credenciales {#review-credential-use-information}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La credencial contiene información que describe el uso deseado al que se puede acceder mediante la aplicación web del usuario final de las extensiones de Acrobat Reader DC. Puede utilizar esta información para determinar el tipo de credencial instalada (ya sea de evaluación o producción) y sus fechas de validez.

1. Abra un explorador web e introduzca esta URL:

   http://localhost:*[puerto]*/ReaderExtensions (donde *[puerto]* es el número de puerto del servidor de aplicaciones)

1. Inicie sesión con el nombre de usuario y la contraseña predeterminados:

   Nombre de usuario: administrador

   Contraseña: password

   >[!NOTE]
   >
   >Debe tener privilegios de administrador o superusuario para iniciar sesión con el nombre de usuario y la contraseña predeterminados. Para permitir que otros usuarios accedan a las extensiones de Acrobat Reader DC, cree las cuentas de usuario en Administración de usuarios y otorgue a los usuarios la función Aplicación web de extensiones de Acrobat Reader DC .

1. Seleccione el alias de credencial en la lista Seleccionar Credencial y revise la información incluida en Fecha de Caducidad y Aviso de Uso Previsto.

>[!NOTE]
>
>La fecha de caducidad de la credencial también está disponible en la página Configuración > Administración del almacén de confianza > Credenciales locales de la consola de administración, en Fecha de caducidad.
