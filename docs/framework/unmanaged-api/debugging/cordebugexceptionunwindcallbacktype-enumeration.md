---
title: CorDebugExceptionUnwindCallbackType, énumération
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 4d2be9960f8935b754791a8badd4ea98b5d54912
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795909"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="70420-102">CorDebugExceptionUnwindCallbackType, énumération</span><span class="sxs-lookup"><span data-stu-id="70420-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="70420-103">Indique l'événement qui est signalé par le rappel lors de la phase de déroulement.</span><span class="sxs-lookup"><span data-stu-id="70420-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70420-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70420-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="70420-105">Membres</span><span class="sxs-lookup"><span data-stu-id="70420-105">Members</span></span>  
  
|<span data-ttu-id="70420-106">Membre</span><span class="sxs-lookup"><span data-stu-id="70420-106">Member</span></span>|<span data-ttu-id="70420-107">Description</span><span class="sxs-lookup"><span data-stu-id="70420-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="70420-108">Début du processus de déroulement.</span><span class="sxs-lookup"><span data-stu-id="70420-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="70420-109">L’exception a été interceptée.</span><span class="sxs-lookup"><span data-stu-id="70420-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70420-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="70420-110">Requirements</span></span>  
 <span data-ttu-id="70420-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70420-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70420-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70420-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70420-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70420-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70420-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70420-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70420-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70420-115">See also</span></span>

- [<span data-ttu-id="70420-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="70420-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
