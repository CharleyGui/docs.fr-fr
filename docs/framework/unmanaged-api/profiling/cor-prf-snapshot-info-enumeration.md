---
title: COR_PRF_SNAPSHOT_INFO, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6ade4f7877e39a8307a36f3a3268f79e8b4d44fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427269"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO, énumération
Spécifie la quantité de données à renvoyer avec un instantané de pile dans chaque appel à la fonction [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membres|Description|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Indique que les valeurs doivent être passées pour tous les paramètres de `StackSnapshotCallback`, à l’exception du paramètre `context`.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Indique que les valeurs doivent être passées pour tous les paramètres de `StackSnapshotCallback`, y compris le paramètre `context`.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Indique qu’un algorithme de parcours de pile alternatif est plus simple à utiliser.|  
  
## <a name="remarks"></a>Notes  
 Les valeurs fournies par l’énumération `COR_PRF_SNAPSHOT_INFO` sont passées en tant que paramètres à la méthode [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DoStackSnapshot, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
