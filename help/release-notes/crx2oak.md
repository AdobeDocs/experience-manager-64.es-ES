---
title: Herramienta de migración CRX2OAK
seo-title: Herramienta de migración CRX2OAK
description: Notas de la versión específicas de la herramienta de migración Adobe Experience Manager 6.4 CRX2OAK.
seo-description: Notas de la versión específicas de la herramienta de migración Adobe Experience Manager 6.4 CRX2OAK.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# Herramienta de migración CRX2OAK {#crx-oak-migration-tool}

## Lista de cambios y correcciones {#list-of-changes-and-fixes}

### 1.8.6 (junio de 2018) {#june}

* OAK-7339 Corregir todos los sidegrades al romper con UnsupportedOperationException en MissingBlobStore mediante la introducción de LoopbackBlobStore
* Usar Oak 1.8.4

### 1.8.4 (abril de 2018) {#april}

* Usar Oak versión 1.8.2
* GRANITE-18104 El error de migración de repos de 6.3 a 6.4 debería ser más significativo
* GRANITE-16571 Sustitución del uso de SHA-1

   * La suma de comprobación de la herramienta ahora es SHA-512 cuando se utiliza la opción —version

* GRANITE-17601 Incorporar la actualización de roble en CRX2Oak con oak-blob-cloud
* GRANITE-18553 crx2oak deja propiedades de versión en el nodo incluso cuando no se migran versiones

### Versión 1.6.8 (marzo de 2017) {#version-march}

* Se ha actualizado la versión Oak a 1.6.1
* CQ-61847 Combina crx2oak-quickstart-extension con crx2oak (perfiles de migración agregados)
* CQ-97488 Promoción y eliminación de modos de ejecución AEM (reescribiendo sling.options.file)
* GRANITE-12798/OAK-4260 Posibilidad de pasar de la clasificación Oak al segmento Oak Tar

### Versión 1.4.2 (marzo de 2016) {#version-march-1}

* Actualizar la versión Oak a 1.4.1
* OAK-3846 / GRANITE-10748 Cambie el nombre de los nodos SNS si infringen restricciones de tipo de nodo
* OAK-3910 / GRANITE-10730 Migración de nodos que heredan de `mix:versionable` sin historial de versiones
* OAK-4128 / GRANITE-11757 `RepositorySidegrade` no copia las propiedades del nodo raíz

### Versión 1.3.4 (enero de 2016) {#version-january}

* Actualizar la versión Oak a 1.3.16
* OAK-3844 / GRANITE-10730 Mejor compatibilidad con nodos con versiones sin historial de versiones
* OAK-3846 Cambie el nombre de los nodos SNS si infringen restricciones de tipo de nodo

### Versión 1.3.2 (diciembre de 2015) {#version-december}

* Actualiza la versión Oak a 1.3.12
* El directorio del almacén de datos no debe moverse después de la migración (GRANITE-10447)
* Combinar crx2oak-quickstart-extension con crx2oak (CQ-61847)
* crx2oak falla en los valores de duplicado en el repositorio (CQ-61906)
* Inicio de larga AEM después de la migración desde CQ 5.x (GRANITE-10309)
* Compatibilidad con varios servidores LDAP en crx2oak (GRANITE-9917)
* Aplicar comprobación para la longitud máxima del nombre del nodo (OAK-3111)
* Admite S3DataSource como fuente de migración (OAK-3685)
