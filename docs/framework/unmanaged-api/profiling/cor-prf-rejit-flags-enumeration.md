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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177096"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="b4343-102">Énumération COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b4343-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="b4343-103">Contient des valeurs qui indiquent comment [l’ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API devrait se comporter.</span><span class="sxs-lookup"><span data-stu-id="b4343-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4343-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b4343-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b4343-105">Members</span></span>  
  
|<span data-ttu-id="b4343-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b4343-106">Member</span></span>|<span data-ttu-id="b4343-107">Description</span><span class="sxs-lookup"><span data-stu-id="b4343-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="b4343-108">Les méthodes ReJITted seront empêchées d’être inlinées dans d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="b4343-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="b4343-109">Recevez `GetFunctionParameters` des rappels pour toutes les méthodes qui en ligne les méthodes demandées pour être ReJITted.</span><span class="sxs-lookup"><span data-stu-id="b4343-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="b4343-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b4343-110">Requirements</span></span>  
 <span data-ttu-id="b4343-111">**Plates-formes:** Voir [.NET Core systèmes d’exploitation pris en charge](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b4343-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="b4343-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4343-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4343-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4343-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4343-114">**.NET Versions-cadre:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4343-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b4343-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4343-115">See also</span></span>

- [<span data-ttu-id="b4343-116">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="b4343-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
