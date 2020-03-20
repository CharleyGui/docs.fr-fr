---
title: Fonction NextMethod (Référence API non managérisée)
description: La fonction NextMethod récupère la méthode suivante dans un recensement.
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
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174925"
---
# <a name="nextmethod-function"></a>NextMethod, fonction
Récupère la méthode suivante dans un recensement qui commence par un appel à [BeginMethodEnumeration](beginmethodenumeration.md).  

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
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[in] Réservée. Ce paramètre doit être de 0.

`pName`  
[out] Un pointeur `null` qui pointe vers avant l’appel. Lorsque la fonction revient, `BSTR` l’adresse d’un nouveau qui contient le nom de la méthode.

`ppSignatureIn`  
[out] Un pointeur qui reçoit un pointeur à un `in` [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient les paramètres de la méthode.

`ppSignatureOut`  
[out] Un pointeur qui reçoit un pointeur à un `out` [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient les paramètres de la méthode.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Il n’y [`BeginEnumeration`](beginenumeration.md) a pas eu d’appel à la fonction. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Il n’y a plus de propriétés dans l’énumération. |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) méthode.

L’appelant commence la séquence d’énumération en appelant la fonction [BeginMethodEnumeration,](beginmethodenumeration.md) puis appelle `WBEM_S_NO_MORE_DATA`la fonction [NextMethod] jusqu’à ce que la fonction revient . Optionnellement, l’appelant termine la séquence en appelant [EndMethodEnumeration](endmethodenumeration.md). L’appelant peut mettre fin à l’énumération tôt en appelant [EndMethodEnumeration](endmethodenumeration.md) à tout moment.

## <a name="example"></a> Exemple

Pour un exemple de C, voir [l’IWbemClassObject: :NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) méthode.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
