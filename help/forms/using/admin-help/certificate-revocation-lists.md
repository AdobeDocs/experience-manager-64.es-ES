---
title: Administración de listas de revocación de certificados
seo-title: Managing certificate revocationlists
description: Obtenga información sobre cómo administrar las listas de revocación de certificados.
seo-description: Learn how to manage certificate revocation lists.
uuid: d8c4b64c-a273-4f5d-8b71-f6ea455c0f0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9744cc2d-5e6b-4341-9270-43d479bdca04
exl-id: 45741270-2d57-4d6d-92ef-65b6c1deb448
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 5%

---

# Administración de listas de revocación de certificados{#managing-certificate-revocationlists}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Mediante la administración de almacenes de confianza, puede importar, editar y eliminar listas de revocación de certificados (CRL). Se admiten las listas de revocación de certificados codificadas Base64 y DER.

## Importar una CRL {#import-a-crl}

1. En la consola de administración, haga clic en Configuración > Administración de almacén de confianza > Listas de revocación de certificados y, a continuación, haga clic en Importar.
1. En el cuadro Alias, escriba un identificador para la CRL.
1. Haga clic en Examinar para localizar la CRL y, a continuación, haga clic en Aceptar.

## Exportar una CRL {#export-a-crl}

1. En la consola de administración, haga clic en Configuración > Administración de almacén de confianza > Listas de revocación de certificados.
1. Haga clic en el nombre de alias de la CRL que desea exportar y, a continuación, haga clic en Exportar.
1. Siga las instrucciones para exportar la CRL. Las CRL se exportan con codificación Base64.
1. Haga clic en Aceptar.

## Eliminar una CRL {#delete-a-crl}

1. En la consola de administración, haga clic en Configuración > Administración de almacén de confianza > Listas de revocación de certificados.
1. Seleccione las casillas de verificación de las listas CRL que desea eliminar, haga clic en Eliminar y, a continuación, haga clic en Aceptar.
