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
ms.openlocfilehash: 3b729d3be84571a48cc9a770d7f06b99723c0d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445065"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="a8c06-102">ICorProfilerCallback::ClassUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="a8c06-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="a8c06-103">Notifies the profiler that a class is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="a8c06-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8c06-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8c06-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8c06-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a8c06-106">[in] Identifies the class that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="a8c06-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8c06-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a8c06-107">Remarks</span></span>  
 <span data-ttu-id="a8c06-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span><span class="sxs-lookup"><span data-stu-id="a8c06-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8c06-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="a8c06-109">Requirements</span></span>  
 <span data-ttu-id="a8c06-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c06-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8c06-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8c06-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8c06-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8c06-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c06-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8c06-114">See also</span></span>

- [<span data-ttu-id="a8c06-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a8c06-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a8c06-116">ClassUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="a8c06-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
