---
title: ICorDebugLoadedModule, interface
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9d3bdcec9e90dab337b595294d114de4bd3d531f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781999"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="e1a95-102">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="e1a95-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="e1a95-103">Fournit des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="e1a95-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1a95-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e1a95-104">Methods</span></span>  
  
|<span data-ttu-id="e1a95-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e1a95-105">Method</span></span>|<span data-ttu-id="e1a95-106">Description</span><span class="sxs-lookup"><span data-stu-id="e1a95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1a95-107">GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="e1a95-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="e1a95-108">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="e1a95-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="e1a95-109">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="e1a95-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="e1a95-110">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="e1a95-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="e1a95-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="e1a95-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="e1a95-112">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="e1a95-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1a95-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e1a95-113">Remarks</span></span>  
 <span data-ttu-id="e1a95-114">L'interface `ICorDebugLoadedModule` est implémentée par un débogueur et est utilisée par les interfaces de débogage du CLR pour obtenir des informations sur le module chargé à partir du débogueur.</span><span class="sxs-lookup"><span data-stu-id="e1a95-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1a95-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e1a95-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e1a95-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="e1a95-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1a95-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e1a95-117">Requirements</span></span>  
 <span data-ttu-id="e1a95-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1a95-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1a95-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1a95-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1a95-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1a95-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1a95-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1a95-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a95-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1a95-122">See also</span></span>

- [<span data-ttu-id="e1a95-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e1a95-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e1a95-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="e1a95-124">Debugging</span></span>](index.md)
