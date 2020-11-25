---
title: COR_PRF_GC_GENERATION, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: 1d7489e997868a9486f77d176580cee18213a99d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718555"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION, énumération

Identifie une génération de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|L’objet est stocké en tant que génération 0.|  
|`COR_PRF_GC_GEN_1`|L’objet est stocké en tant que génération 1.|  
|`COR_PRF_GC_GEN_2`|L’objet est stocké en tant que génération 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|L’objet est stocké dans le tas d’objets volumineux.|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|L’objet est stocké dans le tas d’objets épinglés.|  
  
## <a name="remarks"></a>Remarques  

 Le garbage collector améliore les performances de gestion de la mémoire en divisant les objets en générations en fonction de leur âge. Le « garbage collector » utilise actuellement trois générations, numérotées 0, 1 et 2, et deux segments de tas spéciaux, un pour les objets volumineux et un pour les objets épinglés.
  
 Les objets dont la taille est supérieure à une valeur de seuil sont stockés dans le tas d’objets volumineux. Les objets épinglés peuvent être alloués au tas d’objets épinglés afin d’éviter les coûts de performance liés à leur allocation sur les tas normaux. Les autres objets alloués commencent à appartenir à la génération 0. Tous les objets qui existent après garbage collection se produisent dans la génération 0 sont promus à la génération 1. Les objets qui existent après garbage collection se produisent dans la génération 1 sont déplacés dans la génération 2.  
  
 L’utilisation de générations signifie que le garbage collector ne doit utiliser qu’un sous-ensemble des objets alloués à un moment donné.  
  
 L' `COR_PRF_GC_GENERATION` énumération est utilisée par la structure [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
