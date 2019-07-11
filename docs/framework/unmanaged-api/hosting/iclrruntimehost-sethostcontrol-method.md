---
title: ICLRRuntimeHost::SetHostControl, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cf6255bfd23b38be63cd609798643f9fa1e1f93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765770"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl, méthode
Définit le pointeur d’interface que le common language runtime (CLR) peut utiliser pour obtenir l’implémentation de l’hôte de [IHostControl, Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pHostControl`  
 [in] Pointeur d’interface vers l’implémentation de l’hôte de [IHostControl, Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetHostControl` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_CLR_ALREADY_STARTED|Le CLR a déjà été initialisé.|  
  
## <a name="remarks"></a>Notes  
 Vous devez appeler `SetHostControl` avant que le CLR est initialisé, autrement dit, avant d’appeler [méthode Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) ou utiliser une de la [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). Il est recommandé d’appeler `SetHostControl` immédiatement après l’appel [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou [fonction CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
