---
title: ICLRPolicyManager::SetActionOnFailure, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 143052febe136e969987c35bc06f6c3b3356aedf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140783"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure, méthode
Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’échec spécifié se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `failure`  
 dans L’une des valeurs [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) , indiquant le type d’échec pour lequel agir.  
  
 `action`  
 dans L’une des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , indiquant l’action à entreprendre en cas d’échec. Pour obtenir la liste des valeurs prises en charge, consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois qu’une méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Impossible de définir une action de stratégie pour l’opération spécifiée ou une action de stratégie non valide a été spécifiée pour l’opération.|  
  
## <a name="remarks"></a>Notes  
 Par défaut, le CLR lève une exception lorsqu’il ne parvient pas à allouer une ressource telle que la mémoire. `SetActionOnFailure` permet à l’hôte de remplacer ce comportement en spécifiant l’action de stratégie à prendre en cas d’échec. Le tableau suivant présente les combinaisons de valeurs [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) et [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) qui sont prises en charge. (Le préfixe FAIL_ est omis des valeurs [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) .)  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|x|x||||N/A||  
|eThrowException|x|x||||N/A||  
|`eAbortThread`|x|x||||N/A|x|  
|`eRudeAbortThread`|x|x||||N/A|x|  
|`eUnloadAppDomain`|x|x||x||N/A|x|  
|`eRudeUnloadAppDomain`|x|x||x|x|N/A|x|  
|`eExitProcess`|x|x||x|x|N/A|x|  
|eFastExitProcess|x|x||x|x|N/A||  
|`eRudeExitProcess`|x|x|x|x|x|N/A||  
|`eDisableRuntime`|x|x|x|x|x|N/A||  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction, énumération](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
