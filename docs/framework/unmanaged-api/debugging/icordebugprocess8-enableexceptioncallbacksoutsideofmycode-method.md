---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a58f75ca7abd1bd1f871bcf4637bfd7eb7bdcd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300540"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="d130e-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)</span><span class="sxs-lookup"><span data-stu-id="d130e-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="d130e-103">[Pris en charge dans le .NET Framework 4.6 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="d130e-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="d130e-104">Active ou désactive certains types de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) rappels d’exception.</span><span class="sxs-lookup"><span data-stu-id="d130e-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d130e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d130e-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d130e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d130e-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="d130e-107">[in]</span><span class="sxs-lookup"><span data-stu-id="d130e-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d130e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d130e-108">Remarks</span></span>  
 <span data-ttu-id="d130e-109">Si la valeur de `enableExceptionsOutsideOfJMC` est `false` :</span><span class="sxs-lookup"><span data-stu-id="d130e-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="d130e-110">Une exception DEBUG_EXCEPTION_FIRST_CHANCE pas entraîne un rappel au débogueur.</span><span class="sxs-lookup"><span data-stu-id="d130e-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="d130e-111">Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND pas entraîne un rappel au débogueur si l’exception s’échappe jamais dans le code utilisateur (autrement dit, le chemin d’origine vers un gestionnaire d’exceptions n’a aucune méthode marquée JustMyCode ou JMC).</span><span class="sxs-lookup"><span data-stu-id="d130e-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="d130e-112">La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.</span><span class="sxs-lookup"><span data-stu-id="d130e-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d130e-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d130e-113">Requirements</span></span>  
 <span data-ttu-id="d130e-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d130e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d130e-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d130e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d130e-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d130e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d130e-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d130e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d130e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d130e-118">See also</span></span>

- [<span data-ttu-id="d130e-119">ICorDebugProcess8, interface</span><span class="sxs-lookup"><span data-stu-id="d130e-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="d130e-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d130e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
