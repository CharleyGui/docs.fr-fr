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
ms.openlocfilehash: d01b864be231e5b0a3fd72dc2f3636a87c8cae83
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448630"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION, énumération
Identifie une génération de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|L’objet est stocké en tant que génération 0.|  
|`COR_PRF_GC_GEN_1`|L’objet est stocké en tant que génération 1.|  
|`COR_PRF_GC_GEN_2`|L’objet est stocké en tant que génération 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|L’objet est stocké dans le tas d’objets volumineux.|  
  
## <a name="remarks"></a>Notes  
 Le garbage collector améliore les performances de gestion de la mémoire en divisant les objets en générations en fonction de leur âge. Le « garbage collector » utilise actuellement trois générations, numérotées 0, 1 et 2, ainsi qu’un segment de tas spécial utilisé pour les objets volumineux. Les objets dont la taille est supérieure à une valeur particulière sont stockés dans le tas d’objets volumineux. Les autres objets alloués commencent à appartenir à la génération 0. Tous les objets qui existent après garbage collection se produisent dans la génération 0 sont promus à la génération 1. Les objets qui existent après garbage collection se produisent dans la génération 1 sont déplacés dans la génération 2.  
  
 L’utilisation de générations signifie que le garbage collector ne doit utiliser qu’un sous-ensemble des objets alloués à un moment donné.  
  
 L’énumération `COR_PRF_GC_GENERATION` est utilisée par la structure [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
