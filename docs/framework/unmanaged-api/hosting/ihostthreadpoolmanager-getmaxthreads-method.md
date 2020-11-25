---
title: IHostThreadPoolManager::GetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
ms.openlocfilehash: 3aecebe2803d3a795db801491d0f60a5eb7c00ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730784"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a>IHostThreadPoolManager::GetMaxThreads, méthode

Obtient le nombre maximal de threads que l’hôte conserve simultanément dans le pool de threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pdwMaxWorkerThreads`  
 à Pointeur vers le nombre maximal de threads que l’hôte gère dans le pool de threads.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMaxThreads` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR () n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|L’hôte ne fournit pas d’implémentation de `GetMaxThreads` .|  
  
## <a name="remarks"></a>Remarques  

 Le CLR appelle `GetMaxThreads` pour déterminer le nombre total de threads dans le pool de threads. La méthode [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) obtient le nombre de threads qui ne traitent pas actuellement des éléments de travail. Toutes les demandes au-dessus de la valeur retournée du `pdwMaxWorkerThreads` paramètre restent mises en file d’attente jusqu’à ce que les threads deviennent disponibles.  
  
 Si l’hôte ne fournit pas d’implémentation de `GetMaxThreads` , il doit retourner une valeur HRESULT de E_NOTIMPL.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads, méthode](ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads, méthode](ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)
