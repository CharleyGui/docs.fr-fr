---
title: IHostControl, interface
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195881"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="f1f79-102">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="f1f79-102">IHostControl Interface</span></span>
<span data-ttu-id="f1f79-103">Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.</span><span class="sxs-lookup"><span data-stu-id="f1f79-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1f79-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f1f79-104">Methods</span></span>  
  
|<span data-ttu-id="f1f79-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f1f79-105">Method</span></span>|<span data-ttu-id="f1f79-106">Description</span><span class="sxs-lookup"><span data-stu-id="f1f79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1f79-107">GetHostManager, méthode</span><span class="sxs-lookup"><span data-stu-id="f1f79-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="f1f79-108">Obtient un pointeur d’interface vers l’implémentation de l’hôte de l’interface avec le `IID`spécifié.</span><span class="sxs-lookup"><span data-stu-id="f1f79-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="f1f79-109">SetAppDomainManager, méthode</span><span class="sxs-lookup"><span data-stu-id="f1f79-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="f1f79-110">Avertit l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="f1f79-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1f79-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="f1f79-111">Requirements</span></span>  
 <span data-ttu-id="f1f79-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1f79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f79-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f1f79-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1f79-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1f79-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1f79-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f79-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1f79-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="f1f79-117">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="f1f79-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="f1f79-118">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="f1f79-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f1f79-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f1f79-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
