---
title: ICorProfilerInfo::GetHandleFromThread, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 038f922eaaeb7d660cfbdcc0facb89677bdd154e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863541"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="c0c7b-102">ICorProfilerInfo::GetHandleFromThread, méthode</span><span class="sxs-lookup"><span data-stu-id="c0c7b-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="c0c7b-103">Mappe l’ID d’un thread à un handle de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="c0c7b-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0c7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0c7b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="c0c7b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c0c7b-106">dans ID de thread à mapper.</span><span class="sxs-lookup"><span data-stu-id="c0c7b-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="c0c7b-107">à Pointeur vers un handle de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="c0c7b-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0c7b-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c0c7b-108">Remarks</span></span>  
 <span data-ttu-id="c0c7b-109">Le profileur doit appeler la fonction de `DuplicateHandle` Win32 sur le handle avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="c0c7b-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0c7b-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c0c7b-110">Requirements</span></span>  
 <span data-ttu-id="c0c7b-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0c7b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0c7b-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0c7b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0c7b-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0c7b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0c7b-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0c7b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c7b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0c7b-115">See also</span></span>

- [<span data-ttu-id="c0c7b-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="c0c7b-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
