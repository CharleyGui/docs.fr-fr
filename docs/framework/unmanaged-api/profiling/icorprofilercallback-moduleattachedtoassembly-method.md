---
title: ICorProfilerCallback::ModuleAttachedToAssembly, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3345e2e87ba41f750031deed2d15e13dbe4f06c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769287"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="55374-102">ICorProfilerCallback::ModuleAttachedToAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="55374-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="55374-103">Notifie le profileur qu’un module est attaché à son assembly parent.</span><span class="sxs-lookup"><span data-stu-id="55374-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55374-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55374-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55374-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55374-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="55374-106">[in] L’ID du module qui est attaché.</span><span class="sxs-lookup"><span data-stu-id="55374-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="55374-107">[in] L’ID de l’assembly parent auquel le module est attaché.</span><span class="sxs-lookup"><span data-stu-id="55374-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55374-108">Notes</span><span class="sxs-lookup"><span data-stu-id="55374-108">Remarks</span></span>  
 <span data-ttu-id="55374-109">Un module peut être chargé via une table d’adresse d’importation (IAT), via un appel à `LoadLibrary`, ou via une référence de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="55374-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="55374-110">Par conséquent, le chargeur du common language runtime (CLR) a plusieurs chemins de code pour déterminer l’assembly dans lequel réside un module.</span><span class="sxs-lookup"><span data-stu-id="55374-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="55374-111">Par conséquent, il est possible qu’après [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) est appelée, le module ne sait pas quel assembly il se trouve dans et obtenir l’ID d’assembly parent n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="55374-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="55374-112">Le `ModuleAttachedToAssembly` méthode est appelée lorsque le module est attaché à son assembly parent et son parent ID peut être obtenu.</span><span class="sxs-lookup"><span data-stu-id="55374-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55374-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55374-113">Requirements</span></span>  
 <span data-ttu-id="55374-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55374-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55374-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55374-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55374-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55374-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55374-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55374-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55374-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55374-118">See also</span></span>

- [<span data-ttu-id="55374-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="55374-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
