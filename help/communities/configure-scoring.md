---
title: Esenciales de puntuación y distintivos
seo-title: Esenciales de puntuación y distintivos
description: Descripción general de la función Puntuación y distintivos
seo-description: Descripción general de la función Puntuación y distintivos
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 1%

---


# Esenciales de puntuación y distintivos {#scoring-and-badges-essentials}

La función de puntuación y distintivos de AEM Communities permite identificar y premiar a los miembros de la comunidad.

Los detalles de la configuración de la función se describen en

* [Puntuación y distintivos de comunidades](implementing-scoring.md)

Esta página contiene detalles técnicos adicionales:

* Cómo [mostrar un distintivo](#displaying-badges) como imagen o texto
* Cómo activar el registro extenso [de depuración](#debug-log-for-scoring-and-badging)
* Cómo [acceder a UGC](#ugc-for-scoring-and-badging) relacionado con la puntuación y la insignia

>[!CAUTION]
>
>La estructura de implementación visible en el CRXDE Lite está sujeta a cambios.

## Visualización de distintivos {#displaying-badges}

Indica si un distintivo se muestra como texto o como imagen y se controla en el lado del cliente en la plantilla HBS.

Por ejemplo, busque `this.isAssigned` en `/libs/social/forum/components/hbs/topic/list-item.hbs`,:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

Si es true, isAssigned indica que el distintivo se asignó a una función y que el distintivo debe mostrarse como texto.

Si es false, is Assigned indica que el distintivo se ha concedido para una puntuación ganada y que el distintivo debe mostrarse como una imagen.

Cualquier cambio en este comportamiento se debe realizar en una secuencia de comandos personalizada (ya sea sobrescribir o superponer). Consulte [Personalización del cliente](client-customize.md).

## Registro de depuración para Puntuación e Insignia {#debug-log-for-scoring-and-badging}

Para ayudar a depurar la puntuación y el distintivo, se puede configurar un archivo de registro personalizado. El contenido de este archivo de registro se puede proporcionar a la asistencia al cliente si se producen problemas con la función.

Para obtener instrucciones detalladas, visite [Crear un archivo de registro personalizado](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

Para configurar rápidamente un archivo de registro de inclinación:

1. Acceda a la **[!UICONTROL Compatibilidad con el registro de la consola web de Adobe Experience Manager]**, por ejemplo

   * http://localhost:4502/system/console/slinglog

1. Seleccione **[!UICONTROL Añadir nuevo registrador]**

   1. Seleccione `DEBUG` para **[!UICONTROL Nivel de registro]**
   1. Escriba un nombre para **[!UICONTROL Archivo de registro]**, por ejemplo

      * logs/scoring-debug.log
   1. Introduzca dos entradas **[!UICONTROL Logger]** (clase) (con el icono `+`)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Seleccione **[!UICONTROL Guardar]**



![chlimage_1-247](assets/chlimage_1-248.png)

Para ver las entradas de registro:

* Desde la consola web

   * En el menú **[!UICONTROL Estado]**
   * Seleccione **[!UICONTROL Archivos de registro]**
   * Busque el nombre del archivo de registro, como `scoring-debug`

* En el disco local del servidor

   * El archivo de registro se encuentra en &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log.
   * Por ejemplo, `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC para Puntuación e Insignia {#ugc-for-scoring-and-badging}

Es posible realizar una vista del UGC en relación con la puntuación y la insignia cuando el SRP elegido sea JSRP o MSRP, pero no ASRP. (Si no está familiarizado con estos términos, consulte [Almacenamiento de contenido de la comunidad](working-with-srp.md) y [Información general del proveedor de recursos de Almacenamiento](srp.md)).

Las descripciones para acceder a los datos de puntuación y marca utilizan JSRP, ya que el UGC es fácilmente accesible mediante [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

**JSRP del autor**: experimentar en el entorno del autor resulta en UGC que solo es visible desde el entorno del autor.

**JSRP al publicar**: del mismo modo, si realiza pruebas en el entorno de publicación, será necesario acceder a CRXDE Lite con privilegios de administrador en una instancia de publicación. Si la instancia de publicación se está ejecutando en [modo de producción](../../help/sites-administering/production-ready.md) (nosamplecontent runmode), será necesario [habilitar CRXDE Lite](../../help/sites-administering/enabling-crxde-lite.md).

La ubicación base de UGC en JSRP es `/content/usergenerated/asi/jcr/`.

### API de Puntuación y Badging {#scoring-and-badging-apis}

Las siguientes API están disponibles para su uso:

* [com.adobe.cq.so.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.so.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Los últimos Javadocs para las [versiones](deploy-communities.md#LatestReleases) instaladas están disponibles para los desarrolladores desde el repositorio de Adobe. Consulte [Uso de Maven para comunidades: Javadocs](maven.md#javadocs).

**La ubicación y el formato del UGC en el repositorio están sujetos a cambios sin previo aviso**.

### Ejemplo de configuración {#example-setup}

Las capturas de pantalla de los datos del repositorio provienen de la configuración de la puntuación y la identificación para un foro en dos sitios de AEM diferentes:

1. Un sitio AEM con un identificador único (sitio de comunidad creado mediante un asistente):

   * Uso del sitio Tutorial de introducción (participación) creado durante el [tutorial de introducción](getting-started.md)
   * Localizar el nodo de la página del foro

      * `/content/sites/engage/en/forum/jcr:content`
   * Añadir las propiedades de puntuación y marca

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * Localización del nodo del componente del foro

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Añadir propiedad para mostrar distintivos

      * `allowBadges = true`
   * Un usuario inicia sesión, crea un tema del foro y recibe una insignia de bronce





1. Un sitio AEM *sin* un identificador único:

   * Uso de la guía [Community Components](components-guide.md)
   * Localizar el nodo de la página del foro

      * `/content/community-components/en/forum/jcr:content`
   * Añadir las propiedades de puntuación y marca

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * Localización del nodo del componente del foro

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Añadir propiedad para mostrar distintivos

      * `allowBadges = true`
   * Un usuario inicia sesión, crea un tema del foro y recibe una insignia de bronce




1. A un usuario se le asigna una insignia de moderador mediante cURL:

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Como un usuario ha obtenido dos insignias de bronce y ha recibido una insignia de moderador, así es como aparece el usuario con su entrada en el foro:

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>Este ejemplo no sigue estas optimizaciones:
>
>* los nombres de las reglas de puntuación deben ser globalmente únicos; no deben terminar con el mismo nombre.\
   >  Un ejemplo de lo que *no* debe hacer:\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
   >
   >
* creación de imágenes de distintivo únicas para distintos sitios de AEM

>



### Acceso a UGC de Puntuación {#access-scoring-ugc}

Se prefiere el uso de las [API](#scoring-and-badging-apis).

Para fines de investigación, con JSRP por ejemplo, la carpeta base que contiene puntuaciones es

* `/content/usergenerated/asi/jcr/scoring`

El nodo secundario de `scoring`es el nombre de la regla de puntuación. Por lo tanto, una práctica recomendada es que los nombres de las reglas de puntuación en un servidor sean globalmente únicos.

Para el sitio de participación en la Geometrixx, el usuario y su puntuación se encuentran en una ruta con el nombre de la regla de puntuación, la identificación del sitio de la comunidad ( `engage-ba81p`), una identificación única y la identificación del usuario:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Para el sitio de la guía de componentes de comunidad, el usuario y su puntuación se encuentran en una ruta construida con el nombre de la regla de puntuación, una identificación predeterminada ( `default-site`), una identificación única y la identificación del usuario:

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

La puntuación se almacena en la propiedad `scoreValue_tl`, que puede contener un valor directamente o hacer referencia indirectamente a atomicCounter.

![chlimage_1-251](assets/chlimage_1-251.png)

### Acceso a la insignia UGC {#access-badging-ugc}

Se prefiere el uso de las [API](#scoring-and-badging-apis).

Para fines de investigación, con JSRP por ejemplo, la carpeta base que contiene información sobre las insignias asignadas o adjudicadas es

* /content/usergenerate/asi/jcr

Seguido de la ruta al perfil del usuario, finalizando en una carpeta de distintivos, como

* /home/users/community/w271OOup2Z4DjnOQrviv/perfil/badges

#### Insignia otorgada {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### distintivo asignado {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Información adicional {#additional-information}

Para mostrar una lista ordenada de miembros basada en puntos:

* [Función de ](functions.md#leaderboard-function) tabla de clasificación para incluirla en un sitio de comunidad o en una plantilla de grupo.
* [Componente](enabling-leaderboard.md) de tabla de clasificación, el componente destacado de la función Mesa de clasificación, para la creación de páginas.

