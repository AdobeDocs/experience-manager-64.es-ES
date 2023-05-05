---
title: NO PUBLICAR Interfaz de usuario basada en funciones en Gestión de Correspondencia
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: NO PUBLICAR Interfaz de usuario basada en funciones en Gestión de Correspondencia
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 1%

---


# NO PUBLICAR Interfaz de usuario basada en funciones en Gestión de Correspondencia {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En AEM, el administrador puede proporcionar acceso basado en funciones a diferentes grupos de usuarios que realizan diversas acciones en distintos recursos. Por ejemplo, la funcionalidad para crear o editar diccionarios de datos solo podría estar disponible para los usuarios de un grupo de usuarios específico, mientras que otros usuarios solo podrían ver y utilizar los diccionarios de datos.

La interfaz de AEM muestra las opciones, como crear o editar un tipo de recurso, según el nivel de acceso del usuario. Por ejemplo, si un usuario no tiene los permisos para crear un diccionario de datos, la opción para crear un diccionario de datos no aparece en la interfaz de usuario.

Aunque CRX le permite configurar los derechos de acceso para las cuentas de usuario y de grupo, este artículo trata sobre los derechos de acceso basados en roles o grupos de usuarios.

Para obtener más información sobre grupos, permisos, listas de control de acceso y administración de usuarios y grupos, consulte [Administración de usuarios y seguridad](/help/sites-administering/security.md).

## Administración de permisos {#managing-permissions}

1. Asegúrese de que el usuario para el que desea administrar los permisos se agrega al grupo de usuarios correspondiente.

   Por ejemplo, el usuario John Doe se agrega a los grupos `agents` y `cm-creditcard`. Para obtener más información, consulte Adición de usuarios o grupos a un grupo. Para obtener más información, consulte [Administración de usuarios y grupos de usuarios](/help/communities/users.md).

   ![]()

1. Cree las carpetas según corresponda para permitir los permisos deseados.

   Por ejemplo, si una empresa tiene divisiones de hipotecas, tarjetas de crédito y seguros, puede crear carpetas con nombres `HomeMortgage`, `CreditCard,`y `Insurance` mantener los activos pertinentes y dar acceso selectivamente a los agentes para los activos pertinentes para sus departamentos solamente.

1. Para acceder AEM seguridad de WCM, realice una de las siguientes acciones:

   1. En la pantalla de bienvenida o en varias ubicaciones de AEM, haga clic en el icono de seguridad:

   1. Vaya directamente a `https://[server]:[port]/useradmin`. Asegúrese de iniciar sesión en AEM como administrador.

      ![]()
   El árbol de la izquierda enumera todos los usuarios y grupos que hay actualmente en el sistema. Puede seleccionar las columnas que desea mostrar, ordenar el contenido de las columnas e incluso cambiar el orden en que se muestran arrastrando el encabezado de la columna a una nueva posición.

   Las pestañas proporcionan acceso a varias configuraciones:

1. En la lista del árbol de la izquierda, pulse dos veces el nombre del grupo correspondiente y, a continuación, seleccione la pestaña Permisos .

   Para localizar el nombre del grupo, puede escribir el nombre del grupo en el espacio proporcionado.

1. En la pestaña permisos , vaya a la ruta a la que desee agregar permisos. Las carpetas de Administración de correspondencia se encuentran en la sección `content/apps/cm/` carpeta.

   Seleccione la casilla de verificación de la columna Miembro para los miembros que desea que tengan permisos para esa ruta. Desactive la casilla de verificación del miembro para el que desea eliminar los permisos. Aparece un triángulo rojo en la celda a la que ha realizado cambios.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Los permisos especificados en una carpeta reemplazan a los permisos especificados en sus subcarpetas.

1. Pulse Guardar.
1. Texto de paso
1. Texto de paso
1. Texto de paso

