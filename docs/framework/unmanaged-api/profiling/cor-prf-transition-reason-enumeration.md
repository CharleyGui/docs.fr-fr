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
ms.openlocfilehash: 6d8b408675127cde399a8346f2b9734a0e038cb5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427141"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="d70ad-102">COR_PRF_TRANSITION_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="d70ad-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="d70ad-103">Indique la raison d'une transition de code managé en code non managé, ou l'inverse.</span><span class="sxs-lookup"><span data-stu-id="d70ad-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d70ad-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="d70ad-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d70ad-105">Members</span></span>  
  
|<span data-ttu-id="d70ad-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d70ad-106">Member</span></span>|<span data-ttu-id="d70ad-107">Description</span><span class="sxs-lookup"><span data-stu-id="d70ad-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="d70ad-108">La transition est due à un appel dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="d70ad-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="d70ad-109">La transition est due à un retour d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="d70ad-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d70ad-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d70ad-110">Remarks</span></span>  
 <span data-ttu-id="d70ad-111">Quand une transition se produit, le profileur reçoit un rappel [ICorProfilerCallback :: ManagedToUnmanagedTransition,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback :: UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) , qui fournit une valeur de l’énumération `COR_PRF_TRANSITION_REASON` pour indiquer la raison de la transition.</span><span class="sxs-lookup"><span data-stu-id="d70ad-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70ad-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d70ad-112">Requirements</span></span>  
 <span data-ttu-id="d70ad-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d70ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70ad-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d70ad-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d70ad-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d70ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d70ad-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
