---
title: Fonction QualifierSet_Next (référence des API non managées)
description: La fonction QualifierSet_Next récupère le qualificateur suivant dans une énumération.
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
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721125"
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

`vFunc` dans Ce paramètre n’est pas utilisé.

`ptr` dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`lFlags` dans Réservé. Ce paramètre doit avoir la valeur 0.

`pstrName` à Nom du qualificateur. Si `null` la valeur est, ce paramètre est ignoré ; sinon, `pstrName` ne doit pas pointer vers un valide `BSTR` ou une fuite de mémoire se produit. Si la valeur n’est pas null, la fonction alloue toujours une nouvelle `BSTR` quand elle retourne `WBEM_S_NO_ERROR` .

`pVal` à En cas de réussite, il s’agit de la valeur du qualificateur. Si la fonction échoue, le `VARIANT` pointé par `pVal` n’est pas modifié. Si ce paramètre est `null` , le paramètre est ignoré.

`plFlavor` à Pointeur vers une valeur de type LONG qui reçoit la version du qualificateur. Si les informations de version ne sont pas souhaitées, ce paramètre peut avoir la la `null` .

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre n'est pas valide. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | L’appelant n’a pas appelé [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire disponible insuffisante pour commencer une nouvelle énumération. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Aucun qualificateur supplémentaire n’est laissé dans l’énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) .

Vous appelez la `QualifierSet_Next` fonction à plusieurs reprises pour énumérer tous les qualificateurs jusqu’à ce que la fonction retourne `WBEM_S_NO_MORE_DATA` . Pour terminer l’énumération tôt, appelez la fonction [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) .

L’ordre des qualificateurs retournés pendant l’énumération n’est pas défini.

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
