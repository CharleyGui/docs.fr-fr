---
title: COR_PRF_SNAPSHOT_INFO, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867020"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="d8c0f-102">COR_PRF_SNAPSHOT_INFO, énumération</span><span class="sxs-lookup"><span data-stu-id="d8c0f-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="d8c0f-103">Spécifie la quantité de données à renvoyer avec un instantané de pile dans chaque appel à la fonction [StackSnapshotCallback](stacksnapshotcallback-function.md) du profileur.</span><span class="sxs-lookup"><span data-stu-id="d8c0f-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8c0f-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d8c0f-105">Members</span><span class="sxs-lookup"><span data-stu-id="d8c0f-105">Members</span></span>  
  
|<span data-ttu-id="d8c0f-106">Members</span><span class="sxs-lookup"><span data-stu-id="d8c0f-106">Members</span></span>|<span data-ttu-id="d8c0f-107">Description</span><span class="sxs-lookup"><span data-stu-id="d8c0f-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="d8c0f-108">Indique que les valeurs doivent être passées pour tous les paramètres de `StackSnapshotCallback`, à l’exception du paramètre `context`.</span><span class="sxs-lookup"><span data-stu-id="d8c0f-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="d8c0f-109">Indique que les valeurs doivent être passées pour tous les paramètres de `StackSnapshotCallback`, y compris le paramètre `context`.</span><span class="sxs-lookup"><span data-stu-id="d8c0f-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="d8c0f-110">Indique qu’un algorithme de parcours de pile alternatif est plus simple à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d8c0f-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8c0f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d8c0f-111">Remarks</span></span>  
 <span data-ttu-id="d8c0f-112">Les valeurs fournies par l’énumération `COR_PRF_SNAPSHOT_INFO` sont passées en tant que paramètres à la méthode [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d8c0f-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8c0f-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d8c0f-113">Requirements</span></span>  
 <span data-ttu-id="d8c0f-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8c0f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8c0f-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8c0f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8c0f-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8c0f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8c0f-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8c0f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c0f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8c0f-118">See also</span></span>

- [<span data-ttu-id="d8c0f-119">DoStackSnapshot, méthode</span><span class="sxs-lookup"><span data-stu-id="d8c0f-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="d8c0f-120">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="d8c0f-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
