---
title: IHostTaskManager::SetLocale, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 7730c2dddaca98e4cb06cdb381e8a46ff23c97f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699194"
---
# <a name="ihosttaskmanagersetlocale-method"></a>IHostTaskManager::SetLocale, méthode

Avertit l’hôte que le common language runtime (CLR) a modifié les paramètres régionaux, ou la culture, sur la tâche en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `lcid`  
 dans Valeur de l’identificateur de paramètres régionaux qui correspond à la culture géographique et à la langue qui viennent d’être attribuées.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetLocale` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|L’hôte n’autorise pas le code utilisateur managé à modifier les paramètres régionaux.|  
  
## <a name="remarks"></a>Remarques  

 Le runtime appelle `SetLocale` lorsque la valeur de la <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> propriété est modifiée par le code managé. Cette méthode permet à l’hôte d’exécuter tous les mécanismes qu’il peut avoir pour la synchronisation des paramètres régionaux. Si un hôte n’autorise pas la modification des paramètres régionaux à partir du code managé, ou n’implémente pas de mécanisme pour synchroniser des paramètres régionaux, il doit retourner E_NOTIMPL à partir de cette méthode.  
  
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
- [SetUILocale, méthode](ihosttaskmanager-setuilocale-method.md)
