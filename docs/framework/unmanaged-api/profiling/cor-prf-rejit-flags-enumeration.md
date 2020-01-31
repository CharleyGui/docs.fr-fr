---
title: Énumération COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: fabbcd497dc2f321da90188cebbac6ed4e147492
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867085"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="524a7-102">Énumération COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="524a7-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="524a7-103">Contient des valeurs qui indiquent comment l’API [ICorProfilerInfo10 :: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) doit se comporter.</span><span class="sxs-lookup"><span data-stu-id="524a7-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="524a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="524a7-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="524a7-105">Members</span><span class="sxs-lookup"><span data-stu-id="524a7-105">Members</span></span>  
  
|<span data-ttu-id="524a7-106">Member</span><span class="sxs-lookup"><span data-stu-id="524a7-106">Member</span></span>|<span data-ttu-id="524a7-107">Description</span><span class="sxs-lookup"><span data-stu-id="524a7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="524a7-108">Les méthodes ReJITted ne peuvent pas être inline dans d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="524a7-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="524a7-109">Recevoir des rappels de `GetFunctionParameters` pour toutes les méthodes qui Inline demandent à être ReJITted.</span><span class="sxs-lookup"><span data-stu-id="524a7-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="524a7-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="524a7-110">Requirements</span></span>  
 <span data-ttu-id="524a7-111">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="524a7-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
  
 <span data-ttu-id="524a7-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="524a7-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="524a7-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="524a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="524a7-114">**Versions du .NET Framework :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="524a7-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="524a7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="524a7-115">See also</span></span>

- [<span data-ttu-id="524a7-116">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="524a7-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
