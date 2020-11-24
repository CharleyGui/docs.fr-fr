---
title: IHostAssemblyManager, interface
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: a06e7f13b6de9450aa2a81f28f591c0a3ce8db0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680984"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="c7329-102">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="c7329-102">IHostAssemblyManager Interface</span></span>

<span data-ttu-id="c7329-103">Fournit des méthodes qui permettent à un hôte de spécifier des jeux d’assemblys qui doivent être chargés par le common language runtime (CLR) ou par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c7329-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7329-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c7329-104">Methods</span></span>  
  
|<span data-ttu-id="c7329-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c7329-105">Method</span></span>|<span data-ttu-id="c7329-106">Description</span><span class="sxs-lookup"><span data-stu-id="c7329-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7329-107">GetAssemblyStore, méthode</span><span class="sxs-lookup"><span data-stu-id="c7329-107">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="c7329-108">Obtient un pointeur d’interface vers un [IHostAssemblyStore](ihostassemblystore-interface.md) qui représente la liste des assemblys chargés par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c7329-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="c7329-109">GetNonHostStoreAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="c7329-109">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="c7329-110">Obtient un pointeur d’interface vers un [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) qui représente la liste des assemblys que l’hôte attend que le CLR se charge.</span><span class="sxs-lookup"><span data-stu-id="c7329-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7329-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7329-111">Remarks</span></span>  

 <span data-ttu-id="c7329-112">L’hôte n’est pas tenu d’implémenter `IHostAssemblyManager` ou `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="c7329-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="c7329-113">Si l’hôte implémente `IHostAssemblyManager` , il doit également implémenter `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="c7329-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="c7329-114">Le runtime interroge pour un `IHostAssemblyManager` en appelant [IHostControl :: GetHostManager,](ihostcontrol-gethostmanager-method.md) lors de l’initialisation avec un `IID` de IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="c7329-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7329-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7329-115">Requirements</span></span>  

 <span data-ttu-id="c7329-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7329-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7329-117">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c7329-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7329-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7329-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7329-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7329-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7329-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7329-120">See also</span></span>

- [<span data-ttu-id="c7329-121">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="c7329-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c7329-122">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="c7329-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="c7329-123">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="c7329-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="c7329-124">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c7329-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
