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
ms.openlocfilehash: 65f6be8c12ce057422ad178c759affed170e44ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721710"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="f36fb-102">IAppDomainBinding::OnAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="f36fb-102">IAppDomainBinding::OnAppDomain Method</span></span>

<span data-ttu-id="f36fb-103">Appelée par le common language runtime (CLR) pour notifier l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="f36fb-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f36fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f36fb-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f36fb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f36fb-105">Parameters</span></span>  

 `pAppdomain`  
 <span data-ttu-id="f36fb-106">dans Pointeur vers un objet d’interface [IUnknown](/cpp/atl/iunknown) qui représente le nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="f36fb-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f36fb-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f36fb-107">Requirements</span></span>  

 <span data-ttu-id="f36fb-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f36fb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f36fb-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f36fb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f36fb-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f36fb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f36fb-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f36fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36fb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f36fb-112">See also</span></span>

- [<span data-ttu-id="f36fb-113">IAppDomainBinding, interface</span><span class="sxs-lookup"><span data-stu-id="f36fb-113">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
