---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: e54dd051f0dbd9c1964d381c2e05189c375fa66d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210135"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="f3368-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)</span><span class="sxs-lookup"><span data-stu-id="f3368-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="f3368-103">[Pris en charge dans le .NET Framework 4,6 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="f3368-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="f3368-104">Active ou désactive certains types de rappels d’exception [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f3368-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3368-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3368-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3368-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f3368-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="f3368-107">[in]</span><span class="sxs-lookup"><span data-stu-id="f3368-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3368-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f3368-108">Remarks</span></span>  
 <span data-ttu-id="f3368-109">Si la valeur de `enableExceptionsOutsideOfJMC` est `false` :</span><span class="sxs-lookup"><span data-stu-id="f3368-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="f3368-110">Une exception DEBUG_EXCEPTION_FIRST_CHANCE n'entraîne pas un rappel au débogueur.</span><span class="sxs-lookup"><span data-stu-id="f3368-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="f3368-111">Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND n'entraîne pas un rappel au débogueur si l'exception ne s'échappe jamais dans le code utilisateur (autrement dit, le chemin de l'origine d'une exception vers un gestionnaire d'exceptions n'a aucune méthode marquée JustMyCode ou JMC).</span><span class="sxs-lookup"><span data-stu-id="f3368-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="f3368-112">La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.</span><span class="sxs-lookup"><span data-stu-id="f3368-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3368-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f3368-113">Requirements</span></span>  
 <span data-ttu-id="f3368-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3368-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3368-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3368-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3368-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3368-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3368-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3368-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3368-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3368-118">See also</span></span>

- [<span data-ttu-id="f3368-119">ICorDebugProcess8 (interface)</span><span class="sxs-lookup"><span data-stu-id="f3368-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="f3368-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f3368-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
