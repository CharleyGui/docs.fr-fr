---
title: ICorDebugExceptionDebugEvent, interface
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: c280852d421742cf9e8c2f8dcaa9c0f588f8537b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697387"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="063d9-102">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="063d9-102">ICorDebugExceptionDebugEvent Interface</span></span>

<span data-ttu-id="063d9-103">Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements d’exception.</span><span class="sxs-lookup"><span data-stu-id="063d9-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="063d9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="063d9-104">Methods</span></span>  
  
|<span data-ttu-id="063d9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="063d9-105">Method</span></span>|<span data-ttu-id="063d9-106">Description</span><span class="sxs-lookup"><span data-stu-id="063d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="063d9-107">GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="063d9-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="063d9-108">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="063d9-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="063d9-109">GetNativeIP, méthode</span><span class="sxs-lookup"><span data-stu-id="063d9-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="063d9-110">Obtient le pointeur d'interface natif de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="063d9-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="063d9-111">GetStackPointer, méthode</span><span class="sxs-lookup"><span data-stu-id="063d9-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="063d9-112">Obtient le pointeur de pile de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="063d9-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="063d9-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="063d9-113">Remarks</span></span>  

 <span data-ttu-id="063d9-114">L'interface `ICorDebugExceptionDebugEvent` est implémentée par les types d'événements suivants :</span><span class="sxs-lookup"><span data-stu-id="063d9-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="063d9-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="063d9-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="063d9-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="063d9-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="063d9-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="063d9-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="063d9-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="063d9-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="063d9-119">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="063d9-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="063d9-120">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="063d9-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="063d9-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="063d9-121">Requirements</span></span>  

 <span data-ttu-id="063d9-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="063d9-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="063d9-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="063d9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="063d9-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="063d9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="063d9-125">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="063d9-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063d9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="063d9-126">See also</span></span>

- [<span data-ttu-id="063d9-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="063d9-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="063d9-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="063d9-128">Debugging</span></span>](index.md)
