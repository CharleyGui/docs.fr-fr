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
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114745"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="09b24-102">ICorProfilerInfo5::GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="09b24-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="09b24-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="09b24-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="09b24-104">Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications du CLR.</span><span class="sxs-lookup"><span data-stu-id="09b24-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="09b24-105">Il fournit des fonctionnalités non fournies par la méthode [ICorProfilerInfo :: GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09b24-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b24-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09b24-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09b24-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09b24-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="09b24-108">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="09b24-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="09b24-109">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="09b24-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="09b24-110">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="09b24-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="09b24-111">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="09b24-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="09b24-112">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="09b24-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="09b24-113">Les bits sont décrits dans l’énumération [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="09b24-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09b24-114">Notes</span><span class="sxs-lookup"><span data-stu-id="09b24-114">Remarks</span></span>  
 <span data-ttu-id="09b24-115">La méthode `GetEventMask2` est utilisée pour déterminer les rappels auxquels le profileur s'est abonné.</span><span class="sxs-lookup"><span data-stu-id="09b24-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="09b24-116">En général, vous effectuez un OR logique sur les valeurs `pdwEventsLow` et `pdwEventsHigh` et les nouveaux bits que vous voulez définir, puis vous appelez la méthode [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09b24-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="09b24-117">Cette méthode est l’alternative recommandée à la méthode [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09b24-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b24-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="09b24-118">Requirements</span></span>  
 <span data-ttu-id="09b24-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09b24-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b24-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09b24-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09b24-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09b24-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09b24-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b24-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b24-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09b24-123">See also</span></span>

- [<span data-ttu-id="09b24-124">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="09b24-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="09b24-125">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="09b24-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
