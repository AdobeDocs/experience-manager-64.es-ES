---
title: Integración de JCR
seo-title: JCR Integration
description: Sugerencias para cuándo debe integrarse a nivel de JCR
seo-description: Tips for when you must integrate at the JCR level
uuid: 11518baf-521e-471d-ad4f-2baa76075cfa
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: e6647a11-a36e-4808-bb61-29b2895c6b1d
exl-id: 3e9727a5-32f8-40ad-aa06-619f50d109b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 2%

---

# Integración de JCR{#jcr-integration}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Preferir la API de recursos de Sling a la API de JCR {#prefer-the-sling-resource-api-to-jcr-api}

La API de Sling funciona a un nivel más alto y abstracto que la API de JCR. Esto permite que el código sea más reutilizable e independiente del almacenamiento subyacente. Esto facilita la inclusión de datos virtuales externos a través del mecanismo ResourceProvider si es necesario.

## Evite consultas siempre que sea posible {#avoid-queries-wherever-possible}

Siempre es más rápido navegar por el repositorio para recuperar datos que ejecutar una consulta. Existen casos en los que las consultas serán necesarias, como una consulta del usuario final o la necesidad de encontrar contenido estructurado de todo el repositorio, pero para todos los demás casos, se prefiere navegar a los nodos necesarios. Las consultas siempre deben evitarse en la lógica de renderización, como los componentes de navegación, una &quot;lista de elementos recientes&quot;, recuentos de elementos, etc. En estos casos, es mejor pasar por la jerarquía o prealmacenar en caché el resultado para que se pueda utilizar directamente cuando se represente.

## Restringir el alcance de la observación JCR {#restrict-the-scope-of-jcr-observation}

Al escuchar eventos en el repositorio, es importante reducir el alcance en la medida de lo posible. Por ejemplo, es mucho mejor escuchar un evento en `/etc/mycompany` que escuchar en `/etc`. Nunca escuche eventos en la raíz del repositorio. Además, asegúrese de que los métodos de rellamada se ejecutan lo más rápido posible cuando no hay nada que hacer.

## Eliminación del uso del acceso de administrador JCR {#eliminate-use-of-jcr-admin-access}

A partir del AEM 6, el inicio de sesión en Administración ha quedado obsoleto, al igual que la obtención de una sesión administrativa de ResourceResolverFactory. En su lugar, se deben crear cuentas de servicio para las operaciones de back office que requieran este tipo de acceso y se puede usar ResourceResolverFactory para obtener un ResourceResolver para esta cuenta.
