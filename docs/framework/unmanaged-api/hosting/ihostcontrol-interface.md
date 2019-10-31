---
title: IHostControl, interface
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195881"
---
# <a name="ihostcontrol-interface"></a>IHostControl, interface
Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetHostManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|Obtient un pointeur d’interface vers l’implémentation de l’hôte de l’interface avec le `IID`spécifié.|  
|[SetAppDomainManager, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|Avertit l’hôte qu’un domaine d’application a été créé.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
