---
title: ICorRuntimeHost::CreateDomainSetup, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: 217874e625604613e67170a118a7bc3616e02c4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139647"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a>ICorRuntimeHost::CreateDomainSetup, méthode
Obtient un pointeur d’interface de type IAppDomainSetup vers une instance de <xref:System.AppDomainSetup?displayProperty=nameWithType>. `IAppDomainSetup` fournit des méthodes pour configurer les aspects d’un domaine d’application avant qu’il ne soit créé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAppDomainSetup`  
 à Pointeur d’interface vers une instance de <xref:System.AppDomainSetup?displayProperty=nameWithType>. Ce paramètre étant de type `IUnknown`, les appelants doivent généralement appeler `QueryInterface` sur ce pointeur pour obtenir un pointeur d’interface de type `IAppDomainSetup`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’opération a réussi.|  
|S_FALSE|L’opération n’a pas pu se terminer.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus. Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="remarks"></a>Notes  
 Le pointeur retourné à partir de cette méthode est généralement passé comme paramètre à la méthode [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) .  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Version de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
