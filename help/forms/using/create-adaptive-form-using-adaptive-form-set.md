---
title: Crear un formulario adaptable mediante un conjunto de formularios adaptables
seo-title: Create an adaptive form using a set of adaptive forms
description: Con AEM Forms, puede juntar formularios adaptables para crear un único formulario de gran tamaño y comprender sus características.
seo-description: With AEM Forms, bring adaptive forms together to author a single large adaptive form, and understand its features.
uuid: 1423038b-8261-455b-b4ff-7be7222448c9
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 75ee94f7-e939-409b-b8cb-8fdc3f79bb63
feature: Adaptive Forms
exl-id: 969b0c11-adc7-476e-8c82-d444fccba984
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 95%

---

# Crear un formulario adaptable mediante un conjunto de formularios adaptables {#create-an-adaptive-form-using-a-set-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Información general {#overview}

En un flujo de trabajo, como una aplicación para abrir una cuenta bancaria, los usuarios rellenan varios formularios. En lugar de pedirles que rellenen un conjunto de formularios, puede apilarlos y crear un formulario grande (formulario principal). Cuando se agrega un formulario adaptable al formulario más grande, se agrega como panel (formulario secundario). Se agrega un conjunto de formularios secundarios para crear un formulario principal. Puede mostrar u ocultar paneles basados en los datos introducidos por el usuario. Los botones del formulario principal, como enviar y restablecer, sobrescriben los botones del formulario secundario. Para agregar un formulario adaptable al formulario principal, puede arrastrar y soltar el formulario adaptable desde el explorador de recursos (como los fragmentos de formulario adaptables).

Las funciones disponibles son las siguientes:

* Creación independiente
* Mostrar u ocultar los formularios adecuados
* Carga diferida

Las características como la creación independiente y la carga diferida proporcionan mejoras de rendimiento con respecto al uso de componentes individuales para crear el formulario principal.

>[!NOTE]
>
>No se pueden usar fragmentos o formularios adaptables basados en XFA como formularios secundarios o principales.

## Entre bastidores {#behind-the-scenes}

Se pueden agregar fragmentos y formularios adaptables basados en XSD en el formulario principal. La estructura del formulario principal es la misma que [cualquier formulario adaptable](/help/forms/using/prepopulate-adaptive-form-fields.md). Cuando se agrega un formulario adaptable como formulario secundario, se agrega como panel en el formulario principal. Los datos de un formulario secundario enlazado se almacenan en la sección `data` raíz de la sección `afBoundData` del esquema XML del formulario principal.

Por ejemplo, los clientes rellenan un formulario de solicitud. Los dos primeros campos del formulario son nombre e identidad. Su XML es:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
        </data>
    </afBoundData>
</afData>
```

Agrega otro formulario en la aplicación que permite a los clientes rellenar la dirección de su oficina. La raíz del esquema del formulario secundario es `officeAddress`. Aplique `bindref` `/application/officeAddress` o `/officeAddress`. Si no se proporciona `bindref`, el formulario secundario se agregará como `officeAddress` árbol secundario. Consulte el XML del siguiente formulario:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
        </data>
    </afBoundData>
</afData>
```

Si inserta otro formulario que permita a los clientes proporcionar la dirección de casa, aplique `bindref` `/application/houseAddress or /houseAddress.`El XML tiene el siguiente aspecto:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
            <houseAddress>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </houseAddress>
        </data>
    </afBoundData>
</afData>
```

Si desea mantener el mismo nombre de subraíz que la raíz del esquema (`Address` en este ejemplo), utilice archivos bindrefs indexados.

Por ejemplo, aplique bindrefs `/application/address[1]` o `/address[1]` y `/application/address[2]` o `/address[2]`. El XML del formulario es:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <address>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
            <address>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
        </data>
    </afBoundData>
</afData>
```

Puede cambiar el árbol secundario predeterminado del formulario o fragmento adaptable con la propiedad `bindRef`. La propiedad `bindRef` permite especificar la ruta que señala a una ubicación en la estructura de árbol del esquema XML.

Si el formulario secundario es independiente, sus datos se almacenan en la sección `data` raíz `afUnboundData` del esquema XML del formulario principal.

Puede agregar un formulario adaptable como formulario secundario varias veces. Asegúrese de que `bindRef` se modifica correctamente para que cada instancia utilizada del formulario adaptable apunte a una subraíz diferente debajo de la raíz de los datos.

>[!NOTE]
>
>Si se asignan formularios o fragmentos distintos a la misma subraíz, los datos se sobrescribirán.

## Agregar un formulario adaptable como formulario secundario mediante el explorador de recursos {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Realice los siguientes pasos para agregar un formulario adaptable como formulario secundario mediante el explorador de recursos.

1. Abra el formulario principal en modo de edición.
1. En la barra lateral, haga clic en **Recursos** ![assets-browser](assets/assets-browser.png). En Recursos, seleccione **Formulario adaptable** de la lista desplegable.
   [ ![Seleccionar un formulario adaptable en Recursos](assets/asset.png)](assets/asset-1.png)

1. Arrastre y suelte el formulario adaptable que desee agregar como formulario secundario.
   [ ![Arrastre y suelte el formulario adaptable en el sitio](assets/drag-drop.png)](assets/drag-drop-1.png)El formulario adaptable que suelte se agregará como formulario secundario.
