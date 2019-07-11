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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ffe25cae7122e65bed6aece7b0f6b2abe82c1eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779294"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="b54c6-102">ICorProfilerCallback2::ThreadNameChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="b54c6-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="b54c6-103">Notifie le profileur de code que le nom d’un thread a changé.</span><span class="sxs-lookup"><span data-stu-id="b54c6-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b54c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b54c6-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b54c6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b54c6-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b54c6-106">[in] L’ID du thread.</span><span class="sxs-lookup"><span data-stu-id="b54c6-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b54c6-107">[in] La longueur du nouveau nom du thread.</span><span class="sxs-lookup"><span data-stu-id="b54c6-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="b54c6-108">[in] Le nouveau nom du thread.</span><span class="sxs-lookup"><span data-stu-id="b54c6-108">[in] The new name of the thread.</span></span> <span data-ttu-id="b54c6-109">Le nom ne se termine pas par une valeur null.</span><span class="sxs-lookup"><span data-stu-id="b54c6-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b54c6-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b54c6-110">Requirements</span></span>  
 <span data-ttu-id="b54c6-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b54c6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b54c6-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b54c6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b54c6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b54c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b54c6-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b54c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54c6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b54c6-115">See also</span></span>

- [<span data-ttu-id="b54c6-116">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b54c6-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b54c6-117">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="b54c6-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
