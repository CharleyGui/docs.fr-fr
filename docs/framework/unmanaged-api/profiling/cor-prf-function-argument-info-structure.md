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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 658b88349bedcbcefd0b97226c7bd1fa34f656c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781920"
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO, structure
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
|`numRanges`|Le nombre de blocs d’arguments. Autrement dit, cette valeur est le nombre de [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures dans le `ranges` tableau.|  
|`totalArgumentSize`|La taille totale de tous les arguments. En d’autres termes, cette valeur est la somme des longueurs d’argument.|  
|`ranges`|Un tableau de `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, chacun d’eux représente un bloc d’arguments de fonction.|  
  
## <a name="remarks"></a>Notes  
 Une fonction peut avoir d’arguments. Ces arguments ne peuvent pas être stockés de façon contiguë en mémoire. Vous pouvez avoir un bloc de trois arguments au même endroit, un bloc de deux arguments à un autre endroit et un bloc final d’un argument dans un emplacement différent. Ces arguments sont tous pour la même fonction ; elles sont simplement stockées dans différents emplacements.  
  
 Le `COR_PRF_FUNCTION_ARGUMENT_INFO` structure représente tous les arguments d’une fonction unique. Elle utilise un tableau pour référencer tous les blocs d’arguments de fonction. Par conséquent, pour une fonction unique, vous avez un seul `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, qui fait référence à plusieurs `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, chacun d’eux pointe vers un ou plusieurs arguments de fonction.  
  
 Les arguments qui sont stockés dans les registres sont dispersées dans la mémoire pour générer les structures.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
