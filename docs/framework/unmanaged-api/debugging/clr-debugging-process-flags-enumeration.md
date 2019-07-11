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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef142ed5284262fd758ff13af8207b2290938e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741147"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="c402a-102">CLR_DEBUGGING_PROCESS_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="c402a-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="c402a-103">Fournit des valeurs qui sont utilisées par le [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c402a-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c402a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c402a-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c402a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c402a-105">Members</span></span>  
  
|<span data-ttu-id="c402a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c402a-106">Member</span></span>|<span data-ttu-id="c402a-107">Description</span><span class="sxs-lookup"><span data-stu-id="c402a-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="c402a-108">Ce runtime possède un événement de débogueur managé non-catch-up à envoyer.</span><span class="sxs-lookup"><span data-stu-id="c402a-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="c402a-109">Consultez la section Notes pour la distinction entre les événements de mise à jour et non-catch-up.</span><span class="sxs-lookup"><span data-stu-id="c402a-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="c402a-110">L’événement géré qui est en attente est un <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> demande.</span><span class="sxs-lookup"><span data-stu-id="c402a-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c402a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="c402a-111">Remarks</span></span>  
 <span data-ttu-id="c402a-112">Les événements de mise à jour incluent des processus, ce domaine d’application, assembly, module et les notifications de la création du thread qui donnent le débogueur jusqu'à l’état actuel une fois qu’il a attaché à un processus.</span><span class="sxs-lookup"><span data-stu-id="c402a-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="c402a-113">Les événements de non-catch-up, qui sont indiquées par le `CLR_DEBUGGING_MANAGED_EVENT_PENDING` indicateur, incluez tous les autres événements de débogueur, telles que les exceptions, puis gérés débogage notifications de l’assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="c402a-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="c402a-114">Le `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` indicateur permet au runtime de faire la distinction entre une exception de fin et une demande pour attacher un débogueur managé qui peut être annulé.</span><span class="sxs-lookup"><span data-stu-id="c402a-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c402a-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c402a-115">Requirements</span></span>  
 <span data-ttu-id="c402a-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c402a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c402a-117">**En-tête :** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="c402a-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="c402a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c402a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c402a-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c402a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c402a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c402a-120">See also</span></span>

- [<span data-ttu-id="c402a-121">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="c402a-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="c402a-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="c402a-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
