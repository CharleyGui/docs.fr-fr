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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfcf2c74a2a44bd0539bf78e237e42553696b16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762986"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="09a4a-102">ICorProfilerCallback::AssemblyUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="09a4a-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="09a4a-103">Notifie le profileur qu’un assembly est déchargé.</span><span class="sxs-lookup"><span data-stu-id="09a4a-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09a4a-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09a4a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09a4a-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="09a4a-106">[in] Identifie l’assembly qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="09a4a-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09a4a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="09a4a-107">Remarks</span></span>  
 <span data-ttu-id="09a4a-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations après la `AssemblyUnloadStarted` retourne de la méthode, il s’agit dernière chance du profileur d’obtenir des informations sur cet assembly.</span><span class="sxs-lookup"><span data-stu-id="09a4a-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a4a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09a4a-109">Requirements</span></span>  
 <span data-ttu-id="09a4a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09a4a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a4a-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09a4a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09a4a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09a4a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09a4a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a4a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a4a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09a4a-114">See also</span></span>

- [<span data-ttu-id="09a4a-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="09a4a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="09a4a-116">AssemblyUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="09a4a-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
