---
title: Fonction NextMethod (référence des API non managées)
description: La fonction NextMethod récupère la méthode suivante dans une énumération.
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
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726767"
---
# <a name="nextmethod-function"></a>NextMethod, fonction

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
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
[in] Réservée. Ce paramètre doit avoir la valeur 0.

`pName`  
à Pointeur qui pointe vers `null` avant l’appel. Lorsque la fonction retourne, adresse d’un nouveau `BSTR` qui contient le nom de la méthode.

`ppSignatureIn`  
à Pointeur qui reçoit un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient les `in` paramètres de la méthode.

`ppSignatureOut`  
à Pointeur qui reçoit un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient les `out` paramètres de la méthode.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Aucun appel à la [`BeginEnumeration`](beginenumeration.md) fonction. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Il n’y a plus de propriétés dans l’énumération. |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .

L’appelant commence la séquence d’énumération en appelant la fonction [BeginMethodEnumeration](beginmethodenumeration.md) , puis appelle la fonction [NextMethod] jusqu’à ce que la fonction retourne `WBEM_S_NO_MORE_DATA` . Si vous le souhaitez, l’appelant termine la séquence en appelant [EndMethodEnumeration](endmethodenumeration.md). L’appelant peut arrêter l’énumération tôt en appelant [EndMethodEnumeration](endmethodenumeration.md) à tout moment.

## <a name="example"></a>Exemple

Pour obtenir un exemple C++, consultez la méthode [IWbemClassObject :: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
