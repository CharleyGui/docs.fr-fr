---
title: IHostTaskManager::CallNeedsHostHook, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 7c7af1bbf3d13c3f66d525dfce69d8b49fbe045c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675137"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook, méthode

Permet à l’hôte de spécifier si le common language runtime (CLR) peut incorporer l’appel spécifié à une fonction non managée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `target`  
 dans Adresse dans le fichier exécutable portable (PE) mappé de la fonction non managée qui doit être appelée.  
  
 `pbCallNeedsHostHook`  
 à Pointeur vers une valeur booléenne qui indique si l’hôte requiert que l’appel soit raccordé.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Pour optimiser l’exécution du code, le CLR effectue une analyse de chaque appel de code non managé pendant la compilation pour déterminer si l’appel peut être Inline. `CallNeedsHostHook` permet à l’hôte de substituer cette décision en exigeant qu’un appel à une fonction non managée soit raccordé. Si l’hôte requiert un Hook, le runtime n’incorpore pas l’appel.  
  
 L’hôte nécessite généralement un raccordement à l’endroit où il doit ajuster un État à virgule flottante, ou à la réception d’une notification indiquant qu’un appel passe à un État où l’hôte ne peut pas suivre les demandes de mémoire du runtime ou les verrous pris. Lorsque l’hôte requiert que l’appel soit raccordé, le runtime avertit l’hôte des transitions vers et à partir du code managé en utilisant des appels à [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)et [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
