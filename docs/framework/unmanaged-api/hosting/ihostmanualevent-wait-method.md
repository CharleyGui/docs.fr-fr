---
title: IHostManualEvent::Wait, méthode
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
ms.openlocfilehash: 3fe8434ba4a7fc49b99bdf3084ce4f3981f25a9b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719825"
---
# <a name="ihostmanualeventwait-method"></a>IHostManualEvent::Wait, méthode

Entraîne l’attente de l’instance [IHostManualEvent](ihostmanualevent-interface.md) actuelle jusqu’à ce qu’elle appartienne ou qu’un laps de temps spécifié se soit écoulé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwMilliseconds`  
 dans Nombre de millisecondes à attendre avant de retourner, si l’instance actuelle `IHostManualEvent` n’appartient pas.  
  
 `option`  
 dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si cette opération bloque.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Wait` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_DEADLOCK|L’hôte a détecté un blocage pendant l’intervalle d’attente et a choisi l' `IHostManualEvent` instance actuelle comme victime du blocage.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostAutoEvent, interface](ihostautoevent-interface.md)
- [IHostManualEvent, interface](ihostmanualevent-interface.md)
- [IHostSemaphore, interface](ihostsemaphore-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
