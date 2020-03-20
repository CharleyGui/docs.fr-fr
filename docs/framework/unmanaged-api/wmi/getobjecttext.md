---
title: Fonction GetObjectText (référence API non gestion)
description: La fonction GetObjectText renvoie un rendu textuel d’un objet dans la syntaxe MOF.
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
ms.openlocfilehash: 6881125760e0f1dc38e6b01917d5829edc95e3ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176784"
---
# <a name="getobjecttext-function"></a>GetObjectText, fonction
Renvoie un rendu textuel de l’objet dans la syntaxe format d’objet géré (MOF).

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
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[dans] Normalement 0. Si `WBEM_FLAG_NO_FLAVORS` (ou 0x1) est spécifié, les qualificatifs sont inclus sans informations de propagation ou de saveur.

`pstrObjectText`[out] Un pointeur `null` à une entrée. Au retour, un `BSTR` nouveau attribué qui contient un rendu syntaxe MOF de l’objet.  

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Il y a eu un échec général. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject:GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) méthode.

Le texte MOF retourné ne contient pas toutes les informations sur l’objet, mais seulement assez d’informations pour le compilateur MOF pour être en mesure de recréer l’objet d’origine. Par exemple, aucun qualificatif propagé ou propriété de classe parente n’est inclus.

L’algorithme suivant est utilisé pour reconstruire le texte des paramètres d’une méthode :

1. Les paramètres sont reséquencés dans l’ordre de leurs valeurs d’identification.
1. Paramètres spécifiés comme `[in]` `[out]` et sont combinés en un seul paramètre.

`pstrObjectText`doit être un `null` pointeur à un moment où la fonction est appelée; il ne doit pas pointer vers une chaîne qui est valide avant l’appel de méthode, parce que le pointeur ne sera pas deallocated.

## <a name="requirements"></a>Spécifications  
**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
