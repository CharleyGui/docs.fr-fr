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
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501662"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS, structure
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
|`Flags`|Indique les valeurs de champ qui doivent être calculées et retournées.|  
|`ExplicitGCCount`|Indique le nombre de garbage collection qui ont été forcés par une requête externe.|  
|`GenCollectionsTaken`|Indique le nombre de garbage collection effectués pour chaque génération.|  
|`CommittedKBytes`|Nombre total de kilo-octets validés dans tous les tas.|  
|`ReservedKBytes`|Nombre total de kilo-octets réservés dans tous les tas.|  
|`Gen0HeapSizeKBytes`|Taille, en kilo-octets, du tas de génération zéro.|  
|`Gen1HeapSizeKBytes`|Taille, en kilo-octets, du tas de génération-un.|  
|`Gen2HeapSizeKBytes`|Taille, en kilo-octets, du tas de la génération-2.|  
|`LargeObjectHeapSizeKBytes`|Taille, en kilo-octets, du tas d’objets volumineux.|  
|`KBytesPromotedFromGen0`|Taille, en kilo-octets, des objets promus de la génération zéro à la génération 1.|  
|`KBytesPromotedFromGen1`|Taille, en kilo-octets, des objets promus de la génération 1 à la génération 2.|  
  
## <a name="remarks"></a>Remarques  
 La méthode [ICLRGCManager :: GetStats](iclrgcmanager-getstats-method.md) exige que le `Flags` champ de la `COR_GC_STATS` structure soit défini sur une ou plusieurs valeurs de l’énumération [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) pour spécifier les statistiques à définir.  
  
 Le tableau suivant mappe les statistiques fournies par cette structure aux deux [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) valeurs d’énumération, `COR_GC_COUNTS` et `COR_GC_MEMORYUSAGE` .  
  
|Spécifié par COR_GC_COUNTS|Spécifié par COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Voici un exemple d’utilisation :  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures d'hébergement](hosting-structures.md)
- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
