---
title: Requisitos previos para la integración con Adobe Target
seo-title: Prerequisites for Integrating with Adobe Target
description: Obtenga información sobre los requisitos previos para la integración con Adobe Target.
seo-description: Find out about the prerequisites for integrating with Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
exl-id: f47e5c6a-ed52-4493-83bd-73e5e693d117
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 10%

---

# Requisitos previos para la integración con Adobe Target{#prerequisites-for-integrating-with-adobe-target}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Como parte del [integración de AEM y Adobe Target](/help/sites-administering/target.md), debe registrarse con Adobe Target, configurar el agente de replicación y establecer la configuración de actividad segura en el nodo de publicación.

## Registro con Adobe Target {#registering-with-adobe-target}

Para integrar AEM con Adobe Target, debe tener una cuenta de Adobe Target válida. Esta cuenta debe tener al menos **aprobador **permisos de nivel. Al registrarse en Adobe Target, recibirá un código de cliente. Necesita el código de cliente, el nombre de inicio de sesión y la contraseña de Adobe Target para conectarse AEM Adobe Target.

El código de cliente identifica la cuenta de cliente de Adobe Target al llamar al servidor de Adobe Target.

>[!NOTE]
>
>El equipo de Target también debe habilitar la cuenta para poder usar la integración.
>
>
>Si no es así, póngase en contacto con [Servicio de atención al cliente de Adobe Target](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html).

## Habilitar el agente de replicación de Target {#enabling-the-target-replication-agent}

La prueba y el objetivo [agente de replicación](/help/sites-deploying/replication.md) debe estar habilitado en la instancia de autor. Tenga en cuenta que este agente de replicación no está habilitado de forma predeterminada si ha utilizado la variable [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) ejecute el modo para instalar AEM. Para obtener más información sobre la seguridad del entorno de producción, consulte [Lista de comprobación de seguridad](/help/sites-administering/security-checklist.md).

1. En la página principal de AEM, toque o haga clic en **Herramientas** > **Implementación** > **Replicación**.
1. Toque o haga clic en **Agentes En Autor**.
1. Toque o haga clic en **Prueba y objetivo (prueba y destino)** agente de replicación y, a continuación, toque o haga clic en **Editar**.
1. Seleccione la opción Activado y, a continuación, toque o haga clic en **OK**.

   >[!NOTE]
   >
   >Cuando configure el agente de replicación de Test y Target, en la variable **Transporte** , el URI se establece de forma predeterminada en **tnt:///**. No reemplace este URI por **https://admin.testandtarget.omniture.com**.
   >
   >Tenga en cuenta que si intenta probar la conexión con **tnt:///**, generará un error. Este comportamiento es esperado, ya que este URI es solo para uso interno y no debe usarse con **Probar conexión**.

## Protección del nodo Configuración de actividades {#securing-the-activity-settings-node}

Debe asegurar el nodo de configuración de actividades **cq:ActivitySettings** de la instancia de publicación, para que los usuarios normales no puedan obtener acceso a él. El nodo de configuración de la actividad solo debe ser accesible para el servicio que administra la sincronización de actividades en Adobe Target.

La variable **cq:ActivitySettings** El nodo está disponible en la lista CRXDE, en `/content/campaigns/*nameofbrand*`* *en el nodo activity jcr:content;* *por ejemplo `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Este nodo solo se crea después de que se dirija a un componente.

La variable **cq:ActivitySettings** bajo el jcr:content de la actividad está protegido por las siguientes ACL:

* Denegar todo para todos
* Permitir jcr:read,rep:write para &quot;target-activity-authors&quot; (el autor es un miembro de este grupo de forma predeterminada)
* Permitir jcr:read,rep:write para &quot;targetservice&quot;

Estos ajustes garantizan que los usuarios normales no tengan acceso a las propiedades del nodo. Utilice las mismas ACL en el autor y en la publicación. Consulte [Administración de usuarios y seguridad](/help/sites-administering/security.md) para obtener más información.

## Configuración del externalizador de AEM {#configuring-the-aem-externalizer}

Al editar una actividad en Adobe Target, la dirección URL señala a **localhost** a menos que cambie la dirección URL en el nodo AEM autor.

Para configurar el externalizador de AEM:

1. Vaya a la consola web OSGi en **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Buscar **Externalizador de vínculos de CQ de día** e introduzca el dominio del nodo de creación.

   ![chlimage_1-120](assets/chlimage_1-120.png)
