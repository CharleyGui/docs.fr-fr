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
ms.openlocfilehash: acf449014f5bf5683d5488f8ed2ead963676fe6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728327"
---
# <a name="iclrcontrol-interface"></a>ICLRControl, interface

Fournit des méthodes qui permettent à un hôte d’obtenir des références à, et de configurer des aspects de, le common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCLRManager, méthode](iclrcontrol-getclrmanager-method.md)|Obtient un pointeur d’interface vers une instance de l’un des types de gestionnaires que l’hôte peut utiliser pour configurer le CLR.|  
|[SetAppDomainManagerType, méthode](iclrcontrol-setappdomainmanagertype-method.md)|Définit un type dérivé de <xref:System.AppDomainManager> comme type pour les gestionnaires de domaine d’application.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
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
