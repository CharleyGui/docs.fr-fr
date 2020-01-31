---
title: COR_PRF_CLAUSE_TYPE, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: edf5d61baae28a82aff0d0bd32d1d900085ac375
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867319"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="68537-102">COR_PRF_CLAUSE_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="68537-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="68537-103">Indique le type de clause d'exception où le code vient d'entrer ou qu'il vient de quitter.</span><span class="sxs-lookup"><span data-stu-id="68537-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68537-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68537-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="68537-105">Members</span><span class="sxs-lookup"><span data-stu-id="68537-105">Members</span></span>  
  
|<span data-ttu-id="68537-106">Member</span><span class="sxs-lookup"><span data-stu-id="68537-106">Member</span></span>|<span data-ttu-id="68537-107">Description</span><span class="sxs-lookup"><span data-stu-id="68537-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="68537-108">La clause d’exception n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="68537-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="68537-109">La clause d’exception est une expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="68537-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="68537-110">La clause d’exception est une instruction `catch`.</span><span class="sxs-lookup"><span data-stu-id="68537-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="68537-111">La clause d’exception est une instruction `finally`.</span><span class="sxs-lookup"><span data-stu-id="68537-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68537-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="68537-112">Requirements</span></span>  
 <span data-ttu-id="68537-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68537-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68537-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68537-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68537-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68537-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68537-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68537-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68537-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68537-117">See also</span></span>

- [<span data-ttu-id="68537-118">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="68537-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
