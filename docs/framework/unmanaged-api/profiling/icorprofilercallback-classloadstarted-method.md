---
title: ICorProfilerCallback::ClassLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500362"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="648eb-102">ICorProfilerCallback::ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="648eb-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="648eb-103">Notifie le profileur qu’une classe est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="648eb-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="648eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="648eb-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="648eb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="648eb-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="648eb-106">\[in] identifie la classe en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="648eb-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="648eb-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="648eb-107">Remarks</span></span>  
 <span data-ttu-id="648eb-108">La valeur de `classId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="648eb-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="648eb-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="648eb-109">Requirements</span></span>  
 <span data-ttu-id="648eb-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="648eb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="648eb-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="648eb-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="648eb-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="648eb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="648eb-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="648eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648eb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="648eb-114">See also</span></span>

- [<span data-ttu-id="648eb-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="648eb-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
