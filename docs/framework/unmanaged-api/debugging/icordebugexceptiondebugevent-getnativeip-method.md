---
title: ICorDebugExceptionDebugEvent::GetNativeIP, méthoded
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a3fa4ad73847d172ee8e1c7d239bfc00fe11638
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754334"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="74627-102">ICorDebugExceptionDebugEvent::GetNativeIP, méthoded</span><span class="sxs-lookup"><span data-stu-id="74627-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="74627-103">Obtient le pointeur d'instruction natif de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="74627-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74627-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74627-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74627-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74627-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="74627-106">[out] Pointeur vers le pointeur d'instruction de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="74627-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="74627-107">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="74627-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74627-108">Notes</span><span class="sxs-lookup"><span data-stu-id="74627-108">Remarks</span></span>  
 <span data-ttu-id="74627-109">La signification de ce pointeur d'instruction varie selon le type d'événement, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="74627-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="74627-110">Type d'événement</span><span class="sxs-lookup"><span data-stu-id="74627-110">Event type</span></span>|<span data-ttu-id="74627-111">Signification de la valeur `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="74627-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="74627-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="74627-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="74627-113">Adresse de l'instruction défaillante.</span><span class="sxs-lookup"><span data-stu-id="74627-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="74627-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="74627-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="74627-115">L’adresse de code dans le frame indiqué par le [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) méthode où l’exécution reprend si aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="74627-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="74627-116">L'exception peut provoquer ou non l'exécution de code différent, comme le bloc catch d'une clause `try/catch/finally`, dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="74627-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="74627-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="74627-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="74627-118">Adresse du code où `catch` démarre l’exécution du gestionnaire dans le frame indiqué par le [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="74627-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="74627-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="74627-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="74627-120">`pIP` est égal à 0.</span><span class="sxs-lookup"><span data-stu-id="74627-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="74627-121">Le type d’événement est disponible à partir de la [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="74627-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74627-122">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="74627-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74627-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="74627-123">Requirements</span></span>  
 <span data-ttu-id="74627-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74627-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74627-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74627-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74627-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74627-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74627-127">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74627-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74627-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74627-128">See also</span></span>

- [<span data-ttu-id="74627-129">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="74627-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="74627-130">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="74627-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
