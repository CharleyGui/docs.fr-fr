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
ms.openlocfilehash: 6a378e3579ab9ea8d9534a408d0e456373616cad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213136"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="647f8-102">ICorDebugFunctionBreakpoint, interface</span><span class="sxs-lookup"><span data-stu-id="647f8-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="647f8-103">Étend l’interface ICorDebugBreakpoint pour prendre en charge les points d’arrêt dans les fonctions.</span><span class="sxs-lookup"><span data-stu-id="647f8-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="647f8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="647f8-104">Methods</span></span>  
  
|<span data-ttu-id="647f8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="647f8-105">Method</span></span>|<span data-ttu-id="647f8-106">Description</span><span class="sxs-lookup"><span data-stu-id="647f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="647f8-107">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="647f8-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="647f8-108">Obtient un pointeur d’interface vers un ICorDebugFunction qui fait référence à la fonction dans laquelle le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="647f8-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="647f8-109">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="647f8-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="647f8-110">Obtient l’offset du point d’arrêt dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="647f8-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="647f8-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="647f8-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="647f8-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="647f8-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="647f8-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="647f8-113">Requirements</span></span>  
 <span data-ttu-id="647f8-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="647f8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="647f8-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="647f8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="647f8-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="647f8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="647f8-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="647f8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647f8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="647f8-118">See also</span></span>

- [<span data-ttu-id="647f8-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="647f8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
