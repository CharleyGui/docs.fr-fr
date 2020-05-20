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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616516"
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
|[ICorConfiguration, interface](icorconfiguration-interface.md)|Fournit des méthodes pour configurer le common language runtime (CLR).|  
|[ICorRuntimeHost, interface](icorruntimehost-interface.md)|Fournit des méthodes qui permettent à l’hôte de démarrer et d’arrêter le common language runtime explicitement, de créer et configurer des domaines d’application, d’accéder au domaine par défaut et d’énumérer tous les domaines qui s’exécutent dans le processus.|  
|[IDebuggerInfo, interface](idebuggerinfo-interface.md)|Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.|  
|[IGCHost, interface](igchost-interface.md)|Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.|  
|IValidator|Fournit des méthodes pour la validation des images exécutables portables et un rapport détaillé des erreurs de validation.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. idl  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement des coclasses](hosting-coclasses.md)
