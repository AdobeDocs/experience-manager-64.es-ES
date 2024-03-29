---
title: Copia de seguridad y recuperación del repositorio de Documentum de EMC
seo-title: Backing up and recovering the EMC Documentum repository
description: Este documento describe las tareas necesarias para realizar backup y recuperar el repositorio de Documentum de EMC configurado para su entorno de formularios AEM.
seo-description: This document describes the tasks required to back up and recover the EMC Documentum repository configured for your AEM forms environment.
uuid: ab3b1fb1-25b3-4c95-801f-82d4b58f05ff
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f146202f-25f1-46a0-9943-c483f5f09f9f
exl-id: 89d7b2e1-1d88-4392-89d3-484a98f07121
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 3%

---

# Copia de seguridad y recuperación del repositorio de Documentum de EMC {#backing-up-and-recovering-the-emc-documentum-repository}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

En esta sección se describen las tareas necesarias para realizar backup y recuperar el repositorio de Documentum de EMC configurado para su entorno de formularios AEM.

>[!NOTE]
>
>Estas instrucciones suponen que los formularios AEM con Connectors para ECM y Content Server de Documentum de EMC están instalados y configurados según sea necesario.

Para los procesos de backup y restore, existen dos tareas principales:

* Copia de seguridad (o restauración) del entorno de formularios AEM.
* Backup (o restore) de Content Server de Documentum de EMC.

>[!NOTE]
>
>Haga backup de sus datos de formularios AEM antes de realizar backup en el sistema Documentum de EMC y, posteriormente, restaure el sistema Documentum de EMC antes de restaurar el entorno de formularios AEM.

## Requisitos de software {#software-requirements}

Para realizar las tareas de backup necesarias en Content Server de Documentum de EMC, adquiera una utilidad de terceros apropiada, como NetWorker de EMC o CYA SmartRecovery para Documentum de EMC de CYA. Las siguientes instrucciones describen los pasos para utilizar NetWorker Module de EMC versión 7.2.2.

Necesita los siguientes módulos NetWorker de EMC:

* Módulo NetWorker
* Asistente de Configuración de NetWorker
* Asistente para la configuración de dispositivos NetWorker
* Módulo NetWorker para el tipo de base de datos utilizado por Content Server
* NetWorker Module para Documentum

## Preparación de Document Content Server de EMC para backup y recuperación {#preparing-the-emc-document-content-server-for-backup-and-recovery}

En esta sección se describe la instalación y configuración del software NetWorker de EMC en Content Server.

**Preparación del servidor Documentum de EMC para backup**

1. En Content Server de Documentum de EMC, instale los módulos NetWorker de EMC, aceptando todos los valores predeterminados.

   Durante los procesos de instalación, se le pedirá que introduzca el nombre del servidor del equipo de Content Server como *Nombre del Servidor NetWorker*. Cuando instale el Módulo NetWorker de EMC para su base de datos, elija una instalación &quot;Completa&quot;.

1. Con el contenido de ejemplo siguiente, cree un archivo de configuración denominado *nsrnmd_win.cfg* y guárdelo en una ubicación accesible del servidor de contenido. Los comandos backup y restore llamarán a este archivo.

   El texto siguiente contiene caracteres de formato para los saltos de línea. Si copia este texto en una ubicación fuera de este documento, copie una parte a la vez y elimine los caracteres de formato cuando lo pegue en la nueva ubicación.

   ```as3
    ################################################ 
    # NetWorker Module for Documentum v1.2 nsrnmd_win.cfg D5.3+ example with 
    # typical set of working parameters.  THIS FILE MUST BE SITE-CUSTOMISED. 
    # 
    # Parameters not shown can be set in this file (as per site customisation) #or from the command-line. 
    # 
    # Please refer to the user Guides for details on all parameters, including  
    # those not listed below. 
    # Note: DCTM environment for D6 is slightly different from D5, refer to D6 
    # Installation Guide to update the values. 
    ################################################ 
    #Can get values for most of below from doing as the dctm inst owner: cmd> set DOCUMENTUM=C:\Documentum 
    DM_HOME=C:\Documentum\product\6.0 
    JAVA_HOME=C:\Progra~1\Documentum\java\1.5.0_12 
    JAVA_PATH=C:\Progra~1\Documentum\java\1.5.0_12\bin 
    PATH=C:\WINNT\system32;C:\WINNT;C:\WINNT\system32\WBEM;C:\Documentum\product\6.0\bin;C:\Documentum\fulltext\fast;C:\Documentum\product\6.0\fusion;C:\Program Files\Documentum\Shared;C:\Program Files\Legato\nsr\bin;C:\Program Files\Microsoft SQL Server\80\Tools\Binn;C:\Program Files\Microsoft SQL Server\90\DTS\Binn\;C:\Program Files\Microsoft SQL Server\90\Tools\binn;C:\Program Files\Microsoft SQL Server\90\Tools\Binn\VSShell\Common7\IDE;C:\Program Files\Documentum\java\1.5.0_12\bin;C:\Documentum\config;C:\Documentum 
    #See also manifest dctm.jar file for class path locations 
    CLASSPATH=.;C:\Program Files\Legato\nsr\bin;C:\Program Files\Legato\nsr\bin\nsrnmdde.jar;C:\Program Files\Documentum\java\1.5.0_12\lib\tools.jar;C:\Program Files\Documentum\Shared\dfc.jar;C:\Program Files\Documentum\Shared\aspectjrt.jar;C:\Program Files\Documentum\dctm.jar;C:\Program Files\Documentum\Shared\workflow.jar;C:\Program Files\Documentum\Shared\log4j.jar;C:\Program Files\Documentum\java\1.5.0_12\lib\dt.jar;C:\Documentum\config 
     
    ################################################ 
    #If not using nsrnmdsv -m ALL|DB|DB_LOG|FTI|FTI_ALL|ICF|SA|SA_ALL, set #for backup 
    NMD_SCOPE=ALL 
    #Mandatory when scope (backup or restore) is FTI/SA without -a option 
    #NMD_OBJECT_NAME=filestore_01 
    ################################################ 
    NMDDE_DM_DOCBASE=Docbase 
    NMDDE_DM_USER=Administrator 
    #NMDDE_DM_PASSWD must be set via running: nsrnmdsv -f <nmdcfg> -P <pwd>. 
    ################################################ 
    #DB related hooks to invoke arbitrary scripts: 
    #Set if DB is on a remote host 
    #NMD_DB_HOST=dbhost 
    #Pure basename implies remote host execution; absolute path ... local 
    #execution as in NMD v1.0. 
    # 
    #Remote execution requires script be put in remote nsrexecd bin directory 
    #and D5.3+ host be added to remote nsr\res\servers file w/ nsrexecd recycled 
    # 
    #Refer to user Guides for sample script code. 
    NMD_DB_FULL_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbf.bat 
    NMD_DB_LOG_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbl.bat 
    NMD_DB_INCR_BACKUP_CMD=C:\DocumentumBackup\Scripts\nsrnmddbi.bat 
    ################################################ 
    #For D5.3+ only: NMD_FTI_INCLUDED, NMD_FTI_HOST, NMD_FTI_USER, 
    #NMD_FTI_PASSWD & NMD_FTI_SUBDIRS. 
    #Optional for remote D5.3+ FTI server 
    NMD_FTI_INCLUDED=no 
    #NMD_FTI_HOST=ftihost 
    #Recommended for D5.3+ FTI server quiesce/unquiesce 
    #NMD_FTI_USER=ftiadmin 
    #The index name: optional for D5.3+ FTI server, used with -M FTI_ALL or 
    #-M ALL   
    #NMD_FTI_NAME=rep_name_ftindex_01 
    #Recommended for D5.3+ FTI server quiesce/unquiesce 
    #NMDDE_FTI_PASSWD must be set via running: nsrnmdsv -f <nmdcfg> -P <pwd> 
    #-M FTI. 
    #Pure basename implies remote host execution; absolute path ... local execution 
    #as in NMD v1.0. 
    # 
    #Remote execution requires script be put in remote nsrexecd bin directory 
    #and D5.3+ host be added to remote nsr\res\servers file w/ nsrexecd  
    #recycled. 
    # 
    #See example nsrnmdfti*.bat examples. 
    # 
    #Mandatory for D5.3+ 
    #NMD_BACKUP_FTI_QUIESCE=nsrnmdftiq.bat 
    #NMD_BACKUP_FTI_UNQUIESCE=nsrnmdftiu.bat 
    #Used for D5.3+ to get InstallProfile.xml FTI file in multinode 
    #discovery. 
    #Optional, if not specified, will treat as single-node FTI. 
    #NMD_FTI_GET_INSTPROF=nsrnmdfti_instprof.bat 
    #Mandatory for D5.3+. No spaces in paths or around comma separators. 
    #For remote FTI, paths must be valid at the FTI host. 
    #NMD_FTI_SUBDIRS=F:\Documentum_idx\data\fulltext\fixml,F:\Documentum_idx 
    #\data\fulltext\index 
    ################################################ 
    #Mandatory. No spaces in paths or before comma 
    #separators in NMD_ICF_SUBDIRS_xxx: 
    #NMD_ICF_INCLUDED=yes 
    #NMD_ICF_SUBDIRS=C:\Documentum\dba,C:\Documentum\product\5.3 
    ################################################ 
    NMD_FILEREPORT_INCLUDED=yes 
    NMDDE_METADATA_OUTPUT_DEST=C:\docbase_freports\ 
    ################################################ 
    #Other misc recommended NMD_xxx parameters 
    #Recommended to get more meaningful saveset names 
    NMD_USE_DEFAULT_SAVESET_NAMES=yes 
    #Use following to skip unwanted ICF, FTI and non-SnapImage SA dirs/files. 
    #For example, "<</>> +skip: dm_ftwork_dir" line will skip non-data 
    #files. 
    # 
    #The path will be the same and must exist on D5.3+, remote FTI host, and 
    #RCS hosts correspondingly if used. 
    #NMD_DIRECTIVES_FILE=E:\Program Files\Legato\nsr\res\nsrnmddirectives.txt 
    #For non-SnapImage SA backup 
    #NMD_SA_FULL_NUM_SAVESET=16 
    #NMD_SA_INCR_NUM_SAVESET=4 
    #NMD_USE_SNAPIMAGE=yes 
    ################################################ 
    # DSA setup 
    ################################################ 
    # Name of the config file at the remote sites; 
    # Mandatory, listed in the config file at the primary host. 
    # (if skipped, backup is treated as local) 
    # NMD_RCS_CFG_FILE=rep_name_rcs.cfg 
     
    # SA-host mapping add, optional, will override far-store list info. 
    # No space around comma. 
    # NMD_HOST_SAS_MAP=host01,sa_01,sa_02 
    # NMD_HOST_SAS_MAP=host02,sa_03 
    ################################################ 
    NSR_SERVER=con-dctm 
    #NSR_CLIENT=d5svrhost 
    NSR_GROUP=Default 
    NSR_DATA_VOLUME_POOL=Default 
    #NSR_SNAPIMAGE_DATA_VOLUME_POOL=Default 
    #Relocation dir will be the same on D5+ and remote FTI/SA hosts. 
    NSR_RELOCATION=C:\reloc 
    #NSR_PARALLELISM=16 
    NSR_DEBUG_FILE=C:\Program Files\Legato\nsr\applogs\nmd.log 
    NSR_DEBUG_LEVEL=9 
    ################################################ 
    NMDDE_DM_PASSWD=XAtup9pl
   ```

   Mantener el campo de contraseña del archivo de configuración `NMDDE_DM_PASSWD` en blanco. La contraseña se establecerá en el siguiente paso.

1. Establezca la contraseña del archivo de configuración de la siguiente manera:

   * Abra un símbolo del sistema y cambie a *[NetWorker_root]*\Legato\nsr\bin.
   * Ejecute el siguiente comando: `-nsrnmdsv.exe -f`*&lt;path_to_cfg_file> -P &lt;password>*

1. Cree los archivos ejecutables por lotes (.bat) que se utilizan para realizar una copia de seguridad de la base de datos. (Consulte la documentación de NetWorker). Configure los detalles en los archivos por lotes según su instalación.

   * Copia de seguridad completa de la base de datos (nsrnmdbf.bat):

      *[NetWorker_database_module_root]* `-s`*&lt;networker_server_name>* `-U`*[username ]*`-P`*[password]* `-l full`*&lt;database_name>*

   * Copia de seguridad incremental de la base de datos (nsrnmdbi.bat):

      *[NetWorker_database_module_root]* `-s`*&lt;networker_server_name>* `-U`*[username ]*`-P`*[password]* `-l 1 -R`*&lt;database_name>*

   * Copia de seguridad del registro de la base de datos (nsrnmdbl.bat):

      *[NetWorker_database_module_root]* `-s`*&lt;networker_server_name>* `-U`*[username ]*`-P`*[password]* `-l incr -R`*&lt;database_name>*

      Donde:

      `[NetWorker_database_module_root]` es el directorio de instalación del módulo NetWorker. Por ejemplo, el directorio de instalación predeterminado para NetWorker Module for SQL Server es C:\Program Files\Legato\nsr\bin\nsrsqlsv.

      `NetWorker_Server_Name` es el servidor en el que está instalado NetWorker.

      `username` &amp; `password` son el nombre de usuario y la contraseña del usuario administrador de la base de datos.

      `database_name` es el nombre de la base de datos de la que se va a realizar una copia de seguridad.

**Creación de un dispositivo de copia de seguridad**

1. Cree un nuevo directorio en el servidor de Documentum de EMC y comparta la carpeta otorgando derechos completos a todos los usuarios.
1. Inicie NetWorker Administrator de EMC y haga clic en Administración de medios > Dispositivos.
1. Haga clic con el botón derecho en Dispositivos y seleccione Crear.
1. Introduzca los siguientes valores y haga clic en Aceptar:

   **Nombre:** Ruta completa del directorio compartido

   **Tipo de medio:** `File`

1. Haga clic con el botón derecho en el nuevo dispositivo y seleccione Operaciones.
1. Haga clic en Etiqueta, escriba un nombre, haga clic en Aceptar y, a continuación, haga clic en Montar.

Se añade un dispositivo al que se guardarán los archivos de copia de seguridad. Puede agregar varios dispositivos con diferentes formatos.

## Haga backup de Documentum Content Server de EMC {#back-up-the-emc-documentum-content-server}

Realice las siguientes tareas después de completar una copia de seguridad completa de los datos de los formularios AEM. (Consulte [Copia de seguridad de los datos de AEM formularios](/help/forms/using/admin-help/backing-aem-forms-data.md#backing-up-the-aem-forms-data).)

>[!NOTE]
>
>Las secuencias de comandos requieren la ruta completa al archivo nsrnmd_win.cfg que ha creado en [Preparación de Document Content Server de EMC para backup y recuperación](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery).

1. Abra un símbolo del sistema y cambie a *[NetWorker_root]*\Legato\nsr\bin.
1. Ejecute el siguiente comando:

   ```as3
    - nsrnmdsv.exe -f <path_to_cfg_file>
   ```

## Restauración de Content Server de Documentum de EMC {#restore-the-emc-documentum-content-server}

Realice las siguientes tareas antes de restaurar los datos de los formularios AEM. (Consulte [Recuperación de los datos de los formularios AEM](/help/forms/using/admin-help/recovering-aem-forms-data.md#recovering-the-aem-forms-data).)

>[!NOTE]
>
>Las secuencias de comandos requieren la ruta completa al archivo nsrnmd_win.cfg que ha creado en [Preparación de Document Content Server de EMC para backup y recuperación](backing-recovering-emc-documentum-repository.md#preparing-the-emc-document-content-server-for-backup-and-recovery).

1. Detenga el servicio Docbase que está restaurando.
1. Inicie la utilidad NetWorker User para su módulo de base de datos (por ejemplo, *Usuario NetWorker para SQL Server*).
1. Haga clic en la herramienta Restaurar y, a continuación, seleccione Normal.
1. En la parte izquierda de la pantalla, seleccione la base de datos para la Docbase y haga clic en el botón Start de la barra de herramientas.
1. Cuando se restaure la base de datos, reinicie el servicio Docbase.
1. Abra un símbolo del sistema y cambie a *[NetWorker_root]*\Legato\nsr\bin
1. Ejecute el siguiente comando:

   ```as3
    - nsrnmdrs.exe -B <docbase_name> -f <path_to_cfg_file> -C SA
   ```
