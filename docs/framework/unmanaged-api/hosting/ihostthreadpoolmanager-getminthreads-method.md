---
title: IHostThreadPoolManager::GetMinThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: a05cfb43b5b4a328d22c4df04049a7fa156ca080
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841930"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a>IHostThreadPoolManager::GetMinThreads, méthode
Obtient le nombre minimal de threads inactifs que l’hôte gère dans le pool de threads en prévision des demandes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `MinThreads`  
 à Pointeur vers le nombre minimal de threads de travail inactifs que l’hôte gère actuellement.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMinThreads`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|L’hôte ne fournit pas d’implémentation de `GetMinThreads` .|  
  
## <a name="remarks"></a>Remarques  
 L’hôte n’est pas requis pour fournir une implémentation de `GetMinThreads` . Dans ce cas, elle doit retourner une valeur HRESULT de E_NOTIMPL.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMaxThreads, méthode](ihostthreadpoolmanager-getmaxthreads-method.md)
- [SetMinThreads, méthode](ihostthreadpoolmanager-setminthreads-method.md)
- [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)
