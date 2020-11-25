---
title: CorDebugChainReason, énumération
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
ms.openlocfilehash: 6185c5dda69a0cf7e9847ddc021448612a426b19
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716055"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="7110f-102">CorDebugChainReason, énumération</span><span class="sxs-lookup"><span data-stu-id="7110f-102">CorDebugChainReason Enumeration</span></span>

<span data-ttu-id="7110f-103">Indique la ou les raisons de la mise en route d'une chaîne d'appels.</span><span class="sxs-lookup"><span data-stu-id="7110f-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7110f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7110f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="7110f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7110f-105">Members</span></span>  
  
|<span data-ttu-id="7110f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7110f-106">Member</span></span>|<span data-ttu-id="7110f-107">Description</span><span class="sxs-lookup"><span data-stu-id="7110f-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="7110f-108">Aucune chaîne d'appel n'a été démarrée.</span><span class="sxs-lookup"><span data-stu-id="7110f-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="7110f-109">La chaîne a été démarrée par un constructeur.</span><span class="sxs-lookup"><span data-stu-id="7110f-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="7110f-110">La chaîne a été démarrée par un filtre d'exception.</span><span class="sxs-lookup"><span data-stu-id="7110f-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="7110f-111">La chaîne a été démarrée par du code qui applique la sécurité.</span><span class="sxs-lookup"><span data-stu-id="7110f-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="7110f-112">La chaîne a été démarrée par une stratégie de contexte.</span><span class="sxs-lookup"><span data-stu-id="7110f-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="7110f-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="7110f-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="7110f-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="7110f-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="7110f-115">La chaîne a été démarrée par le démarrage d'une exécution de thread.</span><span class="sxs-lookup"><span data-stu-id="7110f-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="7110f-116">La chaîne a été démarrée par une entrée dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="7110f-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="7110f-117">La chaîne a été démarrée par une entrée dans le code non managé.</span><span class="sxs-lookup"><span data-stu-id="7110f-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="7110f-118">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="7110f-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="7110f-119">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="7110f-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="7110f-120">La chaîne a été démarrée par une évaluation de fonction.</span><span class="sxs-lookup"><span data-stu-id="7110f-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7110f-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="7110f-121">Remarks</span></span>  

 <span data-ttu-id="7110f-122">Utilisez la méthode [ICorDebugChain :: GetReason](icordebugchain-getreason-method.md) pour déterminer les raisons de l’initiation d’une chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="7110f-122">Use the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7110f-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7110f-123">Requirements</span></span>  

 <span data-ttu-id="7110f-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7110f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7110f-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7110f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7110f-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7110f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7110f-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7110f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7110f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7110f-128">See also</span></span>

- [<span data-ttu-id="7110f-129">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="7110f-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
