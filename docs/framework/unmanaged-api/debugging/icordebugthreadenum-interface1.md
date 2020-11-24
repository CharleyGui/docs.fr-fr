---
title: ICorDebugThreadEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: ca7668f23671721477c561774bab03279c4c18c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678556"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="4383b-102">ICorDebugThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="4383b-102">ICorDebugThreadEnum Interface</span></span>

<span data-ttu-id="4383b-103">Implémente les méthodes ICorDebugEnum et énumère les tableaux ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="4383b-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4383b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4383b-104">Methods</span></span>  
  
|<span data-ttu-id="4383b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4383b-105">Method</span></span>|<span data-ttu-id="4383b-106">Description</span><span class="sxs-lookup"><span data-stu-id="4383b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4383b-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="4383b-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="4383b-108">Obtient le nombre d' `ICorDebugThread` instances spécifié à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="4383b-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4383b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4383b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4383b-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4383b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4383b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4383b-111">Requirements</span></span>  

 <span data-ttu-id="4383b-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4383b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4383b-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4383b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4383b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4383b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4383b-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4383b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4383b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4383b-116">See also</span></span>

- [<span data-ttu-id="4383b-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4383b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
