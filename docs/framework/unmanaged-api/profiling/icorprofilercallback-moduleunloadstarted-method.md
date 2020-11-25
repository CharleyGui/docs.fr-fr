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
ms.openlocfilehash: 12d5f7e073337af6034b8f313a2e0161620a65ea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720954"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="72455-102">ICorProfilerCallback::ModuleUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="72455-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>

<span data-ttu-id="72455-103">Notifie le profileur qu’un module est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="72455-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72455-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72455-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="72455-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="72455-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="72455-106">dans ID du module en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="72455-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72455-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="72455-107">Remarks</span></span>  

 <span data-ttu-id="72455-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations après le retour de la `ModuleUnloadStarted` méthode, c’est la dernière chance du profileur pour obtenir des informations sur ce module.</span><span class="sxs-lookup"><span data-stu-id="72455-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72455-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="72455-109">Requirements</span></span>  

 <span data-ttu-id="72455-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72455-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72455-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72455-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72455-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72455-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72455-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72455-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72455-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72455-114">See also</span></span>

- [<span data-ttu-id="72455-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="72455-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="72455-116">ModuleUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="72455-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
