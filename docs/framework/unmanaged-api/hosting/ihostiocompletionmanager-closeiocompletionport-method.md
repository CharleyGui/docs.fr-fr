---
title: IHostIoCompletionManager::CloseIoCompletionPort, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 5e2e49b4c993e127a31b54d40f721e0714198780
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804774"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a>IHostIoCompletionManager::CloseIoCompletionPort, méthode
Demande que l’hôte ferme un port qui a été ouvert par un appel antérieur à [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hPort`  
 dans Handle du port à fermer.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CloseIoCompletionPort`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Un descripteur de port non valide a été passé.|  
  
## <a name="remarks"></a>Notes  
 `hPort`doit être un handle vers un port qui a été créé par un appel antérieur à `CreateIoCompletionPort` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
