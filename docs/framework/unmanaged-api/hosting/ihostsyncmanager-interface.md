---
title: IHostSyncManager, interface
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: e96492270c403f93687245cee8b680dc16b3c787
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803122"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager, interface
Fournit des méthodes qui permettent au common language runtime (CLR) de créer des primitives de synchronisation en appelant l’hôte au lieu d’utiliser les fonctions de synchronisation Win32.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateAutoEvent, méthode](ihostsyncmanager-createautoevent-method.md)|Crée un objet d’événement à réinitialisation automatique.|  
|[CreateCrst, méthode](ihostsyncmanager-createcrst-method.md)|Crée un objet de section critique pour la synchronisation.|  
|[CreateCrstWithSpinCount, méthode](ihostsyncmanager-createcrstwithspincount-method.md)|Crée un objet de section critique avec le nombre de spins pour la synchronisation.|  
|[CreateManualEvent, méthode](ihostsyncmanager-createmanualevent-method.md)|Crée un objet d’événement de réinitialisation manuelle.|  
|[CreateMonitorEvent, méthode](ihostsyncmanager-createmonitorevent-method.md)|Crée un objet d’événement de réinitialisation automatique surveillé.|  
|[CreateRWLockReaderEvent, méthode](ihostsyncmanager-createrwlockreaderevent-method.md)|Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.|  
|[CreateRWLockWriterEvent, méthode](ihostsyncmanager-createrwlockwriterevent-method.md)|Crée un objet d’événement à réinitialisation automatique pour l’implémentation d’un verrou de writer.|  
|[CreateSemaphore, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Crée un objet [IHostSemaphore](ihostsemaphore-interface.md) pour le CLR à utiliser comme sémaphore pour les événements d’attente.|  
|[SetCLRSyncManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Définit l’instance de [ICLRSyncManager](iclrsyncmanager-interface.md) à associer à l' `IHostSyncManager` instance actuelle.|  
  
## <a name="remarks"></a>Notes  
 Le CLR Découvre l’implémentation de l’hôte de `IHostSyncManager` en appelant la méthode [IHostControl :: GetHostManager,](ihostcontrol-gethostmanager-method.md) avec un `IID` de IID_IHostSyncManager.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
