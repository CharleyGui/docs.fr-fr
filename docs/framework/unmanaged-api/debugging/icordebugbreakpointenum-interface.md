---
title: ICorDebugBreakpointEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 22ae1d24040a8ee5000e0ff2fbeb2b45e08050df
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784351"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="f1e2a-102">ICorDebugBreakpointEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f1e2a-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="f1e2a-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="f1e2a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1e2a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f1e2a-104">Methods</span></span>  
  
|<span data-ttu-id="f1e2a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f1e2a-105">Method</span></span>|<span data-ttu-id="f1e2a-106">Description</span><span class="sxs-lookup"><span data-stu-id="f1e2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1e2a-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f1e2a-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="f1e2a-108">Obtient le nombre spécifié d’instances de `ICorDebugBreakpoint` à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="f1e2a-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1e2a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f1e2a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1e2a-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f1e2a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e2a-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f1e2a-111">Requirements</span></span>  
 <span data-ttu-id="f1e2a-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1e2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1e2a-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1e2a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1e2a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1e2a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1e2a-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e2a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1e2a-116">See also</span></span>

- [<span data-ttu-id="f1e2a-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f1e2a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
