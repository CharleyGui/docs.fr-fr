---
title: COR_PRF_JIT_CACHE, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
ms.openlocfilehash: 0061e0772c48626a7ba88280e44b74ef32838a41
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867137"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="29dcd-102">COR_PRF_JIT_CACHE, énumération</span><span class="sxs-lookup"><span data-stu-id="29dcd-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="29dcd-103">Indique le résultat de la recherche d'une fonction mise en cache.</span><span class="sxs-lookup"><span data-stu-id="29dcd-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29dcd-104">`COR_PRF_CACHED_FUNCTION_FOUND` a une valeur égale à zéro, donc `COR_PRF_JIT_CACHE` ne peut pas être utilisé en tant que substitut booléen.</span><span class="sxs-lookup"><span data-stu-id="29dcd-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29dcd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29dcd-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="29dcd-106">Members</span><span class="sxs-lookup"><span data-stu-id="29dcd-106">Members</span></span>  
  
|<span data-ttu-id="29dcd-107">Member</span><span class="sxs-lookup"><span data-stu-id="29dcd-107">Member</span></span>|<span data-ttu-id="29dcd-108">Description</span><span class="sxs-lookup"><span data-stu-id="29dcd-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="29dcd-109">La recherche a trouvé la fonction.</span><span class="sxs-lookup"><span data-stu-id="29dcd-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="29dcd-110">La recherche n’a pas trouvé la fonction.</span><span class="sxs-lookup"><span data-stu-id="29dcd-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29dcd-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="29dcd-111">Requirements</span></span>  
 <span data-ttu-id="29dcd-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29dcd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29dcd-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29dcd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29dcd-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29dcd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29dcd-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29dcd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29dcd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29dcd-116">See also</span></span>

- [<span data-ttu-id="29dcd-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="29dcd-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
