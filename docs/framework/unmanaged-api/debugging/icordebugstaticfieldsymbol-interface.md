---
title: ICorDebugStaticFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4e245e96ac9d47db10072e50a5b3c516d5dd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962676"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="3b7d0-102">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="3b7d0-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="3b7d0-103">Représente les informations sur les symboles de débogage pour un champ static.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b7d0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3b7d0-104">Methods</span></span>  
  
|<span data-ttu-id="3b7d0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3b7d0-105">Method</span></span>|<span data-ttu-id="3b7d0-106">Description</span><span class="sxs-lookup"><span data-stu-id="3b7d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b7d0-107">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="3b7d0-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="3b7d0-108">Obtient l'adresse du champ statique.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="3b7d0-109">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="3b7d0-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="3b7d0-110">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="3b7d0-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="3b7d0-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="3b7d0-112">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b7d0-113">Notes</span><span class="sxs-lookup"><span data-stu-id="3b7d0-113">Remarks</span></span>  
 <span data-ttu-id="3b7d0-114">L’interface `ICorDebugStaticFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ statique.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b7d0-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="3b7d0-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="3b7d0-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b7d0-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b7d0-117">Requirements</span></span>  
 <span data-ttu-id="3b7d0-118">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b7d0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b7d0-119">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3b7d0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b7d0-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b7d0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b7d0-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b7d0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7d0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b7d0-122">See also</span></span>

- [<span data-ttu-id="3b7d0-123">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="3b7d0-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="3b7d0-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3b7d0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3b7d0-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="3b7d0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
