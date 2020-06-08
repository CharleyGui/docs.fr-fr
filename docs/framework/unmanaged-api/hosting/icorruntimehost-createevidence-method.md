---
title: ICorRuntimeHost::CreateEvidence, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 264f16fc9e767584229376e67f5aee6db1069025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501610"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence, méthode
Obtient un pointeur d’interface de type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , qui permet à l’hôte de créer une preuve de sécurité à passer à la méthode [CreateDomain](icorruntimehost-createdomain-method.md) ou [CreateDomainEx](icorruntimehost-createdomainex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pEvidence`  
 à Pointeur d’interface vers une <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance utilisée pour créer la preuve de sécurité. Ce pointeur étant typé `IUnknown` , les appelants doivent généralement appeler `QueryInterface` sur cette interface pour obtenir un pointeur vers un <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L'opération a réussi.|  
|S_FALSE|L’opération n’a pas pu se terminer.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus. Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne une collection vide qui ne peut pas être remplie à partir du code natif. Vous devez utiliser la <xref:System.Security.Policy.Evidence> méthode à la place.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Version de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
