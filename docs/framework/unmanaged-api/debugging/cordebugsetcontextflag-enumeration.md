---
title: CorDebugSetContextFlag, énumération
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: a443332e4f2b0351e99754fae610af39268bb105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789271"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="2318b-102">CorDebugSetContextFlag, énumération</span><span class="sxs-lookup"><span data-stu-id="2318b-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="2318b-103">Indique si le contexte provient du frame (ou feuille) actif ou s'il a été calculé par déroulement à partir d'un autre frame.</span><span class="sxs-lookup"><span data-stu-id="2318b-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2318b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2318b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="2318b-105">Members</span><span class="sxs-lookup"><span data-stu-id="2318b-105">Members</span></span>  
  
|<span data-ttu-id="2318b-106">Member</span><span class="sxs-lookup"><span data-stu-id="2318b-106">Member</span></span>|<span data-ttu-id="2318b-107">Description</span><span class="sxs-lookup"><span data-stu-id="2318b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2318b-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="2318b-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="2318b-109">Le contexte est le contexte actif du thread.</span><span class="sxs-lookup"><span data-stu-id="2318b-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="2318b-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="2318b-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="2318b-111">Le contexte a été calculé en déroulant d’un autre Frame.</span><span class="sxs-lookup"><span data-stu-id="2318b-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2318b-112">Notes</span><span class="sxs-lookup"><span data-stu-id="2318b-112">Remarks</span></span>  
 <span data-ttu-id="2318b-113">`CorDebugSetContextFlag` fournit des valeurs qui sont utilisées par la méthode [ICorDebugStackWalk :: SetContext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2318b-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2318b-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2318b-114">Requirements</span></span>  
 <span data-ttu-id="2318b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2318b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2318b-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2318b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2318b-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2318b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2318b-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2318b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2318b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2318b-119">See also</span></span>

- [<span data-ttu-id="2318b-120">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="2318b-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="2318b-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="2318b-121">Debugging</span></span>](index.md)
