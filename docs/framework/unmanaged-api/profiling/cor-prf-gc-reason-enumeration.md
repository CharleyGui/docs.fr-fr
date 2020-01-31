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
ms.openlocfilehash: ec33e55f840fe735091364ebc35cb7b7c165c10a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867181"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="6bb71-102">COR_PRF_GC_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="6bb71-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="6bb71-103">Indique la raison pour laquelle une récupération de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="6bb71-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb71-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="6bb71-105">Members</span><span class="sxs-lookup"><span data-stu-id="6bb71-105">Members</span></span>  
  
|<span data-ttu-id="6bb71-106">Member</span><span class="sxs-lookup"><span data-stu-id="6bb71-106">Member</span></span>|<span data-ttu-id="6bb71-107">Description</span><span class="sxs-lookup"><span data-stu-id="6bb71-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="6bb71-108">La garbage collection a été induite par une méthode <xref:System.GC.Collect%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bb71-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="6bb71-109">La raison n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6bb71-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bb71-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6bb71-110">Requirements</span></span>  
 <span data-ttu-id="6bb71-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb71-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb71-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6bb71-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6bb71-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bb71-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bb71-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb71-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bb71-115">See also</span></span>

- [<span data-ttu-id="6bb71-116">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="6bb71-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
