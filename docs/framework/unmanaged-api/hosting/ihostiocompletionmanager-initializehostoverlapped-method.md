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
ms.openlocfilehash: cf257ab86d27946c861c89dff5e6f09a42013e58
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804712"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped, méthode
Fournit à l’hôte la possibilité d’initialiser toutes les données personnalisées à ajouter à une `OVERLAPPED` structure Win32 utilisée pour les demandes d’e/s asynchrones.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pvOverlapped`  
 dans Pointeur vers la structure Win32 `OVERLAPPED` à inclure dans la requête d’e/s.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour allouer la ressource demandée.|  
  
## <a name="remarks"></a>Notes  
 Les fonctions de la plate-forme Windows utilisent la `OVERLAPPED` structure pour stocker l’état des demandes d’e/s asynchrones. Le CLR appelle la `InitializeHostOverlapped` méthode pour permettre à l’hôte d’ajouter des données personnalisées à une `OVERLAPPED` instance.  
  
> [!IMPORTANT]
> Pour atteindre le début de leur bloc de données personnalisé, les hôtes doivent définir le décalage sur la taille de la `OVERLAPPED` structure ( `sizeof(OVERLAPPED)` ).  
  
 Une valeur de retour de E_OUTOFMEMORY indique que l’hôte n’a pas réussi à initialiser ses données personnalisées. Dans ce cas, le CLR signale une erreur et fait échouer l’appel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize, méthode](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
