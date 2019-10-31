---
title: AssemblyBindInfo, structure
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192109"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="27772-102">AssemblyBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="27772-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="27772-103">Fournit des informations détaillées sur l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="27772-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27772-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27772-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="27772-105">Membres</span><span class="sxs-lookup"><span data-stu-id="27772-105">Members</span></span>  
  
|<span data-ttu-id="27772-106">Membre</span><span class="sxs-lookup"><span data-stu-id="27772-106">Member</span></span>|<span data-ttu-id="27772-107">Description</span><span class="sxs-lookup"><span data-stu-id="27772-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="27772-108">Identificateur unique pour le `IStream` retourné par un appel à [IHostAssemblyStore ::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), à partir duquel l’assembly référencé doit être chargé.</span><span class="sxs-lookup"><span data-stu-id="27772-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="27772-109">Identificateur unique de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="27772-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="27772-110">Identificateur de l’assembly référencé après l’application des valeurs de stratégie de liaison.</span><span class="sxs-lookup"><span data-stu-id="27772-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="27772-111">L’une des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) qui indiquent les stratégies de contrôle de version, le cas échéant, qui doivent être appliquées à l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="27772-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27772-112">Notes</span><span class="sxs-lookup"><span data-stu-id="27772-112">Remarks</span></span>  
 <span data-ttu-id="27772-113">L’hôte fournit l’identificateur unique `dwAppDomainId` au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="27772-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="27772-114">Après qu’un appel à `IHostAssemblyStore::ProvideAssembly` retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé.</span><span class="sxs-lookup"><span data-stu-id="27772-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="27772-115">Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux.</span><span class="sxs-lookup"><span data-stu-id="27772-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="27772-116">Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à [IHostAssemblyStore ::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="27772-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="27772-117">Par conséquent, l’identificateur doit être unique pour les demandes de module et pour les demandes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="27772-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27772-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="27772-118">Requirements</span></span>  
 <span data-ttu-id="27772-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27772-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27772-120">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="27772-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="27772-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27772-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27772-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27772-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27772-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27772-123">See also</span></span>

- [<span data-ttu-id="27772-124">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="27772-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="27772-125">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="27772-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="27772-126">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="27772-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="27772-127">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="27772-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="27772-128">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="27772-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="27772-129">ModuleBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="27772-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
