---
title: ICorDebugExceptionDebugEvent, interface
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 985edaa14510b7ca03399ae17cf1d89f28fd04c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084650"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="808c7-102">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="808c7-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="808c7-103">Étend l’interface [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) pour prendre en charge les événements d’exception.</span><span class="sxs-lookup"><span data-stu-id="808c7-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="808c7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="808c7-104">Methods</span></span>  
  
|<span data-ttu-id="808c7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="808c7-105">Method</span></span>|<span data-ttu-id="808c7-106">Description</span><span class="sxs-lookup"><span data-stu-id="808c7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="808c7-107">GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="808c7-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="808c7-108">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="808c7-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="808c7-109">GetNativeIP, méthode</span><span class="sxs-lookup"><span data-stu-id="808c7-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="808c7-110">Obtient le pointeur d'interface natif de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="808c7-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="808c7-111">GetStackPointer, méthode</span><span class="sxs-lookup"><span data-stu-id="808c7-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="808c7-112">Obtient le pointeur de pile de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="808c7-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="808c7-113">Notes</span><span class="sxs-lookup"><span data-stu-id="808c7-113">Remarks</span></span>  
 <span data-ttu-id="808c7-114">L'interface `ICorDebugExceptionDebugEvent` est implémentée par les types d'événements suivants :</span><span class="sxs-lookup"><span data-stu-id="808c7-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="808c7-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="808c7-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="808c7-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="808c7-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="808c7-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="808c7-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="808c7-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="808c7-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="808c7-119">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="808c7-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="808c7-120">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="808c7-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="808c7-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="808c7-121">Requirements</span></span>  
 <span data-ttu-id="808c7-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="808c7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="808c7-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="808c7-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="808c7-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="808c7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="808c7-125">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="808c7-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808c7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="808c7-126">See also</span></span>

- [<span data-ttu-id="808c7-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="808c7-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="808c7-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="808c7-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
