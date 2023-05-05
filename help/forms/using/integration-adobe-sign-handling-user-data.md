---
title: Integración con Acrobat Sign | Gestión de datos de usuario
seo-title: Integration with Acrobat Sign | Handling user data
description: AEM Forms se integra con Acrobat Sign para permitir flujos de trabajo de firma electrónica en formularios adaptables para procesar formularios o acuerdos para flujos de trabajo legales, de ventas, de nómina de pagos y de gestión de recursos humanos. Profundizar en los datos de usuario, los almacenes de datos y acceder y eliminar los datos de usuario.
seo-description: AEM Forms integrates with Acrobat Sign to enable e-signature workflows in adaptive forms to process forms or agreements for legal, sales, payroll, human resource management workflows. Dig deeper on user data, data stores, and access and delete user data.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Acrobat Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 34%

---

# Integración con Acrobat Sign | Gestión de datos de usuario {#integration-with-adobe-sign-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM Forms se integra con Acrobat Sign para permitir flujos de trabajo de firma electrónica en formularios adaptables para procesar formularios o acuerdos para flujos de trabajo legales, de ventas, de nómina de pagos y de gestión de recursos humanos. Permite la firma de un solo usuario y de varios, flujos de trabajo de firma secuenciales y simultáneos, la firma de formularios como un usuario anónimo o con la sesión iniciada, y múltiples formas de autenticar a los usuarios.

Cuando un firmante o varios firmantes firman y envían un formulario adaptable, se genera un acuerdo de Acrobat Sign que incluye información sobre los firmantes.

Para obtener más información sobre la integración de AEM Forms con Acrobat Sign, consulte [Uso de Acrobat Sign en un formulario adaptable](/help/forms/using/working-with-adobe-sign.md).

## Almacenamiento de datos y datos de usuarios {#data}

El formulario adaptable habilitado para Acrobat Sign incluye información sobre los firmantes y puede incluir otros datos de usuario recopilados por el formulario adaptable. El servicio Acrobat Sign guarda los datos de usuario con la firma del acuerdo. El acuerdo se guarda en el servidor de Acrobat Sign configurado en los servicios en la nube de AEM Forms. Además, si el formulario adaptable está configurado para utilizar la acción de envío del portal de formularios, los datos del acuerdo se guardan en el almacén de datos del portal de formularios junto con los datos del formulario.

## Acceder y eliminar datos de usuario {#access-and-delete-user-data}

Los datos de usuario se recopilan en el acuerdo, pero no se guardan en ninguna de las tablas de los servicios. Acrobat Sign permite a los administradores realizar sus propias elecciones en la administración de los datos que controlan en el servicio. Los administradores de privacidad del servicio Acrobat Sign pueden enumerar o eliminar acuerdos basados en la dirección de correo electrónico de un solicitante.

Acrobat Sign ofrece una aplicación web que permite buscar acuerdos por parte de los participantes y, si es necesario, eliminarlos. Para obtener más información, consulte [Acrobat Sign: función: Eliminar información del usuario](https://helpx.adobe.com/es/sign/using/gdpr-compliance.html).

Los datos de acuerdo de los formularios adaptables configurados para utilizar la acción de envío del portal de formularios también se guardan en el almacén de datos del portal de formularios. Para acceder y eliminar datos del almacén de datos del portal de formularios, consulte [Portal de Forms | Gestión de datos de usuario](/help/forms/using/forms-portal-handling-user-data.md).
