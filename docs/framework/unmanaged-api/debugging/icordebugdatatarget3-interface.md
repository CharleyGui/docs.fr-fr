---
title: ICorDebugDataTarget3 (interface)
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee94e25201dee4999fd5acb2be44a80454e9efbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911414"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="e83b6-102">ICorDebugDataTarget3 (interface)</span><span class="sxs-lookup"><span data-stu-id="e83b6-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="e83b6-103">Étend logiquement l’interface [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) pour fournir des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="e83b6-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="e83b6-104">Méthode</span><span class="sxs-lookup"><span data-stu-id="e83b6-104">Method</span></span>  
  
|<span data-ttu-id="e83b6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e83b6-105">Method</span></span>|<span data-ttu-id="e83b6-106">Description</span><span class="sxs-lookup"><span data-stu-id="e83b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e83b6-107">GetLoadedModules, méthode</span><span class="sxs-lookup"><span data-stu-id="e83b6-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="e83b6-108">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="e83b6-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e83b6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e83b6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e83b6-110">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e83b6-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e83b6-111">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="e83b6-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e83b6-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e83b6-112">Requirements</span></span>  
 <span data-ttu-id="e83b6-113">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e83b6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e83b6-114">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e83b6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e83b6-115">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e83b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e83b6-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e83b6-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83b6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e83b6-117">See also</span></span>

- [<span data-ttu-id="e83b6-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e83b6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e83b6-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="e83b6-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
