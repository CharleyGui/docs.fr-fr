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
ms.openlocfilehash: bb7dade1ccd46cb9e13d45468c2ca2a8b451b70b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700299"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="989ba-102">ICorProfilerCallback::AssemblyUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="989ba-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>

<span data-ttu-id="989ba-103">Notifie le profileur qu’un assembly est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="989ba-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="989ba-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="989ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="989ba-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="989ba-106">\[in] identifie l’assembly qui est déchargé.</span><span class="sxs-lookup"><span data-stu-id="989ba-106">\[in] Identifies the assembly that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="989ba-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="989ba-107">Remarks</span></span>  

 <span data-ttu-id="989ba-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations après le retour de la `AssemblyUnloadStarted` méthode, c’est la dernière chance du profileur pour obtenir des informations sur cet assembly.</span><span class="sxs-lookup"><span data-stu-id="989ba-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="989ba-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="989ba-109">Requirements</span></span>  

 <span data-ttu-id="989ba-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="989ba-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="989ba-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="989ba-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="989ba-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="989ba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="989ba-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="989ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989ba-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="989ba-114">See also</span></span>

- [<span data-ttu-id="989ba-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="989ba-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="989ba-116">AssemblyUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="989ba-116">AssemblyUnloadFinished Method</span></span>](icorprofilercallback-assemblyunloadfinished-method.md)
