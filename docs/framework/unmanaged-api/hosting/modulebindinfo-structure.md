---
title: ModuleBindInfo, structure
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133749"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="38f27-102">ModuleBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="38f27-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="38f27-103">Fournit des informations détaillées sur le module référencé et l’assembly qui le contient.</span><span class="sxs-lookup"><span data-stu-id="38f27-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38f27-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="38f27-105">Membres</span><span class="sxs-lookup"><span data-stu-id="38f27-105">Members</span></span>  
  
|<span data-ttu-id="38f27-106">Membre</span><span class="sxs-lookup"><span data-stu-id="38f27-106">Member</span></span>|<span data-ttu-id="38f27-107">Description</span><span class="sxs-lookup"><span data-stu-id="38f27-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="38f27-108">Identificateur unique pour le `IStream` retourné par un appel à la méthode [IHostAssemblyStore ::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) à partir de laquelle le module référencé doit être chargé.</span><span class="sxs-lookup"><span data-stu-id="38f27-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="38f27-109">Identificateur unique de l’assembly qui contient le module référencé.</span><span class="sxs-lookup"><span data-stu-id="38f27-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="38f27-110">Nom du module référencé.</span><span class="sxs-lookup"><span data-stu-id="38f27-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38f27-111">Notes</span><span class="sxs-lookup"><span data-stu-id="38f27-111">Remarks</span></span>  
 <span data-ttu-id="38f27-112">`ModuleBindInfo` est passé en tant que paramètre à `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="38f27-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="38f27-113">L’hôte fournit l’identificateur unique `dwAppDomainId` au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="38f27-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="38f27-114">Après qu’un appel à la méthode [IHostAssemblyStore ::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé.</span><span class="sxs-lookup"><span data-stu-id="38f27-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="38f27-115">Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux.</span><span class="sxs-lookup"><span data-stu-id="38f27-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="38f27-116">Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à la méthode `IHostAssemblyStore::ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="38f27-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="38f27-117">Par conséquent, l’identificateur doit être unique pour les requêtes de module, ainsi que pour les demandes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="38f27-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f27-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="38f27-118">Requirements</span></span>  
 <span data-ttu-id="38f27-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f27-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f27-120">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="38f27-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="38f27-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38f27-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38f27-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f27-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f27-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38f27-123">See also</span></span>

- [<span data-ttu-id="38f27-124">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="38f27-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="38f27-125">AssemblyBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="38f27-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="38f27-126">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="38f27-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="38f27-127">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="38f27-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="38f27-128">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="38f27-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
