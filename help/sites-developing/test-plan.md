---
title: Compilación del plan de pruebas
seo-title: Compilación del plan de pruebas
description: Los casos de prueba individuales se combinan en el plan de pruebas
seo-description: Los casos de prueba individuales se combinan en el plan de pruebas
uuid: 99822b02-7b75-422d-ae21-16c4af742567
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3a8302e8-bc61-402c-a9f2-5db3dfa6dd6d
translation-type: tm+mt
source-git-commit: d6c10927d437cfc9371e4baeff5a91ed9a0503c8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Compilación del plan de pruebas{#compiling-your-test-plan}

Los casos de prueba individuales se fusionarán en el plan de pruebas, que también definirá:

## Prioridades

Algunas pruebas tendrán más importancia que otras, por lo que es aconsejable indicar su prioridad.

Por ejemplo, algunas pruebas pueden afectar a una decisión de Go / No-Go y, por lo tanto, deben confirmarse con cada versión provisional probada.

## Iteraciones

Si su proyecto utiliza cualquier forma de iteración de desarrollo (que implica que se están poniendo a disposición varias versiones), es posible que necesite o desee una indicación de los resultados de cada iteración. Esto puede utilizarse para indicar:

* qué pruebas se incluirán en qué iteración.
* los resultados observados para las pruebas repetidas en varias iteraciones.
* que las pruebas prioritarias y las pruebas sobre características básicas se repiten a intervalos regulares.

## Tester

En algún momento puede asignar el equipo de prueba adecuado o una persona de prueba específica (posiblemente según la disponibilidad o la experiencia).

## Resumen o Información general

Para fines de sistema de informes, debe proporcionar una descripción general de los resultados de la prueba:

* Porcentaje de pruebas ya cubiertas.
* Porcentaje de éxito/error.
* Cifras específicas relacionadas con las pruebas prioritarias.
