---
title: ICorProfilerModuleEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: fe11c0bbe273ae07cdae43f681a558e07a291ffb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494889"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="543fc-102">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="543fc-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="543fc-103">Fournit des méthodes pour boucler séquentiellement dans une collection de modules chargés par l’application ou par le profileur.</span><span class="sxs-lookup"><span data-stu-id="543fc-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="543fc-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="543fc-104">Methods</span></span>  
  
|<span data-ttu-id="543fc-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-105">Method</span></span>|<span data-ttu-id="543fc-106">Description</span><span class="sxs-lookup"><span data-stu-id="543fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="543fc-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-107">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="543fc-108">Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerModuleEnum`.</span><span class="sxs-lookup"><span data-stu-id="543fc-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="543fc-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-109">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="543fc-110">Obtient le nombre de modules managés chargés dans l'application.</span><span class="sxs-lookup"><span data-stu-id="543fc-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="543fc-111">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-111">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="543fc-112">Obtient le nombre spécifié de modules contigus dans une collection séquentielle d’objets, à commencer par la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="543fc-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="543fc-113">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-113">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="543fc-114">Déplace le curseur de l'énumérateur à la position de départ de la séquence.</span><span class="sxs-lookup"><span data-stu-id="543fc-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="543fc-115">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-115">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="543fc-116">Fait avancer la position du curseur de l'énumérateur de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="543fc-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="543fc-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="543fc-117">Remarks</span></span>  
 <span data-ttu-id="543fc-118">L'interface `ICorProfilerModuleEnum` est un énumérateur.</span><span class="sxs-lookup"><span data-stu-id="543fc-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="543fc-119">Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="543fc-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="543fc-120">En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="543fc-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="543fc-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="543fc-121">Requirements</span></span>  
 <span data-ttu-id="543fc-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="543fc-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543fc-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="543fc-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="543fc-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="543fc-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="543fc-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543fc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543fc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="543fc-126">See also</span></span>

- [<span data-ttu-id="543fc-127">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="543fc-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="543fc-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="543fc-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="543fc-129">EnumModules, méthode</span><span class="sxs-lookup"><span data-stu-id="543fc-129">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
