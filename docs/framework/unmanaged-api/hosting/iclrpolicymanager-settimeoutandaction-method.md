---
title: ICLRPolicyManager::SetTimeoutAndAction, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120dbfdc463a7441cce8ca7d87561998a8e28eda
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916954"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a>ICLRPolicyManager::SetTimeoutAndAction, méthode
Définit une valeur de délai d’attente pour l’opération spécifiée et spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’opération se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `operation`  
 dans L’une des valeurs [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , indiquant l’opération pour laquelle définir le délai d’attente et `action`la stratégie. Les valeurs suivantes sont prises en charge:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 dans Nouvelle valeur du délai d’attente, en millisecondes. Si la valeur est Infinite, `operation` le délai d’attente n’est jamais dépassé.  
  
 `action`  
 dans L’une des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indiquant l’action de stratégie que le CLR doit prendre `operation` lorsqu’il se produit.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Un délai d’expiration ne peut pas être `operation`défini pour le spécifié, ou une valeur `action`non valide a été fournie pour.|  
  
## <a name="remarks"></a>Notes  
 `SetTimeoutAndAction`encapsule les fonctionnalités des méthodes [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) et [ICLRPolicyManager:: SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) , et peut être appelée à la place des appels séquentiels à ces deux méthodes.  
  
> [!IMPORTANT]
> Toutes les valeurs d’action de stratégie ne peuvent pas être spécifiées comme le comportement de délai d’attente pour les opérations CLR. Consultez les sections notes des rubriques relatives à ces deux méthodes pour connaître les valeurs valides.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrOperation, énumération](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction, énumération](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnTimeout, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [ICLRPolicyManager::SetTimeoutAndAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
