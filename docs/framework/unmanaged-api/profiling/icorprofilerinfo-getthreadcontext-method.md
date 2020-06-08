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
ms.openlocfilehash: 45ae164e79f077549a1d685aa060484240546a10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497948"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="dd196-102">ICorProfilerInfo::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="dd196-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="dd196-103">Obtient l’identité de contexte actuellement associée au thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="dd196-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd196-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd196-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd196-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd196-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="dd196-106">dans ID du thread.</span><span class="sxs-lookup"><span data-stu-id="dd196-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="dd196-107">à Pointeur vers l’ID de contexte actuellement associé au thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="dd196-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="dd196-108">Si aucun contexte n’est actuellement associé au thread, cette fonction retournera CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="dd196-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd196-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dd196-109">Requirements</span></span>  
 <span data-ttu-id="dd196-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd196-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd196-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd196-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd196-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd196-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd196-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd196-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd196-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd196-114">See also</span></span>

- [<span data-ttu-id="dd196-115">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="dd196-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
