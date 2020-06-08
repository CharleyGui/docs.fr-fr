---
title: IHostAssemblyStore, interface
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: cca73eec663b9afd12ecea5ab9d7073ea0168d33
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501554"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="afe36-102">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="afe36-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="afe36-103">Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="afe36-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afe36-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="afe36-104">Methods</span></span>  
  
|<span data-ttu-id="afe36-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="afe36-105">Method</span></span>|<span data-ttu-id="afe36-106">Description</span><span class="sxs-lookup"><span data-stu-id="afe36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afe36-107">ProvideAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="afe36-107">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="afe36-108">Obtient une référence à un assembly qui n’est pas référencé par l' [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) retourné par un appel à [IHostAssemblyManager :: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="afe36-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="afe36-109">ProvideModule, méthode</span><span class="sxs-lookup"><span data-stu-id="afe36-109">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="afe36-110">Résout un module au sein d’un assembly ou d’un fichier de ressources lié (non incorporé).</span><span class="sxs-lookup"><span data-stu-id="afe36-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afe36-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="afe36-111">Remarks</span></span>  
 <span data-ttu-id="afe36-112">`IHostAssemblyStore`permet à un hôte de charger efficacement des assemblys en fonction de l’identité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="afe36-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="afe36-113">L’hôte charge des assemblys en retournant des `IStream` instances qui pointent directement vers les octets.</span><span class="sxs-lookup"><span data-stu-id="afe36-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="afe36-114">Le CLR détermine si un hôte a implémenté `IHostAssemblyStore` en appelant `IHostAssemblyManager::GetNonHostAssemblyStores` lors de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="afe36-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="afe36-115">Cela permet à l’hôte, par exemple, de contrôler la liaison aux assemblys utilisateur, mais de s’appuyer sur le runtime pour effectuer une liaison à .NET Framework assemblys.</span><span class="sxs-lookup"><span data-stu-id="afe36-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afe36-116">En fournissant une implémentation de `IHostAssemblyStore` , l’hôte spécifie son intention de résoudre tous les assemblys qui ne sont pas référencés par le `ICLRAssemblyReferenceList` retourné à partir de `IHostAssemblyManager::GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="afe36-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afe36-117">La version 2,0 de .NET Framework ne permet pas à l’hôte de charger l’image native d’un assembly, comme fourni par l’utilitaire [Ngen. exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="afe36-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe36-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="afe36-118">Requirements</span></span>  
 <span data-ttu-id="afe36-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afe36-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe36-120">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="afe36-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afe36-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="afe36-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afe36-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe36-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe36-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afe36-123">See also</span></span>

- [<span data-ttu-id="afe36-124">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="afe36-124">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="afe36-125">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="afe36-125">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="afe36-126">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="afe36-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
