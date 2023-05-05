---
title: Configurar SSL en Windows Vista
seo-title: Configuring SSL on Windows Vista
description: Aprenda a configurar SSL en Windows Vista.
seo-description: Learn how to configure SSL on Windows Vista.
uuid: 20bfcefb-ec84-4c55-bceb-6af106d883d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 667645a0-53d0-4f9b-a0ba-cc7e366a23a1
exl-id: 8eee2ed2-8263-47f2-b928-214fd9ab5f6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 9%

---

# Configurar SSL en Windows Vista {#configuring-ssl-on-windows-vista}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Para configurar SSL en Windows Vista™, necesita un certificado SSL con claves RSA para la autenticación. Puede utilizar la herramienta de claves Java para crear el certificado.

>[!NOTE]
>
>Windows Vista no funcionará con claves DSA.

Puede ejecutar keytool utilizando un único comando que incluya toda la información necesaria para crear el certificado y el almacén de claves.

**Creación de un certificado SSL**

1. En un símbolo del sistema, vaya a *[PÁGINA PRINCIPAL DE JAVA]*/bin y escriba el siguiente comando para crear el certificado y el almacén de claves:

   `keytool -genkey -keyalg RSA -dname "CN=`*Nombre del host* `, OU=`*Nombre del grupo* `, O=`*Nombre de la empresa* `,L=`*Ciudad******Nombre* `, S=`*Estado* `, C=`*Código del país* `" -alias`*&quot;Certificado LC&quot;* `-keypass` `*key*`*_**password* `-keystore`*keystorename* `.keystore`

   >[!NOTE]
   >
   >Reemplazar *[JAVA_HOME] con el directorio donde está instalado el JDK, y reemplace el texto en cursiva con valores que se correspondan con su entorno.*

1. Tipo `changeit` como contraseña. Esta contraseña es la predeterminada para una instalación de Java y es posible que el administrador del sistema la haya cambiado.
