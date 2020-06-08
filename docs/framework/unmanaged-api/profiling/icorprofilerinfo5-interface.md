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
ms.openlocfilehash: 82f6262c2c576b49be4e7fcaa14043950df4c67a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495625"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="c6609-102">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="c6609-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="c6609-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="c6609-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c6609-104">Une sous-classe de [ICorProfilerInfo4](icorprofilerinfo4-interface.md) qui fournit des méthodes à utiliser par les profileurs de code pour communiquer avec le Common Language Runtime (CLR) afin de contrôler la surveillance des événements.</span><span class="sxs-lookup"><span data-stu-id="c6609-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6609-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c6609-105">Methods</span></span>  
  
|<span data-ttu-id="c6609-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c6609-106">Method</span></span>|<span data-ttu-id="c6609-107">Description</span><span class="sxs-lookup"><span data-stu-id="c6609-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6609-108">GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="c6609-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="c6609-109">Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications du CLR.</span><span class="sxs-lookup"><span data-stu-id="c6609-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="c6609-110">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="c6609-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="c6609-111">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir des notifications d'événements du CLR.</span><span class="sxs-lookup"><span data-stu-id="c6609-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6609-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="c6609-112">Remarks</span></span>  
 <span data-ttu-id="c6609-113">Les méthodes disponibles sur cette interface sont destinées à remplacer les méthodes [ICorProfilerInfo :: GetEventMask](icorprofilerinfo-geteventmask-method.md) et [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6609-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6609-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6609-114">Requirements</span></span>  
 <span data-ttu-id="c6609-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6609-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6609-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6609-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6609-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6609-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6609-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6609-118">See also</span></span>

- [<span data-ttu-id="c6609-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="c6609-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
