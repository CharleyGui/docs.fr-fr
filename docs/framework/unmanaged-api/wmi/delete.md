---
title: Fonction Delete (référence des API non managées)
description: La fonction Delete supprime la propriété spécifiée et tous ses qualificateurs d’une définition de classe CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1bf9bd5d93d1affee649588138456269411d280
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798671"
---
# <a name="delete-function"></a>Delete, fonction

Supprime la propriété spécifiée et tous ses qualificateurs d’une définition de classe CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
dans Nom de la propriété à supprimer. `wszName`doit être un pointeur vers un valide `LPCWSTR`.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | La propriété ne peut pas être supprimée. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` n'est pas valide. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | La propriété spécifiée n’existe pas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | La mémoire est insuffisante pour terminer l’opération. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | La propriété est héritée d’une classe de base. |
| `WBEM_E_SYSTEM_PROPERTY` | | La propriété est une propriété système. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | La fonction a supprimé une valeur par défaut de remplacement pour la classe actuelle. La valeur par défaut de cette propriété dans la classe parente a été réactivée. |

## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la méthode [IWbemClassObject ::D supprim](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** WMINet_Utils.idl

**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performance (informations de référence sur les API non managées)](index.md)
