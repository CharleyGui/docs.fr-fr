---
title: ICorProfilerInfo::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: f8eff85392d355ea54980ac6b29e3c4cebb1b240
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869593"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="accc3-102">ICorProfilerInfo::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="accc3-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="accc3-103">Obtient l’identité de contexte actuellement associée au thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="accc3-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="accc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="accc3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="accc3-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="accc3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="accc3-106">dans ID du thread.</span><span class="sxs-lookup"><span data-stu-id="accc3-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="accc3-107">à Pointeur vers l’ID de contexte actuellement associé au thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="accc3-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="accc3-108">Si aucun contexte n’est actuellement associé au thread, cette fonction retournera CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="accc3-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="accc3-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="accc3-109">Requirements</span></span>  
 <span data-ttu-id="accc3-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="accc3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="accc3-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="accc3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="accc3-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="accc3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="accc3-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="accc3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="accc3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="accc3-114">See also</span></span>

- [<span data-ttu-id="accc3-115">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="accc3-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
