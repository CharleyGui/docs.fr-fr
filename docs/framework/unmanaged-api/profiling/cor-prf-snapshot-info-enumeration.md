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
ms.openlocfilehash: 5290db008bfe5727ed5899c2ed6f7e41ae9a353a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716354"
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
  
## <a name="members"></a>Membres  
  
|Membres|Description|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Indique que les valeurs doivent être passées pour tous les `StackSnapshotCallback` paramètres, à l’exception du `context` paramètre.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Indique que les valeurs doivent être passées pour tous les `StackSnapshotCallback` paramètres, y compris le `context` paramètre.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Indique qu’un algorithme de parcours de pile alternatif est plus simple à utiliser.|  
  
## <a name="remarks"></a>Remarques  

 Les valeurs fournies par l' `COR_PRF_SNAPSHOT_INFO` énumération sont passées en tant que paramètres à la méthode [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DoStackSnapshot, méthode](icorprofilerinfo2-dostacksnapshot-method.md)
- [Énumérations de profilage](profiling-enumerations.md)
