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
ms.openlocfilehash: 8e8caad9f0fc60121dbd1c738a6024da3e4d02f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726000"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="e8ae6-102">ICorDebugVariableHomeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e8ae6-102">ICorDebugVariableHomeEnum Interface</span></span>

<span data-ttu-id="e8ae6-103">Fournit un énumérateur aux variables locales et aux arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="e8ae6-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8ae6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e8ae6-104">Methods</span></span>  
  
|<span data-ttu-id="e8ae6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e8ae6-105">Method</span></span>|<span data-ttu-id="e8ae6-106">Description</span><span class="sxs-lookup"><span data-stu-id="e8ae6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8ae6-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e8ae6-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="e8ae6-108">Obtient le nombre spécifié d’instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui contiennent des informations sur les variables locales et les arguments d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="e8ae6-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8ae6-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8ae6-109">Remarks</span></span>  

 <span data-ttu-id="e8ae6-110">L' `ICorDebugVariableHomeEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="e8ae6-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e8ae6-111">Une `ICorDebugVariableHomeEnum` instance est remplie avec des instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) en appelant la méthode [ICorDebugCode4 :: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e8ae6-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="e8ae6-112">Chaque instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) de la collection représente une variable locale ou un argument dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="e8ae6-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="e8ae6-113">Les objets  [ICorDebugVariableHome](icordebugvariablehome-interface.md) de la collection peuvent être énumérés en appelant la méthode [ICorDebugVariableHomeEnum :: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e8ae6-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ae6-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8ae6-114">Requirements</span></span>  

 <span data-ttu-id="e8ae6-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ae6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ae6-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8ae6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8ae6-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8ae6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8ae6-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ae6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ae6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ae6-119">See also</span></span>

- [<span data-ttu-id="e8ae6-120">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="e8ae6-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="e8ae6-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e8ae6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
