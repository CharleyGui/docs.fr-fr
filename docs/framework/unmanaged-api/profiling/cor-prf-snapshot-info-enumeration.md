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
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867020"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO, énumération
Spécifie la quantité de données à renvoyer avec un instantané de pile dans chaque appel à la fonction [StackSnapshotCallback](stacksnapshotcallback-function.md) du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Members  
  
|Members|Description|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Indique que les valeurs doivent être passées pour tous les paramètres de `StackSnapshotCallback`, à l’exception du paramètre `context`.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Indique que les valeurs doivent être passées pour tous les paramètres de `StackSnapshotCallback`, y compris le paramètre `context`.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Indique qu’un algorithme de parcours de pile alternatif est plus simple à utiliser.|  
  
## <a name="remarks"></a>Notes  
 Les valeurs fournies par l’énumération `COR_PRF_SNAPSHOT_INFO` sont passées en tant que paramètres à la méthode [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DoStackSnapshot, méthode](icorprofilerinfo2-dostacksnapshot-method.md)
- [Énumérations de profilage](profiling-enumerations.md)
