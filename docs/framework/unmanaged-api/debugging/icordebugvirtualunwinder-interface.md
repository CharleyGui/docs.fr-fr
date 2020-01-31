---
title: ICorDebugVirtualUnwinder, interface
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790824"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="f323b-102">ICorDebugVirtualUnwinder, interface</span><span class="sxs-lookup"><span data-stu-id="f323b-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="f323b-103">Fournit des méthodes pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="f323b-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f323b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f323b-104">Methods</span></span>  
  
|<span data-ttu-id="f323b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f323b-105">Method</span></span>|<span data-ttu-id="f323b-106">Name</span><span class="sxs-lookup"><span data-stu-id="f323b-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="f323b-107">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="f323b-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="f323b-108">Obtient le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="f323b-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="f323b-109">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f323b-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="f323b-110">Avance jusqu'au contexte de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="f323b-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f323b-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f323b-111">Remarks</span></span>  
 <span data-ttu-id="f323b-112">Les membres de l'interface `ICorDebugVirtualUnwinder` sont implémentés par le débogueur pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="f323b-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f323b-113">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f323b-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f323b-114">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="f323b-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f323b-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f323b-115">Requirements</span></span>  
 <span data-ttu-id="f323b-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f323b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f323b-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f323b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f323b-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f323b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f323b-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f323b-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f323b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f323b-120">See also</span></span>

- [<span data-ttu-id="f323b-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f323b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f323b-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="f323b-122">Debugging</span></span>](index.md)
