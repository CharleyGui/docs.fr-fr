---
title: IHostSyncManager::CreateMonitorEvent, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: 7fc431861ac8f5c0e47e12e688f4ca004313c062
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704446"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a>IHostSyncManager::CreateMonitorEvent, méthode

Crée un objet d’événement de réinitialisation automatique surveillé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cookie`  
 dans Cookie à associer à l’objet d’événement.  
  
 `ppEvent`  
 à Pointeur vers l’adresse d’une instance [IHostAutoEvent](ihostautoevent-interface.md) , ou null si l’objet d’événement n’a pas pu être créé.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateMonitorEvent` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour créer l’objet d’événement demandé.|  
  
## <a name="remarks"></a>Remarques  

 `CreateMonitorEvent` retourne un `IHostAutoEvent` que le CLR utilise dans son implémentation du type managé <xref:System.Threading.Monitor?displayProperty=nameWithType> . Cette méthode reflète la `CreateEvent` fonction Win32, avec `false` la valeur spécifiée pour le `bManualReset` paramètre.  
  
 L’hôte peut utiliser le cookie pour déterminer quelle tâche est en attente sur l’analyse en appelant la méthode [ICLRSyncManager :: GetMonitorOwner,](iclrsyncmanager-getmonitorowner-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostAutoEvent, interface](ihostautoevent-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
