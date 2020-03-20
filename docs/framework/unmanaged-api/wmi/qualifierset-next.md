---
title: fonction QualifierSet_Next (référence API non gestion)
description: La fonction QualifierSet_Next récupère le prochain qualificatif dans un recensement.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174873"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next, fonction
Récupère le qualificateur suivant dans une énumération commencée avec un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`[dans] Ce paramètre n’est pas utilisé.

`ptr`[dans] Un pointeur à une instance [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`lFlags`[dans] Réservés au. Ce paramètre doit être de 0.

`pstrName`[out] Le nom du qualificatif. Si `null`, ce paramètre est ignoré; autrement, `pstrName` ne doit pas `BSTR` indiquer une fuite valide ou une fuite de mémoire se produit. Si elle n’est pas nulle, la fonction alloue toujours un nouveau `BSTR` quand il revient `WBEM_S_NO_ERROR`.

`pVal`[out] En cas de succès, la valeur pour le qualificatif. Si la fonction `VARIANT` échoue, `pVal` le pointé vers par n’est pas modifié. Si ce `null`paramètre est , le paramètre est ignoré.

`plFlavor`[out] Un pointeur à un LONG qui reçoit la saveur qualificative. Si l’information de saveur n’est pas désirée, ce paramètre peut être `null`.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | L’appelant n’a pas appelé [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour commencer une nouvelle énumération. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Il ne reste plus de qualificatifs dans l’énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemQualifierSet::Méthode suivante.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)

Vous appelez `QualifierSet_Next` la fonction à plusieurs reprises pour énumérer tous les qualificatifs jusqu’à ce que la fonction de retour `WBEM_S_NO_MORE_DATA`. Pour mettre fin à l’énumération tôt, appelez la [fonction QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)

L’ordre des qualificatifs retournés pendant l’énumération n’est pas défini.

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
