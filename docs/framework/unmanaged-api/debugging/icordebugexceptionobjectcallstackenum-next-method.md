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
ms.openlocfilehash: 38de810509f15cf93475eb000837892b99684fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782749"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="e74e5-102">ICorDebugBlockingObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e74e5-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="e74e5-103">Obtient le nombre spécifié d’instances [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations à partir de la pile des appels d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="e74e5-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e74e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e74e5-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e74e5-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e74e5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e74e5-106">dans Nombre d’instances de [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) à récupérer.</span><span class="sxs-lookup"><span data-stu-id="e74e5-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="e74e5-107">à Tableau de pointeurs, chacun pointant vers un objet [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="e74e5-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e74e5-108">à Pointeur vers le nombre d’instances [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="e74e5-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e74e5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e74e5-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e74e5-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e74e5-110">Requirements</span></span>  
 <span data-ttu-id="e74e5-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74e5-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e74e5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e74e5-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e74e5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e74e5-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74e5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e74e5-115">See also</span></span>

- [<span data-ttu-id="e74e5-116">ICorDebugExceptionObjectCallStackEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e74e5-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="e74e5-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e74e5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
