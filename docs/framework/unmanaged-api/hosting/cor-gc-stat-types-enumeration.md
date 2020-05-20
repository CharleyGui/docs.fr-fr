---
title: COR_GC_STAT_TYPES (énumération)
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: cca393ae34144787ab7800baec7c58209394f30e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616714"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES (énumération)
Spécifie les statistiques à enregistrer pour un garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Notes  
 Cette énumération spécifie les statistiques de la structure [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) qui doivent être définies par la méthode [ICLRGCManager :: GetStats](iclrgcmanager-getstats-method.md) .  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Enregistre le nombre de garbage collection effectués pour chaque génération.|  
|`COR_GC_MEMORYUSAGE`|Enregistre l’utilisation de la mémoire et les statistiques de taille de garbage collection.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl, GCHost. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [COR_GC_STATS, structure](cor-gc-stats-structure.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
