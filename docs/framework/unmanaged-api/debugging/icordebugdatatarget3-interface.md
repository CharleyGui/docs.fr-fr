---
title: ICorDebugDataTarget3, interface
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 04e7b9a064d4a06a06b8a1518f06092ba79a3561
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783490"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="1c5ae-102">ICorDebugDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="1c5ae-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="1c5ae-103">Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pour fournir des informations sur les modules chargés.</span><span class="sxs-lookup"><span data-stu-id="1c5ae-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="1c5ae-104">Méthode</span><span class="sxs-lookup"><span data-stu-id="1c5ae-104">Method</span></span>  
  
|<span data-ttu-id="1c5ae-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1c5ae-105">Method</span></span>|<span data-ttu-id="1c5ae-106">Description</span><span class="sxs-lookup"><span data-stu-id="1c5ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c5ae-107">GetLoadedModules, méthode</span><span class="sxs-lookup"><span data-stu-id="1c5ae-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="1c5ae-108">Obtient la liste des modules qui ont été chargés jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="1c5ae-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c5ae-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1c5ae-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c5ae-110">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1c5ae-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1c5ae-111">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="1c5ae-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c5ae-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1c5ae-112">Requirements</span></span>  
 <span data-ttu-id="1c5ae-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c5ae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c5ae-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c5ae-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c5ae-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c5ae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c5ae-116">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c5ae-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c5ae-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c5ae-117">See also</span></span>

- [<span data-ttu-id="1c5ae-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1c5ae-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1c5ae-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="1c5ae-119">Debugging</span></span>](index.md)
