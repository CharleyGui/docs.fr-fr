---
title: ICorRuntimeHost::CurrentDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: 33d56354a560949b2f451df9ef82d4f433951195
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715561"
---
# <a name="icorruntimehostcurrentdomain-method"></a>ICorRuntimeHost::CurrentDomain, méthode

Obtient un pointeur d’interface de type <xref:System.AppDomain?displayProperty=nameWithType> qui représente le domaine chargé sur le thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pAppDomain`  
 à Pointeur de type <xref:System.AppDomain?displayProperty=nameWithType> qui représente le domaine d’application actuel du thread. Ce pointeur étant typé `IUnknown` , les appelants doivent généralement appeler `QueryInterface` pour obtenir un pointeur de type <xref:System._AppDomain> .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L'opération a réussi.|  
|S_FALSE|L’opération n’a pas pu se terminer.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus. Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
