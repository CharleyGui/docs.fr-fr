---
title: ICorProfilerCallback::FunctionUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 988843559e55cc4cacd2a40bb3e6ac51721e99b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175159"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="d60ee-102">ICorProfilerCallback::FunctionUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="d60ee-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="d60ee-103">Informe le profileur que le temps d’exécution a commencé à décharger une fonction.</span><span class="sxs-lookup"><span data-stu-id="d60ee-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d60ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d60ee-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="d60ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d60ee-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="d60ee-106">\[dans] L’ID de la fonction qui est déchargée.</span><span class="sxs-lookup"><span data-stu-id="d60ee-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="d60ee-107">Notes </span><span class="sxs-lookup"><span data-stu-id="d60ee-107">Remarks</span></span>  
 <span data-ttu-id="d60ee-108">La valeur `functionId` du paramètre n’est plus valide après le retour de cette méthode à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="d60ee-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d60ee-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d60ee-109">Requirements</span></span>  
 <span data-ttu-id="d60ee-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d60ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d60ee-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d60ee-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d60ee-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d60ee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d60ee-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d60ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d60ee-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d60ee-114">See also</span></span>

- [<span data-ttu-id="d60ee-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d60ee-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
