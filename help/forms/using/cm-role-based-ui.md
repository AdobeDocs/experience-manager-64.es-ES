---
title: NO PUBLICAR la interfaz de usuario basada en roles en la administración de correspondencias
seo-title: NO PUBLICAR la interfaz de usuario basada en roles en la administración de correspondencias
description: nulo
seo-description: nulo
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 1%

---


# NO PUBLICAR la interfaz de usuario basada en roles en la administración de correspondencias {#do-not-publish-role-based-user-interface-in-correspondence-management}

En AEM, el administrador puede proporcionar acceso basado en roles a diferentes grupos de usuarios que realizan diversas acciones en diferentes recursos. Por ejemplo, la funcionalidad para crear o editar diccionarios de datos solo podía estar disponible para los usuarios de un grupo de usuarios específico, mientras que otros usuarios solo podían vista y usar los diccionarios de datos.

La interfaz de AEM muestra las opciones, como crear o editar un tipo de recurso, según el nivel de acceso del usuario. Por ejemplo, si un usuario no tiene permisos para crear un diccionario de datos, la opción para crear un diccionario de datos no aparece en la interfaz de usuario.

Aunque CRX le permite configurar los derechos de acceso tanto para las cuentas de usuario como de grupo, este artículo trata sobre los derechos de acceso basados en roles o grupos de usuarios.

Para obtener más información sobre grupos, permisos, listas de control de acceso y administración de usuarios y grupos, consulte [Administración de usuarios y seguridad](/help/sites-administering/security.md).

## Administración de permisos {#managing-permissions}

1. Asegúrese de que el usuario para el que desea administrar los permisos se agrega al grupo de usuarios correspondiente.

   Por ejemplo, el usuario John Doe se agrega a los grupos `agents` y `cm-creditcard`. Para obtener más información, consulte Añadir usuarios o grupos en un grupo. Para obtener más información, consulte [Administración de usuarios y grupos de usuarios](/help/communities/users.md).

   ![]()

1. Cree las carpetas según convenga para permitir los permisos deseados.

   Por ejemplo: si una empresa tiene divisiones de hipoteca, tarjeta de crédito y seguros, puede crear carpetas con los nombres `HomeMortgage`, `CreditCard,`y `Insurance` para mantener los activos relevantes y dar acceso selectivo a los agentes para los activos relevantes sólo para sus departamentos.

1. Para acceder a AEM seguridad de WCM, realice una de las siguientes acciones:

   1. En la pantalla de bienvenida o en varias ubicaciones de AEM, haga clic en el icono de seguridad:

   1. Navegue directamente a `https://[server]:[port]/useradmin`. Asegúrese de iniciar sesión en AEM como administrador.

      ![]()
   El árbol izquierdo lista a todos los usuarios y grupos que están actualmente en el sistema. Puede seleccionar las columnas que desee mostrar, ordenar el contenido de las columnas e incluso cambiar el orden en que se muestran las columnas arrastrando el encabezado de columna a una nueva posición.

   Las fichas proporcionan acceso a varias configuraciones:

1. En la lista de árbol de la izquierda, toque con el doble el nombre del grupo correspondiente y, a continuación, seleccione la ficha Permisos.

   Para localizar el nombre del grupo, puede escribir el nombre del grupo en el espacio proporcionado.

1. En la ficha Permisos, desplácese a la ruta a la que desee agregar permisos. Las carpetas de Correspondence Management se encuentran en la carpeta `content/apps/cm/`.

   Seleccione la casilla de verificación en la columna Miembro para los miembros que desee que tengan permisos en esa ruta. Desactive la casilla de verificación del miembro para el que desea quitar permisos. Aparece un triángulo rojo en la celda en la que ha realizado cambios.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Los permisos especificados en una carpeta sustituyen a los permisos especificados en sus subcarpetas.

1. Toque Guardar.
1. Texto del paso
1. Texto del paso
1. Texto del paso

