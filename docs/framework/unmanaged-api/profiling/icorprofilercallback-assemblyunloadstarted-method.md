---
title: ICorProfilerCallback::AssemblyUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 0a677e33950f178b916a5e9e9cbb7bd918c1349b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866609"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="a86d2-102">ICorProfilerCallback::AssemblyUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="a86d2-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="a86d2-103">Notifie le profileur qu’un assembly est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="a86d2-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a86d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a86d2-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a86d2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="a86d2-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="a86d2-106">\[in] identifie l’assembly qui est déchargé.</span><span class="sxs-lookup"><span data-stu-id="a86d2-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="a86d2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a86d2-107">Remarks</span></span>  
 <span data-ttu-id="a86d2-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations après le retour de la méthode `AssemblyUnloadStarted`, il s’agit de la dernière chance du profileur d’obtenir des informations sur cet assembly.</span><span class="sxs-lookup"><span data-stu-id="a86d2-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a86d2-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a86d2-109">Requirements</span></span>  
 <span data-ttu-id="a86d2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a86d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a86d2-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a86d2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a86d2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a86d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a86d2-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a86d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86d2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a86d2-114">See also</span></span>

- [<span data-ttu-id="a86d2-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a86d2-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a86d2-116">AssemblyUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="a86d2-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
