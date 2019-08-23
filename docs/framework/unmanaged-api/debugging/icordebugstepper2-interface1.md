---
title: ICorDebugStepper2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d86f4bbec8971d164966298734388f0744a2d41c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953034"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="410c8-102">ICorDebugStepper2, interface</span><span class="sxs-lookup"><span data-stu-id="410c8-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="410c8-103">Prend en charge le débogage uniquement mon code (uniquement mon code).</span><span class="sxs-lookup"><span data-stu-id="410c8-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="410c8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="410c8-104">Methods</span></span>  
  
|<span data-ttu-id="410c8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="410c8-105">Method</span></span>|<span data-ttu-id="410c8-106">Description</span><span class="sxs-lookup"><span data-stu-id="410c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="410c8-107">SetJMC, méthode</span><span class="sxs-lookup"><span data-stu-id="410c8-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="410c8-108">Définit une valeur qui spécifie si cet effectue des étapes uniquement par le biais du code créé par le développeur d’une application.</span><span class="sxs-lookup"><span data-stu-id="410c8-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="410c8-109">Notes</span><span class="sxs-lookup"><span data-stu-id="410c8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="410c8-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="410c8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410c8-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="410c8-111">Requirements</span></span>  
 <span data-ttu-id="410c8-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410c8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410c8-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="410c8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="410c8-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="410c8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="410c8-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410c8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="410c8-116">See also</span></span>

- [<span data-ttu-id="410c8-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="410c8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
