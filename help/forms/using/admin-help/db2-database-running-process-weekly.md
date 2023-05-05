---
title: "Base de datos DB2: Ejecutar un proceso semanalmente"
seo-title: "DB2 database: Running a process weekly"
description: Vea cómo puede mejorar el rendimiento de la base de datos DB2 de AEM forms.
seo-description: See how you can improve the performance of your AEM forms DB2 database.
uuid: 36070087-c250-41df-a841-aa922e777697
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: fc0e8183-5d50-4fc0-997a-5f3168ba0d70
exl-id: f40fcfab-63e0-4e43-aac5-95426e3dd1fb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 11%

---

# Base de datos DB2: Ejecutar un proceso semanalmente{#db-database-running-a-process-weekly}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Si la base de datos DB2 de los formularios AEM empieza a ejecutarse lentamente, la ejecución semanal del siguiente proceso puede mejorar su rendimiento:

1. Iniciar centro de control DB2:

   (Windows) Seleccione Inicio > Programas > IBM DB2 > Herramientas de administración general > Centro de control.

   (Linux y UNIX) Desde un símbolo del sistema, escriba la variable `db2jcc` comando.

1. En el árbol de objetos del Centro de control de DB2, haga clic en Todas las bases de datos.
1. Haga clic en la base de datos creada para AEM formularios y haga clic en la carpeta Tablas .
1. Seleccione todas las tablas de la base de datos en el panel de contenido, haga clic con el botón derecho en ellas y seleccione Ejecutar estadísticas.
1. Vaya a Estadísticas > Estadísticas de índice.
1. Seleccione Recopilar estadísticas para todos los índices, seleccione Recopilar estadísticas para índices con estadísticas detalladas extendidas y, a continuación, haga clic en Aceptar.

Aparece un mensaje cuando se completa el proceso. Cierre el mensaje.
