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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b712ee0bb8e67f448b7ea2bee3c092367181abad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740208"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="a825f-102">CorDebugExceptionCallbackType, énumération</span><span class="sxs-lookup"><span data-stu-id="a825f-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="a825f-103">Indique le type de rappel effectué à partir d’un [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) événement.</span><span class="sxs-lookup"><span data-stu-id="a825f-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a825f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a825f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="a825f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a825f-105">Members</span></span>  
  
|<span data-ttu-id="a825f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a825f-106">Member</span></span>|<span data-ttu-id="a825f-107">Description</span><span class="sxs-lookup"><span data-stu-id="a825f-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="a825f-108">Une exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="a825f-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="a825f-109">Le processus de clôture d’exception entré le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a825f-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="a825f-110">Le processus de clôture d’exception trouvé un `catch` bloquer dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a825f-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="a825f-111">L’exception n’a pas été gérée.</span><span class="sxs-lookup"><span data-stu-id="a825f-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a825f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a825f-112">Requirements</span></span>  
 <span data-ttu-id="a825f-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a825f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a825f-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a825f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a825f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a825f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a825f-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a825f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a825f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a825f-117">See also</span></span>

- [<span data-ttu-id="a825f-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="a825f-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
