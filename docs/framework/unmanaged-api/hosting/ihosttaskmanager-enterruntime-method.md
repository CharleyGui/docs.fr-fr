---
title: IHostTaskManager::EnterRuntime, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: b255a1d35aa32975c879aac00f7d4edb8ea88d3b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842034"
---
# <a name="ihosttaskmanagerenterruntime-method"></a>IHostTaskManager::EnterRuntime, méthode
Avertit l’hôte qu’un appel à une méthode non managée, tel qu’une méthode d’appel de code non managé, retourne le contrôle d’exécution au common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EnterRuntime`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour terminer l’allocation demandée.|  
  
## <a name="remarks"></a>Remarques  
 `EnterRuntime`est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à la méthode [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) a été effectuée, a fini de s’exécuter, et retourne le contrôle d’exécution au Runtime.  
  
> [!NOTE]
> [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) est appelé pour notifier l’hôte qu’une fonction non managée, pour laquelle un appel antérieur à `LeaveRuntime` a été effectué, effectue un appel dans du code managé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Comment : appeler des DLL natives à partir de code managé à l’aide de PInvoke](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [ICLRTask, interface](iclrtask-interface.md)
- [ICLRTaskManager, interface](iclrtaskmanager-interface.md)
- [IHostTask, interface](ihosttask-interface.md)
- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
- [LeaveRuntime, méthode](ihosttaskmanager-leaveruntime-method.md)
