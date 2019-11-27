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
ms.openlocfilehash: 5e718d05f033cc46fa460a81f6816a13ec32476d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428347"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="27f8b-102">COR_PRF_FINALIZER_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="27f8b-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="27f8b-103">Décrit le finaliseur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="27f8b-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27f8b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="27f8b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="27f8b-105">Members</span></span>  
  
|<span data-ttu-id="27f8b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="27f8b-106">Member</span></span>|<span data-ttu-id="27f8b-107">Description</span><span class="sxs-lookup"><span data-stu-id="27f8b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="27f8b-108">Le finaliseur est critique.</span><span class="sxs-lookup"><span data-stu-id="27f8b-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27f8b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="27f8b-109">Remarks</span></span>  
 <span data-ttu-id="27f8b-110">L’énumération `COR_PRF_FINALIZER_FLAGS` est utilisée par la méthode [ICorProfilerCallback2 :: FinalizeableObjectQueued,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) pour décrire le finaliseur d’un objet.</span><span class="sxs-lookup"><span data-stu-id="27f8b-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f8b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27f8b-111">Requirements</span></span>  
 <span data-ttu-id="27f8b-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f8b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f8b-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27f8b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27f8b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27f8b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27f8b-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f8b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f8b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27f8b-116">See also</span></span>

- [<span data-ttu-id="27f8b-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="27f8b-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
