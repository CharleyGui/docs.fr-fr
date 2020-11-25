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
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730199"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="f07c5-102">ICorDebugBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="f07c5-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="f07c5-103">Représente un point d’arrêt dans une fonction, ou un point de suivi sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="f07c5-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f07c5-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f07c5-104">Methods</span></span>  
  
|<span data-ttu-id="f07c5-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f07c5-105">Method</span></span>|<span data-ttu-id="f07c5-106">Description</span><span class="sxs-lookup"><span data-stu-id="f07c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f07c5-107">Activate, méthode</span><span class="sxs-lookup"><span data-stu-id="f07c5-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="f07c5-108">Définit l’état actif de ce `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="f07c5-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="f07c5-109">IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="f07c5-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="f07c5-110">Obtient une valeur qui indique si ce `ICorDebugBreakpoint` est actif.</span><span class="sxs-lookup"><span data-stu-id="f07c5-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f07c5-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f07c5-111">Remarks</span></span>  

 <span data-ttu-id="f07c5-112">Les points d’arrêt ne prennent pas directement en charge les expressions conditionnelles.</span><span class="sxs-lookup"><span data-stu-id="f07c5-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="f07c5-113">Si de telles fonctionnalités sont souhaitées, un débogueur doit l’implémenter en plus de `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="f07c5-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="f07c5-114">L’interface ICorDebugFunctionBreakpoint étend `ICorDebugBreakpoint` pour prendre en charge les points d’arrêt dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="f07c5-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f07c5-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f07c5-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f07c5-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f07c5-116">Requirements</span></span>  

 <span data-ttu-id="f07c5-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f07c5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f07c5-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f07c5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f07c5-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f07c5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f07c5-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f07c5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07c5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f07c5-121">See also</span></span>

- [<span data-ttu-id="f07c5-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f07c5-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
