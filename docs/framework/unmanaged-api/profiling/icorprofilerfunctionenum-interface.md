---
title: ICorProfilerFunctionEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: add30952588ace0cbc80191617c37d7222cffee7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864490"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="7d968-102">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="7d968-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="7d968-103">Fournit des méthodes pour itérer séquentiellement une collection de fonctions dans le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="7d968-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d968-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7d968-104">Methods</span></span>  
  
|<span data-ttu-id="7d968-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-105">Method</span></span>|<span data-ttu-id="7d968-106">Description</span><span class="sxs-lookup"><span data-stu-id="7d968-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d968-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-107">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="7d968-108">Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerFunctionEnum`.</span><span class="sxs-lookup"><span data-stu-id="7d968-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="7d968-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-109">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="7d968-110">Obtient le nombre de fonctions qui ont été chargées par l'application ou chargées de force par le profileur.</span><span class="sxs-lookup"><span data-stu-id="7d968-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="7d968-111">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-111">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="7d968-112">Obtient le nombre spécifié de fonctions contiguës dans une collection séquentielle de fonctions, à commencer par la position actuelle de l'énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="7d968-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="7d968-113">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-113">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="7d968-114">Déplace le curseur de l'énumérateur à la position de départ de la séquence.</span><span class="sxs-lookup"><span data-stu-id="7d968-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="7d968-115">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-115">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="7d968-116">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="7d968-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d968-117">Notes</span><span class="sxs-lookup"><span data-stu-id="7d968-117">Remarks</span></span>  
 <span data-ttu-id="7d968-118">L'interface `ICorProfilerFunctionEnum` est un énumérateur.</span><span class="sxs-lookup"><span data-stu-id="7d968-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="7d968-119">Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="7d968-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="7d968-120">En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="7d968-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="7d968-121">`ICorProfilerFunctionEnum` énumère les fonctions qui ont déjà été compilées juste-à-temps, mais n'inclut pas les fonctions chargées à partir des images natives générées avec Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="7d968-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d968-122">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7d968-122">Requirements</span></span>  
 <span data-ttu-id="7d968-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d968-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d968-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7d968-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d968-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d968-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d968-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d968-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d968-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d968-127">See also</span></span>

- [<span data-ttu-id="7d968-128">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="7d968-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7d968-129">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7d968-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7d968-130">EnumJITedFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="7d968-130">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
