---
title: ICorDebugDataTarget3 (interface)
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 5f91db291396589a916933bdc7c2a2390dd61a5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136669"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="57228-102">ICorDebugDataTarget3 (interface)</span><span class="sxs-lookup"><span data-stu-id="57228-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="57228-103">Étend logiquement l’interface [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) pour fournir des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="57228-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="57228-104">Méthode</span><span class="sxs-lookup"><span data-stu-id="57228-104">Method</span></span>  
  
|<span data-ttu-id="57228-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="57228-105">Method</span></span>|<span data-ttu-id="57228-106">Description</span><span class="sxs-lookup"><span data-stu-id="57228-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57228-107">GetLoadedModules, méthode</span><span class="sxs-lookup"><span data-stu-id="57228-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="57228-108">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="57228-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57228-109">Notes</span><span class="sxs-lookup"><span data-stu-id="57228-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57228-110">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57228-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="57228-111">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="57228-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57228-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="57228-112">Requirements</span></span>  
 <span data-ttu-id="57228-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57228-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57228-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57228-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57228-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57228-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57228-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57228-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57228-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57228-117">See also</span></span>

- [<span data-ttu-id="57228-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="57228-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="57228-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="57228-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
