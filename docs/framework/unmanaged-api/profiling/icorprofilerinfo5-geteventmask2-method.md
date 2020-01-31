---
title: ICorProfilerInfo5::GetEventMask2, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: f3943eef969f777b40dc51c4900b190561f14887
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868393"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="22a47-102">ICorProfilerInfo5::GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="22a47-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="22a47-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="22a47-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="22a47-104">Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications du CLR.</span><span class="sxs-lookup"><span data-stu-id="22a47-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="22a47-105">Il fournit des fonctionnalités non fournies par la méthode [ICorProfilerInfo :: GetEventMask](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22a47-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a47-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22a47-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22a47-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="22a47-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="22a47-108">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="22a47-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="22a47-109">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="22a47-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="22a47-110">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="22a47-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="22a47-111">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="22a47-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="22a47-112">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="22a47-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="22a47-113">Les bits sont décrits dans l’énumération [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="22a47-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22a47-114">Notes</span><span class="sxs-lookup"><span data-stu-id="22a47-114">Remarks</span></span>  
 <span data-ttu-id="22a47-115">La méthode `GetEventMask2` est utilisée pour déterminer les rappels auxquels le profileur s'est abonné.</span><span class="sxs-lookup"><span data-stu-id="22a47-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="22a47-116">En général, vous effectuez un OR logique sur les valeurs `pdwEventsLow` et `pdwEventsHigh` et les nouveaux bits que vous voulez définir, puis vous appelez la méthode [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22a47-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="22a47-117">Cette méthode est l’alternative recommandée à la méthode [GetEventMask](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22a47-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a47-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="22a47-118">Requirements</span></span>  
 <span data-ttu-id="22a47-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a47-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a47-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22a47-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22a47-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22a47-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22a47-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a47-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a47-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22a47-123">See also</span></span>

- [<span data-ttu-id="22a47-124">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="22a47-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="22a47-125">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="22a47-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
