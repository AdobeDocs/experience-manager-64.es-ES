---
title: Cambiar el conjunto de caracteres
seo-title: Change the character set
description: Puede especificar el conjunto de caracteres utilizado para codificar el flujo de salida. Aprenda a cambiar el conjunto de caracteres.
seo-description: You can specify the character set used to encode the output stream. Learn how you can change the character set.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 7961efc6-4b11-423a-871d-7b37e3f36781
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 1%

---

# Cambiar el conjunto de caracteres {#change-the-character-set}

Puede especificar el conjunto de caracteres utilizado para codificar el flujo de salida.

1. En la consola de administración, haga clic en **[!UICONTROL Servicios > salida]**.
1. En Internacionalización, en la lista Conjunto de caracteres, seleccione un conjunto de caracteres. Esta configuración depende de la variable `TransformationFormat` y `PrintFormat` especificado mediante la API. Para especificar un conjunto de caracteres que no sea el enumerado, seleccione Personalizado y especifique un valor de codificación en el cuadro que se muestra.

   If `TransformationFormat` es PDF y PDF/A o `PrintFormat` es PCL, PostScript, etiqueta Zebra, IPL, DPL, TPCL, GenericColorPCL o GenericPSLevel3, solo se admiten conjuntos de caracteres específicos.

   El conjunto de caracteres debe ser un nombre canónico válido. El valor predeterminado es ISO-8859-1.

1. Haga clic en **[!UICONTROL Guardar]**.
