---
title: Configuración de puntos finales de Remoting
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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 0%

---

# Configuración de puntos finales de Remoting {#configuring-remoting-endpoints}

Un extremo remoto permite que una aplicación creada con Flex invoque el servicio mediante (obsoleto para AEM formularios) AEM Forms Remoting. Se crea automáticamente un punto final remoto para cada servicio activado. Se crea un destino de Flex que tiene el mismo nombre que el extremo y los clientes de Flex pueden crear objetos remotos que apunten a este destino para invocar operaciones en el servicio correspondiente.

## Configuración de extremo remoto {#remoting-endpoint-settings}

**Método de autenticación de cliente de Flex:** Determina el tipo de respuesta que el servidor devuelve al cliente cuando el servicio invocado está habilitado para la seguridad, la operación invocada no admite invocaciones anónimas y el cliente pasa credenciales no válidas o no válidas.
