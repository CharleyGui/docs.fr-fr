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
ms.openlocfilehash: 409a21238f172e5ecdaa8d5bfa237a9f3fe46345
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500908"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="73cdc-102">COR_PRF_GC_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="73cdc-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="73cdc-103">Indique la raison pour laquelle une récupération de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="73cdc-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cdc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73cdc-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="73cdc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="73cdc-105">Members</span></span>  
  
|<span data-ttu-id="73cdc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="73cdc-106">Member</span></span>|<span data-ttu-id="73cdc-107">Description</span><span class="sxs-lookup"><span data-stu-id="73cdc-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="73cdc-108">La garbage collection a été induite par une <xref:System.GC.Collect%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="73cdc-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="73cdc-109">La raison n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="73cdc-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73cdc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="73cdc-110">Requirements</span></span>  
 <span data-ttu-id="73cdc-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73cdc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73cdc-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73cdc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73cdc-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73cdc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73cdc-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73cdc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cdc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73cdc-115">See also</span></span>

- [<span data-ttu-id="73cdc-116">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="73cdc-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
