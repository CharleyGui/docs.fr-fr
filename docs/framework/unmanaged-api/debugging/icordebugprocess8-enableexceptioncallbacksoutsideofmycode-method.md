---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123374"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="74d34-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode (méthode)</span><span class="sxs-lookup"><span data-stu-id="74d34-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="74d34-103">[Pris en charge dans le .NET Framework 4,6 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="74d34-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="74d34-104">Active ou désactive certains types de rappels d’exception [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="74d34-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d34-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74d34-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74d34-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74d34-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="74d34-107">[in]</span><span class="sxs-lookup"><span data-stu-id="74d34-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74d34-108">Notes</span><span class="sxs-lookup"><span data-stu-id="74d34-108">Remarks</span></span>  
 <span data-ttu-id="74d34-109">Si la valeur de `enableExceptionsOutsideOfJMC` est `false` :</span><span class="sxs-lookup"><span data-stu-id="74d34-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="74d34-110">Une exception DEBUG_EXCEPTION_FIRST_CHANCE n’entraîne pas de rappel au débogueur.</span><span class="sxs-lookup"><span data-stu-id="74d34-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="74d34-111">Une exception DEBUG_EXCEPTION_CATCH_HANDLER_FOUND n’entraîne pas de rappel au débogueur si l’exception n’échappe jamais dans le code utilisateur (autrement dit, le chemin d’accès d’une exception d’origine à un gestionnaire d’exceptions n’a aucune méthode marquée comme JustMyCode ou uniquement mon code).</span><span class="sxs-lookup"><span data-stu-id="74d34-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="74d34-112">La valeur par défaut de `enableExceptionsOutsideOfJMC` est `true`.</span><span class="sxs-lookup"><span data-stu-id="74d34-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74d34-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="74d34-113">Requirements</span></span>  
 <span data-ttu-id="74d34-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74d34-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74d34-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74d34-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74d34-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74d34-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74d34-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74d34-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d34-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74d34-118">See also</span></span>

- [<span data-ttu-id="74d34-119">ICorDebugProcess8, interface</span><span class="sxs-lookup"><span data-stu-id="74d34-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="74d34-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="74d34-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
