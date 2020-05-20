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
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615850"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager, méthode
Obtient un pointeur d’interface vers une instance de l’un des types de gestionnaires que l’hôte peut utiliser pour configurer le common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `riid`  
 dans `IID`Du type de gestionnaire à retourner. Les `IID` valeurs suivantes sont prises en charge.  
  
- IID_ICLRDebugManager : spécifie que `ppObject` sera de type [ICLRDebugManager](iclrdebugmanager-interface.md).  
  
- IID_ICLRErrorReportingManager : spécifie que `ppObject` sera de type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).  
  
- IID_ICLRGCManager : spécifie que `ppObject` sera de type [ICLRGCManager](iclrgcmanager-interface.md).  
  
- IID_ICLRHostProtectionManager : spécifie que `ppObject` sera de type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).  
  
- IID_ICLROnEventManager : spécifie que `ppObject` sera de type [ICLROnEventManager](iclroneventmanager-interface.md).  
  
- IID_ICLRPolicyManager : spécifie que `ppObject` sera de type [ICLRPolicyManager](iclrpolicymanager-interface.md).  
  
- IID_ICLRTaskManager : spécifie que `ppObject` sera de type [ICLRTaskManager](iclrtaskmanager-interface.md).  
  
 `ppObject`  
 à Pointeur d’interface vers le gestionnaire demandé, ou null, si un type de gestionnaire non valide a été demandé.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|Le type d’interface n’est pas pris en charge.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRControl, interface](iclrcontrol-interface.md)
- [IHostControl, interface](ihostcontrol-interface.md)
