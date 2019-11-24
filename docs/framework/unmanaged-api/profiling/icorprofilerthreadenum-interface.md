---
title: ICorProfilerThreadEnum, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: b83706176091fd70d48e0f50a0fe5988c876f606
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447619"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="f8729-102">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f8729-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="f8729-103">Fournit des méthodes pour itérer séquentiellement une collection de threads dans le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="f8729-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8729-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f8729-104">Methods</span></span>  
  
|<span data-ttu-id="f8729-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f8729-105">Method</span></span>|<span data-ttu-id="f8729-106">Description</span><span class="sxs-lookup"><span data-stu-id="f8729-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8729-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="f8729-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="f8729-108">Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerThreadEnum`.</span><span class="sxs-lookup"><span data-stu-id="f8729-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="f8729-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="f8729-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="f8729-110">Obtient le nombre de threads utilisés par l'application.</span><span class="sxs-lookup"><span data-stu-id="f8729-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="f8729-111">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f8729-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="f8729-112">Obtient le nombre spécifié de threads contigus dans une collection séquentielle de threads, à commencer par la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="f8729-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="f8729-113">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="f8729-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="f8729-114">Déplace le curseur de l'énumérateur à la position de départ de la séquence.</span><span class="sxs-lookup"><span data-stu-id="f8729-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="f8729-115">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="f8729-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="f8729-116">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="f8729-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8729-117">Notes</span><span class="sxs-lookup"><span data-stu-id="f8729-117">Remarks</span></span>  
 <span data-ttu-id="f8729-118">L'interface `ICorProfilerThreadEnum` est un énumérateur.</span><span class="sxs-lookup"><span data-stu-id="f8729-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="f8729-119">Elle permet au récepteur d’un tableau de récupérer des éléments de l’expéditeur à une fréquence appropriée pour le récepteur.</span><span class="sxs-lookup"><span data-stu-id="f8729-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="f8729-120">En d'autres termes, le récepteur peut contrôler explicitement le flux d'éléments de tableau et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="f8729-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8729-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8729-121">Requirements</span></span>  
 <span data-ttu-id="f8729-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8729-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8729-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8729-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8729-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8729-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8729-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8729-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8729-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8729-126">See also</span></span>

- [<span data-ttu-id="f8729-127">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f8729-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f8729-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f8729-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
