---
title: ICorProfilerCallback::AssemblyLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: df172edb97a82ae3bf2d46c8be6ea05d5445a09a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500427"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="1b1c4-102">ICorProfilerCallback::AssemblyLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c4-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="1b1c4-103">Notifie le profileur qu’un assembly est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="1b1c4-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b1c4-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b1c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1b1c4-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="1b1c4-106">\[in] identifie l’assembly en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="1b1c4-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b1c4-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1b1c4-107">Remarks</span></span>  
 <span data-ttu-id="1b1c4-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: AssemblyLoadFinished,](icorprofilercallback-assemblyloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="1b1c4-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1c4-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b1c4-109">Requirements</span></span>  
 <span data-ttu-id="1b1c4-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1c4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1c4-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b1c4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b1c4-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b1c4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1c4-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1c4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b1c4-114">See also</span></span>

- [<span data-ttu-id="1b1c4-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1b1c4-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
