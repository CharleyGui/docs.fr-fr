---
title: IHostPolicyManager::OnDefaultAction, méthode
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: a22f16c14514b90ce888fafc0ea554bd9f90cb11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684081"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a>IHostPolicyManager::OnDefaultAction, méthode

Avertit l’hôte que le common language runtime (CLR) est sur le point d’exécuter l’action par défaut qui a été définie par un appel à la méthode [ICLRPolicyManager :: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) en réponse à l’abandon ou au <xref:System.AppDomain> déchargement d’un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `operation`  
 dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant le type d’événement auquel le CLR répond.  
  
 `action`  
 dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action que le CLR prend en réponse à l’événement.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OnDefaultAction` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter l’appel. correctement|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrOperation, énumération](eclroperation-enumeration.md)
- [EPolicyAction, énumération](epolicyaction-enumeration.md)
- [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)
- [IHostPolicyManager, interface](ihostpolicymanager-interface.md)
