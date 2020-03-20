---
title: Fonction GetQualifierSet (référence API non gestion)
description: La fonction GetQualifierSet récupère l’ensemble de qualification pour une classe ou une instance.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176771"
---
# <a name="getqualifierset-function"></a>GetQualifierSet, fonction
Récupère le jeu de qualificateurs pour une instance de classe ou une définition de classe.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[dans] Ce paramètre n’est pas utilisé.

`ptr`  
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`ppQualSet`  
[out] Reçoit le pointeur d’interface qui permet l’accès aux qualificatifs de l’objet de classe. `ppQualSet` ne peut pas avoir la valeur `null`. Si une erreur se produit, un nouvel objet n’est pas retourné, et le pointeur n’est pas modifié.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Il y a eu un échec général. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | La méthode spécifiée n’existe pas. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire n'est pas suffisante pour terminer cette opération. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Un paramètre est `null`. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) méthode.

Le [pointeur IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permet à l’appelant d’ajouter, de modifier ou de supprimer ces qualificatifs. Ces qualificatifs ajoutés, édités ou supprimés s’appliquent à l’ensemble de l’instance ou de la définition de classe.

## <a name="requirements"></a>Spécifications  
**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
