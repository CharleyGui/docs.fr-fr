---
title: IHostCrst, interface
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130523"
---
# <a name="ihostcrst-interface"></a>IHostCrst, interface
Sert de représentation de l’hôte d’une section critique pour le Threading.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Enter, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Entre dans la section critique.|  
|[Leave, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Quitte la section critique.|  
|[SetSpinCount, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Définit le nombre de spins pour la section critique.|  
|[TryEnter, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Tente d’entrer dans la section critique et signale la réussite ou l’échec immédiatement.|  
  
## <a name="remarks"></a>Notes  
 `IHostCrst` permet au common language runtime (CLR) de communiquer directement avec la représentation de l’hôte d’une section critique, plutôt que d’utiliser des fonctions Win32 comme `EnterCriticalSection` ou `LeaveCriticalSection`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
