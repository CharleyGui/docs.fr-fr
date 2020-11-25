---
title: ICorRuntimeHost::CreateDomainEx, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: d6d9e06b6ed40bb0e5a65fd64f8bca7abe3afa84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715678"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx, méthode

Crée un domaine d’application. L’appelant reçoit un pointeur d’interface, de type <xref:System._AppDomain> , à une instance de type <xref:System.AppDomain?displayProperty=nameWithType> . Cette méthode permet à l’appelant de passer une instance IAppDomainSetup pour configurer des fonctionnalités supplémentaires de l’instance retournée <xref:System._AppDomain> .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pwzFriendlyName`  
 dans Paramètre facultatif utilisé pour attribuer un nom convivial au domaine. Ce nom convivial peut être affiché dans les interfaces utilisateur, telles que les débogueurs, pour identifier le domaine.  
  
 `pSetup`  
 dans Pointeur d’interface facultatif de type `IAppDomainSetup` , obtenu par un appel à la méthode [ICorRuntimeHost :: CreateDomainSetup,](icorruntimehost-createdomainsetup-method.md) .  
  
 `pIdentityArray`  
 dans Tableau facultatif de pointeurs vers des `IIdentity` instances qui représentent une preuve mappée par le biais d’une stratégie de sécurité pour établir un jeu d’autorisations. Un `IIdentity` objet peut être obtenu en appelant la méthode [CreateEvidence,](icorruntimehost-createevidence-method.md) .  
  
 `pAppDomain`  
 à Pointeur d’interface de type <xref:System._AppDomain> vers une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisée pour mieux contrôler le domaine.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L'opération a réussi.|  
|S_FALSE|L’opération n’a pas pu se terminer.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus. Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="remarks"></a>Remarques  

 `CreateDomainEx` étend les fonctionnalités de [CreateDomain](icorruntimehost-createdomain-method.md) en permettant à l’appelant de passer une `IAppDomainSetup` instance avec des valeurs de propriété pour configurer le domaine d’application.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Version de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain, méthode](icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
