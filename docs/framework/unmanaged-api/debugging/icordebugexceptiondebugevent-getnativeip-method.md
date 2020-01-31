---
title: ICorDebugExceptionDebugEvent::GetNativeIP, méthoded
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788683"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="36012-102">ICorDebugExceptionDebugEvent::GetNativeIP, méthoded</span><span class="sxs-lookup"><span data-stu-id="36012-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="36012-103">Obtient le pointeur d'instruction natif de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="36012-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36012-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36012-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36012-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="36012-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="36012-106">[out] Pointeur vers le pointeur d'instruction de cet événement de débogage d'exception.</span><span class="sxs-lookup"><span data-stu-id="36012-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="36012-107">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="36012-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36012-108">Notes</span><span class="sxs-lookup"><span data-stu-id="36012-108">Remarks</span></span>  
 <span data-ttu-id="36012-109">La signification de ce pointeur d'instruction varie selon le type d'événement, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="36012-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="36012-110">Type d'événement</span><span class="sxs-lookup"><span data-stu-id="36012-110">Event type</span></span>|<span data-ttu-id="36012-111">Signification de la valeur `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="36012-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="36012-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="36012-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="36012-113">Adresse de l'instruction défaillante.</span><span class="sxs-lookup"><span data-stu-id="36012-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="36012-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="36012-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="36012-115">Adresse de code dans le frame indiquée par la méthode [getstackpointer,](icordebugexceptiondebugevent-getstackpointer-method.md) où l’exécution reprend si aucune exception n’a été levée.</span><span class="sxs-lookup"><span data-stu-id="36012-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="36012-116">L'exception peut provoquer ou non l'exécution de code différent, comme le bloc catch d'une clause `try/catch/finally`, dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="36012-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="36012-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="36012-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="36012-118">L’adresse de code où l’exécution du gestionnaire de `catch` démarrera dans le frame indiqué par la méthode [getstackpointer,](icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="36012-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="36012-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="36012-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="36012-120">`pIP` est égal à 0.</span><span class="sxs-lookup"><span data-stu-id="36012-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="36012-121">Le type d’événement est disponible à partir de la méthode [ICorDebugDebugEvent :: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="36012-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36012-122">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="36012-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36012-123">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="36012-123">Requirements</span></span>  
 <span data-ttu-id="36012-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36012-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36012-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36012-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36012-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36012-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36012-127">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36012-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36012-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36012-128">See also</span></span>

- [<span data-ttu-id="36012-129">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="36012-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="36012-130">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="36012-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
