---
title: CorDebugDebugEventKind, énumération
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: e348e0070a5ce619f95dad9ebe4085d17f7ade6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733371"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="bb50b-102">CorDebugDebugEventKind, énumération</span><span class="sxs-lookup"><span data-stu-id="bb50b-102">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="bb50b-103">Indique le type d’événement dont les informations sont décodées par la méthode [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bb50b-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb50b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb50b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="bb50b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bb50b-105">Members</span></span>  
  
|<span data-ttu-id="bb50b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bb50b-106">Member</span></span>|<span data-ttu-id="bb50b-107">Description</span><span class="sxs-lookup"><span data-stu-id="bb50b-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="bb50b-108">Événement de chargement de module.</span><span class="sxs-lookup"><span data-stu-id="bb50b-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="bb50b-109">Événement de déchargement de module.</span><span class="sxs-lookup"><span data-stu-id="bb50b-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="bb50b-110">Exception de première chance.</span><span class="sxs-lookup"><span data-stu-id="bb50b-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="bb50b-111">Exception utilisateur de première chance.</span><span class="sxs-lookup"><span data-stu-id="bb50b-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="bb50b-112">Exception pour laquelle il existe un gestionnaire `catch`.</span><span class="sxs-lookup"><span data-stu-id="bb50b-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="bb50b-113">Exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="bb50b-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb50b-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb50b-114">Remarks</span></span>  

 <span data-ttu-id="bb50b-115">Un membre de l' `CorDebugDebugEventKind` énumération est retourné en appelant la méthode [ICorDebugDebugEvent :: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bb50b-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb50b-116">Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.</span><span class="sxs-lookup"><span data-stu-id="bb50b-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb50b-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb50b-117">Requirements</span></span>  

 <span data-ttu-id="bb50b-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb50b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb50b-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb50b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb50b-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb50b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb50b-121">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb50b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb50b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb50b-122">See also</span></span>

- [<span data-ttu-id="bb50b-123">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="bb50b-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
