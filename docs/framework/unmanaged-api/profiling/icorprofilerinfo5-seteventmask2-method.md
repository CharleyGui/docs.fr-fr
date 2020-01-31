---
title: ICorProfilerInfo5::SetEventMask2, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 10e84b729c8af607165009a8591a69dbc1afcb1e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868380"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="69be7-102">ICorProfilerInfo5::SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="69be7-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="69be7-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="69be7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="69be7-104">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir des notifications d'événements du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="69be7-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="69be7-105">Elle offre plus de fonctionnalités que la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="69be7-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69be7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69be7-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69be7-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="69be7-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="69be7-108">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="69be7-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="69be7-109">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="69be7-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="69be7-110">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="69be7-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="69be7-111">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="69be7-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="69be7-112">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="69be7-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="69be7-113">Les bits sont décrits dans l’énumération [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="69be7-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69be7-114">Notes</span><span class="sxs-lookup"><span data-stu-id="69be7-114">Remarks</span></span>  
 <span data-ttu-id="69be7-115">La méthode `SetEventMask2` est utilisée pour définir les rappels auxquels le profileur s'abonne.</span><span class="sxs-lookup"><span data-stu-id="69be7-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="69be7-116">En général, vous appelez la méthode [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) pour déterminer les bits qui sont définis, effectuez une `pdwEventsLow` logique ou de ses valeurs de `pdwEventsHigh` et des nouveaux bits que vous voulez définir, puis appelez la méthode `SetEventMask2`.</span><span class="sxs-lookup"><span data-stu-id="69be7-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="69be7-117">Cette méthode est l’alternative recommandée à la méthode [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="69be7-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69be7-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="69be7-118">Requirements</span></span>  
 <span data-ttu-id="69be7-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69be7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69be7-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69be7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69be7-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69be7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69be7-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69be7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69be7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69be7-123">See also</span></span>

- [<span data-ttu-id="69be7-124">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="69be7-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="69be7-125">GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="69be7-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
