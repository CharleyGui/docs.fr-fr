---
title: ICorDebugVariableHomeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: a9b65449747fde42f9cd770e33741ef34d33fbb8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121023"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="458ea-102">ICorDebugVariableHomeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="458ea-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="458ea-103">Fournit un énumérateur aux variables locales et aux arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="458ea-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="458ea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="458ea-104">Methods</span></span>  
  
|<span data-ttu-id="458ea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="458ea-105">Method</span></span>|<span data-ttu-id="458ea-106">Description</span><span class="sxs-lookup"><span data-stu-id="458ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="458ea-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="458ea-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="458ea-108">Obtient le nombre spécifié d’instances [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) qui contiennent des informations sur les variables locales et les arguments d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="458ea-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="458ea-109">Notes</span><span class="sxs-lookup"><span data-stu-id="458ea-109">Remarks</span></span>  
 <span data-ttu-id="458ea-110">L’interface `ICorDebugVariableHomeEnum` implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="458ea-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="458ea-111">Une instance de `ICorDebugVariableHomeEnum` est remplie avec des instances [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) en appelant la méthode [ICorDebugCode4 :: EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="458ea-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="458ea-112">Chaque instance [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) de la collection représente une variable locale ou un argument dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="458ea-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="458ea-113">Les objets [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) de la collection peuvent être énumérés en appelant la méthode [ICorDebugVariableHomeEnum :: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="458ea-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458ea-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="458ea-114">Requirements</span></span>  
 <span data-ttu-id="458ea-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="458ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458ea-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="458ea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="458ea-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="458ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="458ea-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458ea-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="458ea-119">See also</span></span>

- [<span data-ttu-id="458ea-120">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="458ea-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="458ea-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="458ea-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
