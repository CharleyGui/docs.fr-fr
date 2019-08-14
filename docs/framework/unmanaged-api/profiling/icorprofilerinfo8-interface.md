---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973819"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="54c05-102">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="54c05-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="54c05-103">Sous-classe de [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) qui fournit des méthodes pour demander des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="54c05-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="54c05-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="54c05-104">Methods</span></span>  

| <span data-ttu-id="54c05-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="54c05-105">Method</span></span>|<span data-ttu-id="54c05-106">Description</span><span class="sxs-lookup"><span data-stu-id="54c05-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="54c05-107">Méthode IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="54c05-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="54c05-108">Détermine si une fonction n’a pas de métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="54c05-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="54c05-109">Méthode GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="54c05-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="54c05-110">Mappe un pointeur d’instruction de code managé à une FunctionID.</span><span class="sxs-lookup"><span data-stu-id="54c05-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="54c05-111">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="54c05-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="54c05-112">Méthode GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="54c05-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="54c05-113">Récupère des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="54c05-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="54c05-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54c05-114">Requirements</span></span>  
<span data-ttu-id="54c05-115">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="54c05-116">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="54c05-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="54c05-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="54c05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="54c05-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54c05-118">See also</span></span>
- [<span data-ttu-id="54c05-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="54c05-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
