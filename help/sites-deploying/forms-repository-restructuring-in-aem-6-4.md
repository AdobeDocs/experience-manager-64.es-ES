---
title: Reestructuración del repositorio de Forms en AEM 6.4
seo-title: Forms Repository Restructuring in AEM 6.4
description: Aprenda a realizar los cambios necesarios para migrar a la nueva estructura de repositorios en AEM 6.4 para Forms.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Upgrading
exl-id: a2d6524e-3f5b-4d1e-af64-61ff95889657
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 8%

---

# Reestructuración del repositorio de Forms en AEM 6.4{#forms-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Tal como se describe en el elemento principal [Reestructuración de repositorios en AEM 6.4](/help/sites-deploying/repository-restructuring.md) , los clientes que actualicen a AEM 6.4 deben utilizar esta página para evaluar el esfuerzo de trabajo asociado con los cambios en el repositorio que afectan a la solución de AEM Forms. Algunos cambios requieren un esfuerzo de trabajo durante el proceso de actualización de AEM 6.4, mientras que otros se pueden aplazar hasta una actualización de 6.5.

**Con actualización a la versión 6.4**

* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Antes de la actualización a la versión 6.5**

* [Configuración del Cloud Service Echosign](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Configuraciones del Cloud Service de Recaptcha](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Configuraciones del Cloud Service de Typekit](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Misc](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Con actualización a la versión 6.4 {#with-upgrade}

### Misc {#misc}

| **Ubicación anterior** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/fp/components` |
| **Directrices de reestructuración** | Las referencias explícitas del código personalizado a la ubicación Heredado deben actualizarse a la ubicación Nueva . |
| **Notas** | Estas bibliotecas de cliente no deben modificarse ni ampliarse. |

| **Ubicación anterior** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/rte` |
| **Directrices de reestructuración** | Para los recursos de las bibliotecas de cliente a los que se puede hacer referencia mediante rutas absolutas, debe utilizar rutas más nuevas en los recursos nuevos. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/af/authoring/clientlibs` |
| **Directrices de reestructuración** | Para los recursos de las bibliotecas de cliente a los que se puede hacer referencia mediante rutas absolutas, debe utilizar rutas más nuevas en los recursos nuevos. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/xfaforms/clientlibs/` |
| **Directrices de reestructuración** | Para los recursos de las bibliotecas de cliente a los que se puede hacer referencia mediante rutas absolutas, debe utilizar rutas más nuevas en los recursos nuevos. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/af/runtime/clientlibs` |
| **Directrices de reestructuración** | Para los recursos de las bibliotecas de cliente a los que se puede hacer referencia mediante rutas absolutas, debe utilizar rutas más nuevas en los recursos nuevos. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/af/runtime/clientlibs` |
| **Directrices de reestructuración** | Para los recursos de las bibliotecas de cliente a los que se puede hacer referencia mediante rutas absolutas, debe utilizar rutas más nuevas en los recursos nuevos. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/expeditor/clientlibs` |
| **Directrices de reestructuración** | Para los recursos de las bibliotecas de cliente a los que se puede hacer referencia mediante rutas absolutas, debe utilizar rutas más nuevas en los recursos nuevos. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/fmaddon` |
| **Directrices de reestructuración** | Nunca se recomendó ni se admitió cambiar estos clientlibs. Si se han realizado modificaciones en estos clientlibs, se deben revertir para utilizar el código proporcionado por el AEM. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/aep` |
|---|---|
| **Nuevas ubicaciones** | `/var/fd/content/annotations` |
| **Directrices de reestructuración** | Nunca se recomendó ni se admitió cambiar estos clientlibs. Si se han realizado modificaciones en estos clientlibs, se deben revertir para utilizar el código proporcionado por el AEM. |
| **Notas** | N/D |

## Antes de la actualización a la versión 6.5 {#prior-to-upgrade}

### Configuración del Cloud Service Echosign {#echosign-cloud-service-configuration}

| **Ubicación anterior** | `/etc/cloudservices/echosign` |
|---|---|
| **Nuevas ubicaciones** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Directrices de reestructuración** | La variable [Migración de contenido diferido](/help/sites-deploying/lazy-content-migration.md) que se activará desde la interfaz de usuario de migración de Forms. |
| **Notas** | N/D |

### Configuraciones del Cloud Service de Recaptcha {#recaptcha-cloud-service-configurations}

| **Ubicación anterior** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Nuevas ubicaciones** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Directrices de reestructuración** | La variable [Migración de contenido diferido](/help/sites-deploying/lazy-content-migration.md) que se activará desde la interfaz de usuario de migración de Forms. |
| **Notas** | N/D |

### Configuraciones del Cloud Service de Typekit {#typekit-cloud-service-configurations}

| **Ubicación anterior** | `/etc/cloudservices/typekit` |
|---|---|
| **Nuevas ubicaciones** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Directrices de reestructuración** | La variable [Migración de contenido diferido](/help/sites-deploying/lazy-content-migration.md) que se activará desde la interfaz de usuario de migración de Forms. |
| **Notas** | N/D |

### Misc {#misc-1}

| **Ubicación anterior** | `/etc/cloudservices/fdm` |
|---|---|
| **Nuevas ubicaciones** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Directrices de reestructuración** | La variable [Migración de contenido diferido](/help/sites-deploying/lazy-content-migration.md) que se activará desde la interfaz de usuario de migración de Forms. |
| **Notas** | N/D |

| **Ubicación anterior** | `/etc/designs/fd/fp` |
|---|---|
| **Nuevas ubicaciones** | `/libs/fd/fp` |
| **Directrices de reestructuración** | Cualquier referencia a las plantillas /etc debería actualizarse finalmente para que apunten a sus `/libs` homólogos. |
| **Notas** | N/D |
