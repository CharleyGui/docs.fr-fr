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
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498399"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="15ec5-102">ICorProfilerInfo::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="15ec5-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="15ec5-103">Obtient l’ID du thread actuel, s’il s’agit d’un thread managé.</span><span class="sxs-lookup"><span data-stu-id="15ec5-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ec5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15ec5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15ec5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15ec5-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="15ec5-106">à Pointeur vers l’ID retourné du thread managé.</span><span class="sxs-lookup"><span data-stu-id="15ec5-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15ec5-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="15ec5-107">Remarks</span></span>  
 <span data-ttu-id="15ec5-108">Si le thread actuel est un thread du runtime interne ou un autre thread non managé, `GetCurrentThreadID` retourne CORPROF_E_NOT_MANAGED_THREAD comme HRESULT, et la valeur retournée du `pThreadId` paramètre est null.</span><span class="sxs-lookup"><span data-stu-id="15ec5-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15ec5-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="15ec5-109">Requirements</span></span>  
 <span data-ttu-id="15ec5-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15ec5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15ec5-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15ec5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15ec5-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15ec5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15ec5-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15ec5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ec5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15ec5-114">See also</span></span>

- [<span data-ttu-id="15ec5-115">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="15ec5-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
