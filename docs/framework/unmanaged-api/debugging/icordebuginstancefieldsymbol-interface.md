---
title: ICorDebugInstanceFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 2ed1d70f554ca0a4a49639fe53a2ddbb0497c0a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122733"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="cb5e9-102">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="cb5e9-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="cb5e9-103">Représente les informations sur les symboles de débogage pour un champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb5e9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="cb5e9-104">Methods</span></span>  
  
|<span data-ttu-id="cb5e9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="cb5e9-105">Method</span></span>|<span data-ttu-id="cb5e9-106">Description</span><span class="sxs-lookup"><span data-stu-id="cb5e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb5e9-107">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="cb5e9-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="cb5e9-108">Obtient le nom du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="cb5e9-109">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="cb5e9-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="cb5e9-110">Obtient l'offset en octets de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="cb5e9-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="cb5e9-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="cb5e9-112">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb5e9-113">Notes</span><span class="sxs-lookup"><span data-stu-id="cb5e9-113">Remarks</span></span>  
 <span data-ttu-id="cb5e9-114">L'interface `ICorDebugInstanceFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb5e9-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="cb5e9-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="cb5e9-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5e9-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="cb5e9-117">Requirements</span></span>  
 <span data-ttu-id="cb5e9-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5e9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5e9-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb5e9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb5e9-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb5e9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb5e9-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5e9-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5e9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb5e9-122">See also</span></span>

- [<span data-ttu-id="cb5e9-123">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="cb5e9-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="cb5e9-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="cb5e9-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cb5e9-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="cb5e9-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
