---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2cca915eda44d73aea7469e5f752c57309c2300d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495162"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="a3359-102">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="a3359-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="a3359-103">Sous-classe de [ICorProfilerInfo7](icorprofilerinfo7-interface.md) qui fournit des méthodes pour demander des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="a3359-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="a3359-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a3359-104">Methods</span></span>  

| <span data-ttu-id="a3359-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a3359-105">Method</span></span>|<span data-ttu-id="a3359-106">Description</span><span class="sxs-lookup"><span data-stu-id="a3359-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a3359-107">Méthode IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="a3359-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="a3359-108">Détermine si une fonction n’a pas de métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="a3359-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="a3359-109">Méthode GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="a3359-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="a3359-110">Mappe un pointeur d’instruction de code managé à une FunctionID.</span><span class="sxs-lookup"><span data-stu-id="a3359-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="a3359-111">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="a3359-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="a3359-112">Méthode GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="a3359-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="a3359-113">Récupère des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="a3359-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a3359-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a3359-114">Requirements</span></span>  
<span data-ttu-id="a3359-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3359-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a3359-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3359-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a3359-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3359-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a3359-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3359-118">See also</span></span>

- [<span data-ttu-id="a3359-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a3359-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
