---
title: WritePropertyValue (fonction) (référence des API non managées)
description: La fonction WritePropertyValue écrit les octets à une propriété.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47120ff9de9e6e4802c5aea990841b235cd6c74c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783066"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue (fonction)
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
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.

`lHandle`  
[in] Entier qui contient le handle qui identifie cette propriété. Le handle peut être récupéré en appelant le [GetPropertyHandle](getpropertyhandle.md) (fonction).   

`lNumBytes`  
[in] Le nombre d’octets écrits dans la propriété. Consultez le [notes](#remarks) section pour plus d’informations.

`pHandle`   
[out] Pointeur vers le tableau d’octets qui contient les données.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Une incompatibilité de type s’est produite. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) (méthode).

Utilisez cette fonction pour définir la chaîne et tous les autres non -`DWORD` ou non-`QWORD` données.

Pour les valeurs de propriété sans chaînes, `lNumBytes` doit être la taille des données correctes du type de propriété spécifié. Pour les valeurs de propriété de chaîne, `lNumBytes` doit être la longueur de la chaîne spécifiée en octets et la chaîne lui-même doit être de même longueur en octets et être suivie d’un caractère de fin de la valeur null.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
