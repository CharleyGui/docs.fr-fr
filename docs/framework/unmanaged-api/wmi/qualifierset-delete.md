---
title: fonction QualifierSet_Delete (Référence API non gestion)
description: La fonction QualifierSet_Delete supprime un qualificatif par nom.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174899"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete, fonction
Supprime un qualificateur spécifié par nom.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`  
[dans] Ce paramètre n’est pas utilisé.

`ptr`[dans] Un pointeur à une instance [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`wszName`[dans] Le nom du qualificatif à supprimer.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Le paramètre `wszName` n’est pas valide. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Supprimer ce qualificatif est illégal. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le qualificatif spécifié n’a pas été trouvé. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Le remplacement local a été supprimé et le qualificatif original de l’objet parent a repris la portée. |

## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à la méthode [IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)

En raison des règles de propagation qualificatives, un qualificatif particulier peut avoir été hérité d’un autre objet et simplement remplacé dans la classe ou l’instance actuelle. Dans ce cas, la `QualifierSet_Delete` méthode réinitialise le qualificatif à sa valeur héritée originale. La fonction dans ce cas `WBEM_S_RESET_TO_DEFAULT`renvoie le code d’état .

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
