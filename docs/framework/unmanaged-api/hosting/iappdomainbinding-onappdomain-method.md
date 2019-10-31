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
ms.openlocfilehash: 37c02b878cd52034603ab6cafe4d8aaca594cbe9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126887"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="5a0f3-102">IAppDomainBinding::OnAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="5a0f3-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="5a0f3-103">Appelée par le common language runtime (CLR) pour notifier l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="5a0f3-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a0f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a0f3-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a0f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5a0f3-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="5a0f3-106">dans Pointeur vers un objet d’interface [IUnknown](/cpp/atl/iunknown) qui représente le nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5a0f3-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a0f3-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="5a0f3-107">Requirements</span></span>  
 <span data-ttu-id="5a0f3-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a0f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a0f3-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5a0f3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a0f3-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5a0f3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a0f3-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a0f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0f3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a0f3-112">See also</span></span>

- [<span data-ttu-id="5a0f3-113">IAppDomainBinding, interface</span><span class="sxs-lookup"><span data-stu-id="5a0f3-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
