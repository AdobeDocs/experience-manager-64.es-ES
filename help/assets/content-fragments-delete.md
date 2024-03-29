---
title: 'Fragmentos de contenido: Eliminar consideraciones'
seo-title: Content Fragments - Delete Considerations
description: 'Fragmentos de contenido: Eliminar consideraciones'
seo-description: Content Fragments - Delete Considerations
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Content Fragments
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 71%

---

# Fragmentos de contenido: Eliminar consideraciones {#content-fragments-delete-considerations}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>Algunas funciones de fragmento de contenido requieren la aplicación de [AEM 6.4 Service Pack 2 (6.4.2.0) o posterior](/help/release-notes/sp-release-notes.md).

## Permisos: Eliminar o no eliminar {#permissions-delete-or-not-delete}

La capacidad para eliminar contenido es potente, pero potencialmente sensible, y muchas industrias necesitan restringir y controlar cómo se distribuyen estos privilegios.

Con respecto a los permisos de eliminación, los fragmentos de contenido deben considerarse en dos niveles:

1. **El fragmento de contenido como una sola entidad.**

   * **Caso de uso**: un usuario que necesita editar/actualizar un fragmento de contenido: **y eliminar un fragmento completo**.
   * **Permisos**[](/help/sites-administering/security.md#actions)[: el permiso Eliminar se puede asignar a través de Administración de usuarios o grupos](/help/sites-administering/security.md#managing-permissions).

1. **Las diversas subentidades que conforman un fragmento de contenido; por ejemplo, variaciones, subnodos.**

   La operación básica del editor de fragmentos de contenido requiere que se puedan eliminar estos subelementos transitorios. Por ejemplo, al manipular variaciones; también al editar metadatos o administrar contenido asociado.

   * **Caso de uso**: un usuario que necesita editar/actualizar un fragmento de contenido: **sin permitir eliminar un fragmento completo**.
   * **Permisos**: consulte [Permisos necesarios para la funcionalidad del editor únicamente](content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Cuando un usuario no tiene [Eliminar](/help/sites-administering/security.md#actions) permisos, el editor de fragmentos de contenido funciona en *solo lectura* en el menú contextual.

>[!NOTE]
>
>Consulte también [Cómo auditar las operaciones de administración de usuarios en AEM](/help/sites-administering/audit-user-management-operations.md).

## Permisos necesarios para la funcionalidad del editor únicamente {#permissions-required-for-editor-functionality-only}

Para los usuarios que necesiten editar o actualizar un fragmento de contenido, **sin permitirles eliminar un fragmento completo**, se deben asignar permisos específicos, ya que la operación básica del editor de fragmentos de contenido requiere que se puedan eliminar subelementos transitorios.

Por ejemplo, al manipular variaciones; también al editar metadatos o administrar contenido asociado.

>[!NOTE]
>
>Los permisos de eliminación, necesarios para editar o actualizar un fragmento de contenido, se incluyen en el permiso de eliminación [asignado a través de Administración de usuarios o grupos](/help/sites-administering/security.md#managing-permissions).

Los permisos necesarios para editar o actualizar un fragmento deben aplicarse al nodo que contiene el fragmento de contenido o a un nodo principal adecuado (en cualquier nivel de `/content/dam`). Cuando se asigna a un nodo principal de este tipo, los permisos se aplican a todos los nodos dentro de esa rama.

Por ejemplo, una carpeta que contendrá todos los fragmentos de contenido, como:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Configuración de permisos en `/content/dam` también es posible, ya que todos los fragmentos de contenido se almacenan aquí.
>
>Sin embargo, esta acción se aplica a los mismos permisos de eliminación a *todos* los demás tipos de recursos también.

Los permisos previos para permitir que un usuario o grupo específico edite o actualice un fragmento de contenido son los siguientes:

>[!NOTE]
>
>Esta lista muestra todos los privilegios necesarios, no solo los de eliminación.

* Para los nodos o carpetas del fragmento de contenido:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Para la variable `jcr:content`nodo de todos los fragmentos de contenido:

   * `jcr:addChildNodes`, `jcr:modifyProperties` y `jcr:removeChildNodes`

* Para todos los nodos siguientes `jcr:content` de todos los fragmentos de contenido:

   * `jcr:addChildNodes`, `jcr:modifyProperties` y `jcr:removeChildNodes`, `jcr:removeNode`

Estos `remove` los privilegios deben [administradas mediante Listas de control de acceso, dentro del CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management).

La variable `add` y `modify` los privilegios de también se pueden administrar en CRXDE Lite o mediante la consola Administración de usuarios .

Por ejemplo, la definición de la variable `remove` privilegios para un grupo `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
