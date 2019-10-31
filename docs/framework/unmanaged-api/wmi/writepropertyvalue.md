---
title: Fonction WritePropertyValue (référence des API non managées)
description: La fonction WritePropertyValue écrit des octets dans une propriété.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107288"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue fonction)
Écrit un nombre spécifié d’octets dans une propriété identifiée par un descripteur de propriété.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`lHandle`  
dans Entier qui contient le handle qui identifie cette propriété. Le descripteur peut être récupéré en appelant la fonction [GetPropertyHandle](getpropertyhandle.md) .   

`lNumBytes`  
dans Nombre d’octets écrits dans la propriété. Pour plus d’informations, consultez la section [Notes](#remarks) .

`pHandle`   
à Pointeur vers le tableau d’octets qui contient les données.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Une incompatibilité de type s’est produite. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) .

Utilisez cette fonction pour définir la chaîne et toutes les autres données non`DWORD` ou non`QWORD`.

Pour les valeurs de propriété qui ne sont pas des chaînes, `lNumBytes` doit être la bonne taille de données du type de propriété spécifié. Pour les valeurs de propriété de type chaîne, `lNumBytes` doit correspondre à la longueur de la chaîne spécifiée en octets, et la chaîne elle-même doit être de longueur égale en octets et être suivie d’un caractère de fin null.

## <a name="requirements"></a>spécifications  
**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
