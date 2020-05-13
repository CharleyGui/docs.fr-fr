---
title: ICorDebugRuntimeUnwindableFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379389"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="279ba-102">ICorDebugRuntimeUnwindableFrame, interface</span><span class="sxs-lookup"><span data-stu-id="279ba-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="279ba-103">Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.</span><span class="sxs-lookup"><span data-stu-id="279ba-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="279ba-104">Remarks</span><span class="sxs-lookup"><span data-stu-id="279ba-104">Remarks</span></span>  
 <span data-ttu-id="279ba-105">`ICorDebugRuntimeUnwindableFrame`est une version spécialisée de l’interface ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="279ba-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="279ba-106">Elle est utilisée par les méthodes non managées qui requièrent que le runtime déroule un frame sur la pile active.</span><span class="sxs-lookup"><span data-stu-id="279ba-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="279ba-107">Les conventions de déroulement existantes ne fonctionnent pas, car elles n’utilisent pas de code compilé juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="279ba-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="279ba-108">Quand le débogueur voit un frame déroulable, il doit utiliser la méthode [ICorDebugStackWalk :: Next](icordebugstackwalk-next-method.md) pour le dérouler, mais il doit effectuer l’inspection elle-même.</span><span class="sxs-lookup"><span data-stu-id="279ba-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="279ba-109">Quand le débogueur reçoit un `ICorDebugRuntimeUnwindableFrame` , il peut appeler la méthode [ICorDebugStackWalk :: GetContext](icordebugstackwalk-getcontext-method.md) pour récupérer le contexte du frame.</span><span class="sxs-lookup"><span data-stu-id="279ba-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="279ba-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="279ba-110">Requirements</span></span>  
 <span data-ttu-id="279ba-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="279ba-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="279ba-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="279ba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="279ba-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="279ba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="279ba-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="279ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279ba-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="279ba-115">See also</span></span>

- [<span data-ttu-id="279ba-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="279ba-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="279ba-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="279ba-117">Debugging</span></span>](index.md)
