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
ms.openlocfilehash: 7c6b328793e6437682ad8d642e611be30e7b0fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702145"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType, méthode

Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.  
  
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
 dans Combinaison de valeurs d’énumération [EInitializeNewDomainFlags,](einitializenewdomainflags-enumeration.md) qui fournissent des informations sur le gestionnaire de domaine d’application.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="remarks"></a>Remarques  

 Actuellement, la seule valeur définie pour `dwInitializeDomainFlags` est `eInitializeNewDomainFlags_NoSecurityChanges` , qui indique à l’Common Language Runtime (CLR) que le gestionnaire de domaine d’application ne modifiera pas les paramètres de sécurité pendant l’exécution de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode. Cela permet au CLR d’optimiser le chargement des assemblys qui ont l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut conditionnel (APTCA). Cela peut entraîner une amélioration significative du temps de démarrage si la fermeture transitive de cet ensemble d’assemblys est importante.  
  
> [!IMPORTANT]
> Si l’hôte spécifie `eInitializeNewDomainFlags_NoSecurityChanges` pour le gestionnaire de domaine d’application, une <xref:System.InvalidOperationException> exception est levée si une tentative est faite pour modifier la sécurité du domaine d’application.  
  
 L’appel de la méthode [ICLRControl :: SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)équivaut à l’appel `ICLRDomainManager::SetAppDomainManagerType` de avec `eInitializeNewDomainFlags_None` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement](index.md)
- [ICLRDomainManager, interface](iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags, énumération](einitializenewdomainflags-enumeration.md)
