---
title: COR_GC_STATS, structure
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 630c365c8710388ae3e913bedece0fb710da7cd9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768139"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS, structure
Fournit des statistiques sur le mécanisme de garbage collection du common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`Flags`|Indique les valeurs de champ doivent être calculées et retournées.|  
|`ExplicitGCCount`|Indique le nombre de garbage collection qui ont été forcés par demande externe.|  
|`GenCollectionsTaken`|Indique le nombre de garbage collections effectué pour chaque génération.|  
|`CommittedKBytes`|Le nombre total de kilo-octets validés dans tous les tas.|  
|`ReservedKBytes`|Le nombre total de kilo-octets réservés dans tous les tas.|  
|`Gen0HeapSizeKBytes`|La taille, en kilo-octets, du tas de génération zéro.|  
|`Gen1HeapSizeKBytes`|La taille, en kilo-octets, du tas de génération une.|  
|`Gen2HeapSizeKBytes`|La taille, en kilo-octets, du tas de génération deux.|  
|`LargeObjectHeapSizeKBytes`|La taille, en kilo-octets, du tas des objets volumineux.|  
|`KBytesPromotedFromGen0`|La taille, en kilo-octets, des objets promus de la génération zéro à la génération une.|  
|`KBytesPromotedFromGen1`|La taille, en kilo-octets, des objets promus de la génération une génération deux.|  
  
## <a name="remarks"></a>Notes  
 Le [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) méthode requiert le `Flags` champ la `COR_GC_STATS` structure à être définie sur une ou plusieurs valeurs de la [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) énumération pour spécifier quel les statistiques doivent être définies.  
  
 Le tableau suivant mappe les statistiques fournies par cette structure et les deux [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valeurs d’énumération, `COR_GC_COUNTS` et `COR_GC_MEMORYUSAGE`.  
  
|Spécifié par COR_GC_COUNTS|Spécifié par COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Un exemple de l’utilisation est la suivante :  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** GCHost.idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Gestion automatique de la mémoire](../../../../docs/standard/automatic-memory-management.md)
- [Nettoyage de la mémoire](../../../../docs/standard/garbage-collection/index.md)
