---
title: PutMethod (fonction) (référence des API non managées)
description: La fonction PutMethod crée une méthode.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca510f30f0f38ae54eb83046b0e9d5541db882d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758690"
---
# <a name="putmethod-function"></a>PutMethod (fonction)
Crée une méthode.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`wszName`  
[in] Le nom de la méthode à créer. 

`lFlags`  
[in] Réservée. Ce paramètre doit être 0.

`pSignatureIn`  
[in] Un pointeur vers une copie de la [classe __Parameters](/windows/desktop/WmiSdk/--parameters) qui contient le `in` paramètres de la méthode. Ce paramètre est ignoré si la valeur `null`.  

`pSignatureOut`  
[in]  Un pointeur vers une copie de la [classe __Parameters](/windows/desktop/WmiSdk/--parameters) qui contient le `out` paramètres de la méthode. Ce paramètre est ignoré si la valeur `null`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Le `[in, out]` paramètre de méthode spécifié à la fois dans le *pInSignature* et *pOutSignature* objets ont des qualificateurs différents.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Il manque la spécification d’un paramètre de méthode le **ID** qualificateur. |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | La série d’ID qui est affectée aux paramètres de méthode n’est pas consécutif ou n’a pas été commencent à 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | La valeur de retour pour une méthode a un **ID** qualificateur. |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Une tentative a été effectuée pour réutiliser un nom de méthode existant d’une classe parente, et les signatures ne correspondent pas. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi. |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) (méthode).

Cet appel de méthode est uniquement pris en charge `ptr` est une définition de classe CIM. Manipulation de la méthode n’est pas disponible à partir de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointeurs qui pointent vers des instances CIM.

Les utilisateurs ne peuvent pas créer des méthodes dont les noms commencent ou finir par un trait de soulignement. Cela est réservé pour les propriétés et les classes système.

Pour une méthode, le `in` et `out` paramètres sont décrits en tant que propriétés dans [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objets.

Un `[in/out]` paramètre peut être défini en ajoutant la même propriété pour les deux objets vers lequel pointés le `pInSignature` et `pOutSignature` paramètres. Dans ce cas, les propriétés partagent le même **ID** valeur du qualificateur.

Chaque propriété dans un [__Parameters](/windows/desktop/WmiSdk/--parameters) objet de classe autre que `ReturnValue` doit avoir un **ID** qualificateur, une valeur numérique de base zéro qui identifie l’ordre dans lequel les paramètres apparaissent. Aucun deux paramètres ne peuvent avoir le même **ID** valeur et non **ID** valeur peut être ignorée. Si des conditions se produit, le `PutMethod` fonction renvoie `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Exemple

Pour obtenir un exemple, consultez le [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) (méthode).

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
