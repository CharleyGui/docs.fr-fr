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
ms.openlocfilehash: e1e114070f39e75254fc1bc0f8c1bf3e4733d5a2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703371"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="7db5c-102">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="7db5c-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="7db5c-103">Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au common language runtime (CLR), sans avoir à créer ou à comprendre cette identité.</span><span class="sxs-lookup"><span data-stu-id="7db5c-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7db5c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7db5c-104">Methods</span></span>  
  
|<span data-ttu-id="7db5c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7db5c-105">Method</span></span>|<span data-ttu-id="7db5c-106">Description</span><span class="sxs-lookup"><span data-stu-id="7db5c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7db5c-107">Méthode Get</span><span class="sxs-lookup"><span data-stu-id="7db5c-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="7db5c-108">Obtient l’identité de l’assembly au niveau de l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="7db5c-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7db5c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7db5c-109">Remarks</span></span>  
 <span data-ttu-id="7db5c-110">Les méthodes telles que [ICLRAssemblyIdentityManager :: GetProbingAssembliesFromReference,](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) retournent une `ICLRProbingAssemblyEnum` instance.</span><span class="sxs-lookup"><span data-stu-id="7db5c-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7db5c-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="7db5c-111">Requirements</span></span>  
 <span data-ttu-id="7db5c-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7db5c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7db5c-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7db5c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7db5c-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7db5c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7db5c-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7db5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db5c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7db5c-116">See also</span></span>

- [<span data-ttu-id="7db5c-117">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="7db5c-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="7db5c-118">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="7db5c-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7db5c-119">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="7db5c-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
