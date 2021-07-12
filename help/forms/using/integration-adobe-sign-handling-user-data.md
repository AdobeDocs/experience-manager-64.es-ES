---
title: Integración con Adobe Sign | Gestión de datos de usuario
seo-title: Integración con Adobe Sign | Gestión de datos de usuario
description: AEM Forms se integra con Adobe Sign para permitir flujos de trabajo de firma electrónica en formularios adaptables para procesar formularios o acuerdos para flujos de trabajo legales, de ventas, de nómina de pagos y de gestión de recursos humanos. Profundizar en los datos de usuario, los almacenes de datos y acceder y eliminar los datos de usuario.
seo-description: AEM Forms se integra con Adobe Sign para permitir flujos de trabajo de firma electrónica en formularios adaptables para procesar formularios o acuerdos para flujos de trabajo legales, de ventas, de nómina de pagos y de gestión de recursos humanos. Profundizar en los datos de usuario, los almacenes de datos y acceder y eliminar los datos de usuario.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Integración con Adobe Sign | Gestión de datos de usuario {#integration-with-adobe-sign-handling-user-data}

AEM Forms se integra con Adobe Sign para permitir flujos de trabajo de firma electrónica en formularios adaptables para procesar formularios o acuerdos para flujos de trabajo legales, de ventas, de nómina de pagos y de gestión de recursos humanos. Permite la firma de un solo usuario y de varios usuarios, flujos de trabajo de firma secuenciales y simultáneos, la firma de formularios como usuario anónimo o que ha iniciado sesión y múltiples formas de autenticar a los usuarios.

Cuando un firmante o varios firmantes firman y envían un formulario adaptable, se genera un acuerdo de Adobe Sign que incluye información sobre los firmantes.

Para obtener más información sobre la integración de AEM Forms con Adobe Sign, consulte [Uso de Adobe Sign en un formulario adaptable](/help/forms/using/working-with-adobe-sign.md).

## Almacenamiento de datos y datos de usuarios {#data}

El formulario adaptable habilitado para Adobe Sign incluye información sobre los firmantes y puede incluir otros datos de usuario recopilados por el formulario adaptable. El servicio Adobe Sign guarda los datos de usuario con la firma del acuerdo. El acuerdo se guarda en el servidor de Adobe Sign configurado en los servicios en la nube de AEM Forms. Además, si el formulario adaptable está configurado para utilizar la acción de envío de Forms Portal, los datos del acuerdo se guardan en el almacén de datos del portal de formularios junto con los datos del formulario.

## Acceso y eliminación de datos de usuario {#access-and-delete-user-data}

Los datos de usuario se recopilan dentro del acuerdo, pero no se guardan en ninguna de las tablas de servicios. Adobe Sign permite a los administradores realizar sus propias elecciones en la administración de los datos que controlan en el servicio. Los administradores de privacidad del servicio Adobe Sign pueden enumerar o eliminar acuerdos basados en la dirección de correo electrónico de un solicitante.

Adobe Sign ofrece una aplicación web que permite buscar acuerdos por parte de los participantes y, si es necesario, eliminarlos. Para obtener más información, consulte [Adobe Sign - Función: Eliminar información de usuario](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Los datos de acuerdos para formularios adaptables configurados para utilizar la acción de envío de Forms Portal también se guardan en el almacén de datos del portal de formularios. Para acceder y eliminar datos del almacén de datos del portal de formularios, consulte [Portal de Forms | Gestión de datos de usuario](/help/forms/using/forms-portal-handling-user-data.md).
