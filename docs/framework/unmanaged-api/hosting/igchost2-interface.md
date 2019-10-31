---
title: IGCHost2, interface
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 43c16415c91521194e0d88be84dd176c3fdadad1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134838"
---
# <a name="igchost2-interface"></a><span data-ttu-id="e50bf-102">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="e50bf-102">IGCHost2 Interface</span></span>
<span data-ttu-id="e50bf-103">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e50bf-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e50bf-104">Pour un nouveau développement, nous vous recommandons d’utiliser à la place l’interface [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e50bf-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e50bf-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e50bf-105">Methods</span></span>  
  
|<span data-ttu-id="e50bf-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e50bf-106">Method</span></span>|<span data-ttu-id="e50bf-107">Description</span><span class="sxs-lookup"><span data-stu-id="e50bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e50bf-108">SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="e50bf-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="e50bf-109">Définit la taille du segment et la taille maximale de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="e50bf-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="e50bf-110">Permet des tailles de génération 0 et de segment supérieures à `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e50bf-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e50bf-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="e50bf-111">Requirements</span></span>  
 <span data-ttu-id="e50bf-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e50bf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e50bf-113">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="e50bf-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e50bf-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e50bf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e50bf-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e50bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50bf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e50bf-116">See also</span></span>

- [<span data-ttu-id="e50bf-117">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e50bf-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e50bf-118">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="e50bf-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="e50bf-119">CorRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="e50bf-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
