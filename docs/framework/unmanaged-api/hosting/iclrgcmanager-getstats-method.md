---
title: ICLRGCManager::GetStats, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 70fe8b132f03925c41b6bc7aae8e60fea1b05202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678270"
---
# <a name="iclrgcmanagergetstats-method"></a>ICLRGCManager::GetStats, méthode

Obtient un jeu de statistiques actuelles sur le système de garbage collection du common language runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pStats`  
 [in, out] Instance [COR_GC_STATS](cor-gc-stats-structure.md) qui contient les statistiques demandées.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetStats` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Le CLR calcule et retourne uniquement les statistiques qui sont spécifiées par le `Flags` champ de `pStats` .  
  
 Définissez le `Flags` champ sur une ou plusieurs valeurs de l’énumération [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) pour spécifier les statistiques de la structure [COR_GC_STATS](cor-gc-stats-structure.md) à définir.  
  
 Voici un exemple d’utilisation :  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS, structure](cor-gc-stats-structure.md)
- [COR_GC_STAT_TYPES (énumération)](cor-gc-stat-types-enumeration.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLRGCManager, interface](iclrgcmanager-interface.md)
- [Interfaces d'hébergement du CLR](clr-hosting-interfaces.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
