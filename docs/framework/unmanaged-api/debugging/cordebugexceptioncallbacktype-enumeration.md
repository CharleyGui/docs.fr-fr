---
title: CorDebugExceptionCallbackType, énumération
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: c927dcde99f5217ee7c160359385e0b953034380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132239"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="89f07-102">CorDebugExceptionCallbackType, énumération</span><span class="sxs-lookup"><span data-stu-id="89f07-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="89f07-103">Indique le type de rappel effectué à partir d’un événement [ICorDebugManagedCallback2 :: exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89f07-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89f07-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="89f07-105">Membres</span><span class="sxs-lookup"><span data-stu-id="89f07-105">Members</span></span>  
  
|<span data-ttu-id="89f07-106">Membre</span><span class="sxs-lookup"><span data-stu-id="89f07-106">Member</span></span>|<span data-ttu-id="89f07-107">Description</span><span class="sxs-lookup"><span data-stu-id="89f07-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="89f07-108">Une exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="89f07-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="89f07-109">L’exception Windup processus a entré le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89f07-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="89f07-110">Le processus Windup de l’exception a trouvé un bloc `catch` dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89f07-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="89f07-111">L’exception n’a pas été gérée.</span><span class="sxs-lookup"><span data-stu-id="89f07-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89f07-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="89f07-112">Requirements</span></span>  
 <span data-ttu-id="89f07-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f07-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f07-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89f07-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89f07-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89f07-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89f07-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f07-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f07-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89f07-117">See also</span></span>

- [<span data-ttu-id="89f07-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="89f07-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
