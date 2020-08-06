---
title: Información del sistema de Vista
seo-title: Información del sistema de Vista
description: Obtenga información sobre cómo puede vista los gráficos de supervisión de recursos y la información sobre el servidor que ejecuta AEM formularios.
seo-description: Obtenga información sobre cómo puede vista los gráficos de supervisión de recursos y la información sobre el servidor que ejecuta AEM formularios.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# Información del sistema de Vista {#view-system-information}

La ficha Sistema muestra gráficos de supervisión de recursos e información sobre el servidor que ejecuta AEM formularios. Para acceder a esta información, en la consola de administración, haga clic en Monitor de estado en la esquina superior derecha de la página. Si está ejecutando AEM formularios en un entorno agrupado, la información que se muestra corresponde al nodo seleccionado en la lista Servidor.

Para guardar la información actual del sistema como archivo de propiedades, haga clic en Guardar.

El panel derecho de la ficha Sistema muestra representaciones gráficas de la siguiente información:

* Elementos de tarea y recuento de trabajo
* Uso del montón y del montón comprometido
* Uso no heap y no Heap comprometido

Puede arrastrar el puntero a lo largo de la línea de tiempo para obtener los valores de un punto específico en el tiempo.

>[!NOTE]
>
>Los datos del gráfico, los valores de información del servidor y la hora del reloj se actualizan cada 10 minutos. La información no se muestra en tiempo real.

El panel izquierdo de la ficha Sistema muestra la siguiente información sobre el servidor o nodo:

**Máquina virtual:** Versión de Java Virtual Machine (JVM) en el servidor.

**Proveedor de máquina virtual:** Fabricante del JVM.

**Versión de máquina virtual:** Número de versión de JVM

**Nombre del equipo:** Nombre de host del servidor en el que están instalados AEM formularios.

**Tiempo de activación:** Tiempo, en horas y minutos, que el servidor se ha estado ejecutando.

**Compilador Just-In-Time:** Nombre del compilador que se está utilizando.

**Tiempo de compilación:** Cantidad de tiempo empleado en la compilación.

**Número de subprocesos activos:** Número total de subprocesos presentes actualmente en el sistema de formularios AEM.

**Número de subprocesos en pico:** El mayor número de subprocesos activos jamás grabados en el sistema.

**Número de clases cargadas:** Número de clases cargadas en el JVM.

**Número de clases descargadas:** Número de clases descargadas de JVM.

**Heap mínimo:** Cantidad mínima de pila que se utilizó.

**Máximo montón:** Cantidad máxima de pila que se utilizó.

**Nombre del sistema operativo:** Nombre del sistema operativo que se ejecuta en el servidor de formularios AEM.

**Versión del sistema operativo:** Número de versión del sistema operativo que se ejecuta en el servidor de formularios AEM.

**Arco del sistema operativo:** La arquitectura del sistema operativo en la que se ejecuta JVM.

**Número de procesadores:** Número de procesadores del sistema.

**Argumentos de máquina virtual:** Argumento utilizado por JVM.

**Ruta de clase:** Ruta de clase utilizada por JVM.

**Ruta de biblioteca:** Ruta de biblioteca utilizada por el JVM.

**Ruta de clase de arranque:** Ruta de la clase de inicio utilizada por JVM.

**Tipo de servidor de aplicaciones:** Tipo de servidor de aplicaciones utilizado para ejecutar AEM formularios.

**Versión del servidor de aplicaciones:** Número de versión del servidor de aplicaciones utilizado para ejecutar AEM formularios.

**Proveedor del servidor de aplicaciones:** Fabricante del servidor de aplicaciones utilizado para ejecutar AEM formularios.

**Fecha de instalación:** Fecha (en formato aaaa-mm-dd) en la que se instalaron AEM formularios.

**Versión de AEM formularios:** Versión de AEM formularios instalados.

**Versión del parche:** Número de parche de AEM formularios.

**Nombre de la base de datos:** Tipo de base de datos utilizada por AEM formularios.

**Versión de la base de datos:** Número de versión de la base de datos utilizada por AEM formularios.

**Nombre de unidad de base de datos:** Nombre del controlador utilizado por la JVM para conectarse a la base de datos.

**Versión del controlador de base de datos:** Versión del controlador utilizado por el JVM para conectarse a la base de datos.

El botón **Guardar** permite guardar la información del sistema en un archivo de propiedad.
