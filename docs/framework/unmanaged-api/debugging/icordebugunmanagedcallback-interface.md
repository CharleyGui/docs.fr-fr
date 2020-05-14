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
ms.openlocfilehash: dd5baa282d15d121b62b4dc4dd41bcf9ff393570
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395878"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="241db-102">ICorDebugUnmanagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="241db-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="241db-103">Fournit une notification des événements natifs qui ne sont pas directement liés au common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="241db-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="241db-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="241db-104">Methods</span></span>  
  
|<span data-ttu-id="241db-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="241db-105">Method</span></span>|<span data-ttu-id="241db-106">Description</span><span class="sxs-lookup"><span data-stu-id="241db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="241db-107">DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="241db-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="241db-108">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="241db-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="241db-109">Notes</span><span class="sxs-lookup"><span data-stu-id="241db-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="241db-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="241db-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="241db-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="241db-111">Requirements</span></span>  
 <span data-ttu-id="241db-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="241db-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="241db-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="241db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="241db-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="241db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="241db-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="241db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="241db-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="241db-116">See also</span></span>

- [<span data-ttu-id="241db-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="241db-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
