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
ms.openlocfilehash: 505015877985492edab4b761b379f33f1e5c6660
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729978"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="725d5-102">ModuleBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="725d5-102">ModuleBindInfo Structure</span></span>

<span data-ttu-id="725d5-103">Fournit des informations détaillées sur le module référencé et l’assembly qui le contient.</span><span class="sxs-lookup"><span data-stu-id="725d5-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="725d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="725d5-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="725d5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="725d5-105">Members</span></span>  
  
|<span data-ttu-id="725d5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="725d5-106">Member</span></span>|<span data-ttu-id="725d5-107">Description</span><span class="sxs-lookup"><span data-stu-id="725d5-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="725d5-108">Identificateur unique pour le `IStream` retourné par un appel à la méthode [IHostAssemblyStore ::P rovidemodule](ihostassemblystore-providemodule-method.md) à partir de laquelle le module référencé doit être chargé.</span><span class="sxs-lookup"><span data-stu-id="725d5-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="725d5-109">Identificateur unique de l’assembly qui contient le module référencé.</span><span class="sxs-lookup"><span data-stu-id="725d5-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="725d5-110">Nom du module référencé.</span><span class="sxs-lookup"><span data-stu-id="725d5-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="725d5-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="725d5-111">Remarks</span></span>  

 <span data-ttu-id="725d5-112">`ModuleBindInfo` est passé en tant que paramètre à `IHostAssemblyStore::ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="725d5-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="725d5-113">L’hôte fournit l’identificateur unique `dwAppDomainId` au Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="725d5-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="725d5-114">Après qu’un appel à la méthode [IHostAssemblyStore ::P rovideassembly](ihostassemblystore-provideassembly-method.md) retourne, le runtime utilise l’identificateur pour déterminer si le contenu du `IStream` a été mappé.</span><span class="sxs-lookup"><span data-stu-id="725d5-114">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="725d5-115">Dans ce cas, le runtime charge la copie existante au lieu de remapper le flux.</span><span class="sxs-lookup"><span data-stu-id="725d5-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="725d5-116">Le runtime utilise également cet identificateur comme clé de recherche pour les flux retournés par les appels à la `IHostAssemblyStore::ProvideAssembly` méthode.</span><span class="sxs-lookup"><span data-stu-id="725d5-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="725d5-117">Par conséquent, l’identificateur doit être unique pour les requêtes de module, ainsi que pour les demandes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="725d5-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725d5-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="725d5-118">Requirements</span></span>  

 <span data-ttu-id="725d5-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="725d5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725d5-120">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="725d5-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="725d5-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="725d5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="725d5-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725d5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725d5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="725d5-123">See also</span></span>

- [<span data-ttu-id="725d5-124">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="725d5-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="725d5-125">AssemblyBindInfo, structure</span><span class="sxs-lookup"><span data-stu-id="725d5-125">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="725d5-126">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="725d5-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="725d5-127">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="725d5-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="725d5-128">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="725d5-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
