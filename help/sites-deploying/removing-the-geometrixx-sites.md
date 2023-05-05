---
title: Eliminación de sitios de Geometrixx
seo-title: Removing the Geometrixx Sites
description: Obtenga información sobre cómo eliminar el contenido de la Geometrixx de ejemplo.
seo-description: Learn how to remove the sample Geometrixx content.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
exl-id: 495031fb-b559-4071-abc4-93d238ce136d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# Eliminación de sitios de Geometrixx{#removing-the-geometrixx-sites}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

AEM incluye un conjunto de sitios web de Geometrixx de ejemplo. Puede eliminar este contenido de muestra a través de la variable **Administrador de paquetes**.

Los paquetes individuales relacionados con geometrixx son:

* `cq-geometrixx-outdoors-ugc-pkg-*<version>*.zip`
* `cq-geometrixx-pkg-*<version>*.zip`
* `cq-content-mac-*<version>*.zip`
* `cq-geometrixx-login-pkg-*<version>*.zip`
* `cq-geometrixx-users-pkg-*<version>*.zip`
* `cq-geometrixx-workflow-pkg-*<version>*.zip`
* `cq-geometrixx-outdoors-pkg-*<version>*.zip`
* `cq-geometrixx-commons-pkg-*<version>*.zip`
* `cq-geometrixx-media-pkg-*<version>*.zip`

Para quitar un paquete individual, haga clic en **Desinstalar** en ese paquete.

También hay un superpaquete:

* `cq-geometrixx-all-pkg-5.6.12.zip`

Este paquete incluye todos los paquetes individuales anteriores. Para eliminar todo el contenido relacionado con geometrixx a la vez, haga clic en **Desinstalar** en este paquete. El super-paquete irá al estado desinstalado, y todos los paquetes individuales desaparecerán de la vista del gestor de paquetes.

Ahora tiene una instancia de AEM &quot;vacía&quot; sin ningún sitio de demostración.

>[!NOTE]
>
>Al actualizar, los sitios de geometrixx se vuelven a instalar automáticamente. Es posible que tenga que eliminar los sitios web de geometrixx después de actualizar si no desea estos ejemplos.
