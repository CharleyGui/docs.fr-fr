---
title: ICorDebugInstanceFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777526"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="b6be7-102">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="b6be7-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="b6be7-103">Représente les informations sur les symboles de débogage pour un champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="b6be7-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6be7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b6be7-104">Methods</span></span>  
  
|<span data-ttu-id="b6be7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b6be7-105">Method</span></span>|<span data-ttu-id="b6be7-106">Description</span><span class="sxs-lookup"><span data-stu-id="b6be7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6be7-107">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="b6be7-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="b6be7-108">Obtient le nom du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="b6be7-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="b6be7-109">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="b6be7-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="b6be7-110">Obtient l'offset en octets de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="b6be7-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="b6be7-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b6be7-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="b6be7-112">Obtient la taille en octets du champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="b6be7-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6be7-113">Notes</span><span class="sxs-lookup"><span data-stu-id="b6be7-113">Remarks</span></span>  
 <span data-ttu-id="b6be7-114">L'interface `ICorDebugInstanceFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ d'instance.</span><span class="sxs-lookup"><span data-stu-id="b6be7-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6be7-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b6be7-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b6be7-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="b6be7-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6be7-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b6be7-117">Requirements</span></span>  
 <span data-ttu-id="b6be7-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6be7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6be7-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6be7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6be7-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6be7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6be7-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6be7-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6be7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6be7-122">See also</span></span>

- [<span data-ttu-id="b6be7-123">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="b6be7-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="b6be7-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b6be7-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b6be7-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="b6be7-125">Debugging</span></span>](index.md)
