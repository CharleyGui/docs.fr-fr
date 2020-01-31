---
title: ICorProfilerThreadEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 230b02b71abea48b1c3ad4094ea90812493149d1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860993"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="9336d-102">ICorProfilerThreadEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="9336d-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="9336d-103">Obtient le nombre de threads utilisés par l'application.</span><span class="sxs-lookup"><span data-stu-id="9336d-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9336d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9336d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9336d-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9336d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9336d-106">à Nombre de threads utilisés par l’application.</span><span class="sxs-lookup"><span data-stu-id="9336d-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9336d-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9336d-107">Requirements</span></span>  
 <span data-ttu-id="9336d-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9336d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9336d-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9336d-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9336d-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9336d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9336d-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9336d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9336d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9336d-112">See also</span></span>

- [<span data-ttu-id="9336d-113">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="9336d-113">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="9336d-114">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="9336d-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
