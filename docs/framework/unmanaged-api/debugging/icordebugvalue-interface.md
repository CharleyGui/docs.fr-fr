---
title: ICorDebugValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: 77d28d8eef97a934c15ac29725f856f4bf39e6ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140161"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="d546d-102">ICorDebugValue, interface</span><span class="sxs-lookup"><span data-stu-id="d546d-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="d546d-103">Représente une valeur dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="d546d-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="d546d-104">La valeur peut être une valeur de lecture ou d’écriture.</span><span class="sxs-lookup"><span data-stu-id="d546d-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d546d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d546d-105">Methods</span></span>  
  
|<span data-ttu-id="d546d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="d546d-106">Method</span></span>|<span data-ttu-id="d546d-107">Description</span><span class="sxs-lookup"><span data-stu-id="d546d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d546d-108">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="d546d-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="d546d-109">Cette méthode n’est pas implémentée actuellement.</span><span class="sxs-lookup"><span data-stu-id="d546d-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="d546d-110">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="d546d-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="d546d-111">Obtient l’adresse de cet objet `ICorDebugValue`, qui est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="d546d-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="d546d-112">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="d546d-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="d546d-113">Obtient la taille, en octets, de cet objet `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="d546d-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="d546d-114">GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="d546d-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="d546d-115">Obtient le type primitif de cet objet `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="d546d-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d546d-116">Notes</span><span class="sxs-lookup"><span data-stu-id="d546d-116">Remarks</span></span>  
 <span data-ttu-id="d546d-117">En général, la propriété d’un objet de valeur est passée lorsqu’elle est retournée.</span><span class="sxs-lookup"><span data-stu-id="d546d-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="d546d-118">Le destinataire est responsable de la suppression d’une référence de l’objet lorsqu’il est terminé avec l’objet.</span><span class="sxs-lookup"><span data-stu-id="d546d-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="d546d-119">Selon l’emplacement à partir duquel la valeur a été récupérée, la valeur peut ne pas rester valide après la reprise du processus.</span><span class="sxs-lookup"><span data-stu-id="d546d-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="d546d-120">Ainsi, en général, la valeur ne doit pas être maintenue à travers un appel de la méthode [ICorDebugController :: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d546d-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d546d-121">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d546d-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d546d-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="d546d-122">Requirements</span></span>  
 <span data-ttu-id="d546d-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d546d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d546d-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d546d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d546d-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d546d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d546d-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d546d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d546d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d546d-127">See also</span></span>

- [<span data-ttu-id="d546d-128">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="d546d-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="d546d-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d546d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
