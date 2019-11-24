---
title: COR_PRF_FUNCTION, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 40698a49ac7012c4f67eb88b1ead04c80f3dea77
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428325"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="992a6-102">COR_PRF_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="992a6-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="992a6-103">Fournit une représentation unique d'une fonction en combinant son ID avec l'ID de sa version recompilée.</span><span class="sxs-lookup"><span data-stu-id="992a6-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="992a6-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="992a6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="992a6-105">Members</span></span>  
  
|<span data-ttu-id="992a6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="992a6-106">Member</span></span>|<span data-ttu-id="992a6-107">Description</span><span class="sxs-lookup"><span data-stu-id="992a6-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="992a6-108">The ID of the function.</span><span class="sxs-lookup"><span data-stu-id="992a6-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="992a6-109">The ID of the recompiled function.</span><span class="sxs-lookup"><span data-stu-id="992a6-109">The ID of the recompiled function.</span></span> <span data-ttu-id="992a6-110">A value of 0 (zero) represents the original version of the function.</span><span class="sxs-lookup"><span data-stu-id="992a6-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="992a6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="992a6-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="992a6-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="992a6-112">Requirements</span></span>  
 <span data-ttu-id="992a6-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="992a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="992a6-114">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="992a6-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="992a6-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="992a6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="992a6-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="992a6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992a6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="992a6-117">See also</span></span>

- [<span data-ttu-id="992a6-118">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="992a6-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
