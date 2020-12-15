---
title: 'Fragmentos de contenido: Eliminar consideraciones'
seo-title: 'Fragmentos de contenido: Eliminar consideraciones'
description: 'Fragmentos de contenido: Eliminar consideraciones'
seo-description: 'Fragmentos de contenido: Eliminar consideraciones'
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: aheimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
translation-type: tm+mt
source-git-commit: 3fa80e73fb6e9400fbeba29d80aa57e080b6f333
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 12%

---


# Fragmentos de contenido: Eliminar consideraciones {#content-fragments-delete-considerations}

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](/help/release-notes/sp-release-notes.md).

## Permisos - Eliminar o No eliminar {#permissions-delete-or-not-delete}

La capacidad para eliminar contenido es poderosa, pero potencialmente sensible, y muchas industrias necesitan restringir y controlar cómo se distribuyen estos privilegios.

Con respecto a los permisos de eliminación, los fragmentos de contenido deben considerarse en dos niveles:

1. **Fragmento de contenido como una sola entidad.**

   * **Caso** de uso: Usuario que necesita editar/actualizar un fragmento de contenido  **y eliminar un fragmento** completo.
   * **Permisos**: El  [](/help/sites-administering/security.md#actions) permiso Eliminar se puede  [asignar a través de Administración de usuarios y/o grupos](/help/sites-administering/security.md#managing-permissions).

1. **Las varias subentidades que conforman un fragmento de contenido; por ejemplo, variaciones, subnodos.**

   El funcionamiento básico del editor de fragmentos de contenido requiere que se puedan eliminar estos subelementos transitorios. Por ejemplo, al manipular variaciones; también al editar metadatos o administrar el contenido asociado.

   * **Caso** de uso: Usuario que necesita editar/actualizar un fragmento de contenido  **sin tener permiso para eliminar un fragmento** completo.
   * **Permisos**: Consulte  [Permisos requeridos solo](content-fragments-delete.md#permissions-required-for-editor-functionality-only) para la funcionalidad del editor.

>[!NOTE]
>
>Cuando un usuario no tiene permisos [Delete](/help/sites-administering/security.md#actions), el editor de fragmentos de contenido funciona en modo *de sólo lectura*.

>[!NOTE]
>
>Consulte también [Cómo auditar las operaciones de administración de usuarios en AEM](/help/sites-administering/audit-user-management-operations.md).

## Permisos requeridos para la funcionalidad del editor solamente {#permissions-required-for-editor-functionality-only}

Para los usuarios que necesiten editar o actualizar un fragmento de contenido, **sin permitirles eliminar un fragmento completo**, se deben asignar permisos específicos, ya que la operación básica del editor de fragmentos de contenido requiere que se puedan eliminar subelementos transitorios.

Por ejemplo, al manipular variaciones; también al editar metadatos o administrar el contenido asociado.

>[!NOTE]
>
>Los permisos de eliminación, necesarios para editar o actualizar un fragmento de contenido, se incluyen en el permiso de eliminación [asignado a través de Administración de usuarios y/o grupos](/help/sites-administering/security.md#managing-permissions).

Los permisos necesarios para editar o actualizar un fragmento deben aplicarse al nodo que contiene el fragmento de contenido o a un nodo principal adecuado (en cualquier nivel en `/content/dam`). Cuando se asignan a dicho nodo principal, los permisos se aplicarán a todos los nodos de esa rama.

Por ejemplo, una carpeta que contendrá todos los fragmentos de contenido, como:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>También es posible establecer los permisos en `/content/dam`, ya que todos los fragmentos de contenido se almacenan aquí.
>
>Sin embargo, esta acción también aplica los mismos permisos de eliminación a *todos* otros tipos de recursos.

Los requisitos previos de permisos para permitir que un usuario o grupo específico edite o actualice un fragmento de contenido son:

>[!NOTE]
>
>Esta lista muestra todos los privilegios requeridos, no solo los privilegios de eliminación.

* Para los nodos o carpetas del fragmento de contenido:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Para el nodo `jcr:content` de todos los fragmentos de contenido:

   * `jcr:addChildNodes`,  `jcr:modifyProperties` y  `jcr:removeChildNodes`

* Para todos los nodos por debajo de `jcr:content` de todos los fragmentos de contenido:

   * `jcr:addChildNodes`,  `jcr:modifyProperties` y  `jcr:removeChildNodes`,  `jcr:removeNode`

Estos `remove` privilegios deben [administrarse usando Listas de Control de acceso, dentro de CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

Los privilegios `add` y `modify` también se pueden administrar en CRXDE Lite o mediante la consola Administración de usuarios.

Por ejemplo, la definición de los privilegios `remove` para un grupo `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)

