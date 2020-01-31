---
title: ICorProfilerInfo::SetEventMask, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
ms.openlocfilehash: ed39411fa88c38da58e8a881c47d19b3b8c9ff8d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869276"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="63bc4-102">ICorProfilerInfo::SetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="63bc4-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="63bc4-103">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir une notification du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="63bc4-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63bc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63bc4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63bc4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="63bc4-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="63bc4-106">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="63bc4-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="63bc4-107">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="63bc4-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="63bc4-108">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="63bc4-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63bc4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="63bc4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63bc4-110">Vous devez appeler la méthode [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) au lieu de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="63bc4-110">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="63bc4-111">Bien que la méthode `SetEventMask` continue d’être prise en charge, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) fournit des fonctionnalités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="63bc4-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63bc4-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="63bc4-112">Requirements</span></span>  
 <span data-ttu-id="63bc4-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63bc4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63bc4-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63bc4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63bc4-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63bc4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63bc4-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63bc4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bc4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63bc4-117">See also</span></span>

- [<span data-ttu-id="63bc4-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="63bc4-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="63bc4-119">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="63bc4-119">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
