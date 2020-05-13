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
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209615"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="ce0a4-102">ICorDebugFrame, interface</span><span class="sxs-lookup"><span data-stu-id="ce0a4-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="ce0a4-103">Représente un frame sur la pile en cours.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce0a4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce0a4-104">Methods</span></span>  
  
|<span data-ttu-id="ce0a4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-105">Method</span></span>|<span data-ttu-id="ce0a4-106">Description</span><span class="sxs-lookup"><span data-stu-id="ce0a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce0a4-107">CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="ce0a4-108">Obtient un ICorDebugStepper pour exécuter des opérations pas à pas relatives à ce `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="ce0a4-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="ce0a4-109">GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="ce0a4-110">Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle appelée par ce frame, ou retourne la valeur null s’il s’agit du frame le plus profond dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="ce0a4-111">GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="ce0a4-112">Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle qui a appelé ce frame, ou retourne la valeur null s’il s’agit du frame le plus à l’extérieur dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="ce0a4-113">GetChain, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="ce0a4-114">Obtient un pointeur vers l’ICorDebugChain `ICorDebugFrame` dont il fait partie.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="ce0a4-115">GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="ce0a4-116">Obtient un pointeur vers le ICorDebugCode associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="ce0a4-117">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="ce0a4-118">Obtient un pointeur vers le ICorDebugFunction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="ce0a4-119">GetFunctionToken, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="ce0a4-120">Obtient le jeton de métadonnées pour la fonction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="ce0a4-121">GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="ce0a4-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="ce0a4-122">Obtient la plage d’adresses absolues du frame de pile représenté par ce `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="ce0a4-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce0a4-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce0a4-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0a4-124">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ce0a4-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce0a4-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce0a4-125">Requirements</span></span>  
 <span data-ttu-id="ce0a4-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce0a4-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce0a4-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce0a4-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce0a4-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce0a4-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce0a4-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce0a4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0a4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce0a4-130">See also</span></span>

- [<span data-ttu-id="ce0a4-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ce0a4-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
