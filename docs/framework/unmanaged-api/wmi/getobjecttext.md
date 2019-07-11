---
title: Getobjecttext, fonction (référence des API non managées)
description: Getobjecttext, de la fonction retourne un rendu textuel d’un objet dans la syntaxe MOF.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746499"
---
# <a name="getobjecttext-function"></a>GetObjectText, fonction
Retourne un rendu textuel de l’objet dans la syntaxe de Format MOF (Managed Object).

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
[in] Ce paramètre n’est pas utilisé.

`ptr`  
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lFlags`  
[in] Généralement 0. Si `WBEM_FLAG_NO_FLAVORS` (ou 0 x 1) est spécifiée, les qualificateurs sont inclus sans les informations de la propagation ou la version.

`pstrObjectText`   
[out] Un pointeur vers un `null` sur ENTRÉE. Moment du retour, qui vient d’être alloué `BSTR` qui contient un rendu de la syntaxe MOF de l’objet.  

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Il y a eu une défaillance générale. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n’est pas valide. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire est insuffisante pour terminer l’opération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) (méthode).

Le texte MOF retourné ne contient pas toutes les informations sur l’objet, mais suffisamment d’informations pour le compilateur MOF être en mesure de recréer l’objet d’origine. Par exemple, aucun qualificateurs propagés ou les propriétés de la classe parent ne sont incluses.

L’algorithme suivant est utilisé pour reconstruire le texte des paramètres d’une méthode :

1. Les paramètres sont resequenced dans l’ordre de leurs valeurs d’identificateur.
1. Les paramètres sont spécifiés en tant que `[in]` et `[out]` sont combinés en un seul paramètre.
 
`pstrObjectText` doit être un pointeur vers un `null` lorsque la fonction est appelée ; il ne doit pas pointer vers une chaîne qui est valide avant l’appel de méthode, car le pointeur n’est pas libéré.

## <a name="requirements"></a>Configuration requise  
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
