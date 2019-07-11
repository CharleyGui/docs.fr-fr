---
title: NextMethod (fonction) (référence des API non managées)
description: La fonction NextMethod extrait la méthode suivante dans une énumération.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a730947b0c962d801975917cdf752136e7221c4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746477"
---
# <a name="nextmethod-function"></a>NextMethod (fonction)
Récupère la méthode suivante dans une énumération qui commence par un appel à [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Réservée. Ce paramètre doit être 0.

`pName`  
[out] Un pointeur qui pointe vers `null` avant l’appel. Lorsque la fonction est retournée, l’adresse d’un nouveau `BSTR` qui contient le nom de méthode. 

`ppSignatureIn`  
[out] Un pointeur qui reçoit un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient le `in` paramètres de la méthode. 

`ppSignatureOut`  
[out] Un pointeur qui reçoit un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient le `out` paramètres de la méthode. 

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Il n’y avait aucun appel à la [ `BeginEnumeration` ](beginenumeration.md) (fonction). |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Il n’existe aucune autre propriété dans l’énumération. |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) (méthode).

L’appelant commence la séquence d’énumération en appelant le [BeginMethodEnumeration](beginmethodenumeration.md) de fonction et appelle ensuite la fonction [NextMethod] jusqu'à ce que la fonction retourne `WBEM_S_NO_MORE_DATA`. Si vous le souhaitez, l’appelant termine la séquence en appelant [EndMethodEnumeration](endmethodenumeration.md). L’appelant peut arrêter l’énumération au début en appelant [EndMethodEnumeration](endmethodenumeration.md) à tout moment.

## <a name="example"></a>Exemple

Pour obtenir un exemple C++, consultez le [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) (méthode).

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
