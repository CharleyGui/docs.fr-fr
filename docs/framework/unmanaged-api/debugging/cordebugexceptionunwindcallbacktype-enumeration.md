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
ms.openlocfilehash: e714c41812c8aaccd713115712df05744cc015e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789387"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="93d2f-102">CorDebugExceptionUnwindCallbackType, énumération</span><span class="sxs-lookup"><span data-stu-id="93d2f-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="93d2f-103">Indique l'événement qui est signalé par le rappel lors de la phase de déroulement.</span><span class="sxs-lookup"><span data-stu-id="93d2f-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93d2f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="93d2f-105">Members</span><span class="sxs-lookup"><span data-stu-id="93d2f-105">Members</span></span>  
  
|<span data-ttu-id="93d2f-106">Member</span><span class="sxs-lookup"><span data-stu-id="93d2f-106">Member</span></span>|<span data-ttu-id="93d2f-107">Description</span><span class="sxs-lookup"><span data-stu-id="93d2f-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="93d2f-108">Début du processus de déroulement.</span><span class="sxs-lookup"><span data-stu-id="93d2f-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="93d2f-109">L’exception a été interceptée.</span><span class="sxs-lookup"><span data-stu-id="93d2f-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93d2f-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="93d2f-110">Requirements</span></span>  
 <span data-ttu-id="93d2f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93d2f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d2f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93d2f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93d2f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93d2f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93d2f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d2f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d2f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93d2f-115">See also</span></span>

- [<span data-ttu-id="93d2f-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="93d2f-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
