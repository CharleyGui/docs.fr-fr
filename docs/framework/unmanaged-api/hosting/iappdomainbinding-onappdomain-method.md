---
title: IAppDomainBinding::OnAppDomain, méthode
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
ms.openlocfilehash: 2d5dbd003d0ea5decae0025d47e6bd5c1fb1ed4a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617072"
---
# <a name="iappdomainbindingonappdomain-method"></a>IAppDomainBinding::OnAppDomain, méthode
Appelée par le common language runtime (CLR) pour notifier l’hôte qu’un domaine d’application a été créé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAppdomain`  
 dans Pointeur vers un objet d’interface [IUnknown](/cpp/atl/iunknown) qui représente le nouveau domaine d’application.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IAppDomainBinding, interface](iappdomainbinding-interface.md)
