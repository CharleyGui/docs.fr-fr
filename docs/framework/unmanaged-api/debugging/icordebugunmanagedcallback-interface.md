---
title: ICorDebugUnmanagedCallback, interface
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: fdd2fee11e9353c3aa3faee2b137597e4ba47801
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791179"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="843dd-102">ICorDebugUnmanagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="843dd-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="843dd-103">Fournit une notification des événements natifs qui ne sont pas directement liés au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="843dd-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="843dd-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="843dd-104">Methods</span></span>  
  
|<span data-ttu-id="843dd-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="843dd-105">Method</span></span>|<span data-ttu-id="843dd-106">Description</span><span class="sxs-lookup"><span data-stu-id="843dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="843dd-107">DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="843dd-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="843dd-108">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="843dd-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="843dd-109">Notes</span><span class="sxs-lookup"><span data-stu-id="843dd-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="843dd-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="843dd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="843dd-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="843dd-111">Requirements</span></span>  
 <span data-ttu-id="843dd-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="843dd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="843dd-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="843dd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="843dd-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="843dd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="843dd-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="843dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843dd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="843dd-116">See also</span></span>

- [<span data-ttu-id="843dd-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="843dd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
