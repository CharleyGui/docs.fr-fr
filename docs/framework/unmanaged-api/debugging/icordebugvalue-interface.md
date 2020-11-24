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
ms.openlocfilehash: 7d3c35ed6cda637e3b885afe089ddfa590d51076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683600"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="e5e02-102">ICorDebugValue, interface</span><span class="sxs-lookup"><span data-stu-id="e5e02-102">ICorDebugValue Interface</span></span>

<span data-ttu-id="e5e02-103">Représente une valeur dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="e5e02-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="e5e02-104">La valeur peut être une valeur de lecture ou d’écriture.</span><span class="sxs-lookup"><span data-stu-id="e5e02-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5e02-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e5e02-105">Methods</span></span>  
  
|<span data-ttu-id="e5e02-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e5e02-106">Method</span></span>|<span data-ttu-id="e5e02-107">Description</span><span class="sxs-lookup"><span data-stu-id="e5e02-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5e02-108">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="e5e02-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="e5e02-109">Cette méthode n'est pas implémentée à l'heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="e5e02-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="e5e02-110">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="e5e02-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="e5e02-111">Obtient l’adresse de cet `ICorDebugValue` objet, qui est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="e5e02-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="e5e02-112">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="e5e02-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="e5e02-113">Obtient la taille, en octets, de cet `ICorDebugValue` objet.</span><span class="sxs-lookup"><span data-stu-id="e5e02-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="e5e02-114">GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="e5e02-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="e5e02-115">Obtient le type primitif de cet `ICorDebugValue` objet.</span><span class="sxs-lookup"><span data-stu-id="e5e02-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5e02-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5e02-116">Remarks</span></span>  

 <span data-ttu-id="e5e02-117">En général, la propriété d’un objet de valeur est passée lorsqu’elle est retournée.</span><span class="sxs-lookup"><span data-stu-id="e5e02-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="e5e02-118">Le destinataire est responsable de la suppression d’une référence de l’objet lorsqu’il est terminé avec l’objet.</span><span class="sxs-lookup"><span data-stu-id="e5e02-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="e5e02-119">Selon l’emplacement à partir duquel la valeur a été récupérée, la valeur peut ne pas rester valide après la reprise du processus.</span><span class="sxs-lookup"><span data-stu-id="e5e02-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="e5e02-120">Ainsi, en général, la valeur ne doit pas être maintenue à travers un appel de la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e5e02-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5e02-121">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e5e02-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e02-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5e02-122">Requirements</span></span>  

 <span data-ttu-id="e5e02-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e02-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e02-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5e02-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5e02-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5e02-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5e02-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e02-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e02-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5e02-127">See also</span></span>

- [<span data-ttu-id="e5e02-128">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="e5e02-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="e5e02-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e5e02-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
