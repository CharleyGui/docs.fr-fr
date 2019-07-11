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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28feddffff7dc5dba1860b3d2d1327a17bd08190
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772953"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType, méthode
Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, du Gestionnaire de domaine qui sera utilisé pour initialiser le domaine d’application par défaut.  
  
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
 [in] Le nom complet de l’assembly qui contient le type de gestionnaire de domaine application ; par exemple : "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 [in] Le nom de type du Gestionnaire de domaine, y compris l’espace de noms.  
  
 `dwInitializeDomainFlags`  
 [in] Une combinaison de [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) valeurs d’énumération qui fournissent des informations sur le Gestionnaire de domaine d’application.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
  
## <a name="remarks"></a>Notes  
 Actuellement, la seule valeur définie pour `dwInitializeDomainFlags` est `eInitializeNewDomainFlags_NoSecurityChanges`, ce qui indique le common language runtime (CLR) que le Gestionnaire de domaine d’application ne modifiera pas de paramètres de sécurité pendant l’exécution de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> (méthode). Cela permet au CLR d’optimiser le chargement d’assemblys qui ont l’instruction conditionnelle <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA). Si la fermeture transitive de cet ensemble d’assemblys est importante, cela peut entraîner une amélioration significative du temps de démarrage.  
  
> [!IMPORTANT]
>  Si l’hôte spécifie `eInitializeNewDomainFlags_NoSecurityChanges` pour le Gestionnaire de domaine d’application, un <xref:System.InvalidOperationException> est levée si une tentative est faite pour modifier la sécurité du domaine d’application.  
  
 Appel de la [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)méthode revient à appeler `ICLRDomainManager::SetAppDomainManagerType` avec `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags, énumération](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
