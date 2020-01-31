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
ms.openlocfilehash: daca2849908a7798b588ff06f6e117d412db1b33
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867267"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="65e95-102">COR_PRF_FINALIZER_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="65e95-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="65e95-103">Décrit le finaliseur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="65e95-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65e95-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="65e95-105">Members</span><span class="sxs-lookup"><span data-stu-id="65e95-105">Members</span></span>  
  
|<span data-ttu-id="65e95-106">Member</span><span class="sxs-lookup"><span data-stu-id="65e95-106">Member</span></span>|<span data-ttu-id="65e95-107">Description</span><span class="sxs-lookup"><span data-stu-id="65e95-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="65e95-108">Le finaliseur est critique.</span><span class="sxs-lookup"><span data-stu-id="65e95-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65e95-109">Notes</span><span class="sxs-lookup"><span data-stu-id="65e95-109">Remarks</span></span>  
 <span data-ttu-id="65e95-110">L’énumération `COR_PRF_FINALIZER_FLAGS` est utilisée par la méthode [ICorProfilerCallback2 :: FinalizeableObjectQueued,](icorprofilercallback2-finalizeableobjectqueued-method.md) pour décrire le finaliseur d’un objet.</span><span class="sxs-lookup"><span data-stu-id="65e95-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e95-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="65e95-111">Requirements</span></span>  
 <span data-ttu-id="65e95-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e95-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e95-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65e95-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65e95-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65e95-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65e95-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e95-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e95-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65e95-116">See also</span></span>

- [<span data-ttu-id="65e95-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="65e95-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
