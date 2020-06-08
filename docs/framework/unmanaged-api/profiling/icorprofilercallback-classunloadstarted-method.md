---
title: ICorProfilerCallback::ClassUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 86402abca5386f34256f1f44f674f1e1898ad5fd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500349"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="71b23-102">ICorProfilerCallback::ClassUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="71b23-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="71b23-103">Notifie le profileur qu’une classe est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="71b23-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71b23-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71b23-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="71b23-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="71b23-106">\[in] identifie la classe qui est déchargée.</span><span class="sxs-lookup"><span data-stu-id="71b23-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="71b23-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="71b23-107">Remarks</span></span>  
 <span data-ttu-id="71b23-108">La valeur de `classId` n’est pas valide pour une demande d’informations après le retour de la `ClassUnloadStarted` méthode, il s’agit de la dernière chance du profileur pour obtenir des informations sur cette classe.</span><span class="sxs-lookup"><span data-stu-id="71b23-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71b23-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="71b23-109">Requirements</span></span>  
 <span data-ttu-id="71b23-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71b23-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71b23-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71b23-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71b23-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71b23-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71b23-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71b23-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b23-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71b23-114">See also</span></span>

- [<span data-ttu-id="71b23-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="71b23-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="71b23-116">ClassUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="71b23-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
