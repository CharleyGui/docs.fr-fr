---
title: ICorDebugVirtualUnwinder (interface)
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 59ecf3da4b44af7b04dec26fbc3ea182c185d04a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396452"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="bf4ea-102">ICorDebugVirtualUnwinder (interface)</span><span class="sxs-lookup"><span data-stu-id="bf4ea-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="bf4ea-103">Fournit des méthodes pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="bf4ea-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf4ea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bf4ea-104">Methods</span></span>  
  
|<span data-ttu-id="bf4ea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="bf4ea-105">Method</span></span>|<span data-ttu-id="bf4ea-106">Nom</span><span class="sxs-lookup"><span data-stu-id="bf4ea-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="bf4ea-107">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="bf4ea-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="bf4ea-108">Obtient le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="bf4ea-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="bf4ea-109">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="bf4ea-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="bf4ea-110">Avance jusqu'au contexte de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="bf4ea-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf4ea-111">Notes</span><span class="sxs-lookup"><span data-stu-id="bf4ea-111">Remarks</span></span>  
 <span data-ttu-id="bf4ea-112">Les membres de l'interface `ICorDebugVirtualUnwinder` sont implémentés par le débogueur pour faciliter le déroulement de la pile.</span><span class="sxs-lookup"><span data-stu-id="bf4ea-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf4ea-113">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bf4ea-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="bf4ea-114">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="bf4ea-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf4ea-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf4ea-115">Requirements</span></span>  
 <span data-ttu-id="bf4ea-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf4ea-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf4ea-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf4ea-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf4ea-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf4ea-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf4ea-119">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf4ea-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4ea-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf4ea-120">See also</span></span>

- [<span data-ttu-id="bf4ea-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bf4ea-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bf4ea-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="bf4ea-122">Debugging</span></span>](index.md)
