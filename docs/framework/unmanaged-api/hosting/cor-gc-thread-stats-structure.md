---
title: COR_GC_THREAD_STATS, structure
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 25a90965dc5466b7cf1a07140705424cf2ba4cd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699233"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS, structure

Contient des statistiques par thread relatives à garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`PerThreadAllocation`|Nombre d’octets de mémoire alloués sur le thread associé à l’instance actuelle `COR_GC_THREAD_STATS` . Ce nombre est effacé à zéro chaque fois qu’un garbage collection de génération zéro se produit.|  
|`Flags`|Nombre d’octets promus à une génération supérieure au garbage collection le plus récent.|  
  
## <a name="remarks"></a>Remarques  

 [ICLRTask :: GetMemStats,](iclrtask-getmemstats-method.md) accepte un paramètre de sortie de type `COR_GC_THREAD_STATS` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
- [IHostTask, interface](ihosttask-interface.md)
