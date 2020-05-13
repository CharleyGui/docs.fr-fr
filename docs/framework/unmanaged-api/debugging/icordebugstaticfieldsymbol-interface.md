---
title: ICorDebugStaticFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379437"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="f2e92-102">ICorDebugStaticFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f2e92-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="f2e92-103">Représente les informations sur les symboles de débogage pour un champ static.</span><span class="sxs-lookup"><span data-stu-id="f2e92-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2e92-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f2e92-104">Methods</span></span>  
  
|<span data-ttu-id="f2e92-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f2e92-105">Method</span></span>|<span data-ttu-id="f2e92-106">Description</span><span class="sxs-lookup"><span data-stu-id="f2e92-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2e92-107">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="f2e92-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="f2e92-108">Obtient l'adresse du champ statique.</span><span class="sxs-lookup"><span data-stu-id="f2e92-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="f2e92-109">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="f2e92-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="f2e92-110">Obtient le nom du champ static.</span><span class="sxs-lookup"><span data-stu-id="f2e92-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="f2e92-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="f2e92-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="f2e92-112">Obtient la taille en octets du champ static.</span><span class="sxs-lookup"><span data-stu-id="f2e92-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2e92-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="f2e92-113">Remarks</span></span>  
 <span data-ttu-id="f2e92-114">L’interface `ICorDebugStaticFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ statique.</span><span class="sxs-lookup"><span data-stu-id="f2e92-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2e92-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f2e92-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f2e92-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="f2e92-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2e92-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2e92-117">Requirements</span></span>  
 <span data-ttu-id="f2e92-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2e92-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2e92-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2e92-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2e92-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2e92-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2e92-121">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2e92-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e92-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2e92-122">See also</span></span>

- [<span data-ttu-id="f2e92-123">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f2e92-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="f2e92-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f2e92-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f2e92-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="f2e92-125">Debugging</span></span>](index.md)
