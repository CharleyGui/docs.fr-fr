---
title: COR_PRF_FINALIZER_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: 2b766715d6d87ab17a7cdabf721bbebf67e1ff13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718577"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="e550f-102">COR_PRF_FINALIZER_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="e550f-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>

<span data-ttu-id="e550f-103">Décrit le finaliseur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="e550f-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e550f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e550f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e550f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e550f-105">Members</span></span>  
  
|<span data-ttu-id="e550f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e550f-106">Member</span></span>|<span data-ttu-id="e550f-107">Description</span><span class="sxs-lookup"><span data-stu-id="e550f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="e550f-108">Le finaliseur est critique.</span><span class="sxs-lookup"><span data-stu-id="e550f-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e550f-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="e550f-109">Remarks</span></span>  

 <span data-ttu-id="e550f-110">L' `COR_PRF_FINALIZER_FLAGS` énumération est utilisée par la méthode [ICorProfilerCallback2 :: FinalizeableObjectQueued,](icorprofilercallback2-finalizeableobjectqueued-method.md) pour décrire le finaliseur d’un objet.</span><span class="sxs-lookup"><span data-stu-id="e550f-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e550f-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e550f-111">Requirements</span></span>  

 <span data-ttu-id="e550f-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e550f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e550f-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e550f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e550f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e550f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e550f-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e550f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e550f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e550f-116">See also</span></span>

- [<span data-ttu-id="e550f-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="e550f-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
