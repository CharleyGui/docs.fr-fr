---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: eedd16006781de517587e5138543b9b9eca3ff90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733605"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="061e4-102">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="061e4-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="061e4-103">Sous-classe de [ICorProfilerInfo7](icorprofilerinfo7-interface.md) qui fournit des méthodes pour demander des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="061e4-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="061e4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="061e4-104">Methods</span></span>  

| <span data-ttu-id="061e4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="061e4-105">Method</span></span>|<span data-ttu-id="061e4-106">Description</span><span class="sxs-lookup"><span data-stu-id="061e4-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="061e4-107">Méthode IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="061e4-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="061e4-108">Détermine si une fonction n’a pas de métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="061e4-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="061e4-109">Méthode GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="061e4-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="061e4-110">Mappe un pointeur d’instruction de code managé à une FunctionID.</span><span class="sxs-lookup"><span data-stu-id="061e4-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="061e4-111">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="061e4-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="061e4-112">Méthode GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="061e4-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="061e4-113">Récupère des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="061e4-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="061e4-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="061e4-114">Requirements</span></span>  

<span data-ttu-id="061e4-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="061e4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="061e4-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="061e4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="061e4-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="061e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="061e4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="061e4-118">See also</span></span>

- [<span data-ttu-id="061e4-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="061e4-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
