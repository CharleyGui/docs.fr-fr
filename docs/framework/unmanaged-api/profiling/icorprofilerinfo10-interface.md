---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863242"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="e3ec0-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="e3ec0-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="e3ec0-103">Une sous-classe de [ICorProfilerInfo9](icorprofilerinfo9-interface.md) qui fournit des méthodes pour modifier la fonction il, les informations de requête du runtime, et interrompre et reprendre le Runtime.</span><span class="sxs-lookup"><span data-stu-id="e3ec0-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="e3ec0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e3ec0-104">Methods</span></span>  

| <span data-ttu-id="e3ec0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e3ec0-105">Method</span></span>|<span data-ttu-id="e3ec0-106">Description</span><span class="sxs-lookup"><span data-stu-id="e3ec0-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="e3ec0-107">Méthode EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="e3ec0-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="e3ec0-108">À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="e3ec0-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="e3ec0-109">Méthode IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="e3ec0-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="e3ec0-110">À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="e3ec0-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="e3ec0-111">Méthode GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="e3ec0-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="e3ec0-112">Obtient la valeur du seuil LOH configuré.</span><span class="sxs-lookup"><span data-stu-id="e3ec0-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="e3ec0-113">Méthode RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="e3ec0-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="e3ec0-114">ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.</span><span class="sxs-lookup"><span data-stu-id="e3ec0-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="e3ec0-115">Méthode SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="e3ec0-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="e3ec0-116">Interrompt le runtime sans exécuter de GC.</span><span class="sxs-lookup"><span data-stu-id="e3ec0-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="e3ec0-117">Méthode ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="e3ec0-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="e3ec0-118">Reprend le runtime sans exécuter de GC.</span><span class="sxs-lookup"><span data-stu-id="e3ec0-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e3ec0-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e3ec0-119">Requirements</span></span>  
<span data-ttu-id="e3ec0-120">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e3ec0-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="e3ec0-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3ec0-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="e3ec0-122">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ec0-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="e3ec0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3ec0-123">See also</span></span>

- [<span data-ttu-id="e3ec0-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="e3ec0-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
