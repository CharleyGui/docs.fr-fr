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
ms.openlocfilehash: 3b4f85072b9dcf87d696b979fa6cbf4e59393f82
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453037"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="22bdc-102">Énumération COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="22bdc-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="22bdc-103">Contient des valeurs qui indiquent comment l’API [ICorProfilerInfo10 :: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) doit se comporter.</span><span class="sxs-lookup"><span data-stu-id="22bdc-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22bdc-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="22bdc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="22bdc-105">Members</span></span>  
  
|<span data-ttu-id="22bdc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="22bdc-106">Member</span></span>|<span data-ttu-id="22bdc-107">Description</span><span class="sxs-lookup"><span data-stu-id="22bdc-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="22bdc-108">Les méthodes ReJITted ne peuvent pas être inline dans d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="22bdc-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="22bdc-109">Recevoir des rappels de `GetFunctionParameters` pour toutes les méthodes qui Inline demandent à être ReJITted.</span><span class="sxs-lookup"><span data-stu-id="22bdc-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="22bdc-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="22bdc-110">Requirements</span></span>  
 <span data-ttu-id="22bdc-111">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="22bdc-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="22bdc-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22bdc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22bdc-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22bdc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22bdc-114">**Versions de .NET Framework :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22bdc-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="22bdc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22bdc-115">See also</span></span>

- [<span data-ttu-id="22bdc-116">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="22bdc-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
