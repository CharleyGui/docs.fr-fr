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
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175146"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="46717-102">ICorProfilerCallback::ModuleUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="46717-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="46717-103">Informe le profileur qu’un module est déchargé.</span><span class="sxs-lookup"><span data-stu-id="46717-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46717-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46717-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="46717-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46717-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="46717-106">[dans] L’ID du module qui est déchargé.</span><span class="sxs-lookup"><span data-stu-id="46717-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46717-107">Notes </span><span class="sxs-lookup"><span data-stu-id="46717-107">Remarks</span></span>  
 <span data-ttu-id="46717-108">La valeur `moduleId` de n’est pas `ModuleUnloadStarted` valide pour une demande d’information après le retour de la méthode - c’est la dernière chance du profileur d’obtenir des informations sur ce module.</span><span class="sxs-lookup"><span data-stu-id="46717-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46717-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46717-109">Requirements</span></span>  
 <span data-ttu-id="46717-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46717-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46717-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46717-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46717-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46717-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46717-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46717-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46717-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46717-114">See also</span></span>

- [<span data-ttu-id="46717-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="46717-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="46717-116">ModuleUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="46717-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
