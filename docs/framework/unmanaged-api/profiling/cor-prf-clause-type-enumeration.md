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
ms.openlocfilehash: c3058229a3c2b3c529136dad70fea35a23708a33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718655"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="c989d-102">COR_PRF_CLAUSE_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="c989d-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>

<span data-ttu-id="c989d-103">Indique le type de clause d'exception où le code vient d'entrer ou qu'il vient de quitter.</span><span class="sxs-lookup"><span data-stu-id="c989d-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c989d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c989d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="c989d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c989d-105">Members</span></span>  
  
|<span data-ttu-id="c989d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c989d-106">Member</span></span>|<span data-ttu-id="c989d-107">Description</span><span class="sxs-lookup"><span data-stu-id="c989d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="c989d-108">La clause d’exception n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c989d-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="c989d-109">La clause d’exception est une expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="c989d-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="c989d-110">La clause d’exception est une `catch` instruction.</span><span class="sxs-lookup"><span data-stu-id="c989d-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="c989d-111">La clause d’exception est une `finally` instruction.</span><span class="sxs-lookup"><span data-stu-id="c989d-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c989d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c989d-112">Requirements</span></span>  

 <span data-ttu-id="c989d-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c989d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c989d-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c989d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c989d-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c989d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c989d-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c989d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c989d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c989d-117">See also</span></span>

- [<span data-ttu-id="c989d-118">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="c989d-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
