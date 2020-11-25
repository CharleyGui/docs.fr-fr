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
ms.openlocfilehash: 6df08889af30542af5a128cbffc38a57ce640fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728925"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="f2aa7-102">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f2aa7-102">ICLRProbingAssemblyEnum Interface</span></span>

<span data-ttu-id="f2aa7-103">Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au common language runtime (CLR), sans avoir à créer ou à comprendre cette identité.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2aa7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f2aa7-104">Methods</span></span>  
  
|<span data-ttu-id="f2aa7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f2aa7-105">Method</span></span>|<span data-ttu-id="f2aa7-106">Description</span><span class="sxs-lookup"><span data-stu-id="f2aa7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2aa7-107">Méthode Get</span><span class="sxs-lookup"><span data-stu-id="f2aa7-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="f2aa7-108">Obtient l’identité de l’assembly au niveau de l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2aa7-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2aa7-109">Remarks</span></span>  

 <span data-ttu-id="f2aa7-110">Les méthodes telles que [ICLRAssemblyIdentityManager :: GetProbingAssembliesFromReference,](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retournent une `ICLRProbingAssemblyEnum` instance.</span><span class="sxs-lookup"><span data-stu-id="f2aa7-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2aa7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2aa7-111">Requirements</span></span>  

 <span data-ttu-id="f2aa7-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2aa7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2aa7-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2aa7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2aa7-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2aa7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2aa7-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2aa7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2aa7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2aa7-116">See also</span></span>

- [<span data-ttu-id="f2aa7-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="f2aa7-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="f2aa7-118">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="f2aa7-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f2aa7-119">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="f2aa7-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
