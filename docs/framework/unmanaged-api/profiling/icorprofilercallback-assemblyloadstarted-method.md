---
title: ICorProfilerCallback::AssemblyLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ace66630176149a18a174fad24f782a289b0e9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763001"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="cfbfa-102">ICorProfilerCallback::AssemblyLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="cfbfa-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="cfbfa-103">Notifie le profileur qu’un assembly est chargé.</span><span class="sxs-lookup"><span data-stu-id="cfbfa-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfbfa-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfbfa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cfbfa-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="cfbfa-106">[in] Identifie l’assembly qui est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="cfbfa-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfbfa-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cfbfa-107">Remarks</span></span>  
 <span data-ttu-id="cfbfa-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations jusqu'à ce que le [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="cfbfa-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbfa-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cfbfa-109">Requirements</span></span>  
 <span data-ttu-id="cfbfa-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfbfa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbfa-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cfbfa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfbfa-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfbfa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfbfa-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbfa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbfa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfbfa-114">See also</span></span>

- [<span data-ttu-id="cfbfa-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="cfbfa-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
