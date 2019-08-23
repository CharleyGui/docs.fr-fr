---
title: ICorDebugVirtualUnwinder (interface)
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f78417d613023bb4fb7325560c0c06abe0874aba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967939"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="a6700-102">ICorDebugVirtualUnwinder (interface)</span><span class="sxs-lookup"><span data-stu-id="a6700-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="a6700-103">Fournit des méthodes pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="a6700-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6700-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a6700-104">Methods</span></span>  
  
|<span data-ttu-id="a6700-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a6700-105">Method</span></span>|<span data-ttu-id="a6700-106">Name</span><span class="sxs-lookup"><span data-stu-id="a6700-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="a6700-107">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="a6700-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="a6700-108">Obtient le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="a6700-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="a6700-109">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="a6700-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="a6700-110">Avance jusqu'au contexte de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a6700-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6700-111">Notes</span><span class="sxs-lookup"><span data-stu-id="a6700-111">Remarks</span></span>  
 <span data-ttu-id="a6700-112">Les membres de l'interface `ICorDebugVirtualUnwinder` sont implémentés par le débogueur pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="a6700-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6700-113">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a6700-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a6700-114">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="a6700-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6700-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6700-115">Requirements</span></span>  
 <span data-ttu-id="a6700-116">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6700-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6700-117">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6700-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6700-118">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6700-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6700-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6700-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6700-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6700-120">See also</span></span>

- [<span data-ttu-id="a6700-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a6700-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a6700-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="a6700-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
