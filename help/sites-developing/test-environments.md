---
title: ¿Qué entornos de prueba son necesarios?
seo-title: Which Test Environments are needed?
description: Se deben considerar varios entornos como parte de las pruebas
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 3%

---

# ¿Qué entornos de prueba se necesitarán?{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para definir qué configuraciones de prueba, debe tener en cuenta lo siguiente:

**Desarrollo** - Para la unidad y ciertas pruebas de integración.

**Pruebas** - Para la mayoría de las pruebas.

**Activo** - Para las pruebas de rendimiento y de estrés finales. También para pruebas de aceptación con el cliente.

También deberá decidir qué instancias necesitará donde (normalmente al menos una de cada uno para todos los niveles de prueba):

**Autor** : Esta instancia permite a los autores introducir y publicar contenido.

**Publicación** - Esta instancia presenta el sitio web en su formulario publicado para el acceso de los visitantes.

Debe probarse junto con Dispatcher.

Finalmente, debe considerarse el hardware real - cualquier prueba de rendimiento debe realizarse en un sistema lo más cerca posible de la configuración del entorno en directo final. Por este motivo, también se recomienda dividir el lanzamiento del proyecto en:

**Lanzamiento en software** - Menor disponibilidad; que permite tiempo para pruebas de rendimiento, ajustes y optimización en condiciones realistas en el entorno de producción.

**Lanzamiento en disco** - Disponibilidad completa.
