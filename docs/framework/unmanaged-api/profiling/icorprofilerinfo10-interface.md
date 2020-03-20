---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175068"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="1df85-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="1df85-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="1df85-103">Une sous-classe [d’ICorProfilerInfo9](icorprofilerinfo9-interface.md) qui fournit des méthodes pour modifier la fonction IL, interroger les informations à partir du temps d’exécution, et suspendre et reprendre l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1df85-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="1df85-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1df85-104">Methods</span></span>  

| <span data-ttu-id="1df85-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1df85-105">Method</span></span>|<span data-ttu-id="1df85-106">Description</span><span class="sxs-lookup"><span data-stu-id="1df85-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="1df85-107">Méthode EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="1df85-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="1df85-108">Compte tenu d’un ObjectID, de rappel et de clientData, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="1df85-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="1df85-109">Méthode IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="1df85-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="1df85-110">Compte tenu d’un ObjectID, détermine si l’objet se trouve dans un segment de lecture seulement.</span><span class="sxs-lookup"><span data-stu-id="1df85-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="1df85-111">Méthode GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="1df85-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="1df85-112">Obtient la valeur du seuil LOH configuré.</span><span class="sxs-lookup"><span data-stu-id="1df85-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="1df85-113">Méthode RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="1df85-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="1df85-114">ReJITs les méthodes demandées, ainsi que tous les inliners des méthodes demandées.</span><span class="sxs-lookup"><span data-stu-id="1df85-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="1df85-115">Méthode SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="1df85-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="1df85-116">Suspend le temps d’exécution sans effectuer un GC.</span><span class="sxs-lookup"><span data-stu-id="1df85-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="1df85-117">Méthode ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="1df85-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="1df85-118">Reprend le temps d’exécution sans effectuer un GC.</span><span class="sxs-lookup"><span data-stu-id="1df85-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="1df85-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1df85-119">Requirements</span></span>  
<span data-ttu-id="1df85-120">**Plates-formes:** Voir [.NET Core systèmes d’exploitation pris en charge](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1df85-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="1df85-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1df85-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="1df85-122">**Versions .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df85-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1df85-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1df85-123">See also</span></span>

- [<span data-ttu-id="1df85-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="1df85-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
