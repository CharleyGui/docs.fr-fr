---
title: CorRuntimeHost, coclasse
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136907"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost, coclasse
Fournit des interfaces pour la gestion des applications exécutées par l’common language runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|[ICorConfiguration, interface](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Fournit des méthodes pour configurer le common language runtime (CLR).|  
|[ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Fournit des méthodes qui permettent à l’hôte de démarrer et d’arrêter le common language runtime explicitement, de créer et configurer des domaines d’application, d’accéder au domaine par défaut et d’énumérer tous les domaines qui s’exécutent dans le processus.|  
|[IDebuggerInfo, interface](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.|  
|[IGCHost, interface](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.|  
|IValidator|Fournit des méthodes pour la validation des images exécutables portables et un rapport détaillé des erreurs de validation.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Coclasses d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
