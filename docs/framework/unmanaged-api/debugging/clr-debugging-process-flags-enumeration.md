---
title: CLR_DEBUGGING_PROCESS_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
ms.openlocfilehash: b9185600d9d8b2a33830d86642727ac54b87a9cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099658"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="bda75-102">CLR_DEBUGGING_PROCESS_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="bda75-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="bda75-103">Fournit des valeurs utilisées par la méthode [ICLRDebugging :: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bda75-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bda75-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="bda75-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bda75-105">Members</span></span>  
  
|<span data-ttu-id="bda75-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bda75-106">Member</span></span>|<span data-ttu-id="bda75-107">Description</span><span class="sxs-lookup"><span data-stu-id="bda75-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="bda75-108">Ce runtime a un événement de débogueur géré non intercepté à envoyer.</span><span class="sxs-lookup"><span data-stu-id="bda75-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="bda75-109">Consultez la section Notes pour la distinction entre les événements de rattrapage et de non-rattrapage.</span><span class="sxs-lookup"><span data-stu-id="bda75-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="bda75-110">L’événement managé en attente est une demande <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bda75-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bda75-111">Notes</span><span class="sxs-lookup"><span data-stu-id="bda75-111">Remarks</span></span>  
 <span data-ttu-id="bda75-112">Les événements de rattrapage incluent les notifications de processus, de domaine d’application, d’assembly, de module et de création de thread qui mettent le débogueur à l’état actuel une fois qu’il est attaché à un processus.</span><span class="sxs-lookup"><span data-stu-id="bda75-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="bda75-113">Les événements de non-rattrapage, indiqués par l’indicateur `CLR_DEBUGGING_MANAGED_EVENT_PENDING`, incluent tous les autres événements du débogueur, tels que les exceptions et les notifications de l’Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="bda75-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="bda75-114">L’indicateur `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` permet au runtime de faire la différence entre une exception d’arrêt et une demande d’attachement d’un débogueur managé qui peut être annulé.</span><span class="sxs-lookup"><span data-stu-id="bda75-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bda75-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="bda75-115">Requirements</span></span>  
 <span data-ttu-id="bda75-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bda75-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda75-117">**En-tête :** Metahost. idl, Metahost. h</span><span class="sxs-lookup"><span data-stu-id="bda75-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="bda75-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bda75-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bda75-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda75-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda75-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bda75-120">See also</span></span>

- [<span data-ttu-id="bda75-121">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="bda75-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="bda75-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="bda75-122">Debugging</span></span>](index.md)
