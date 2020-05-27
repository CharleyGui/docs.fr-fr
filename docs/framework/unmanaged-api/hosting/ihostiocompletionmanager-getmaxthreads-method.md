---
title: IHostIoCompletionManager::GetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: a97a7abf4f561a5aba41d8019f2ba5bd8e879acd
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804737"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a>IHostIoCompletionManager::GetMaxThreads, méthode
Obtient le nombre maximal de threads que l’hôte peut allouer aux demandes d’e/s de service.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pdwMaxIoCompletionThreads`  
 à Pointeur vers le nombre maximal de threads dans le pool de threads que l’hôte peut allouer aux demandes d’e/s de service.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMaxThreads`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|L’hôte ne fournit pas d’implémentation de `GetMaxThreads` .|  
  
## <a name="remarks"></a>Notes  
 Un hôte peut souhaiter exercer un contrôle exclusif sur le nombre de threads pouvant être alloués pour traiter les demandes d’e/s, pour des raisons telles que l’implémentation, les performances ou l’évolutivité. Pour cette raison, l’hôte n’est pas tenu d’implémenter `GetMaxThreads` . Dans ce cas, l’hôte doit retourner E_NOTIMPL à partir de cette méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
