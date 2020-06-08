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
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503391"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="37482-102">ICorProfilerCallback::ModuleAttachedToAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="37482-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="37482-103">Notifie le profileur qu’un module est attaché à son assembly parent.</span><span class="sxs-lookup"><span data-stu-id="37482-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37482-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37482-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37482-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="37482-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="37482-106">dans ID du module qui est attaché.</span><span class="sxs-lookup"><span data-stu-id="37482-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="37482-107">dans ID de l’assembly parent auquel le module est attaché.</span><span class="sxs-lookup"><span data-stu-id="37482-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37482-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="37482-108">Remarks</span></span>  
 <span data-ttu-id="37482-109">Un module peut être chargé par le biais d’une table d’adresses d’importation (IAT), d’un appel à `LoadLibrary` ou par le biais d’une référence de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="37482-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="37482-110">Par conséquent, le chargeur common language runtime (CLR) a plusieurs chemins de code pour déterminer l’assembly dans lequel un module vit.</span><span class="sxs-lookup"><span data-stu-id="37482-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="37482-111">Par conséquent, il est possible qu’après l’appel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , le module ne connaisse pas l’assembly dans lequel il se trouve et l’obtention de l’ID d’assembly parent n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="37482-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="37482-112">La `ModuleAttachedToAssembly` méthode est appelée quand le module est attaché à son assembly parent et que son ID d’assembly parent peut être obtenu.</span><span class="sxs-lookup"><span data-stu-id="37482-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37482-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="37482-113">Requirements</span></span>  
 <span data-ttu-id="37482-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37482-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37482-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37482-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="37482-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37482-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37482-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37482-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37482-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37482-118">See also</span></span>

- [<span data-ttu-id="37482-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="37482-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
