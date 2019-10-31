---
title: ICorDebugBlockingObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 6c742f541b358b40e6e2fd44ca437b0dd72e29b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091085"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="f2289-102">ICorDebugBlockingObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f2289-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="f2289-103">Obtient le nombre spécifié d’instances [cordebugexceptionobjectstackframe,](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations à partir de la pile des appels d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="f2289-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2289-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2289-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2289-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2289-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f2289-106">dans Nombre d’instances de [cordebugexceptionobjectstackframe,](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) à récupérer.</span><span class="sxs-lookup"><span data-stu-id="f2289-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f2289-107">à Tableau de pointeurs, chacun pointant vers un objet [cordebugexceptionobjectstackframe,](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f2289-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f2289-108">à Pointeur vers le nombre d’instances [cordebugexceptionobjectstackframe,](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="f2289-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2289-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f2289-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2289-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="f2289-110">Requirements</span></span>  
 <span data-ttu-id="f2289-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2289-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2289-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2289-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2289-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2289-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2289-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2289-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2289-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2289-115">See also</span></span>

- [<span data-ttu-id="f2289-116">ICorDebugExceptionObjectCallStackEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f2289-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="f2289-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f2289-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
