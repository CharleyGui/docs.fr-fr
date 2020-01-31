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
ms.openlocfilehash: 75fb92be078c40f49ddcdc6662535b2a0be7a6ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866557"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="0b5a5-102">ICorProfilerCallback::ClassUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="0b5a5-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="0b5a5-103">Notifie le profileur qu’une classe est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="0b5a5-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b5a5-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b5a5-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0b5a5-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="0b5a5-106">\[in] identifie la classe qui est déchargée.</span><span class="sxs-lookup"><span data-stu-id="0b5a5-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b5a5-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0b5a5-107">Remarks</span></span>  
 <span data-ttu-id="0b5a5-108">La valeur de `classId` n’est pas valide pour une demande d’informations après le retour de la méthode `ClassUnloadStarted`, c’est la dernière chance du profileur pour obtenir des informations sur cette classe.</span><span class="sxs-lookup"><span data-stu-id="0b5a5-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5a5-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0b5a5-109">Requirements</span></span>  
 <span data-ttu-id="0b5a5-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5a5-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b5a5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b5a5-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b5a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b5a5-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5a5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b5a5-114">See also</span></span>

- [<span data-ttu-id="0b5a5-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="0b5a5-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0b5a5-116">ClassUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="0b5a5-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
