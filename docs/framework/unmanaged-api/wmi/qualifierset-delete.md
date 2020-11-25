---
title: Fonction QualifierSet_Delete (référence des API non managées)
description: La fonction QualifierSet_Delete supprime un qualificateur par son nom.
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
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721151"
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
dans Ce paramètre n’est pas utilisé.

`ptr` dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName` dans Nom du qualificateur à supprimer.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Le paramètre `wszName` n'est pas valide. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | La suppression de ce qualificateur n’est pas conforme. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Le qualificateur spécifié est introuvable. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | La substitution locale a été supprimée et le qualificateur d’origine de l’objet parent a repris la portée. |

## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemQualifierSet ::D supprim](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .

En raison des règles de propagation des qualificateurs, un qualificateur particulier peut avoir été hérité d’un autre objet et simplement substitué dans la classe ou l’instance actuelle. Dans ce cas, la `QualifierSet_Delete` méthode réinitialise le qualificateur à sa valeur héritée d’origine. Dans ce cas, la fonction retourne le code d’état `WBEM_S_RESET_TO_DEFAULT` .

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
