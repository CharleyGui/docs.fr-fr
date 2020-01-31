---
title: ICorProfilerInfo::GetCurrentThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: e70d8ee40e16e37a12f8ed4033d2aa7489f0f25e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863944"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="003a7-102">ICorProfilerInfo::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="003a7-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="003a7-103">Obtient l’ID du thread actuel, s’il s’agit d’un thread managé.</span><span class="sxs-lookup"><span data-stu-id="003a7-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="003a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="003a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="003a7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="003a7-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="003a7-106">à Pointeur vers l’ID retourné du thread managé.</span><span class="sxs-lookup"><span data-stu-id="003a7-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="003a7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="003a7-107">Remarks</span></span>  
 <span data-ttu-id="003a7-108">Si le thread actuel est un thread du runtime interne ou un autre thread non managé, `GetCurrentThreadID` retourne CORPROF_E_NOT_MANAGED_THREAD comme HRESULT, et la valeur retournée du paramètre `pThreadId` sera null.</span><span class="sxs-lookup"><span data-stu-id="003a7-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="003a7-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="003a7-109">Requirements</span></span>  
 <span data-ttu-id="003a7-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="003a7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="003a7-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="003a7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="003a7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="003a7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="003a7-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="003a7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003a7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="003a7-114">See also</span></span>

- [<span data-ttu-id="003a7-115">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="003a7-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
