---
title: ICLRDebugManager::EndConnection, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2af6970907eb9895750ca58065b2e0cb735cea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969405"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection, méthode
Supprime l’association entre une liste de tâches et un identificateur et un nom convivial.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwConnectionId`  
 dans Identificateur spécifique à l’hôte pour la connexion et la liste associée de tâches common language runtime (CLR).  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EndConnection`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) n’a jamais été `dwConnectionId`appelé à `dwConnectionId` l’aide de, ou était égal à zéro.|  
  
## <a name="remarks"></a>Notes  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) fournit trois méthodes, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)et `EndConnection`, pour associer des listes de tâches à des identificateurs et des noms conviviaux.  
  
> [!IMPORTANT]
> Ces trois méthodes doivent être appelées dans un ordre spécifique pour chaque ensemble de tâches. `BeginConnection`est appelé en premier pour établir une nouvelle connexion. `SetConnectionTasks`est appelé ensuite pour fournir l’ensemble des tâches à associer à cette connexion. `EndConnection`est appelé en dernier pour supprimer l’association entre la liste des tâches et l’identificateur et le nom convivial. Toutefois, les appels de différentes connexions peuvent être imbriqués.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [SetConnectionTasks, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
