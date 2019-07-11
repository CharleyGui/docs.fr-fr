---
title: ICLRTask2::BeginPreventAsyncAbort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23ead080823ace1b091568108af8866dcbca14ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770267"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort, méthode
Nouveau thread de retards demandes d’abandon de ce qui entraîne des abandons de thread sur le thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HOST_E_INVALIDOPERATION|La méthode a été appelée sur un thread qui n’est pas le thread actuel.|  
  
## <a name="remarks"></a>Notes  
 Appel de cette méthode incrémente le compteur de délai d’abandon de thread pour le thread actuel d’une unité.  
  
 Les appels à `BeginPreventAsyncAbort` et [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) peuvent être imbriqués. Tant que le compteur est supérieur à zéro, pour le thread actuel abandons de thread. Si cet appel n’est pas associé à un appel à la `EndPreventAsyncAbort` (méthode), il est possible d’atteindre un état dans lequel thread abandons ne peut pas être remis au thread actuel.  
  
 Le délai n’est pas reconnue pour un thread qui abandonne lui-même.  
  
 La fonctionnalité exposée par cette fonctionnalité est utilisée en interne par la machine virtuelle (VM). Une mauvaise utilisation de ces méthodes peut-être provoquer un comportement non spécifié dans la machine virtuelle. Par exemple, l’appel `EndPreventAsyncAbort` sans appeler d’abord `BeginPreventAsyncAbort` Impossible de définir le compteur à zéro lors de la machine virtuelle a précédemment incrémenté. De même, le compteur interne n’est pas vérifié pour dépassement de capacité. S’il dépasse sa limite intégrale, car il est incrémenté par l’hôte et la machine virtuelle, le comportement résultant n’est pas spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EndPreventAsyncAbort, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [ICLRTask2, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
