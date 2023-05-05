---
title: Instalación del Feature Pack 18912 para la migración masiva de recursos
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: El paquete de funciones 18912 le permite ingerir recursos de forma masiva mediante FTP o migrar recursos de Dynamic Media Classic a Dynamic Media en AEM. Este feature pack opcional está disponible en la asistencia de Adobe.
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 4%

---

# Instalación del paquete de características 18912 para la migración masiva de recursos {#installing-feature-pack}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

La instalación del paquete de características 18912 es _opcional_.

El paquete de funciones 18912 le permite ingerir recursos de forma masiva directamente a Dynamic Media - Scene 7 en modo AEM mediante FTP, o migrar recursos de Dynamic Media Classic a Dynamic Media - Scene7 en modo AEM. El paquete de funciones está disponible en [Adobe Professional Services](https://www.adobe.com/es/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Aunque es posible utilizar el paquete de funciones para migrar masivamente recursos por su cuenta de Dynamic Media Classic a Dynamic Media - Scene7 en modo AEM o migrar masivamente recursos mediante la función FTP en Dynamic Media Classic, el Adobe sí lo hace *not* recomendar este método debido a la complejidad involucrada.
>
>Como tal, los paquetes de funciones de migración, como este, están *only* se admite como parte de un proyecto de migración mediante [Adobe Professional Services](https://www.adobe.com/es/experience-cloud/consulting-services.html).

Antes de instalar este paquete de funciones, primero debe crear un usuario de servicio y proporcionar esa información al Adobe.

Consulte también [Configuración de Dynamic Media: modo Scene7](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**Para instalar el paquete de características 18912 para la migración masiva de recursos**,

1. En la instancia de AEM, vaya a **[!UICONTROL Herramientas > Seguridad > Usuarios > Crear usuario]**. Este usuario de servicio debe tener permisos de lectura y escritura para `/content/dam`.
1. En el **[!UICONTROL ID]** y **[!UICONTROL Contraseña]** , introduzca un nombre de usuario y una contraseña; por ejemplo, `FTP User`. Este nombre aparece en la cronología como el usuario que creó el recurso. Cuando se carga un recurso desde FTP, se considera creado cuando se carga en el servidor FTP y se AEM.
1. Contacto [Asistencia al cliente de Adobe para el Experience Manager](https://helpx.adobe.com/es/contact/enterprise-support.ec.html) para solicitar acceso al paquete de funciones 18912 para descargarlo. Es posible que necesite la siguiente información cuando contacte con el servicio de asistencia técnica:

   * Dirección IP del servidor para la instancia de Autor, incluido el número de puerto (de forma predeterminada, el número de puerto es 4502).
   * AEM nombre de usuario y contraseña del servicio del paso anterior.

1. La asistencia al cliente de Adobe para AEM le proporciona las credenciales de FTP y acceso al paquete de funciones 18912.

1. Cuando reciba el paquete de características 18912, instálelo.

   Consulte [Cómo trabajar con paquetes](/help/sites-administering/package-manager.md) para obtener más información sobre el uso de Distribución de software y paquetes en AEM.
