---
title: ICorProfilerCallback2::ThreadNameChanged, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 1149298b4c5e521b37aae6ec48d463f395f18ae3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439558"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="b9841-102">ICorProfilerCallback2::ThreadNameChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="b9841-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="b9841-103">Notifies the code profiler that the name of a thread has changed.</span><span class="sxs-lookup"><span data-stu-id="b9841-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9841-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9841-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9841-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9841-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b9841-106">[in] The ID of the thread.</span><span class="sxs-lookup"><span data-stu-id="b9841-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b9841-107">[in] The length of the new name of the thread.</span><span class="sxs-lookup"><span data-stu-id="b9841-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="b9841-108">[in] The new name of the thread.</span><span class="sxs-lookup"><span data-stu-id="b9841-108">[in] The new name of the thread.</span></span> <span data-ttu-id="b9841-109">The name is not null-terminated.</span><span class="sxs-lookup"><span data-stu-id="b9841-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9841-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="b9841-110">Requirements</span></span>  
 <span data-ttu-id="b9841-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9841-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9841-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9841-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9841-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9841-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9841-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9841-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9841-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9841-115">See also</span></span>

- [<span data-ttu-id="b9841-116">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b9841-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b9841-117">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="b9841-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
