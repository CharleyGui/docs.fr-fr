---
title: IHostPolicyManager, interface
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804327"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager, interface
Fournit des méthodes qui notifient l’hôte des actions que le common language runtime (CLR) effectue en cas d’abandons, de délais d’attente ou d’échecs.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnDefaultAction, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Avertit l’hôte que le CLR va prendre l’action par défaut spécifiée par un appel à [ICLRPolicyManager :: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) en réponse à l’abandon ou au <xref:System.AppDomain> déchargement d’un thread.|  
|[OnFailure, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Avertit l’hôte que le CLR est sur le point d’exécuter l’action spécifiée par un appel à [ICLRPolicyManager :: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) en réponse à une allocation de ressource ou à un échec de récupération.|  
|[OnTimeout, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Avertit l’hôte que le CLR va prendre l’action spécifiée par un appel à [ICLRPolicyManager :: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) en réponse à un délai d’attente.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](eclrfailure-enumeration.md)
- [EClrOperation, énumération](eclroperation-enumeration.md)
- [EPolicyAction, énumération](epolicyaction-enumeration.md)
- [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
