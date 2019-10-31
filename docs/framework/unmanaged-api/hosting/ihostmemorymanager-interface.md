---
title: IHostMemoryManager, interface
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128645"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager, interface
Fournit des méthodes qui permettent au common language runtime (CLR) de faire des demandes de mémoire virtuelle via l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Avertit l’hôte que le common language runtime (CLR) a acquis la mémoire spécifiée à partir du système d’exploitation.|  
|[CreateMAlloc, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Obtient un pointeur d’interface vers une instance d' [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) utilisée pour demander des allocations de mémoire à partir d’un tas créé par l’hôte.|  
|[GetMemoryLoad, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Obtient la quantité de mémoire physique en cours d’utilisation, telle qu’elle est signalée par l’hôte.|  
|[NeedsVirtualAddressSpace, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Avertit l’hôte que le CLR va tenter d’utiliser la mémoire spécifiée.|  
|[RegisterMemoryNotificationCallback, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Inscrit un pointeur vers une fonction de rappel que l’hôte appelle pour notifier le CLR de la charge de mémoire actuelle sur l’ordinateur.|  
|[ReleasedVirtualAddressSpace, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Avertit l’hôte que le CLR a fini d’utiliser la mémoire spécifiée.|  
|[VirtualAlloc, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui réserve ou valide une région de pages dans l’espace d’adressage virtuel du processus appelant.|  
|[VirtualFree, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui libère, annule ou libère et annule la validation d’une région de pages dans l’espace d’adressage virtuel du processus appelant.|  
|[VirtualProtect, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui modifie la protection sur une région de pages validées dans l’espace d’adressage virtuel du processus appelant.|  
|[VirtualQuery, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Sert de wrapper logique pour la fonction Win32 correspondante, qui récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.|  
  
## <a name="remarks"></a>Notes  
 `IHostMemoryManager` fournit également des méthodes pour que le CLR obtienne un pointeur permettant d’effectuer des demandes de mémoire sur le tas et d’obtenir le niveau de sollicitation de la mémoire dans le processus, comme indiqué par l’hôte.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMalloc, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
