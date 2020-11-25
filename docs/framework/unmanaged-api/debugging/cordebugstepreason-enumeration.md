---
title: CorDebugStepReason, énumération
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 50903b3737c0fc63eda2b1190e4c3d961ce3ae7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726039"
---
# <a name="cordebugstepreason-enumeration"></a><span data-ttu-id="25d34-102">CorDebugStepReason, énumération</span><span class="sxs-lookup"><span data-stu-id="25d34-102">CorDebugStepReason Enumeration</span></span>

<span data-ttu-id="25d34-103">Indique le résultat d'une étape individuelle.</span><span class="sxs-lookup"><span data-stu-id="25d34-103">Indicates the outcome of an individual step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25d34-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a><span data-ttu-id="25d34-105">Membres</span><span class="sxs-lookup"><span data-stu-id="25d34-105">Members</span></span>  
  
|<span data-ttu-id="25d34-106">Membre</span><span class="sxs-lookup"><span data-stu-id="25d34-106">Member</span></span>|<span data-ttu-id="25d34-107">Description</span><span class="sxs-lookup"><span data-stu-id="25d34-107">Description</span></span>|  
|------------|-----------------|  
|`STEP_NORMAL`|<span data-ttu-id="25d34-108">Exécution pas à pas terminée normalement, au sein de la même fonction.</span><span class="sxs-lookup"><span data-stu-id="25d34-108">Stepping completed normally, within the same function.</span></span>|  
|`STEP_RETURN`|<span data-ttu-id="25d34-109">L’exécution pas à pas a continué normalement, après le retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="25d34-109">Stepping continued normally, after the function returned.</span></span>|  
|`STEP_CALL`|<span data-ttu-id="25d34-110">L’exécution pas à pas a continué normalement, au début d’une fonction récemment appelée.</span><span class="sxs-lookup"><span data-stu-id="25d34-110">Stepping continued normally, at the beginning of a newly called function.</span></span>|  
|`STEP_EXCEPTION_FILTER`|<span data-ttu-id="25d34-111">Une exception a été générée et le contrôle a été passé à un filtre d’exception.</span><span class="sxs-lookup"><span data-stu-id="25d34-111">An exception was generated and control was passed to an exception filter.</span></span>|  
|`STEP_EXCEPTION_HANDLER`|<span data-ttu-id="25d34-112">Une exception a été générée et le contrôle a été passé à un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="25d34-112">An exception was generated and control was passed to an exception handler.</span></span>|  
|`STEP_INTERCEPT`|<span data-ttu-id="25d34-113">Le contrôle a été passé à un intercepteur.</span><span class="sxs-lookup"><span data-stu-id="25d34-113">Control was passed to an interceptor.</span></span>|  
|`STEP_EXIT`|<span data-ttu-id="25d34-114">Le thread s’est arrêté avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="25d34-114">The thread exited before the step was completed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25d34-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="25d34-115">Requirements</span></span>  

 <span data-ttu-id="25d34-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25d34-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25d34-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25d34-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25d34-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25d34-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25d34-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25d34-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d34-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25d34-120">See also</span></span>

- [<span data-ttu-id="25d34-121">StepComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="25d34-121">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)
- [<span data-ttu-id="25d34-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="25d34-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
