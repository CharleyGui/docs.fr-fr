---
title: COR_PRF_GC_REASON, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: f10ec279e67b86448298745a488f5b3e833e8c39
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447373"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="1bc31-102">COR_PRF_GC_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="1bc31-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="1bc31-103">Indique la raison pour laquelle une récupération de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="1bc31-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bc31-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="1bc31-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1bc31-105">Members</span></span>  
  
|<span data-ttu-id="1bc31-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1bc31-106">Member</span></span>|<span data-ttu-id="1bc31-107">Description</span><span class="sxs-lookup"><span data-stu-id="1bc31-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="1bc31-108">La garbage collection a été induite par une méthode <xref:System.GC.Collect%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bc31-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="1bc31-109">La raison n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1bc31-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1bc31-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bc31-110">Requirements</span></span>  
 <span data-ttu-id="1bc31-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bc31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bc31-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bc31-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bc31-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bc31-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bc31-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bc31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc31-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bc31-115">See also</span></span>

- [<span data-ttu-id="1bc31-116">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="1bc31-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
