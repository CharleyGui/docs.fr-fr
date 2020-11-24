---
title: ICLRSyncManager::GetMonitorOwner, méthode
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: a2cb82d8071518af4d4bc3276871f3846a5a5693
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687079"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>ICLRSyncManager::GetMonitorOwner, méthode

Obtient l’instance [IHostTask](ihosttask-interface.md) qui possède le moniteur identifié par le cookie spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cookie`  
 dans Cookie associé à l’analyse.  
  
 `ppOwnerHostTask`  
 à Pointeur vers `IHostTask` qui possède actuellement le moniteur, ou null si aucune tâche n’est propriétaire.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 L’hôte appelle généralement dans le cadre `GetMonitorOwner` d’un mécanisme de détection des verrous mortels. Le cookie est associé à une analyse lorsqu’il est créé à l’aide d’un appel à [IHostSyncManager :: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).  
  
> [!NOTE]
> Un appel pour libérer l’événement sous-jacent du moniteur peut se bloquer, mais n’interbloquera pas, si un appel à cette méthode est actuellement en vigueur sur le cookie associé à cette analyse. D’autres tâches peuvent également se bloquer si elles essaient d’acquérir ce moniteur.  
  
 `GetMonitorOwner` retourne toujours immédiatement et peut être appelé à tout moment après un appel à `CreateMonitorEvent` . L’hôte n’a pas besoin d’attendre qu’une tâche attende l’événement.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
