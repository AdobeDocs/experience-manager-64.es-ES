---
title: Configurar puntos finales remotos
seo-title: Configuring Remoting endpoints
description: Aprenda a configurar puntos finales remotos.
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 8%

---

# Configurar puntos finales remotos {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Un extremo remoto permite que una aplicación creada con Flex invoque el servicio mediante (obsoleto para AEM formularios) AEM Forms Remoting. Se crea automáticamente un punto final remoto para cada servicio activado. Se crea un destino de Flex que tiene el mismo nombre que el extremo y los clientes de Flex pueden crear objetos remotos que apunten a este destino para invocar operaciones en el servicio correspondiente.

## Configuración de extremo remoto {#remoting-endpoint-settings}

**Método de autenticación de cliente de Flex:** Determina el tipo de respuesta que el servidor devuelve al cliente cuando el servicio invocado está habilitado para la seguridad, la operación invocada no admite invocaciones anónimas y el cliente pasa credenciales no válidas o no válidas.
