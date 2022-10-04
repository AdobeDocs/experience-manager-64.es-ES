---
title: Hacer que las fuentes estén disponibles
seo-title: Make fonts available
description: Asegúrese de que las fuentes utilizadas en un formulario están disponibles para su uso en el servidor de aplicaciones J2EE que aloja AEM formularios.
seo-description: Ensure that the fonts used within a form are available for use on the J2EE application server hosting AEM forms.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
exl-id: 33d63ec9-b100-48b4-b84d-a9de82c24f86
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Hacer que las fuentes estén disponibles {#make-fonts-available}

Asegúrese de que las fuentes utilizadas en un formulario están disponibles para su uso en el servidor de aplicaciones J2EE que aloja AEM formularios. Por ejemplo, considere el siguiente escenario. Un diseñador de formularios agrega una fuente al directorio de fuentes que utiliza Designer y crea un formulario que utiliza esa fuente en un equipo independiente. Para que el servicio Output use la fuente, colóquela en el directorio fuentes del cliente. Si el directorio de fuentes del cliente no existe, cree un directorio en el servidor de aplicaciones J2EE que hospede AEM formularios.

Para obtener información sobre la configuración de fuentes adicional, consulte [Configuración general de AEM formularios](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**Especifique la ubicación del directorio de fuentes del cliente**

1. En la consola de administración, haga clic en Configuración > Configuración de sistemas principales > Configuraciones.
1. En el cuadro Ubicación del directorio de fuentes del sistema, escriba la ruta al directorio de fuentes del cliente. Se pueden agregar varios directorios separados por punto y coma **;**
1. Haga clic en Aceptar.
1. Reinicie el sistema en el que están instalados AEM formularios.

>[!NOTE]
>
>Las fuentes se seleccionan de la caché de fuentes del sistema de Windows y es necesario reiniciar el sistema para actualizar la caché. Después de especificar el directorio de fuentes del cliente, asegúrese de reiniciar el sistema en el que está instalado AEM formulario.
