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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84ff6cb79abdb60a3c01c66580ed6fc10f6c137e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762931"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="d5b41-102">ICorProfilerCallback::ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="d5b41-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="d5b41-103">Informe le profileur qu’une classe est chargée.</span><span class="sxs-lookup"><span data-stu-id="d5b41-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5b41-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b41-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5b41-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="d5b41-106">[in] Identifie la classe qui est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="d5b41-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5b41-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d5b41-107">Remarks</span></span>  
 <span data-ttu-id="d5b41-108">La valeur de `classId` n’est pas valide pour une demande d’informations jusqu'à ce que le [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="d5b41-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b41-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d5b41-109">Requirements</span></span>  
 <span data-ttu-id="d5b41-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5b41-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b41-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5b41-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5b41-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5b41-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5b41-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b41-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b41-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5b41-114">See also</span></span>

- [<span data-ttu-id="d5b41-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d5b41-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
