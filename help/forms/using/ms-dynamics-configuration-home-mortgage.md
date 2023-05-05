---
title: Configurar Microsoft Dynamics 365 para el flujo de trabajo de la hipoteca de vivienda del sitio de referencia We.Finance
seo-title: Configure Microsoft Dynamics 365 for the home mortgage workflow of the We.Finance reference site
description: Aprenda a aprovechar los servicios de Microsoft® Dynamics 365 mediante formularios adaptables en el flujo de trabajo de las hipotecas del sitio de referencia de We.Finance
seo-description: Learn how to leverage the Microsoft® Dynamics 365 services through adaptive forms for the home mortgage workflow of the We.Finance Reference site
uuid: a0656d90-84c7-46d1-9a16-dadcc19ff9ef
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: develop, Configuration
discoiquuid: 6b31397a-fb06-4043-9368-59fb4fce8afa
exl-id: 7e1f417e-6a6b-4ef2-a453-866331fe3e96
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 83%

---

# Configurar Microsoft Dynamics 365 para el flujo de trabajo de la hipoteca de vivienda del sitio de referencia We.Finance {#configure-microsoft-dynamics-for-the-home-mortgage-workflow-of-the-we-finance-reference-site}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Aprenda a aprovechar los servicios de Microsoft® Dynamics 365 mediante formularios adaptables en el flujo de trabajo de las hipotecas del sitio de referencia de We.Finance

## Información general {#overview}

Microsoft® Dynamics 365 es un software de gestión de relaciones con el cliente (CRM) y planificación de recursos empresariales (ERP) que proporciona soluciones empresariales para crear y administrar cuentas de cliente, contactos, posibles clientes, oportunidades y casos.

AEM Forms proporciona un servicio en la nube para integrar Dynamics 365 con el módulo [Integración de datos de Forms](/help/forms/using/data-integration.md). El escenario [Recorrido por la aplicación Hogar Mortgage con Microsoft® Dynamics](/help/forms/using/finance-reference-site-walkthrough.md#home-mortgage-application-walkthrough-with-microsoft-dynamics) muestra cómo un cliente utiliza el sitio de referencia de We.Finance para solicitar un préstamo cuando el sitio utiliza Microsoft® Dynamics para la integración de datos de Forms. Antes de poder usar el tutorial de la solicitud de hipoteca con el escenario de Microsoft® Dynamics, debe configurar Microsoft® Dynamics 365 para utilizarlo con el sitio de referencia de We.Finance.

## Requisitos previos {#prerequisites}

Antes de comenzar a configurar Dynamics 365, asegúrese de que dispone de lo siguiente:

* [Configuración de sitios de referencia de AEM Forms](/help/forms/using/setup-reference-sites.md).

* AEM 6.3 Forms Service Pack 1 y versiones posteriores
* Una cuenta de Microsoft® Dynamics 365
* La aplicación registrada del servicio de Dynamics 365 con Microsoft® Azure Active Directory
* El ID de y el secreto de cliente de la aplicación registrada

## Vinculación del simulador de hipoteca con la página de inicio del sitio {#link-the-home-mortgage-calculator-with-your-site-home-page}

1. En la instancia de autor, vaya a la siguiente página:

   https://[servidor]:[puerto]/editor.html/content/we-finance/global/en/loan-landing-page.html

1. Desplácese hacia abajo hasta el simulador de hipoteca.
1. Resalte el panel de la columna derecha (simulador) y pulse en él para mostrar el menú emergente. En el menú emergente, pulse Configurar. Se abre el cuadro de diálogo Editar contenedor de AEM Forms.

   ![panel_configuración_simulador](assets/calculatorconfigurepanel.png)

1. En el cuadro de diálogo Editar contenedor de AEM Forms, busque la ruta del recurso, seleccione el simulador de hipoteca en la siguiente ruta y pulse **Confirmar**:

   formsanddocuments/We.Finance/MS Dynamics/

   ![selección_ruta_del_recurso](assets/selectassetpath.png)

1. Pulse **Listo**.
1. Publique la página editada.

   >[!NOTE]
   >
   >El enlace de los campos del simulador con el FDM está preconfigurado a través del paquete del sitio de referencia de We.Finance. Para ver el enlace, puede abrir el formulario en el modo Autor y ver las referencias de enlace de campo.

1. Para crear una entidad personalizada para almacenar el registro de solicitantes de la solicitud de hipoteca, importe el paquete de la solución AEMFormsFSIRefsite_1_0.zip en la instancia de Microsoft® Dynamics:

   1. Descargue el paquete desde la siguiente ubicación:

      `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip`

   1. Importe el paquete de la solución en la instancia de Microsoft® Dynamics. En la instancia de Microsoft® Dynamics, vaya a **Configuración** > **Soluciones** y, a continuación, toque **Importar**.

1. Para configurar los detalles de contacto del usuario utilizados en el sitio de referencia, importe el paquete Sarah Rose Contact.CSV en su instancia de Microsoft® Dynamics:

   1. Descargue el paquete desde la siguiente ubicación:

      `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

   1. Importe el paquete en la instancia de Microsoft® Dynamics. En la instancia de Microsoft® Dynamics, vaya a **Ventas** > **Contactos** y, a continuación, toque **Importar datos**.
