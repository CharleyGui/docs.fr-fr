---
title: ICorDebugLoadedModule (interface)
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9da6aba61382381fc25fe70615976cd0e744ee1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910003"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="2a09b-102">ICorDebugLoadedModule (interface)</span><span class="sxs-lookup"><span data-stu-id="2a09b-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="2a09b-103">Fournit des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="2a09b-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a09b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2a09b-104">Methods</span></span>  
  
|<span data-ttu-id="2a09b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2a09b-105">Method</span></span>|<span data-ttu-id="2a09b-106">Description</span><span class="sxs-lookup"><span data-stu-id="2a09b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a09b-107">GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="2a09b-107">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="2a09b-108">Obtient l'adresse de base du module chargé.</span><span class="sxs-lookup"><span data-stu-id="2a09b-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="2a09b-109">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="2a09b-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|<span data-ttu-id="2a09b-110">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="2a09b-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="2a09b-111">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="2a09b-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="2a09b-112">Obtient la taille en octets du module chargé.</span><span class="sxs-lookup"><span data-stu-id="2a09b-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a09b-113">Notes</span><span class="sxs-lookup"><span data-stu-id="2a09b-113">Remarks</span></span>  
 <span data-ttu-id="2a09b-114">L'interface `ICorDebugLoadedModule` est implémentée par un débogueur et est utilisée par les interfaces de débogage du CLR pour obtenir des informations sur le module chargé à partir du débogueur.</span><span class="sxs-lookup"><span data-stu-id="2a09b-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a09b-115">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2a09b-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2a09b-116">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="2a09b-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a09b-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a09b-117">Requirements</span></span>  
 <span data-ttu-id="2a09b-118">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a09b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a09b-119">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a09b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a09b-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a09b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a09b-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a09b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a09b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a09b-122">See also</span></span>

- [<span data-ttu-id="2a09b-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2a09b-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2a09b-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="2a09b-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
