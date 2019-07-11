---
title: ICorProfilerCallback::ModuleUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c99ddc66cca0a0d0083cfa19cfca34a1e557d4e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769149"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="a8b9d-102">ICorProfilerCallback::ModuleUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="a8b9d-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="a8b9d-103">Notifie le profileur qu’un module est déchargé.</span><span class="sxs-lookup"><span data-stu-id="a8b9d-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8b9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8b9d-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a8b9d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8b9d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a8b9d-106">[in] L’ID du module qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="a8b9d-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8b9d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a8b9d-107">Remarks</span></span>  
 <span data-ttu-id="a8b9d-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations après la `ModuleUnloadStarted` retourne de la méthode, il s’agit dernière chance du profileur d’obtenir des informations sur ce module.</span><span class="sxs-lookup"><span data-stu-id="a8b9d-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8b9d-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8b9d-109">Requirements</span></span>  
 <span data-ttu-id="a8b9d-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8b9d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8b9d-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8b9d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8b9d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8b9d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8b9d-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8b9d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b9d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8b9d-114">See also</span></span>

- [<span data-ttu-id="a8b9d-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a8b9d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a8b9d-116">ModuleUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="a8b9d-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
