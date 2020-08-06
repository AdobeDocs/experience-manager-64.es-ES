---
title: Instalación de Feature Pack 18912 para la migración masiva de recursos
seo-title: Instalación de Feature Pack 18912 para la migración masiva de recursos
description: El paquete de funciones 18912 le permite realizar ingestas masivas de recursos mediante FTP o migrar recursos de Dynamic Media Classic a Dynamic Media en AEM. Este paquete de funciones opcional está disponible en la compatibilidad con Adobe.
seo-description: El paquete de funciones 18912 le permite realizar ingestas masivas de recursos mediante FTP o migrar recursos de Dynamic Media Classic a Dynamic Media en AEM. Este paquete de funciones opcional está disponible en la compatibilidad con Adobe.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Instalación del paquete de funciones 18912 para la migración masiva de recursos {#installing-feature-pack}

La instalación del paquete de funciones 18912 es _opcional_.

El paquete de funciones 18912 le permite realizar la ingesta masiva de recursos directamente en el modo Dynamic Media - Scene 7 en AEM mediante FTP, o bien, migrar recursos de Dynamic Media Classic a Dynamic Media - modo Scene7 en AEM. El paquete de funciones está disponible en [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Aunque es posible utilizar el paquete de funciones para migrar recursos por su cuenta de forma masiva del modo Dynamic Media Classic al modo Dynamic Media - Scene 7 en AEM o para migrar recursos de forma masiva mediante la función de FTP en Dynamic Media Classic, Adobe *no* recomienda este método debido a la complejidad que conlleva.
>
>De este modo, los paquetes de funciones de migración, como este, *solo* se admiten como parte de un proyecto de migración a través de [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Antes de instalar este paquete de funciones, primero debe crear un usuario de servicio y proporcionar esa información a Adobe.

Consulte también [Configuración de Dynamic Media: modo](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html)Scene7.

**Para instalar el paquete de funciones 18912 para la migración** masiva de recursos,

1. En la instancia de AEM, vaya a **[!UICONTROL Herramientas > Seguridad > Usuarios > Crear usuario]**. Este usuario de servicio debe tener permisos de lectura y escritura para `/content/dam`.
1. En los campos **[!UICONTROL ID]** y **[!UICONTROL Contraseña]** , introduzca un nombre de usuario y una contraseña; por ejemplo, `FTP User`. Este nombre aparece en la línea de tiempo como el usuario que creó el recurso. Cuando se carga un recurso desde FTP, se considera que se crea al cargarlo en el servidor FTP y se transfiere a AEM.
1. Póngase en contacto con el servicio de asistencia técnica empresarial de [Adobe para que el Experience Manager](https://helpx.adobe.com/es/contact/enterprise-support.ec.html) solicite el acceso al paquete de funciones 18912 para descargarlo. Es posible que necesite la siguiente información cuando se ponga en contacto con la asistencia técnica:

   * Dirección IP del servidor para la instancia de Autor, incluido el número de puerto (de forma predeterminada, el número de puerto es 4502).
   * Nombre de usuario y contraseña del usuario del servicio de AEM del paso anterior.

1. La asistencia técnica para empresas de Adobe para AEM le proporciona las credenciales de FTP y acceso al paquete de funciones 18912.

1. Cuando reciba el paquete de funciones 18912, instálelo.

   Consulte [Cómo trabajar con paquetes](/help/sites-administering/package-manager.md) para obtener más información sobre el uso de Distribución de software y paquetes en AEM.
