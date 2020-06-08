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
ms.openlocfilehash: 8027cdcde8281c363207e309bf65fcd90c03b626
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495617"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="4795b-102">ICorProfilerInfo5::SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="4795b-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="4795b-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="4795b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4795b-104">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir des notifications d'événements du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4795b-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="4795b-105">Elle offre plus de fonctionnalités que la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4795b-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4795b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4795b-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4795b-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4795b-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="4795b-108">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="4795b-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="4795b-109">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="4795b-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="4795b-110">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4795b-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="4795b-111">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="4795b-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="4795b-112">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="4795b-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="4795b-113">Les bits sont décrits dans l’énumération [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4795b-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4795b-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="4795b-114">Remarks</span></span>  
 <span data-ttu-id="4795b-115">La méthode `SetEventMask2` est utilisée pour définir les rappels auxquels le profileur s'abonne.</span><span class="sxs-lookup"><span data-stu-id="4795b-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="4795b-116">En général, vous appelez la méthode [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) pour déterminer les bits qui sont définis, effectuez une ou logique de ses `pdwEventsLow` `pdwEventsHigh` valeurs et et de tous les nouveaux bits que vous voulez définir, puis appelez la `SetEventMask2` méthode.</span><span class="sxs-lookup"><span data-stu-id="4795b-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="4795b-117">Cette méthode est l’alternative recommandée à la méthode [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4795b-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4795b-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4795b-118">Requirements</span></span>  
 <span data-ttu-id="4795b-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4795b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4795b-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4795b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4795b-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4795b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4795b-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4795b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4795b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4795b-123">See also</span></span>

- [<span data-ttu-id="4795b-124">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="4795b-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="4795b-125">GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="4795b-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
