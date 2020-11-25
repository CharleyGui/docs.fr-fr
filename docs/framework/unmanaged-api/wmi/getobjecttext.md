---
title: Fonction GetObjectText (référence des API non managées)
description: La fonction GetObjectText retourne un rendu textuel d’un objet dans la syntaxe MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6ad2b29202222d594cc7976a13929002164314a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718369"
---
# <a name="getobjecttext-function"></a>GetObjectText, fonction

Retourne un rendu textuel de l’objet dans la syntaxe du format MOF (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
dans Ce paramètre n’est pas utilisé.

`ptr`  
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
dans Normalement 0. Si `WBEM_FLAG_NO_FLAVORS` (ou 0x1) est spécifié, les qualificateurs sont inclus sans propagation ni informations de version.

`pstrObjectText` à Pointeur vers un à l' `null` entrée. Au retour, un qui vient d’être alloué `BSTR` contient un rendu de syntaxe MOF de l’objet.  

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Une défaillance générale s’est produite. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .

Le texte MOF retourné ne contient pas toutes les informations relatives à l’objet, mais uniquement les informations nécessaires au compilateur MOF pour pouvoir recréer l’objet d’origine. Par exemple, aucun qualificateur propagé ou propriété de classe parente n’est inclus.

L’algorithme suivant est utilisé pour reconstruire le texte des paramètres d’une méthode :

1. Les paramètres sont reséquencés dans l’ordre de leurs valeurs d’identificateur.
1. Les paramètres spécifiés en tant que `[in]` et `[out]` sont combinés en un seul paramètre.

`pstrObjectText` doit être un pointeur vers un `null` lorsque la fonction est appelée ; elle ne doit pas pointer vers une chaîne valide avant l’appel de la méthode, car le pointeur n’est pas libéré.

## <a name="requirements"></a>Configuration requise  

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
