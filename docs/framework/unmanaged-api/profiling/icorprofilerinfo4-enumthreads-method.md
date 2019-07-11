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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d4cffc7c407db6acd15462e1e00769101e44b40
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780868"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="20ba8-102">ICorProfilerInfo4::EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="20ba8-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="20ba8-103">Retourne un énumérateur qui fournit des méthodes pour boucler séquentiellement dans la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="20ba8-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ba8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20ba8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20ba8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20ba8-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="20ba8-106">[out] Un pointeur vers un [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="20ba8-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20ba8-107">Notes</span><span class="sxs-lookup"><span data-stu-id="20ba8-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ba8-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="20ba8-108">Requirements</span></span>  
 <span data-ttu-id="20ba8-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20ba8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20ba8-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20ba8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20ba8-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20ba8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20ba8-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20ba8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ba8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20ba8-113">See also</span></span>

- [<span data-ttu-id="20ba8-114">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="20ba8-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="20ba8-115">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="20ba8-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="20ba8-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="20ba8-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="20ba8-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="20ba8-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
