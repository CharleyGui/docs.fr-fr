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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30500e8ea55f8298b9a980e34dc611b58a51bdcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916398"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="c4906-102">COR_PRF_JIT_CACHE, énumération</span><span class="sxs-lookup"><span data-stu-id="c4906-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="c4906-103">Indique le résultat de la recherche d'une fonction mise en cache.</span><span class="sxs-lookup"><span data-stu-id="c4906-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4906-104">`COR_PRF_CACHED_FUNCTION_FOUND`a une valeur égale à zéro, `COR_PRF_JIT_CACHE` donc ne peut pas être utilisé en tant que substitut booléen.</span><span class="sxs-lookup"><span data-stu-id="c4906-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4906-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4906-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="c4906-106">Membres</span><span class="sxs-lookup"><span data-stu-id="c4906-106">Members</span></span>  
  
|<span data-ttu-id="c4906-107">Membre</span><span class="sxs-lookup"><span data-stu-id="c4906-107">Member</span></span>|<span data-ttu-id="c4906-108">Description</span><span class="sxs-lookup"><span data-stu-id="c4906-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="c4906-109">La recherche a trouvé la fonction.</span><span class="sxs-lookup"><span data-stu-id="c4906-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="c4906-110">La recherche n’a pas trouvé la fonction.</span><span class="sxs-lookup"><span data-stu-id="c4906-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4906-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4906-111">Requirements</span></span>  
 <span data-ttu-id="c4906-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4906-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4906-113">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4906-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4906-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4906-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4906-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4906-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4906-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4906-116">See also</span></span>

- [<span data-ttu-id="c4906-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="c4906-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
