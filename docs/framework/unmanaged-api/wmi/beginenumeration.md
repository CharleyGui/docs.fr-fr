---
title: Fonction BeginEnumeration (Référence API non gestion)
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
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176875"
---
# <a name="beginenumeration-function"></a>BeginEnumeration, fonction
Réinitialise un enumérateur au début de l’énumération.  

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
[dans] Ce paramètre n’est pas utilisé.

`ptr`\
[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lEnumFlags`\
[dans] Une combinaison peu sage des drapeaux ou des valeurs décrites dans la section [Remarques](#remarks) qui contrôle les propriétés incluses dans le recensement.

## <a name="return-value"></a>Valeur retournée

Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | La combinaison des `lEnumFlags` drapeaux est invalide, ou un argument invalide a été spécifié. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Un deuxième `BeginEnumeration` appel a été fait [`EndEnumeration`](endenumeration.md)sans un appel intermédiaire à . |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour commencer une nouvelle énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a été réussi.  |
  
## <a name="remarks"></a>Notes 

Cette fonction enveloppe un appel à [l’IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) méthode.

Les drapeaux qui peuvent `lEnumFlags` être passés comme l’argument sont définis dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code.  Vous pouvez combiner un drapeau de chaque groupe avec n’importe quel drapeau de n’importe quel autre groupe. Cependant, les drapeaux du même groupe s’excluent mutuellement.

**Groupe 1**

|Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Inclure les propriétés qui constituent la clé seulement. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Inclure les propriétés qui sont des références d’objet seulement. |

**Groupe 2**

Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Limiter l’énumération aux propriétés du système seulement. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Inclure les propriétés locales et propagées, mais exclure les propriétés du système de l’énumération. |

Pour les classes :

Constant  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Limiter l’énumération aux propriétés remplacées dans la définition de classe. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Limiter l’énumération aux propriétés remplacées dans la définition de classe actuelle et aux nouvelles propriétés définies dans la classe. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Un masque (plutôt qu’un drapeau) à appliquer contre une `lEnumFlags` valeur pour vérifier si l’un ou l’autre `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` est réglé. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitez l’énumération aux propriétés qui sont définies ou modifiées dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitez l’énumération aux propriétés héritées des classes de base. |

Pour les cas :

Constant  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limitez l’énumération aux propriétés qui sont définies ou modifiées dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limitez l’énumération aux propriétés héritées des classes de base. |

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** WMINet_Utils.idl  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
