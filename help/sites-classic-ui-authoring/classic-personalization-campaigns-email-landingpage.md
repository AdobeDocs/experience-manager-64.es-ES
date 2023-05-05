---
title: Creación de una página de aterrizaje del boletín eficaz
seo-title: Creating an Effective Newsletter Landing Page
description: Una página de aterrizaje de newsletter eficaz le ayuda a obtener el mayor número de personas posible para suscribirse al boletín informativo (u otra campaña de marketing por correo electrónico). Puede utilizar la información recopilada de los registros al boletín informativo para obtener posibles clientes.
seo-description: An effective newsletter landing page helps you get as many people as possible to sign up for your newsletter (or other email marketing campaign). You can use the information you gather from your newsletter sign ups to get leads.
uuid: 810f3d1c-6648-4342-9fbc-0701765311a1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: dfe0ad66-9df5-4ea3-9e66-543b5ccd594a
exl-id: 1ab81235-2627-4304-bbf2-71598de948db
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 1%

---

# Creación de una página de aterrizaje del boletín eficaz{#creating-an-effective-newsletter-landing-page}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Una página de aterrizaje de newsletter eficaz le ayuda a obtener el mayor número de personas posible para suscribirse al boletín informativo (u otra campaña de marketing por correo electrónico). Puede utilizar la información recopilada de los registros al boletín informativo para obtener posibles clientes.

Para crear una página de aterrizaje de boletín eficaz, debe hacer lo siguiente:

1. Cree una lista para el boletín, de modo que los usuarios puedan suscribirse al mismo.
1. Cree el formulario de registro. Al hacerlo, añada un paso del flujo de trabajo que añada automáticamente a la persona que se registre al boletín a su lista de posibles clientes.
1. Cree una página de confirmación que dé las gracias a los usuarios por registrarse y que posiblemente les proporcione una promoción.
1. Agregue teasers.

>[!NOTE]
>
>Adobe no tiene previsto mejorar aún más esta capacidad (Administración de posibles clientes y listas).\
>La recomendación es aprovechar [Adobe Campaign y su integración AEM](/help/sites-administering/campaign.md).

## Creación de una lista para el boletín {#creating-a-list-for-the-newsletter}

Cree una lista, por ejemplo, **Newsletter de Geometrixx**, en MCM para el boletín al que los usuarios deben suscribirse. La creación de listas se describe en [Creación de listas](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#creatingnewlists).

A continuación se muestra un ejemplo de una lista:

![mcm_listcreate](assets/mcm_listcreate.png)

## Crear un formulario de registro {#create-a-sign-up-form}

Cree un formulario de registro a la newsletter que permita a los usuarios suscribirse a las etiquetas. El sitio web del Geometrixx de ejemplo proporciona una página de boletín en la barra de herramientas de Geometrixx donde puede crear el formulario.

Para crear su propio formulario de boletín, consulte la información sobre la creación de formularios en la [Documentación de Forms](/help/sites-authoring/default-components.md#form). El boletín utiliza las etiquetas de la biblioteca de etiquetas. Para agregar etiquetas adicionales, consulte [Administración de etiquetas](/help/sites-authoring/tags.md#tagadministration).

Los campos ocultos del siguiente ejemplo proporcionan la cantidad mínima de información básica (correo electrónico); además, puede agregar más campos más adelante, pero esto afectará a la tasa de conversión.

El siguiente ejemplo es un formulario creado en http://localhost:4502/cf#/content/geometrixx/en/toolbar/newsletter.html.

1. Cree el formulario.

   ![mcm_newsletterpage](assets/mcm_newsletterpage.png)

1. Haga clic en **Editar** en el componente Formulario para configurar el formulario para que vaya a una página de agradecimiento (consulte [Creación de páginas de agradecimiento](#creating-a-thank-you-page)).

   ![dc_formstart_thankyou](assets/dc_formstart_thankyou.png)

1. Establezca la acción Formulario (esto es lo que sucederá cuando envíe el formulario) y configure el grupo para asignar los usuarios registrados a la lista que ha creado anteriormente (por ejemplo, newsletter de geometrixx).

   ![dc_formstart_thankyouadvanced](assets/dc_formstart_thankyouadvanced.png)

## Creación de una página de agradecimiento {#creating-a-thank-you-page}

Cuando los usuarios hagan clic en **Suscribirse ahora**, desea que se abra una página de agradecimiento automáticamente. Cree la página de agradecimiento en la página del boletín de Geometrixx. Después de crear el formulario del boletín, edite el componente Formulario y añada la ruta a la página de agradecimiento.

Al enviar la solicitud, el usuario se convierte en un **Gracias** página tras la cual recibirán un correo electrónico. Esta página de agradecimiento se creó en /content/geometrixx/en/toolbar/newsletter/thank_you.

![mcm_newsletter_thankyoupage](assets/mcm_newsletter_thankyoupage.png)

## Adición de teasers {#adding-teasers}

Agregar [teasers](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers) para dirigirse a audiencias específicas. Por ejemplo, puede agregar teasers a la página de agradecimiento y a la página de registro al boletín.

Para añadir teasers con el fin de que la página de base de la newsletter sea eficaz:

1. Cree un párrafo de teaser para obtener un regalo de registro. Select **First** como estrategia e incluir texto que les informe qué regalo van a recibir.

   ![dc_teaser_thankyou](assets/dc_teaser_thankyou.png)

1. Cree un párrafo de teaser para la página de agradecimiento. Select **First** como estrategia e incluir texto que indique que el regalo está en camino.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Cree una campaña con los dos teasers, etiquete uno con la palabra negocio y deje otro sin etiquetar.

## Inserción de contenido en los suscriptores {#pushing-content-to-subscribers}

Impulse cualquier cambio en las páginas a través de la funcionalidad de Newsletter en MCM. A continuación, inserte contenido actualizado en los suscriptores.

Consulte [Envío de boletines](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters).
