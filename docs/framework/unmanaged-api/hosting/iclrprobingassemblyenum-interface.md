---
title: ICLRProbingAssemblyEnum, interface
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: e1459c1604f3f8f043fd9b61533235ab7861c910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120563"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="c5040-102">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="c5040-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="c5040-103">Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au common language runtime (CLR), sans avoir à créer ou à comprendre cette identité.</span><span class="sxs-lookup"><span data-stu-id="c5040-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5040-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c5040-104">Methods</span></span>  
  
|<span data-ttu-id="c5040-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c5040-105">Method</span></span>|<span data-ttu-id="c5040-106">Description</span><span class="sxs-lookup"><span data-stu-id="c5040-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5040-107">Get, méthode</span><span class="sxs-lookup"><span data-stu-id="c5040-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="c5040-108">Obtient l’identité de l’assembly au niveau de l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="c5040-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5040-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c5040-109">Remarks</span></span>  
 <span data-ttu-id="c5040-110">Les méthodes telles que [ICLRAssemblyIdentityManager :: GetProbingAssembliesFromReference,](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retournent une instance `ICLRProbingAssemblyEnum`.</span><span class="sxs-lookup"><span data-stu-id="c5040-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5040-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="c5040-111">Requirements</span></span>  
 <span data-ttu-id="c5040-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5040-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5040-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5040-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5040-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c5040-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5040-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5040-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5040-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5040-116">See also</span></span>

- [<span data-ttu-id="c5040-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="c5040-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c5040-118">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="c5040-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c5040-119">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="c5040-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
