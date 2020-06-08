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
ms.openlocfilehash: c7ad94bf766e0fcdbff95b0766cf68c2196a2c71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503329"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="1d2ff-102">ICorProfilerCallback::ModuleUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="1d2ff-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="1d2ff-103">Notifie le profileur qu’un module est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d2ff-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="1d2ff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d2ff-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1d2ff-106">dans ID du module en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d2ff-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d2ff-107">Remarks</span></span>  
 <span data-ttu-id="1d2ff-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations après le retour de la `ModuleUnloadStarted` méthode, c’est la dernière chance du profileur pour obtenir des informations sur ce module.</span><span class="sxs-lookup"><span data-stu-id="1d2ff-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d2ff-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1d2ff-109">Requirements</span></span>  
 <span data-ttu-id="1d2ff-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d2ff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d2ff-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d2ff-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d2ff-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d2ff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d2ff-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d2ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2ff-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d2ff-114">See also</span></span>

- [<span data-ttu-id="1d2ff-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1d2ff-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1d2ff-116">ModuleUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="1d2ff-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
