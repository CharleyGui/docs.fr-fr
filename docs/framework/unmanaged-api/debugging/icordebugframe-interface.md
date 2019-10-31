---
title: ICorDebugFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124072"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="429e5-102">ICorDebugFrame, interface</span><span class="sxs-lookup"><span data-stu-id="429e5-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="429e5-103">Représente un frame sur la pile en cours.</span><span class="sxs-lookup"><span data-stu-id="429e5-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="429e5-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="429e5-104">Methods</span></span>  
  
|<span data-ttu-id="429e5-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-105">Method</span></span>|<span data-ttu-id="429e5-106">Description</span><span class="sxs-lookup"><span data-stu-id="429e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="429e5-107">CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="429e5-108">Obtient un ICorDebugStepper pour exécuter des opérations pas à pas relatives à cette `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="429e5-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="429e5-109">GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="429e5-110">Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle appelée par ce frame, ou retourne null s’il s’agit du frame le plus profond dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="429e5-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="429e5-111">GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="429e5-112">Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle qui a appelé ce frame, ou retourne la valeur null s’il s’agit du frame le plus à l’extérieur dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="429e5-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="429e5-113">GetChain, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="429e5-114">Obtient un pointeur vers l’ICorDebugChain auquel ce `ICorDebugFrame` fait partie.</span><span class="sxs-lookup"><span data-stu-id="429e5-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="429e5-115">GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="429e5-116">Obtient un pointeur vers le ICorDebugCode associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="429e5-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="429e5-117">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="429e5-118">Obtient un pointeur vers le ICorDebugFunction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="429e5-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="429e5-119">GetFunctionToken, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="429e5-120">Obtient le jeton de métadonnées pour la fonction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="429e5-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="429e5-121">GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="429e5-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="429e5-122">Obtient la plage d’adresses absolues du frame de pile représenté par ce `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="429e5-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="429e5-123">Notes</span><span class="sxs-lookup"><span data-stu-id="429e5-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="429e5-124">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="429e5-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="429e5-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="429e5-125">Requirements</span></span>  
 <span data-ttu-id="429e5-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="429e5-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="429e5-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="429e5-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="429e5-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="429e5-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="429e5-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="429e5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429e5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="429e5-130">See also</span></span>

- [<span data-ttu-id="429e5-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="429e5-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
