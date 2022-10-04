---
title: Limitaciones de copia de seguridad del Generador de PDF
seo-title: PDF Generator backup limitations
description: Obtenga información sobre las limitaciones de copia de seguridad de Generador de PDF.
seo-description: Learn about PDF Generator backup limitations.
uuid: 9537ffde-4396-46d1-81ea-edcd25923ffb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 23386353-b2bf-49f1-947a-dd7587bba175
noindex: true
exl-id: d2ba9881-02b6-470b-b110-7d4609e6ab24
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# Limitaciones de copia de seguridad del Generador de PDF {#pdf-generator-backup-limitations}

No se puede realizar una copia de seguridad del directorio temporal que utiliza PDF Generator para convertir archivos. Aunque el servicio se restaurará correctamente, los datos se pueden perder porque el Generador de PDF revisa y borra el contenido del directorio temporal a intervalos establecidos.
