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
ms.openlocfilehash: d5cdb8c6740970f6a7469be8c763961bf76d6ecc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795936"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="35028-102">CorDebugExceptionCallbackType, énumération</span><span class="sxs-lookup"><span data-stu-id="35028-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="35028-103">Indique le type de rappel effectué à partir d’un événement [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="35028-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35028-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35028-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="35028-105">Membres</span><span class="sxs-lookup"><span data-stu-id="35028-105">Members</span></span>  
  
|<span data-ttu-id="35028-106">Membre</span><span class="sxs-lookup"><span data-stu-id="35028-106">Member</span></span>|<span data-ttu-id="35028-107">Description</span><span class="sxs-lookup"><span data-stu-id="35028-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="35028-108">Une exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="35028-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="35028-109">L’exception Windup processus a entré le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="35028-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="35028-110">Le processus Windup de l’exception `catch` a trouvé un bloc dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="35028-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="35028-111">L’exception n’a pas été gérée.</span><span class="sxs-lookup"><span data-stu-id="35028-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35028-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35028-112">Requirements</span></span>  
 <span data-ttu-id="35028-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35028-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35028-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35028-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35028-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35028-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35028-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35028-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35028-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35028-117">See also</span></span>

- [<span data-ttu-id="35028-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="35028-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
