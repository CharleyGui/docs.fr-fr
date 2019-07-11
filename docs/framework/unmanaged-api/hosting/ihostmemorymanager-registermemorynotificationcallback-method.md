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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48580f5ac71b906c302ee7ce1b98e7d4334f2482
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767737"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback, méthode
Enregistre un pointeur vers une fonction de rappel que l’hôte appelle pour avertir le common language runtime (CLR) de la charge actuelle de la mémoire sur l’ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Un pointeur d’interface vers un [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance qui est implémentée par le CLR.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que le `ICLRMemoryNotificationCallback` interface ne définit qu’une seule méthode ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) et parce que `pCallback` est un pointeur vers un `ICLRMemoryNotificationCallback` instance fournie par le CLR, le l’inscription est efficace pour la fonction de rappel elle-même. L’hôte appelle `OnMemoryNotification` à signaler des conditions de sollicitation de la mémoire, plutôt qu’à l’aide de Win32 standard `CreateMemoryResourceNotification` (fonction). Pour plus d’informations, consultez la documentation de la plateforme de Windows.  
  
> [!NOTE]
>  Les appels à `OnMemoryNotification` ne jamais se bloquer. Elles retournent toujours immédiatement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMemoryNotificationCallback, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
