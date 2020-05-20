---
title: ICLRPolicyManager, interface
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703474"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager, interface
Fournit des méthodes qui permettent à l’hôte de spécifier des actions de stratégie à prendre en cas d’échecs et de délais d’attente.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetActionOnFailure, méthode](iclrpolicymanager-setactiononfailure-method.md)|Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’échec spécifié se produit.|  
|[SetActionOnTimeout, méthode](iclrpolicymanager-setactionontimeout-method.md)|Spécifie l’action de stratégie que le CLR doit prendre lorsque l’opération spécifiée expire.|  
|[SetDefaultAction, méthode](iclrpolicymanager-setdefaultaction-method.md)|Spécifie l’action de stratégie que le CLR doit prendre lorsque l’opération spécifiée se produit.|  
|[SetTimeout, méthode](iclrpolicymanager-settimeout-method.md)|Définit une valeur de délai d’attente pour l’opération spécifiée.|  
|[SetTimeoutAndAction, méthode](iclrpolicymanager-settimeoutandaction-method.md)|Définit une valeur de délai d’attente pour l’opération spécifiée et spécifie l’action de stratégie que le CLR doit prendre lorsque l’opération se produit.|  
|[SetUnhandledExceptionPolicy, méthode](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Spécifie le comportement du CLR lorsqu’une exception non gérée se produit.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](eclrfailure-enumeration.md)
- [EClrOperation, énumération](eclroperation-enumeration.md)
- [EPolicyAction, énumération](epolicyaction-enumeration.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
