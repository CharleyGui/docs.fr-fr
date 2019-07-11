---
title: BeginEnumeration, fonction (référence des API non managées)
description: La fonction BeginEnumeration réinitialise l’énumérateur au début de l’énumération
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ccf39c019094d896ca20534fccbbccf38ab1dd3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761808"
---
# <a name="beginenumeration-function"></a>BeginEnumeration, fonction
Réinitialise l’énumérateur au début de l’énumération.  

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
[in] Ce paramètre n’est pas utilisé.

`ptr`\
[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.

`lEnumFlags`\
[in] Une combinaison au niveau du bit des indicateurs ou des valeurs décrites dans le [notes](#remarks) section qui contrôle les propriétés incluses dans l’énumération.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |`Value`  |Description  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | La combinaison d’indicateurs dans `lEnumFlags` n’est pas valide ou non valide argument a été spécifié. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Un deuxième appel à `BeginEnumeration` a été effectuée sans appel intermédiaire à [ `EndEnumeration` ](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour commencer une nouvelle énumération. |
|`WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi.  |
  
## <a name="remarks"></a>Notes

Cette fonction encapsule un appel à la [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) (méthode).

Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.  Vous pouvez combiner un indicateur de chaque groupe avec n’importe quel indicateur à partir d’un autre groupe. Toutefois, les indicateurs à partir du même groupe sont mutuellement exclusifs. 

**Groupe 1**

|Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Inclure les propriétés qui constituent la clé uniquement. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Inclure les propriétés qui sont des références d’objet. |

**Groupe 2**

Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Limiter l’énumération aux propriétés du système. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Les propriétés locales et propagées mais exclut les propriétés système à partir de l’énumération. |

Pour les classes :

Constante  |Valeur  |Description  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Limiter l’énumération aux propriétés de substitution dans la définition de classe. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Limiter l’énumération aux propriétés de substitution dans la définition de classe en cours et de nouvelles propriétés définies dans la classe. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Un masque (au lieu d’un indicateur) à appliquer par rapport à un `lEnumFlags` valeur à vérifier si `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` est définie. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limiter l’énumération aux propriétés qui sont définies ou modifiées dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limiter l’énumération de propriétés qui sont héritées de classes de base. |

Pour les instances :

Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Limiter l’énumération aux propriétés qui sont définies ou modifiées dans la classe elle-même. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Limiter l’énumération de propriétés qui sont héritées de classes de base. |

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [WMI et compteurs de performances (référence des API non managées)](index.md)
