---
title: Configurar la contraseña de enlace LDAP
seo-title: Configure the LDAP bind password
description: Obtenga información sobre cómo configurar el campo de contraseña de enlace antes de importar el archivo de configuración en otro sistema.
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: eaa2c889-d116-4209-9063-0c0b32dd8849
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 8%

---

# Configurar la contraseña de enlace LDAP{#configure-the-ldap-bind-password}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para evitar riesgos de seguridad, el campo bind password en el archivo de configuración exportado (config.xml) no está configurado. Antes de importar el archivo de configuración en otro sistema, asegúrese de configurar esta contraseña. Esta contraseña anula una contraseña existente almacenada en la base de datos. Una contraseña nula no invalida un valor de contraseña no nula existente.

1. En la consola de administración, haga clic en Configuración > Administración de usuarios > Configuración > Importar y exportar archivos de configuración.
1. Para exportar la configuración actual a un archivo, haga clic en Exportar y guarde el archivo de configuración en otra ubicación.
1. En el archivo , busque la variable `Domains` > *[Su nombre de dominio]* > `DirectoryConfigs` > `LDAPGroupConfig` nodo . Este es un ejemplo:

   ```as3
    <node name="LDAPGroupConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="batchSize" value="200" />  
            <entry key="binduser" value="cn=Directory Manager" />  
            <entry key="bindpassword" value="" /> 
        </map>
   ```

   Escriba un valor para `bindpassword` y guarde los cambios.

1. En el archivo , busque la variable `Domains` > *[Su nombre de dominio]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` nodo . Este es un ejemplo:

   ```as3
    <node name="LDAPUserConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="batchSize" value="200" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="bindpassword" value="" /> 
            <entry key="binduser" value="cn=Directory Manager" />  
        </map>
   ```

   Escriba un valor para `bindpassword` y guarde los cambios.

1. Para importar el archivo actualizado, en Administración de usuarios, haga clic en Configuración > Importar y exportar archivos de configuración.
1. Haga clic en Examinar para buscar el archivo, haga clic en Importar y, a continuación, haga clic en Aceptar.
