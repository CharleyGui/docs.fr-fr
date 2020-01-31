---
title: COR_PRF_TRANSITION_REASON, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867044"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="a52fd-102">COR_PRF_TRANSITION_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="a52fd-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="a52fd-103">Indique la raison d'une transition de code managé en code non managé, ou l'inverse.</span><span class="sxs-lookup"><span data-stu-id="a52fd-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a52fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a52fd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="a52fd-105">Members</span><span class="sxs-lookup"><span data-stu-id="a52fd-105">Members</span></span>  
  
|<span data-ttu-id="a52fd-106">Member</span><span class="sxs-lookup"><span data-stu-id="a52fd-106">Member</span></span>|<span data-ttu-id="a52fd-107">Description</span><span class="sxs-lookup"><span data-stu-id="a52fd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="a52fd-108">La transition est due à un appel dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="a52fd-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="a52fd-109">La transition est due à un retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="a52fd-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a52fd-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a52fd-110">Remarks</span></span>  
 <span data-ttu-id="a52fd-111">Quand une transition se produit, le profileur reçoit un rappel [ICorProfilerCallback :: ManagedToUnmanagedTransition,](icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback :: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) , qui fournit une valeur de l’énumération `COR_PRF_TRANSITION_REASON` pour indiquer la raison de la transition.</span><span class="sxs-lookup"><span data-stu-id="a52fd-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a52fd-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a52fd-112">Requirements</span></span>  
 <span data-ttu-id="a52fd-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a52fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a52fd-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a52fd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a52fd-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a52fd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a52fd-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a52fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
