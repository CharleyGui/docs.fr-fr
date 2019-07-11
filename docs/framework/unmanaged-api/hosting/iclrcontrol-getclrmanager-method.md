---
title: ICLRControl::GetCLRManager, méthode
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86299a1f64120b3ca0ec858975b824b7e7288af9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773264"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager, méthode
Obtient un pointeur d’interface vers une instance d’un des types de gestionnaires que l’hôte peut utiliser pour configurer le common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `riid`  
 [in] Le `IID` du type de gestionnaire à retourner. Ce qui suit `IID` valeurs sont prises en charge.  
  
- IID_ICLRDebugManager: Spécifie que `ppObject` sera de type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).  
  
- IID_ICLRErrorReportingManager: Spécifie que `ppObject` sera de type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).  
  
- IID_ICLRGCManager : Spécifie que `ppObject` sera de type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).  
  
- IID_ICLRHostProtectionManager: Spécifie que `ppObject` sera de type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).  
  
- IID_ICLROnEventManager: Spécifie que `ppObject` sera de type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).  
  
- IID_ICLRPolicyManager: Spécifie que `ppObject` sera de type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).  
  
- IID_ICLRTaskManager: Spécifie que `ppObject` sera de type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).  
  
 `ppObject`  
 [out] Un pointeur d’interface vers le gestionnaire demandé, ou null, si un type de gestionnaire non valide a été demandé.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La méthode a été retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|Le type d’interface n’est pas pris en charge.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [IHostControl, interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
