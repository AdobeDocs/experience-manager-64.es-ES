---
title: Administración programática de los nodos Preferences
seo-title: Programmatically managing the PreferencesNodes
description: Utilice la API de servicio del Administrador de preferencias (Java) para administrar mediante programación los nodos de preferencias.
seo-description: Use the Preferences Manager Service API (Java) to programmatically manage the Preferences Nodes.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: d580b32c-a344-4a8c-bd61-0949da76d981
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 4%

---

# Administración programática de los nodos de preferencias {#programmatically-managing-the-preferencesnodes}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En este tema se describe cómo utilizar la API de servicio de Administrador de preferencias (Java) para administrar mediante programación los nodos de preferencias.

Puede cambiar manualmente los ajustes de configuración desde la interfaz de usuario del administrador. Para cambiar las opciones, vaya a `Home>Settings>User Management> Configuration>Manual Configuration`. Importar `config.xml` después de realizar los cambios, observará que todos los cambios excepto los realizados en el nodo `/Adobe/Adobe Experience Manager Forms/Config/UM persist` se pierden. La vista previa de Importación y exportación de administración de usuarios no admite el cambio de los ajustes de configuración de otros componentes. Ahora, estos cambios se pueden realizar utilizando `PreferencesManagerServiceClient` API.

**Resumen de los pasos** Para administrar mediante programación los nodos de preferencias, realice los pasos siguientes:

1. Incluir archivos de proyecto.
1. Crear un cliente PreferencesManagerService
1. Invocar la función adecuada o las operaciones de permisos

**Incluir archivos de proyecto**

Incluya los archivos necesarios en el proyecto de desarrollo. Si está creando una aplicación cliente utilizando Java, incluya los archivos JAR necesarios. Si utiliza servicios web, asegúrese de incluir los archivos proxy.

**Crear un cliente PreferencesManagerService**

Para poder realizar mediante programación una operación User Management PreferencesManagerService, debe crear un cliente PreferencesManagerService. Con la API de Java, esto se consigue creando un objeto PreferencesManagerServiceClient .

**Invocar la función adecuada o las operaciones de permisos**

Una vez creado el cliente de servicio, puede invocar las operaciones del Administrador de preferencias. El cliente de servicio le permite leer y establecer permisos.
