---
title: ICLRSyncManager::CreateRWLockOwnerIterator, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: f8fde4905c41dffde90c6361b5a8cdffa15deb4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503963"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator, méthode
Demande que le common language runtime (CLR) crée un itérateur que l’hôte doit utiliser pour déterminer l’ensemble des tâches en attente sur un verrou de lecteur-writer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cookie`  
 dans Cookie associé au verrou lecteur-writer souhaité.  
  
 `pIterator`  
 à Pointeur vers un itérateur qui peut être passé aux méthodes [GetRWLockOwnerNext,](iclrsyncmanager-getrwlockownernext-method.md) et [DeleteRWLockOwnerIterator,](iclrsyncmanager-deleterwlockowneriterator-method.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`a été appelé sur un thread qui exécute actuellement du code managé.|  
  
## <a name="remarks"></a>Remarques  
 En général, les hôtes appellent les `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` méthodes, et `GetRWLockOwnerNext` pendant la détection des verrous mortels. L’hôte est chargé de s’assurer que le verrou lecteur-writer est toujours valide, car le CLR n’effectue aucune tentative de maintien du verrou de lecture-écriture. Plusieurs stratégies sont disponibles pour l’hôte afin de garantir la validité du verrou :  
  
- L’hôte peut bloquer les appels de version sur le verrou lecteur-writer (par exemple, [IHostSemaphore :: ReleaseSemaphore,](ihostsemaphore-releasesemaphore-method.md)) tout en veillant à ce que ce bloc ne provoque pas d’interblocage.  
  
- L’hôte peut empêcher la sortie d’attendre l’objet d’événement associé au verrou lecteur-writer, ce qui garantit que ce bloc ne provoque pas d’interblocage.  
  
> [!NOTE]
> `CreateRWLockOwnerIterator`doit être appelé uniquement sur les threads qui exécutent actuellement du code non managé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
