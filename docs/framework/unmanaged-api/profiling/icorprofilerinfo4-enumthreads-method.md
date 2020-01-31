---
title: ICorProfilerInfo4::EnumThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: 5bea1b75e94d8011d3582d4f07d36bbc7a560502
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862215"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="305d1-102">ICorProfilerInfo4::EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="305d1-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="305d1-103">Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein de la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="305d1-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="305d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="305d1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="305d1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="305d1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="305d1-106">à Pointeur vers une interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="305d1-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="305d1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="305d1-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="305d1-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="305d1-108">Requirements</span></span>  
 <span data-ttu-id="305d1-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="305d1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="305d1-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="305d1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="305d1-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="305d1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="305d1-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="305d1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305d1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="305d1-113">See also</span></span>

- [<span data-ttu-id="305d1-114">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="305d1-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="305d1-115">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="305d1-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="305d1-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="305d1-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="305d1-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="305d1-117">Profiling</span></span>](index.md)
