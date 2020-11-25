---
title: ICorProfilerCallback6, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 2176b624a427994b9d2af4b5eba31a64c9288a0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725467"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="53201-102">ICorProfilerCallback6, interface</span><span class="sxs-lookup"><span data-stu-id="53201-102">ICorProfilerCallback6 Interface</span></span>

<span data-ttu-id="53201-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="53201-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="53201-104">Sous-classe de [ICorProfilerCallback5](icorprofilercallback5-interface.md) qui fournit une méthode de rappel que le Common Language Runtime utilise pour notifier à un profileur qu’un assembly est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="53201-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53201-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="53201-105">Methods</span></span>  
  
|<span data-ttu-id="53201-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="53201-106">Method</span></span>|<span data-ttu-id="53201-107">Description</span><span class="sxs-lookup"><span data-stu-id="53201-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53201-108">GetAssemblyReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="53201-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="53201-109">Notifie le profileur qu'un assembly en est au tout début du chargement, quand le CLR (Common Langage Runtime) effectue un parcours de fermeture de références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="53201-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53201-110">Notes</span><span class="sxs-lookup"><span data-stu-id="53201-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53201-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="53201-111">Requirements</span></span>  

 <span data-ttu-id="53201-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53201-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53201-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53201-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53201-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53201-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53201-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53201-115">See also</span></span>

- [<span data-ttu-id="53201-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="53201-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
