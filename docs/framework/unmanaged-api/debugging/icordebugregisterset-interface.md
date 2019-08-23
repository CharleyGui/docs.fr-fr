---
title: ICorDebugRegisterSet, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6419a525a8a542295751defb97e67a83220730b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965066"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="07c3c-102">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="07c3c-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="07c3c-103">Représente l’ensemble des registres disponibles sur l’ordinateur qui exécute actuellement le code.</span><span class="sxs-lookup"><span data-stu-id="07c3c-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07c3c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="07c3c-104">Methods</span></span>  
  
|<span data-ttu-id="07c3c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="07c3c-105">Method</span></span>|<span data-ttu-id="07c3c-106">Description</span><span class="sxs-lookup"><span data-stu-id="07c3c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07c3c-107">GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="07c3c-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="07c3c-108">Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="07c3c-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="07c3c-109">GetRegistersAvailable, méthode</span><span class="sxs-lookup"><span data-stu-id="07c3c-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="07c3c-110">Obtient un masque de bits indiquant les registres `ICorDebugRegisterSet` actuellement disponibles.</span><span class="sxs-lookup"><span data-stu-id="07c3c-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="07c3c-111">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="07c3c-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="07c3c-112">Obtient le contexte du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="07c3c-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="07c3c-113">SetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="07c3c-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="07c3c-114">Non implémenté pour la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07c3c-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="07c3c-115">SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="07c3c-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="07c3c-116">Non implémenté pour le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="07c3c-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07c3c-117">Notes</span><span class="sxs-lookup"><span data-stu-id="07c3c-117">Remarks</span></span>  
 <span data-ttu-id="07c3c-118">L' `ICorDebugRegisterSet` interface prend en charge uniquement les registres 32 bits.</span><span class="sxs-lookup"><span data-stu-id="07c3c-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="07c3c-119">Utilisez l’interface [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) sur les plateformes telles que IA-64 qui requièrent des registres supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="07c3c-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07c3c-120">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="07c3c-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07c3c-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="07c3c-121">Requirements</span></span>  
 <span data-ttu-id="07c3c-122">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07c3c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c3c-123">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="07c3c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07c3c-124">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07c3c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07c3c-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07c3c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c3c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07c3c-126">See also</span></span>

- [<span data-ttu-id="07c3c-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="07c3c-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="07c3c-128">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="07c3c-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
