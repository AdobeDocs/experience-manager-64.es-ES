---
title: Comprobador de vínculos externos
seo-title: Comprobador de vínculos externos
description: Obtenga información sobre el Comprobador de vínculos externos en AEM.
seo-description: Obtenga información sobre el Comprobador de vínculos externos en AEM.
uuid: fd0c6ff6-52d2-4096-af40-54786e9d9ab8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 49b195b2-78c4-49f9-b07a-a87b73624c2c
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Comprobador de vínculos externos{#the-external-link-checker}

AEM proporciona un comprobador de vínculos externo. Comprobador de vínculos:

* analiza todas las páginas de contenido
* genera una lista de todos los vínculos válidos y no válidos
* marca los vínculos no válidos como rotos in situ en las páginas de contenido individuales

## Cómo validar vínculos externos {#how-to-validate-external-links}

Para utilizar el comprobador de vínculos externo:

1. Open the **Tools** console.
1. Haga doble clic en el Comprobador **de vínculos** externos (a la derecha o a la izquierda). Se genera una lista de todos los vínculos externos.
1. Valide un vínculo específico seleccionándolo en la lista y luego haciendo clic en **Comprobar**:

   ![chlimage_1-109](assets/chlimage_1-109.png)

   Información como:

   * estado del vínculo
   * URL
   * tiempo transcurrido desde la última validación del vínculo
   * tiempo transcurrido desde la última vez que el vínculo estuvo disponible
   * tiempo transcurrido desde la última vez que se accedió al vínculo
   se muestra.

1. En las páginas de contenido individuales, los vínculos no válidos se mostrarán como rotos:

   ![chlimage_1-110](assets/chlimage_1-110.png)

