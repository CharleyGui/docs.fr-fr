---
title: ICorProfilerInfo5, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: e6df5dcb26d61d30407d1efeeed7d207744276fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124189"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="ec580-102">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="ec580-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="ec580-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="ec580-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ec580-104">Une sous-classe de [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) qui fournit des méthodes à utiliser par les profileurs de code pour communiquer avec le Common Language Runtime (CLR) afin de contrôler la surveillance des événements.</span><span class="sxs-lookup"><span data-stu-id="ec580-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec580-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ec580-105">Methods</span></span>  
  
|<span data-ttu-id="ec580-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="ec580-106">Method</span></span>|<span data-ttu-id="ec580-107">Description</span><span class="sxs-lookup"><span data-stu-id="ec580-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec580-108">GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="ec580-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="ec580-109">Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications du CLR.</span><span class="sxs-lookup"><span data-stu-id="ec580-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="ec580-110">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="ec580-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="ec580-111">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir des notifications d'événements du CLR.</span><span class="sxs-lookup"><span data-stu-id="ec580-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec580-112">Notes</span><span class="sxs-lookup"><span data-stu-id="ec580-112">Remarks</span></span>  
 <span data-ttu-id="ec580-113">Les méthodes disponibles sur cette interface sont destinées à remplacer les méthodes [ICorProfilerInfo :: GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) et [ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ec580-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec580-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="ec580-114">Requirements</span></span>  
 <span data-ttu-id="ec580-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec580-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec580-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec580-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec580-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec580-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec580-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec580-118">See also</span></span>

- [<span data-ttu-id="ec580-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ec580-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
