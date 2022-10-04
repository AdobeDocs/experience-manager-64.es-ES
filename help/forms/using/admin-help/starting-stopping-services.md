---
title: Inicio y parada de servicios
seo-title: Starting and stopping services
description: Obtenga información sobre cómo iniciar y detener servicios asociados con módulos AEM Forms y el servidor de aplicaciones y la base de datos.
seo-description: Learn how to start and stop services associated with AEM Forms modules and the application server and database.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
exl-id: 6e0607d6-171c-4119-95a1-373b30fb63c1
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Inicio y parada de servicios {#starting-and-stopping-services}

Existen dos tipos de servicios que forman parte de AEM formularios:

* Servicios que controlan el servidor de aplicaciones de formularios AEM y la base de datos.
* Servicios que controlan módulos de formularios AEM

## Iniciar o detener los servicios asociados con AEM módulos de formularios {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM módulos de formularios (por ejemplo, Forms, Rights Management, Output) funcionan como servicios. A veces, es posible que necesite detener o iniciar los servicios para estos módulos de formularios AEM. Por ejemplo, debe detener y, a continuación, reiniciar un servicio de formularios AEM después de cambiar una configuración para el servicio.

1. En la consola de administración, haga clic en **Servicios** > **Aplicaciones y servicios** > **Administración de servicios**.
1. En la página Administración de servicios, active la casilla situada junto al servicio que desea detener o iniciar y haga clic en Detener o Iniciar.

## Iniciar o detener servicios para el servidor de aplicaciones y la base de datos {#start-or-stop-services-for-the-application-server-and-database}

Una implementación completa de AEM formularios incluye un servidor de aplicaciones y servicios de base de datos:

* *`[application server]`* para formularios AEM
* *`[database]`* para formularios AEM

En Windows, se puede acceder a estos servicios a través del **Herramientas administrativas** > **Panel Servicios**. Por ejemplo, si ha instalado AEM formularios en JBoss mediante el método llave en mano, verá los siguientes servicios disponibles en su sistema:

* JBoss para formularios Adobe Experience Manager
* Formularios de MySQL para Adobe Experience Manager

Para iniciar o detener estos servicios, selecciónelos en la lista del panel Servicios y haga clic en el botón de acción correspondiente del panel.

En UNIX® o Linux, escriba el siguiente texto desde una línea de comandos, donde *`[service name]`* es el nombre del servicio que está verificando:

```as3
     ps -A | grep [service name]
```
