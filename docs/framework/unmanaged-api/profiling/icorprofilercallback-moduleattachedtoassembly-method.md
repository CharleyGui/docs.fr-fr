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
ms.openlocfilehash: bcf5c5c9044a30fc8259dbc54bad8f3141f0f926
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733111"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="bf7f5-102">ICorProfilerCallback::ModuleAttachedToAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="bf7f5-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>

<span data-ttu-id="bf7f5-103">Notifie le profileur qu’un module est attaché à son assembly parent.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf7f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf7f5-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf7f5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf7f5-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="bf7f5-106">dans ID du module qui est attaché.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="bf7f5-107">dans ID de l’assembly parent auquel le module est attaché.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf7f5-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="bf7f5-108">Remarks</span></span>  

 <span data-ttu-id="bf7f5-109">Un module peut être chargé par le biais d’une table d’adresses d’importation (IAT), d’un appel à `LoadLibrary` ou par le biais d’une référence de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="bf7f5-110">Par conséquent, le chargeur common language runtime (CLR) a plusieurs chemins de code pour déterminer l’assembly dans lequel un module vit.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="bf7f5-111">Par conséquent, il est possible qu’après l’appel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , le module ne connaisse pas l’assembly dans lequel il se trouve et l’obtention de l’ID d’assembly parent n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="bf7f5-112">La `ModuleAttachedToAssembly` méthode est appelée quand le module est attaché à son assembly parent et que son ID d’assembly parent peut être obtenu.</span><span class="sxs-lookup"><span data-stu-id="bf7f5-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf7f5-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bf7f5-113">Requirements</span></span>  

 <span data-ttu-id="bf7f5-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf7f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf7f5-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf7f5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf7f5-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf7f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf7f5-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf7f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf7f5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf7f5-118">See also</span></span>

- [<span data-ttu-id="bf7f5-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="bf7f5-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
