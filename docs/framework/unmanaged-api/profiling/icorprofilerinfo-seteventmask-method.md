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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3f61caf0f4993c49d2956a37068aa826c4ac29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772116"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="8a87f-102">ICorProfilerInfo::SetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="8a87f-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="8a87f-103">Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir une notification du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="8a87f-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a87f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a87f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a87f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a87f-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="8a87f-106">[en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="8a87f-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="8a87f-107">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="8a87f-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="8a87f-108">Les bits sont décrits dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="8a87f-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a87f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8a87f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a87f-110">Vous devez appeler la [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthode au lieu de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8a87f-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="8a87f-111">Bien que le `SetEventMask` méthode continue à être pris en charge, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) fournit des fonctionnalités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8a87f-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a87f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a87f-112">Requirements</span></span>  
 <span data-ttu-id="8a87f-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a87f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a87f-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a87f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a87f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a87f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a87f-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a87f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a87f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a87f-117">See also</span></span>

- [<span data-ttu-id="8a87f-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="8a87f-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="8a87f-119">SetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="8a87f-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
