---
title: ICLRControl, interface
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615835"
---
# <a name="iclrcontrol-interface"></a>ICLRControl, interface
Fournit des méthodes qui permettent à un hôte d’obtenir des références à, et de configurer des aspects de, le common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCLRManager, méthode](iclrcontrol-getclrmanager-method.md)|Obtient un pointeur d’interface vers une instance de l’un des types de gestionnaires que l’hôte peut utiliser pour configurer le CLR.|  
|[SetAppDomainManagerType, méthode](iclrcontrol-setappdomainmanagertype-method.md)|Définit un type dérivé de <xref:System.AppDomainManager> comme type pour les gestionnaires de domaine d’application.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRDebugManager, interface](iclrdebugmanager-interface.md)
- [ICLRGCManager, interface](iclrgcmanager-interface.md)
- [ICLRHostBindingPolicyManager, interface](iclrhostbindingpolicymanager-interface.md)
- [ICLRHostProtectionManager, interface](iclrhostprotectionmanager-interface.md)
- [ICLROnEventManager, interface](iclroneventmanager-interface.md)
- [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)
- [IHostControl, interface](ihostcontrol-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
