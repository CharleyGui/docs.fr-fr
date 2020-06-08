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
ms.openlocfilehash: 758e5b71443b127c80c820eb8531056530e81b13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495695"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="c5abf-102">ICorProfilerInfo5::GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="c5abf-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="c5abf-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="c5abf-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c5abf-104">Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications du CLR.</span><span class="sxs-lookup"><span data-stu-id="c5abf-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="c5abf-105">Il fournit des fonctionnalités non fournies par la méthode [ICorProfilerInfo :: GetEventMask](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c5abf-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5abf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5abf-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5abf-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5abf-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="c5abf-108">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="c5abf-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="c5abf-109">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="c5abf-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="c5abf-110">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c5abf-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="c5abf-111">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="c5abf-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="c5abf-112">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="c5abf-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="c5abf-113">Les bits sont décrits dans l’énumération [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c5abf-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5abf-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5abf-114">Remarks</span></span>  
 <span data-ttu-id="c5abf-115">La méthode `GetEventMask2` est utilisée pour déterminer les rappels auxquels le profileur s'est abonné.</span><span class="sxs-lookup"><span data-stu-id="c5abf-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="c5abf-116">En général, vous effectuez un OR logique sur `pdwEventsLow` les `pdwEventsHigh` valeurs et et les nouveaux bits que vous voulez définir, puis vous appelez la méthode [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c5abf-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="c5abf-117">Cette méthode est l’alternative recommandée à la méthode [GetEventMask](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c5abf-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5abf-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5abf-118">Requirements</span></span>  
 <span data-ttu-id="c5abf-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5abf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5abf-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5abf-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5abf-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5abf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5abf-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5abf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5abf-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5abf-123">See also</span></span>

- [<span data-ttu-id="c5abf-124">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="c5abf-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="c5abf-125">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="c5abf-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
