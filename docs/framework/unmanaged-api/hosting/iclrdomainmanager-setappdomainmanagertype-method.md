---
title: ICLRDomainManager::SetAppDomainManagerType, méthode
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129333"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType, méthode
Spécifie le type, dérivé de la classe <xref:System.AppDomainManager?displayProperty=nameWithType>, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `wszAppDomainManagerAssembly`  
 dans Nom complet de l’assembly qui contient le type de gestionnaire de domaine d’application ; par exemple : « AdMgrExample, version = 1.0.0.0, culture = neutral, PublicKeyToken = 6856bccf150f00b3 ».  
  
 `wszAppDomainManagerType`  
 dans Nom de type du gestionnaire de domaine d’application, y compris l’espace de noms.  
  
 `dwInitializeDomainFlags`  
 dans Combinaison de valeurs d’énumération [EInitializeNewDomainFlags,](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) qui fournissent des informations sur le gestionnaire de domaine d’application.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="remarks"></a>Notes  
 Actuellement, la seule valeur définie pour `dwInitializeDomainFlags` est `eInitializeNewDomainFlags_NoSecurityChanges`, ce qui indique au common language runtime (CLR) que le gestionnaire de domaine d’application ne modifiera pas les paramètres de sécurité lors de l’exécution de la méthode <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>. Cela permet au CLR d’optimiser le chargement des assemblys qui ont l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> conditionnel (APTCA). Cela peut entraîner une amélioration significative du temps de démarrage si la fermeture transitive de cet ensemble d’assemblys est importante.  
  
> [!IMPORTANT]
> Si l’hôte spécifie `eInitializeNewDomainFlags_NoSecurityChanges` pour le gestionnaire de domaine d’application, un <xref:System.InvalidOperationException> est levé si une tentative est faite pour modifier la sécurité du domaine d’application.  
  
 L’appel de la méthode [ICLRControl :: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)équivaut à appeler `ICLRDomainManager::SetAppDomainManagerType` avec `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags, énumération](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
