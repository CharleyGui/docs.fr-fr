---
title: IHostSecurityContext, interface
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501493"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="e80f2-102">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="e80f2-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="e80f2-103">Permet à l’common language runtime (CLR) de conserver les informations de contexte de sécurité implémentées par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="e80f2-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e80f2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e80f2-104">Methods</span></span>  
  
|<span data-ttu-id="e80f2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e80f2-105">Method</span></span>|<span data-ttu-id="e80f2-106">Description</span><span class="sxs-lookup"><span data-stu-id="e80f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e80f2-107">Capture, méthode</span><span class="sxs-lookup"><span data-stu-id="e80f2-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="e80f2-108">Obtient un clone de l' `IHostSecurityContext` instance retournée à partir d’un appel à [IHostSecurityManager :: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="e80f2-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e80f2-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="e80f2-109">Remarks</span></span>  
 <span data-ttu-id="e80f2-110">Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le CLR et le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e80f2-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="e80f2-111">Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code.</span><span class="sxs-lookup"><span data-stu-id="e80f2-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="e80f2-112">`IHostSecurityContext`encapsule ces informations de contexte de sécurité, qui sont opaques pour le Runtime.</span><span class="sxs-lookup"><span data-stu-id="e80f2-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="e80f2-113">Le Runtime Capture ces informations à l’aide de `Capture` et les déplace à travers la répartition des éléments de travail du pool de threads, l’exécution du finaliseur et les constructeurs de module et de classe.</span><span class="sxs-lookup"><span data-stu-id="e80f2-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e80f2-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e80f2-114">Requirements</span></span>  
 <span data-ttu-id="e80f2-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e80f2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e80f2-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e80f2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e80f2-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e80f2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e80f2-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e80f2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80f2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e80f2-119">See also</span></span>

- [<span data-ttu-id="e80f2-120">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="e80f2-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="e80f2-121">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="e80f2-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="e80f2-122">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="e80f2-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
