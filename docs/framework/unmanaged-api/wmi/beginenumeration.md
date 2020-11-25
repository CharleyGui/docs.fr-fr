---
title: Fonction BeginEnumeration (référence des API non managées)
description: La fonction BeginEnumeration réinitialise un énumérateur au début de l’énumération
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708216"
---
# <a name="beginenumeration-function"></a>BeginEnumeration, fonction

Rétablit un énumérateur au début de l’énumération.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>Paramètres

`vFunc`\
dans Ce paramètre n’est pas utilisé.

`ptr`\
dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lEnumFlags`\
dans Combinaison d’opérations de bits des indicateurs ou valeurs décrites dans la section [Notes](#remarks) qui contrôle les propriétés incluses dans l’énumération.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | La combinaison d’indicateurs dans `lEnumFlags` n’est pas valide ou un argument non valide a été spécifié. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Un deuxième appel à `BeginEnumeration` a été effectué sans appel à [`EndEnumeration`](endenumeration.md) . |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Mémoire disponible insuffisante pour commencer une nouvelle énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de la fonction a réussi.  |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la méthode [IWbemClassObject :: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Les indicateurs qui peuvent être passés en tant qu' `lEnumFlags` argument sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.  Vous pouvez associer un indicateur de chaque groupe à n’importe quel indicateur de n’importe quel autre groupe. Toutefois, les indicateurs du même groupe s’excluent mutuellement.

**Groupe 1**

|Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Inclut les propriétés qui constituent la clé uniquement. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Inclut les propriétés qui sont des références d’objet uniquement. |

**Groupe 2**

Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Limitez l’énumération aux propriétés système uniquement. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Incluez les propriétés locales et propagées, mais excluez les propriétés système de l’énumération. |

Pour les classes :

Constante  |Value  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Limitez l’énumération aux propriétés substituées dans la définition de classe. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Limitez l’énumération aux propriétés substituées dans la définition de classe actuelle et aux nouvelles propriétés définies dans la classe. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Masque (plutôt qu’un indicateur) à appliquer à une `lEnumFlags` valeur pour vérifier si `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` est défini. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitez l’énumération aux propriétés définies ou modifiées dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitez l’énumération aux propriétés héritées des classes de base. |

Pour les instances :

Constante  |Value  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitez l’énumération aux propriétés définies ou modifiées dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitez l’énumération aux propriétés héritées des classes de base. |

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils. idl  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
