---
title: ICLRIoCompletionManager::OnComplete, méthode
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 15119974acf74b49669e5ffbee59fbff9e5c84c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714098"
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete, méthode

Notifie le common language runtime (CLR) de l’état d’une demande d’e/s qui a été effectuée à l’aide d’un appel à la méthode [IHostIoCompletionManager :: bind](ihostiocompletionmanager-bind-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwErrorCode`  
 dans Valeur HRESULT qui indique l’état de l’opération de liaison.  
  
- S_OK indique que l’opération s’est terminée avec succès.  
  
- HOST_E_INTERRUPTED indique que l’appel s’est terminé avant l’achèvement.  
  
- E_FAIL indique qu’une erreur catastrophique, irrécupérable ou inconnue s’est produite.  
  
 `NumberOfBytesTransferred`  
 dans Nombre d’octets transférés pendant le traitement de la requête d’e/s.  
  
 `pvOverlapped`  
 dans Pointeur vers la `OVERLAPPED` structure qui a été passée à l’appel à la `IHostIoCompletionManager::Bind` méthode.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OnComplete` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Si l’hôte implémente une abstraction d’achèvement d’e/s, le CLR effectue des demandes d’e/s via l’hôte à l’aide de méthodes de [IHostIoCompletionManager](ihostiocompletionmanager-interface.md). L’hôte appelle ensuite la `OnComplete` méthode pour notifier l’exécution du résultat de ces requêtes.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager, interface](ihostthreadpoolmanager-interface.md)
