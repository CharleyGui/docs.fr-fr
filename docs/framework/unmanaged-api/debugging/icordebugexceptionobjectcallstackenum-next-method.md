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
ms.openlocfilehash: 6fce9f61e222d0fc1763495de162a94a7fc22689
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975977"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="28c57-102">ICorDebugBlockingObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="28c57-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="28c57-103">Obtient le nombre spécifié d’instances [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations à partir de la pile des appels d’un objet exception.</span><span class="sxs-lookup"><span data-stu-id="28c57-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28c57-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28c57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28c57-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="28c57-106">dans Nombre d’instances de [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) à récupérer.</span><span class="sxs-lookup"><span data-stu-id="28c57-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="28c57-107">à Tableau de pointeurs, chacun pointant vers un objet [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="28c57-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="28c57-108">à Pointeur vers le nombre d’instances [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="28c57-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28c57-109">Notes</span><span class="sxs-lookup"><span data-stu-id="28c57-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c57-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="28c57-110">Requirements</span></span>  
 <span data-ttu-id="28c57-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28c57-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28c57-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28c57-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28c57-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28c57-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28c57-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28c57-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c57-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28c57-115">See also</span></span>

- [<span data-ttu-id="28c57-116">ICorDebugExceptionObjectCallStackEnum, interface</span><span class="sxs-lookup"><span data-stu-id="28c57-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="28c57-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="28c57-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
