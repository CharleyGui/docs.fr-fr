---
title: ICorProfilerCallback::AssemblyUnloadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a75d31f0a2c844895363bb4693dbcb5aba4cce1f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775511"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="15788-102">ICorProfilerCallback::AssemblyUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="15788-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="15788-103">Informe le profileur qu’un assembly a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="15788-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15788-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15788-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15788-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15788-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="15788-106">[in] Identifie l’assembly qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="15788-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="15788-107">[in] HRESULT qui indique si l’assembly a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="15788-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15788-108">Notes</span><span class="sxs-lookup"><span data-stu-id="15788-108">Remarks</span></span>  
 <span data-ttu-id="15788-109">La valeur de `assemblyId` n’est pas valide pour une demande d’informations après la [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) méthode retourne.</span><span class="sxs-lookup"><span data-stu-id="15788-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="15788-110">Certaines parties du déchargement de l’assembly peuvent continuer après le `AssemblyUnloadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="15788-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="15788-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="15788-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="15788-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement de l’assembly a réussi.</span><span class="sxs-lookup"><span data-stu-id="15788-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15788-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="15788-113">Requirements</span></span>  
 <span data-ttu-id="15788-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15788-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15788-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15788-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15788-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15788-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15788-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15788-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15788-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15788-118">See also</span></span>

- [<span data-ttu-id="15788-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="15788-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
