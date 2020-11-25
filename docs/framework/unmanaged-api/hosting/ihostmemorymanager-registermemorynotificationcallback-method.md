---
title: IHostMemoryManager::RegisterMemoryNotificationCallback, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: edb29378412583d7cdec804b08f8f622d642b02f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731304"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback, méthode

Inscrit un pointeur vers une fonction de rappel que l’hôte appelle pour notifier le common language runtime (CLR) de la charge de mémoire actuelle sur l’ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pCallback`  
 dans Pointeur d’interface vers une instance [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) qui est implémentée par le CLR.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Étant donné que l' `ICLRMemoryNotificationCallback` interface définit une seule méthode ([ICLRMemoryNotificationCallback :: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)) et que `pCallback` est un pointeur vers une `ICLRMemoryNotificationCallback` instance fournie par le CLR, l’inscription est effective pour la fonction de rappel elle-même. L’hôte appelle `OnMemoryNotification` pour signaler des conditions de sollicitation de la mémoire, au lieu d’utiliser la fonction Win32 standard `CreateMemoryResourceNotification` . Pour plus d’informations, consultez la documentation de la plateforme Windows.  
  
> [!NOTE]
> Appels à `OnMemoryNotification` ne jamais bloquer. Ils retournent toujours immédiatement.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMemoryNotificationCallback, interface](iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager, interface](ihostmemorymanager-interface.md)
