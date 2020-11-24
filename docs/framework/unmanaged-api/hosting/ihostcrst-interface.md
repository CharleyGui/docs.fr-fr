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
ms.openlocfilehash: 350af708456914c73929d2b8887173cf784d4294
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680554"
---
# <a name="ihostcrst-interface"></a>IHostCrst, interface

Sert de représentation de l’hôte d’une section critique pour le Threading.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Enter, méthode](ihostcrst-enter-method.md)|Entre dans la section critique.|  
|[Leave, méthode](ihostcrst-leave-method.md)|Quitte la section critique.|  
|[SetSpinCount, méthode](ihostcrst-setspincount-method.md)|Définit le nombre de spins pour la section critique.|  
|[TryEnter, méthode](ihostcrst-tryenter-method.md)|Tente d’entrer dans la section critique et signale la réussite ou l’échec immédiatement.|  
  
## <a name="remarks"></a>Remarques  

 `IHostCrst` permet à l’common language runtime (CLR) de communiquer directement avec la représentation de l’hôte d’une section critique, plutôt que d’utiliser des fonctions Win32 telles que `EnterCriticalSection` ou `LeaveCriticalSection` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
