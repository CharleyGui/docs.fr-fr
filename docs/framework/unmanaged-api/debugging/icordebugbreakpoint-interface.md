---
title: ICorDebugBreakpoint, interface
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 29bb84341c2cb4177c43f798d25a1a6d50099aa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122800"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="15601-102">ICorDebugBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="15601-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="15601-103">Représente un point d’arrêt dans une fonction, ou un point de suivi sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="15601-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15601-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="15601-104">Methods</span></span>  
  
|<span data-ttu-id="15601-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="15601-105">Method</span></span>|<span data-ttu-id="15601-106">Description</span><span class="sxs-lookup"><span data-stu-id="15601-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15601-107">Activate, méthode</span><span class="sxs-lookup"><span data-stu-id="15601-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="15601-108">Définit l’état actif de cette `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="15601-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="15601-109">IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="15601-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="15601-110">Obtient une valeur qui indique si ce `ICorDebugBreakpoint` est actif.</span><span class="sxs-lookup"><span data-stu-id="15601-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15601-111">Notes</span><span class="sxs-lookup"><span data-stu-id="15601-111">Remarks</span></span>  
 <span data-ttu-id="15601-112">Les points d’arrêt ne prennent pas directement en charge les expressions conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="15601-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="15601-113">Si de telles fonctionnalités sont souhaitées, un débogueur doit l’implémenter sur `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="15601-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="15601-114">L’interface ICorDebugFunctionBreakpoint étend `ICorDebugBreakpoint` pour prendre en charge les points d’arrêt dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="15601-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15601-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="15601-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15601-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="15601-116">Requirements</span></span>  
 <span data-ttu-id="15601-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15601-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15601-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15601-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15601-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15601-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15601-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15601-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15601-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15601-121">See also</span></span>

- [<span data-ttu-id="15601-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="15601-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
