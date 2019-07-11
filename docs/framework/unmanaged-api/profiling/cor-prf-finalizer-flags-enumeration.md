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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a66b2b94765c3d59327e500f1e208dc93cd8e231
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781936"
---
# <a name="corprffinalizerflags-enumeration"></a><span data-ttu-id="687d3-102">COR_PRF_FINALIZER_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="687d3-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="687d3-103">Décrit le finaliseur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="687d3-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="687d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="687d3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="687d3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="687d3-105">Members</span></span>  
  
|<span data-ttu-id="687d3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="687d3-106">Member</span></span>|<span data-ttu-id="687d3-107">Description</span><span class="sxs-lookup"><span data-stu-id="687d3-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="687d3-108">Le finaliseur est critique.</span><span class="sxs-lookup"><span data-stu-id="687d3-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="687d3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="687d3-109">Remarks</span></span>  
 <span data-ttu-id="687d3-110">Le `COR_PRF_FINALIZER_FLAGS` énumération est utilisée par le [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) méthode pour décrire le finaliseur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="687d3-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="687d3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="687d3-111">Requirements</span></span>  
 <span data-ttu-id="687d3-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="687d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="687d3-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="687d3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="687d3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="687d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="687d3-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="687d3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="687d3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="687d3-116">See also</span></span>

- [<span data-ttu-id="687d3-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="687d3-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
