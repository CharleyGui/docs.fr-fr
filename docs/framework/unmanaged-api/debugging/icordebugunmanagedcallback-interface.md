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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a34454e7e007b4eba557c712cb824362aa5047c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952974"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="5425d-102">ICorDebugUnmanagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5425d-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="5425d-103">Fournit une notification des événements natifs qui ne sont pas directement liés au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5425d-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5425d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5425d-104">Methods</span></span>  
  
|<span data-ttu-id="5425d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5425d-105">Method</span></span>|<span data-ttu-id="5425d-106">Description</span><span class="sxs-lookup"><span data-stu-id="5425d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5425d-107">DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="5425d-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="5425d-108">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="5425d-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5425d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="5425d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5425d-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5425d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5425d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5425d-111">Requirements</span></span>  
 <span data-ttu-id="5425d-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5425d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5425d-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5425d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5425d-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5425d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5425d-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5425d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5425d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5425d-116">See also</span></span>

- [<span data-ttu-id="5425d-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5425d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
