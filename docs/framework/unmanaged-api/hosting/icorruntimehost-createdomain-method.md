---
title: ICorRuntimeHost::CreateDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 74f17c77e74edb1226dda2d9ebaa9486e1769ce4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762355"
---
# <a name="icorruntimehostcreatedomain-method"></a>ICorRuntimeHost::CreateDomain, méthode
Crée un domaine d’application. L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> vers une instance de type <xref:System.AppDomain?displayProperty=nameWithType> .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzFriendlyName`  
 dans Paramètre facultatif utilisé pour attribuer un nom convivial au domaine. Ce nom convivial peut être affiché dans les interfaces utilisateur, telles que les débogueurs, pour identifier le domaine.  
  
 `pIdentityArray`  
 dans Tableau facultatif de pointeurs vers des `IIdentity` instances qui représentent une preuve mappée par le biais d’une stratégie de sécurité pour établir un jeu d’autorisations. Un `IIdentity` objet peut être obtenu en appelant la méthode [CreateEvidence,](icorruntimehost-createevidence-method.md) .  
  
 `pAppDomain`  
 à Pointeur d’interface de type <xref:System._AppDomain> vers une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisée pour mieux contrôler le domaine.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L'opération a réussi.|  
|S_FALSE|L’opération n’a pas pu se terminer.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus. Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
