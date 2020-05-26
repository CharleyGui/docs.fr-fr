---
title: IHostSemaphore::Wait, méthode
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: 22d570711c293dd8c0cc6fefd198dd46d6489bea
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803535"
---
# <a name="ihostsemaphorewait-method"></a>IHostSemaphore::Wait, méthode
Entraîne l’attente de l’instance [IHostSemaphore](ihostsemaphore-interface.md) actuelle jusqu’à ce qu’elle appartienne ou que la durée spécifiée soit écoulée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwMilliseconds`  
 dans Nombre de millisecondes à attendre avant de retourner, si l’instance actuelle `IHostSemaphore` n’appartient pas.  
  
 `option`  
 dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , en spécifiant l’action que l’hôte doit effectuer si cette opération bloque.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Wait`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_DEADLOCK|L’hôte a détecté un blocage pendant l’intervalle d’attente et a choisi l' `IHostSemaphore` instance actuelle comme victime du blocage.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostAutoEvent, interface](ihostautoevent-interface.md)
- [IHostManualEvent, interface](ihostmanualevent-interface.md)
- [IHostSemaphore, interface](ihostsemaphore-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
