---
title: IHostCrst::SetSpinCount, méthode
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: 22274759f931da614a234efe0a6f6eb3aade027c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729562"
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount, méthode

Définit le nombre de spins pour l’instance [IHostCrst](ihostcrst-interface.md) actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwSpinCount`  
 dans Nouveau nombre de spins pour l' `IHostCrst` instance actuelle.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetSpinCount` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Sur les systèmes multiprocesseurs, si la section critique représentée par l' `IHostCrst` instance actuelle n’est pas disponible, un thread appelant fait tourner les `dwSpinCount` heures avant d’appeler [IHostSemaphore :: wait](ihostsemaphore-wait-method.md) sur un sémaphore associé à la section critique. Si la section critique devient libre pendant l’opération de rotation, le thread appelant évite l’opération d’attente.  
  
 L’utilisation de `dwSpinCount` est identique à l’utilisation du paramètre du même nom dans la `InitializeCriticalSectionAndSpinCount` fonction Win32.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostCrst, interface](ihostcrst-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
