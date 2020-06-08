---
title: ICorProfilerCallback::ModuleLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503352"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="c061b-102">ICorProfilerCallback::ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="c061b-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="c061b-103">Notifie le profileur qu’un module est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="c061b-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c061b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c061b-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c061b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c061b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c061b-106">dans ID du module en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="c061b-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c061b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c061b-107">Remarks</span></span>  
 <span data-ttu-id="c061b-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="c061b-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c061b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c061b-109">Requirements</span></span>  
 <span data-ttu-id="c061b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c061b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c061b-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c061b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c061b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c061b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c061b-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c061b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c061b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c061b-114">See also</span></span>

- [<span data-ttu-id="c061b-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c061b-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
