---
title: COR_PRF_FUNCTION_ARGUMENT_INFO, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
ms.openlocfilehash: 5feda2ce6dc97576d0b1d4f16ca2b9dd5f3fb05e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718556"
---
# <a name="cor_prf_function_argument_info-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO, structure

Représente les arguments d’une fonction, selon un ordre de gauche à droite.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`numRanges`|Nombre de blocs d’arguments. Autrement dit, cette valeur est le nombre de structures de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) dans le `ranges` tableau.|  
|`totalArgumentSize`|Taille totale de tous les arguments. En d’autres termes, cette valeur est la somme des longueurs des arguments.|  
|`ranges`|Tableau de `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, chacune représentant un bloc d’arguments de fonction.|  
  
## <a name="remarks"></a>Remarques  

 Une fonction peut avoir de nombreux arguments. Ces arguments peuvent ne pas être stockés de façon contiguë en mémoire. Vous pouvez avoir un bloc de trois arguments à un seul endroit, un bloc de deux arguments à un autre emplacement et un bloc final d’un argument à un autre emplacement. Ces arguments sont tous pour la même fonction ; ils sont simplement stockés à différents emplacements.  
  
 La `COR_PRF_FUNCTION_ARGUMENT_INFO` structure représente tous les arguments d’une fonction unique. Elle utilise un tableau pour faire référence à tous les blocs d’arguments de fonction. Ainsi, pour une fonction unique, vous avez une `COR_PRF_FUNCTION_ARGUMENT_INFO` structure unique, qui fait référence `COR_PRF_FUNCTION_ARGUMENT_RANGE` à plusieurs structures, chacune pointant vers un ou plusieurs arguments de fonction.  
  
 Les arguments stockés dans les registres sont vidés en mémoire pour générer les structures.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de profilage](profiling-structures.md)
