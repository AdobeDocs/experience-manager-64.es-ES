---
title: Herramienta de migración CRX2OAK
seo-title: CRX2OAK Migration Tool
description: Notas de la versión específicas de la herramienta de migración Adobe Experience Manager 6.4 CRX2OAK.
seo-description: Release notes specific to the Adobe Experience Manager 6.4 CRX2OAK Migration tool.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# Herramienta de migración CRX2OAK {#crx-oak-migration-tool}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

## Lista de cambios y correcciones {#list-of-changes-and-fixes}

### 1.8.6 (junio de 2018) {#june}

* OAK-7339 Corregir todos los sigres rompiendo con UnsupportedOperationException en MissingBlobStore al introducir LoopbackBlobStore
* Usar Oak 1.8.4

### 1.8.4 (abril de 2018) {#april}

* Usar Oak versión 1.8.2
* El error de migración de repositorios GRANITE-18104 de 6.3 a 6.4 debería ser más significativo
* GRANITE-16571 Sustitución del uso de SHA-1

   * La suma de comprobación de la herramienta ahora es SHA-512 al utilizar la opción —version

* GRANITE-17601 Incruste oak-upgrade en CRX2Oak con oak-blob-cloud
* GRANITE-18553 crx2oak deja propiedades de versión en el nodo incluso cuando las versiones no se migran

### Versión 1.6.8 (marzo de 2017) {#version-march}

* Se ha actualizado la versión de Oak a la 1.6.1
* CQ-61847 Combine crx2oak-quickstart-extension con crx2oak (se han agregado perfiles de migración)
* CQ-97488 Promocionar y soltar modos AEM ejecución (reescribiendo sling.options.file)
* GRANITE-12798/OAK-4260 Posibilidad de pasar de la clasificación Oak a Oak Segment Tar

### Versión 1.4.2 (marzo de 2016) {#version-march-1}

* Actualizar la versión de Oak a 1.4.1
* OAK-3846 / GRANITE-10748 Cambiar el nombre de los nodos SNS si infringen restricciones de tipo de nodo
* OAK-3910 / GRANITE-10730 Migración de nodos que heredan de `mix:versionable` sin historial de versiones
* OAK-4128 / GRANITE-11757 `RepositorySidegrade` no copia propiedades del nodo raíz

### Versión 1.3.4 (enero de 2016) {#version-january}

* Actualización de la versión de Oak a la 1.3.16
* OAK-3844 / GRANITE-10730 Mejor soporte para nodos versionables sin historiales de versiones
* OAK-3846 Cambiar el nombre de los nodos SNS si infringen restricciones de tipo de nodo

### Versión 1.3.2 (diciembre de 2015) {#version-december}

* Actualiza la versión de Oak a la 1.3.12
* El directorio del almacén de datos no debe moverse después de la migración (GRANITE-10447)
* Combine crx2oak-quickstart-extension con crx2oak (CQ-61847)
* crx2oak falla en los valores duplicados en el repositorio (CQ-61906)
* Inicio de AEM prolongado después de la migración desde CQ5.x (GRANITE-10309)
* Compatibilidad con varios servidores LDAP en crx2oak (GRANITE-9917)
* Aplicar comprobación para la longitud máxima del nombre del nodo (OAK-3111)
* Compatibilidad con S3DataSource como fuente de migración (OAK-3685)
