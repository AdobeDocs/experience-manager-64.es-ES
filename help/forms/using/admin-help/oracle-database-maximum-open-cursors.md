---
title: Umbral máximo de cursores abiertos de la base de datos de Oracle
seo-title: Oracle database maximum open cursors threshold
description: Obtenga información sobre cómo configurar un valor máximo para cursores abiertos en Oracle.
seo-description: Learn about configuring a maximum value for open cursors in Oracle.
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 16%

---

# Umbral máximo de cursores abiertos de la base de datos de Oracle {#oracle-database-maximum-open-cursors-threshold}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para configurar un valor máximo para cursores abiertos en Oracle, es posible que tenga que ajustar este valor a un número que sea apropiado para su aplicación. Es evidente que bajo una carga moderada, el promedio de cursores abiertos era de 2700. Se recomienda comenzar con un límite superior de 3000. Para obtener más información, vaya a [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
