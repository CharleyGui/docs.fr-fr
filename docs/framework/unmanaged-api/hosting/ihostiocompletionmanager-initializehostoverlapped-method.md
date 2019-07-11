---
title: IHostIoCompletionManager::InitializeHostOverlapped, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d27799e427efd3659dc2864e7d1e8e2061c5c19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780776"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped, méthode
Fournit à l’hôte avec la possibilité d’initialiser toutes les données personnalisées à ajouter à un Win32 `OVERLAPPED` structure qui est utilisé pour les demandes d’e/s asynchrones.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pvOverlapped`  
 [in] Un pointeur vers Win32 `OVERLAPPED` structure pour être inclus dans la demande d’e/s.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire était insuffisante pour allouer la ressource demandée.|  
  
## <a name="remarks"></a>Notes  
 La plateforme Windows fonctions utilisent la `OVERLAPPED` structure pour stocker l’état des demandes d’e/s asynchrones. Le CLR appelle le `InitializeHostOverlapped` méthode pour permettre à l’hôte pour ajouter des données personnalisées à un `OVERLAPPED` instance.  
  
> [!IMPORTANT]
>  Pour atteindre le début de leur bloc de données personnalisées, les hôtes doivent définir le décalage à la taille de la `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).  
  
 Une valeur de retour E_OUTOFMEMORY indique que l’hôte n’a pas pu initialiser ses données personnalisées. Dans ce cas, le CLR signale une erreur et fait échouer l’appel.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
