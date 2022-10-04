---
title: Recorrido por el sitio web de referencia de la renovación automática de seguros de We.Finance
seo-title: We.Finance Auto Insurance Renewal reference site walkthrough
description: Lea en el tutorial detallado del sitio de referencia del caso de uso de We.Finance Auto Insurance , que muestra cómo AEM formularios y su integración con Microsoft Dynamics ayudan a personalizar la experiencia del cliente en una empresa de servicios financieros.
seo-description: Read on detailed reference site walkthrough of We.Finance Auto Insurance use case which showcases how AEM forms and its integration with Microsoft Dynamics helps personalize customer experience in a financial service company.
uuid: 18676ab4-9f8d-4014-b751-2a722fd152da
contentOwner: dekalra
topic-tags: introduction
discoiquuid: a960d489-f5a3-436a-b028-54292648c7be
exl-id: db416cbc-27a7-4a2c-b4b3-43e8963faf22
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Recorrido por el sitio web de referencia de la renovación automática de seguros de We.Finance {#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## Requisitos previos {#pre-requisites}

Configure el sitio de referencia tal como se describe en [Configuración del sitio de referencia de Forms de AEM 6.4](/help/forms/using/setup-reference-sites.md).

## Situación del sitio de referencia de We.Finance  {#we-finance-reference-site-scenario}

El sitio de We.Finance es un sitio de servicios financieros diseñado para ayudarle a aprender a utilizar las comunicaciones interactivas de AEM Forms.

Lea el tutorial detallado del caso de uso de We.Finance Auto Insurance , que muestra cómo AEM formularios y su integración con Microsoft Dynamics ayudan a personalizar la experiencia del cliente en una empresa de servicios financieros. El tutorial interactivo está diseñado para facilitar la implementación de transacciones digitales complejas y la comunicación con los clientes en una empresa financiera.

**El recorrido comienza con el caso de uso:**

Sarah Rose es una cliente existente de We.Finance y ha adquirido una póliza de seguro de automóvil. Ahora es el momento del año para la renovación de su póliza de seguro. Gloria Rios, Agente de Seguros, We.Finance envía un recordatorio a Sarah sobre su renovación de pólizas. Sarah sigue las instrucciones proporcionadas en el correo electrónico y completa correctamente el proceso.

## Recorrido por aplicación de Seguros Automáticos {#auto-insurance-application-walkthrough}

El escenario de la aplicación de seguros automáticos de We.Finance es una narración visual para el usuario y se basa en dos personalidades:

* Sarah Rose, una cliente de We.Finance
* Gloria Rios, Agente de Seguros, We.Finance

### Gloria envía una comunicación de renovación de pólizas de seguro desde We.Finance {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria inicia sesión en AEM instancia, hace clic en **Renovación del seguro automático,** y luego clics **Abra la interfaz de usuario del agente.** El clic añade un prefijo al documento de seguro con los detalles de la póliza de Sarah Rose. Clics de Gloria **Submit** y se muestra un mensaje en la pantalla &quot;Envío iniciado&quot; y, a continuación, en pocos segundos &quot;Enviado correctamente&quot;.

Sarah recibe un correo electrónico con el asunto &quot;Su renovación automática del seguro&quot;.

![agent_ui_email](assets/agent_ui_email.png)

#### Véalo usted mismo {#see-it-yourself}

Vaya a **Adobe Experience Manager** > **Forms** > **Forms y documentos** > **We.Finance** > **Seguros automáticos**. Seleccione el **Renovación del seguro automático** comunicación interactiva y haga clic en **Abrir la interfaz de usuario del agente**. La comunicación interactiva se abre en la interfaz de usuario del agente. Introduzca una dirección de correo electrónico válida para recibir el correo electrónico con el documento de directiva adjunto y haga clic en Enviar.

Puede acceder a la comunicación interactiva Renovación automática de seguros y revisarla directamente desde `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.`

### Sarah recibe una comunicación de renovación de pólizas de seguro de We.Finance y decide renovar {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah recibe un correo electrónico con un adjunto de We.Finance que le recuerda que su póliza de Seguros Automáticos está a punto de caducar. El archivo adjunto es la versión impresa de su carta de Seguros Automáticos.

Sarah hace clic **Renovar ahora** y se dirige a la versión web de su carta de seguro automático. Además de esta carta, Sarah encuentra la cantidad de días que le quedan para que su política caduque. La página proporciona a Sarah una visión general básica de los detalles de su póliza de seguro, como el número de póliza, el importe vencido y otra información, como ofertas de descuento y recompensas por lealtad. Sarah vuelve a hacer clic **Renovar ahora** en la parte inferior de la directiva.

![ref1](assets/ref1.png)

#### Funcionamiento {#how-it-works}

La salida web y de impresión de su carta de Seguros Automáticos se crean utilizando las capacidades multicanal de Interactive Communications.

El botón Renovar ahora del correo electrónico está vinculado a la aplicación Renovación de seguro automático, que es una comunicación interactiva en una instancia de publicación.

#### Véalo usted mismo {#see-it-yourself-1}

Debe haber recibido un correo electrónico con un PDF adjunto. El PDF es una versión impresa de su carta de Seguros Automáticos. Haga clic en **Renovar ahora** para llegar a la versión web de la directiva. Compruebe su información personal y los detalles de la directiva y haga clic en **Renovar ahora** que le lleva a otra comunicación interactiva.

La variable **Renovar ahora** en el correo electrónico dirige a Sarah a la versión web de la directiva. Puede visitar la siguiente URL:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

Puede consultar el resumen detallado de su Renovación automática de seguros y hacer clic en **Renovar ahora** en la parte inferior de la página.

### Sarah llega a la página de pago {#sarah-reaches-the-payment-page}

We.Finance lleva a Sarah a la página de Pagos. Sarah vuelve a verificar su número de directiva y fecha de caducidad con sus registros. En el lado derecho de la página, verifica el resumen de pago de su renovación con un descuento del 10% sobre la cantidad total.

#### Funcionamiento {#how-it-works-1}

El botón Renovar ahora dirige a Sarah a la página de pago. La página de pago es un formulario adaptable.

#### Véalo usted mismo {#see-it-yourself-2}

Haga clic en **Renovar ahora** para llegar a la página Pago. Rellene la información de la tarjeta de crédito y haga clic en **Realizar pago.**

Puede acceder a la página de pago en la instancia de creación en

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah hace el pago y completa el proceso {#sarah-makes-the-payment-and-completes-the-process}

Sarah rellena sus datos y clics de la tarjeta de crédito **Realizar pago**.

#### Funcionamiento {#how-it-works-2}

Cuando Sarah rellena los detalles de la tarjeta de crédito y hace clic en Enviar, se procesa su pago con tarjeta de crédito y aparece un mensaje de agradecimiento configurado en el formulario adaptable en la pantalla.

#### Véalo usted mismo {#see-it-yourself-3}

Puede ver el mensaje de confirmación después de hacer clic en Realizar pago en

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
