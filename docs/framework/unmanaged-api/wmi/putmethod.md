---
title: Fonction PutMethod (référence API non managérisée)
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
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174912"
---
# <a name="putmethod-function"></a>PutMethod, fonction
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
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`  
[dans] Le nom de la méthode à créer.

`lFlags`  
[in] Réservée. Ce paramètre doit être de 0.

`pSignatureIn`  
[dans] Un pointeur à une copie de la classe `in` __Parameters [système](/windows/desktop/WmiSdk/--parameters) qui contient les paramètres de la méthode. Ce paramètre est `null`ignoré si défini à .  

`pSignatureOut`  
[dans]  Un pointeur à une copie de la classe `out` __Parameters [système](/windows/desktop/WmiSdk/--parameters) qui contient les paramètres de la méthode. Ce paramètre est `null`ignoré si défini à .

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un ou plusieurs paramètres ne sont pas valides. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | Le `[in, out]` paramètre de méthode spécifié dans les objets *pInSignature* et *pOutSignature* ont des qualificatifs différents.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Un paramètre de méthode manque la spécification du qualificatif **d’identification.** |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | La série ID qui est attribuée aux paramètres de la méthode n’est pas consécutive ou ne commence pas à 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | La valeur de retour d’une méthode a un qualificatif **d’identification.** |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | On a tenté de réutiliser un nom de méthode existant d’une classe de parents, et les signatures ne correspondaient pas. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi. |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à la méthode [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

Cet appel de méthode `ptr` n’est pris en charge que s’il s’agit d’une définition de classe de l’ICM. La manipulation de la méthode n’est pas disponible à partir des pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers les instances de l’ICM.

Les utilisateurs ne peuvent pas créer des méthodes avec des noms qui commencent ou se terminent par un soulignement. Ceci est réservé aux classes et aux propriétés du système.

Pour une méthode, `out` les paramètres et les `in` paramètres sont décrits comme des propriétés dans les objets [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

Un `[in/out]` paramètre peut être défini en ajoutant la `pInSignature` même `pOutSignature` propriété aux deux objets pointés par les paramètres et les paramètres. Dans ce cas, les propriétés partagent la même valeur de qualification **d’identification.**

Chaque propriété dans un objet de `ReturnValue` classe [__Parameters](/windows/desktop/WmiSdk/--parameters) autre que doit avoir un qualificatif **d’identification,** une valeur numérique à base de zéro qui identifie l’ordre dans lequel les paramètres apparaissent. Aucun des deux paramètres ne peut avoir la même valeur **d’identification,** et aucune valeur **d’identification** ne peut être ignorée. Si l’une `PutMethod` ou `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`l’autre condition se produit, la fonction revient .

## <a name="example"></a> Exemple

Par exemple, voir la méthode [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
