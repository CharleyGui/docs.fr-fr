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
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176524"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS, structure
Fournit des statistiques sur le mécanisme de collecte des ordures de l’heure courante de course de langue (CLR).  
  
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
|`Flags`|Indique quelles valeurs de champ doivent être calculées et retournées.|  
|`ExplicitGCCount`|Indique le nombre de collectes d’ordures qui ont été forcées à la demande externe.|  
|`GenCollectionsTaken`|Indique le nombre de collectes d’ordures effectuées pour chaque génération.|  
|`CommittedKBytes`|Le nombre total de kilooctets commis dans tous les tas.|  
|`ReservedKBytes`|Le nombre total de kilooctets réservés dans tous les tas.|  
|`Gen0HeapSizeKBytes`|La taille, en kilooctets, du tas de génération zéro.|  
|`Gen1HeapSizeKBytes`|La taille, en kilooctets, du tas de génération un.|  
|`Gen2HeapSizeKBytes`|La taille, en kilooctets, du tas de génération-deux.|  
|`LargeObjectHeapSizeKBytes`|La taille, en kilooctets, du grand tas d’objets.|  
|`KBytesPromotedFromGen0`|La taille, en kilooctets, des objets promus de la génération zéro à la première génération.|  
|`KBytesPromotedFromGen1`|La taille, en kilooctets, des objets promus de la première génération à la deuxième génération.|  
  
## <a name="remarks"></a>Notes   
 La méthode [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) méthode exige que le `Flags` champ de la `COR_GC_STATS` structure doit être mis à une ou plusieurs valeurs de [l’énumération COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) pour spécifier quelles statistiques doivent être définies.  
  
 Le tableau suivant dresse la carte des statistiques fournies par cette `COR_GC_COUNTS` `COR_GC_MEMORYUSAGE`structure aux deux [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valeurs d’énumération, et .  
  
|Spécifié par COR_GC_COUNTS|Spécifié par COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Un exemple de l’utilisation est le suivant :  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** GCHost.idl  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
