---
title: Interface ICorProfilerCallback7
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: 9a49d8e1ff31942c6564ab560d6726b9ede26466
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499140"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="faad3-102">Interface ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="faad3-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="faad3-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="faad3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="faad3-104">Sous-classe de [ICorProfilerCallback6](icorprofilercallback6-interface.md) qui fournit une méthode de rappel que le Common Language Runtime utilise pour informer le profileur de la mise à jour du flux de symbole associé à un module en mémoire.</span><span class="sxs-lookup"><span data-stu-id="faad3-104">A subclass of [ICorProfilerCallback6](icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="faad3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="faad3-105">Methods</span></span>  
  
|<span data-ttu-id="faad3-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="faad3-106">Method</span></span>|<span data-ttu-id="faad3-107">Description</span><span class="sxs-lookup"><span data-stu-id="faad3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="faad3-108">ModuleInMemorySymbolsUpdated, méthode</span><span class="sxs-lookup"><span data-stu-id="faad3-108">ModuleInMemorySymbolsUpdated Method</span></span>](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="faad3-109">Notifie le profileur de la mise à jour du flux de symbole associé à un module en mémoire.</span><span class="sxs-lookup"><span data-stu-id="faad3-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="faad3-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="faad3-110">Requirements</span></span>  
 <span data-ttu-id="faad3-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faad3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faad3-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="faad3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="faad3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faad3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faad3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faad3-114">See also</span></span>

- [<span data-ttu-id="faad3-115">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="faad3-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
