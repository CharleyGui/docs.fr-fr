---
title: ICorProfilerInfo6, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: fba57a88cd3af582b4edf0e5bdbf6ac48020c9f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495504"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="313a6-102">ICorProfilerInfo6, interface</span><span class="sxs-lookup"><span data-stu-id="313a6-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="313a6-103">[Pris en charge dans le .NET Framework 4,6 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="313a6-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="313a6-104">Sous-classe de [ICorProfilerInfo5](icorprofilerinfo5-interface.md) qui fournit un énumérateur pour toutes les méthodes définies dans un module Ngen donné et incluse dans une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="313a6-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="313a6-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="313a6-105">Methods</span></span>  
  
|<span data-ttu-id="313a6-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="313a6-106">Method</span></span>|<span data-ttu-id="313a6-107">Description</span><span class="sxs-lookup"><span data-stu-id="313a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="313a6-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="313a6-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="313a6-109">Retourne un énumérateur pour toutes les méthodes qui appartiennent à un module NGen donné et qui sont inline dans le corps d’une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="313a6-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="313a6-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="313a6-110">Requirements</span></span>  
 <span data-ttu-id="313a6-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="313a6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="313a6-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="313a6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="313a6-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="313a6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="313a6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="313a6-114">See also</span></span>

- [<span data-ttu-id="313a6-115">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="313a6-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
