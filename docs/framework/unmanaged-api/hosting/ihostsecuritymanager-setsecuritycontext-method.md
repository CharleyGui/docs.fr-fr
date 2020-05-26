---
title: IHostSecurityManager::SetSecurityContext, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: 79ef08ef70ad1132ceacc3e2b997651e57032b9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803810"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a>IHostSecurityManager::SetSecurityContext, méthode
Définit le contexte de sécurité du thread en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `eContextType`  
 dans L’une des valeurs [EContextType,](econtexttype-enumeration.md) , indiquant le type de contexte que le Common Language Runtime (CLR) place sur l’hôte.  
  
 `ppSecurityContext`  
 à Pointeur vers l’adresse d’un nouvel objet [IHostSecurityContext](ihostsecuritycontext-interface.md) .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetSecurityContext`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Le CLR appelle `SetSecurityContext` dans plusieurs scénarios. Avant d’exécuter des constructeurs et des finaliseurs de classe et de module, le CLR appelle `SetSecurityContext` pour protéger l’hôte des échecs d’exécution. Il réinitialise ensuite le contexte de sécurité à son état d’origine après l’exécution du constructeur ou du finaliseur, en utilisant un autre appel à `SetSecurityContext` . Un modèle similaire se produit avec l’exécution d’e/s. Si l’hôte implémente [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), le CLR appelle `SetSecurityContext` après que l’hôte a appelé [ICLRIoCompletionManager :: OnComplete](iclriocompletionmanager-oncomplete-method.md).  
  
 À des points asynchrones dans les threads de travail, le CLR appelle `SetSecurityContext` dans <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> ou dans [IHostThreadPoolManager :: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), selon que l’hôte ou le CLR implémente le pool de threads.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [EContextType, énumération](econtexttype-enumeration.md)
- [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
- [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)
