---
title: "Base de datos de Microsoft SQL Server: Ajustar la configuración"
seo-title: "Microsoft SQL Server database: Fine-tuning the configuration"
description: Aprenda cómo puede ajustar la configuración de la base de datos de Microsoft SQL Server.
seo-description: Learn how you can fine tune the configuration of your Microsoft SQL Server database.
uuid: 2d618aab-3c67-4edb-a28f-a20904689e6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS, SG_AEMFORMS
discoiquuid: 70559a94-42ea-411a-a32f-5f38bc17ff96
exl-id: 5392027c-eb5a-49c4-bf9b-fe7d399ae0a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 6%

---

# Base de datos de Microsoft SQL Server: Ajustar la configuración {#microsoft-sql-server-database-fine-tuning-the-configuration}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Debe cambiar la configuración predeterminada al usar Microsoft SQL Server. Haga clic con el botón derecho en el servidor local de Oracle Enterprise Manager para acceder al cuadro de diálogo de propiedades.

## Configuración de memoria {#memory-settings}

Cambie la asignación mínima de memoria a un número lo más grande posible. Si la base de datos se está ejecutando en un equipo independiente, utilice toda la memoria. La configuración predeterminada no asigna la memoria de forma agresiva, lo que dificulta el rendimiento en casi cualquier base de datos. Debe ser más agresivo a la hora de asignar memoria a las máquinas de producción.

## Configuración del procesador {#processor-settings}

Modifique la configuración del procesador y, lo que es más importante, active la casilla de verificación Mejorar la prioridad de SQL Server en Windows para que el servidor utilice tantos ciclos como sea posible. La configuración Usar fibras NT es menos importante, pero es posible que también desee seleccionarla.

## Configuración de la base de datos {#database-settings}

Cambie la configuración de la base de datos. La configuración más importante es Intervalo de recuperación, que especifica la cantidad máxima de tiempo de espera para la recuperación después de un bloqueo. La configuración predeterminada es de un minuto. El uso de un valor mayor, de 5 a 15 minutos, mejora el rendimiento porque le da al servidor más tiempo para escribir cambios desde el registro de la base de datos de nuevo en los archivos de la base de datos.

>[!NOTE]
>
>Esta configuración no compromete el comportamiento transaccional porque solo cambia la duración de la reproducción del archivo de registro que debe realizarse al inicio.

Establezca el tamaño asignado de espacio tanto para el registro como para el archivo de datos para que sea mucho mayor que la base de datos inicial. Tenga en cuenta cuánto puede crecer la base de datos a lo largo de un año. Lo ideal es que los archivos de registro y datos se asignen en forma contigua para que los datos no terminen fragmentados en todo el disco.
