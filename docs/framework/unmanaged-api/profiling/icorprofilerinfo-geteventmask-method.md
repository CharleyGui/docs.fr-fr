---
title: ICorProfilerInfo::GetEventMask, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fea50b9d42511540197c80d4ba402834b216830
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957944"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="635cc-102">ICorProfilerInfo::GetEventMask, méthode</span><span class="sxs-lookup"><span data-stu-id="635cc-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="635cc-103">Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications d'événement du CLR.</span><span class="sxs-lookup"><span data-stu-id="635cc-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="635cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="635cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="635cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="635cc-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="635cc-106">[en sortie] Un pointeur vers une valeur de 4 octets qui spécifie les catégories des événements.</span><span class="sxs-lookup"><span data-stu-id="635cc-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="635cc-107">Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents.</span><span class="sxs-lookup"><span data-stu-id="635cc-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="635cc-108">Les bits sont décrits dans l’énumération [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="635cc-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="635cc-109">Notes</span><span class="sxs-lookup"><span data-stu-id="635cc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="635cc-110">Vous devez appeler la méthode [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) au lieu de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="635cc-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="635cc-111">Bien que `SetEventMask` la méthode continue d’être prise en charge, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) fournit des fonctionnalités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="635cc-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="635cc-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="635cc-112">Requirements</span></span>  
 <span data-ttu-id="635cc-113">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="635cc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="635cc-114">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="635cc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="635cc-115">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="635cc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="635cc-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="635cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635cc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="635cc-117">See also</span></span>

- [<span data-ttu-id="635cc-118">GetEventMask2, méthode</span><span class="sxs-lookup"><span data-stu-id="635cc-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="635cc-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="635cc-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
