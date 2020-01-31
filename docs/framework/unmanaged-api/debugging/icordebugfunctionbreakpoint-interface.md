---
title: ICorDebugFunctionBreakpoint, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: 5e3804335bacefad61c4f521ea1ef1444b7b1fed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777706"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="2fff4-102">ICorDebugFunctionBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="2fff4-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="2fff4-103">Étend l’interface ICorDebugBreakpoint pour prendre en charge les points d’arrêt dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="2fff4-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2fff4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2fff4-104">Methods</span></span>  
  
|<span data-ttu-id="2fff4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2fff4-105">Method</span></span>|<span data-ttu-id="2fff4-106">Description</span><span class="sxs-lookup"><span data-stu-id="2fff4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2fff4-107">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="2fff4-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="2fff4-108">Obtient un pointeur d’interface vers un ICorDebugFunction qui fait référence à la fonction dans laquelle le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="2fff4-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="2fff4-109">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="2fff4-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="2fff4-110">Obtient l’offset du point d’arrêt dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="2fff4-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fff4-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2fff4-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fff4-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="2fff4-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fff4-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2fff4-113">Requirements</span></span>  
 <span data-ttu-id="2fff4-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fff4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fff4-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fff4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fff4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fff4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fff4-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fff4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fff4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fff4-118">See also</span></span>

- [<span data-ttu-id="2fff4-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2fff4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
