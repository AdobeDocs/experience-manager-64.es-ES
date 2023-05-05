---
title: Configurar el bloqueo de cuentas
seo-title: Configure account-locking settings
description: Utilice la opción Habilitar bloqueo de cuenta para bloquear cuentas de usuario después de un número específico de errores de autenticación consecutivos.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 10%

---

# Configurar el bloqueo de cuentas {#configure-account-locking-settings}

>[!CAUTION]
>
>AEM 6.4 ha llegado al final de la compatibilidad ampliada y esta documentación ya no se actualiza. Para obtener más información, consulte nuestra [períodos de asistencia técnica](https://helpx.adobe.com/es/support/programs/eol-matrix.html). Buscar las versiones compatibles [here](https://experienceleague.adobe.com/docs/).

Cuando agregue un dominio, especifique si desea habilitar el bloqueo de cuentas. Cuando se selecciona la opción Habilitar bloqueo de cuenta, las cuentas de usuario se bloquean después de un número especificado de errores de autenticación consecutivos. Después de un período de tiempo especificado, el usuario puede intentar autenticarse de nuevo. Esta función evita que los usuarios prueben varias combinaciones de credenciales para acceder al sistema.

Utilice la configuración de la página Administración de dominios para especificar el número máximo de errores de autenticación y el período de tiempo que las cuentas están bloqueadas. Esta configuración se aplica a todos los dominios que tienen habilitado el bloqueo de cuentas.

1. En la consola de administración, haga clic en **[!UICONTROL Configuración > Administración de usuarios > Administración de dominios]**.
1. En el cuadro Máximo de errores de autenticación consecutiva , introduzca el número de veces consecutivas que un usuario puede intentar iniciar sesión sin éxito antes de que su cuenta se bloquee. El valor predeterminado es 20.
1. En el cuadro Desbloquear la cuenta después de (minutos) , introduzca el número de minutos que la cuenta de usuario está bloqueada. Tras el número de minutos especificado, el usuario puede intentar iniciar sesión de nuevo. El valor predeterminado es 30.
1. Haga clic en **[!UICONTROL Guardar]**.
