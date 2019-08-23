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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8192bd7ccaebab78158f11adb79509031132ecd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937018"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="a09e6-102">ICorDebugBreakpointEnum, interface</span><span class="sxs-lookup"><span data-stu-id="a09e6-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="a09e6-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="a09e6-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a09e6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a09e6-104">Methods</span></span>  
  
|<span data-ttu-id="a09e6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a09e6-105">Method</span></span>|<span data-ttu-id="a09e6-106">Description</span><span class="sxs-lookup"><span data-stu-id="a09e6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a09e6-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="a09e6-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="a09e6-108">Obtient le nombre d' `ICorDebugBreakpoint` instances spécifié à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="a09e6-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a09e6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a09e6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a09e6-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="a09e6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09e6-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a09e6-111">Requirements</span></span>  
 <span data-ttu-id="a09e6-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a09e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09e6-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a09e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a09e6-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a09e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a09e6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09e6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a09e6-116">See also</span></span>

- [<span data-ttu-id="a09e6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a09e6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
