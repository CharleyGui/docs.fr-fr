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
ms.openlocfilehash: 97e06a2f20dcc2bb3815b98ba29ff230e37ff29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730160"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="5ce65-102">ICorDebugBreakpointEnum, interface</span><span class="sxs-lookup"><span data-stu-id="5ce65-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="5ce65-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="5ce65-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ce65-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5ce65-104">Methods</span></span>  
  
|<span data-ttu-id="5ce65-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5ce65-105">Method</span></span>|<span data-ttu-id="5ce65-106">Description</span><span class="sxs-lookup"><span data-stu-id="5ce65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ce65-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="5ce65-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="5ce65-108">Obtient le nombre d' `ICorDebugBreakpoint` instances spécifié à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="5ce65-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ce65-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ce65-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ce65-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5ce65-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce65-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ce65-111">Requirements</span></span>  

 <span data-ttu-id="5ce65-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ce65-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce65-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ce65-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ce65-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ce65-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ce65-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce65-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce65-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ce65-116">See also</span></span>

- [<span data-ttu-id="5ce65-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5ce65-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
