---
title: Requisitos previos para la integración con Adobe Target
seo-title: Requisitos previos para la integración con Adobe Target
description: Descubra los requisitos previos para la integración con Adobe Target.
seo-description: Descubra los requisitos previos para la integración con Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
translation-type: tm+mt
source-git-commit: 152f60a7c9579d89cca5dc326679dc5a08d4dd5f

---


# Requisitos previos para la integración con Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Como parte de la [integración de AEM y Adobe Target](/help/sites-administering/target.md), debe registrarse en Adobe Target, configurar el agente de replicación y proteger la configuración de la actividad en el nodo de publicación.

## Registrarse con Adobe Target {#registering-with-adobe-target}

Para integrar AEM con Adobe Target, debe tener una cuenta válida de Adobe Target. Esta cuenta debe tener como mínimo **aprobador **nivel de permisos. Al registrarse en Adobe Target, recibe un código de cliente. Necesita el código de cliente, el nombre de inicio de sesión y la contraseña de Adobe Target para conectar AEM a Adobe Target.

El código de cliente identifica la cuenta de cliente de Adobe Target al llamar al servidor de Adobe Target.

>[!NOTE]
>
>El equipo de Target también debe habilitar su cuenta para poder usar la integración.
>
>
>Si no es así, póngase en contacto con el servicio de atención al cliente de [Adobe Target](https://marketing.adobe.com/resources/help/en_US/target/target/r_problem.html).

## Habilitación del agente de replicación de Target {#enabling-the-target-replication-agent}

El agente [de](/help/sites-deploying/replication.md) replicación de Test y Target debe estar habilitado en la instancia de creación. Tenga en cuenta que este agente de replicación no está habilitado de forma predeterminada si ha utilizado el modo [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) durante la instalación de AEM. Para obtener más información sobre la seguridad del entorno de producción, consulte la lista de comprobación [de seguridad](/help/sites-administering/security-checklist.md).

1. En la página de inicio de AEM, toque o haga clic en **Herramientas** > **Implementación** > **Replicación**.
1. Toque o haga clic en **Agentes al autor**.
1. Toque o haga clic en el agente de replicación **Test and Target (test and target)** y, a continuación, toque o haga clic en **Editar**.
1. Seleccione la opción Habilitado y toque o haga clic en **Aceptar**.

   >[!NOTE]
   >
   >Al configurar el agente de replicación de Test y Target, en la ficha **Transporte** , el URI se establece de forma predeterminada en **tnt:///**. No reemplace este URI por **https://admin.testandtarget.omniture.com**.
   >
   >Tenga en cuenta que si intenta probar la conexión con **tnt:///**, se producirá un error. Este comportamiento es esperado, ya que este URI es solo para uso interno y no debe usarse con **Test Connection**.

## Seguridad del nodo de configuración de actividades {#securing-the-activity-settings-node}

You must secure the activity settings node **cq:ActivitySettings** on the publish instance so that it is inaccessible to normal users. El nodo de configuración de la actividad solo debe ser accesible para el servicio que administra la sincronización de actividades en Adobe Target.

**El nodo** cq:ActivitySettings`/content/campaigns/*nameofbrand*` está disponible en la lista CRXDE en *** en el nodo activity jcr:content; *por ejemplo `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Este nodo solo se crea después de que se dirija a un componente.

El nodo **cq:ActivitySettings** situado debajo de jcr:content de la actividad está protegido por las siguientes ACL:

* Denegar todo para todos
* Permitir jcr:read,rep:write para &quot;target-activity-author&quot; (el autor es un miembro de este grupo de forma predeterminada)
* Permitir jcr:read,rep:write para &quot;targetservice&quot;

Esta configuración garantiza que los usuarios normales no tengan acceso a las propiedades del nodo. Utilice las mismas ACL en el autor y en la publicación. Consulte Administración [de usuarios y seguridad](/help/sites-administering/security.md) para obtener más información.

## Configuración del externalizador de AEM {#configuring-the-aem-externalizer}

Al editar una actividad en Adobe Target, la dirección URL apunta a **localhost** , a menos que cambie la dirección URL en el nodo de creación de AEM.

Para configurar el externalizador de AEM:

1. Vaya a la consola web OSGi en **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Busque **Day CQ Link Externalizer** e introduzca el dominio del nodo de creación.

   ![chlimage_1-120](assets/chlimage_1-120.png)

