---
title: ICorDebugDataTarget, interface
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930822"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="b0361-102">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="b0361-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="b0361-103">Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="b0361-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0361-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b0361-104">Methods</span></span>  
  
|<span data-ttu-id="b0361-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b0361-105">Method</span></span>|<span data-ttu-id="b0361-106">Description</span><span class="sxs-lookup"><span data-stu-id="b0361-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0361-107">GetPlatform, méthode</span><span class="sxs-lookup"><span data-stu-id="b0361-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="b0361-108">Fournit des informations sur la plateforme, y compris l’architecture du processeur et le système d’exploitation, sur lesquelles le processus cible est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b0361-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="b0361-109">ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="b0361-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="b0361-110">Obtient un bloc de mémoire contiguë commençant à l’adresse spécifiée et le retourne dans la mémoire tampon fournie.</span><span class="sxs-lookup"><span data-stu-id="b0361-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="b0361-111">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="b0361-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="b0361-112">Demande le contexte de thread actuel pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="b0361-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0361-113">Notes</span><span class="sxs-lookup"><span data-stu-id="b0361-113">Remarks</span></span>  
 <span data-ttu-id="b0361-114">`ICorDebugDataTarget`et ses méthodes présentent les caractéristiques suivantes:</span><span class="sxs-lookup"><span data-stu-id="b0361-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="b0361-115">Les services de débogage appellent des méthodes sur cette interface pour accéder à la mémoire et à d’autres données dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="b0361-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="b0361-116">Le client du débogueur doit implémenter cette interface de manière appropriée pour la cible particulière (par exemple, un processus en direct ou un vidage de mémoire).</span><span class="sxs-lookup"><span data-stu-id="b0361-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="b0361-117">Les `ICorDebugDataTarget` méthodes ne peuvent être appelées qu’à partir de méthodes implémentées dans d’autres `ICorDebug*` interfaces.</span><span class="sxs-lookup"><span data-stu-id="b0361-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="b0361-118">Cela permet de s’assurer que le client du débogueur contrôle le thread sur lequel il est appelé, et à quel moment.</span><span class="sxs-lookup"><span data-stu-id="b0361-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="b0361-119">L' `ICorDebugDataTarget` implémentation doit toujours retourner des informations à jour sur la cible.</span><span class="sxs-lookup"><span data-stu-id="b0361-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="b0361-120">Le processus cible doit être arrêté et ne pas être modifié de quelque `ICorDebug*` manière que ce soit `ICorDebugDataTarget` pendant que les interfaces (et par conséquent les méthodes) sont appelées.</span><span class="sxs-lookup"><span data-stu-id="b0361-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="b0361-121">Si la cible est un processus en direct et que son état change, la méthode [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) doit être à nouveau appelée pour fournir une instance de remplacement de ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="b0361-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0361-122">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="b0361-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0361-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b0361-123">Requirements</span></span>  
 <span data-ttu-id="b0361-124">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0361-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0361-125">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0361-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0361-126">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0361-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0361-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0361-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0361-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0361-128">See also</span></span>

- [<span data-ttu-id="b0361-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b0361-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b0361-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="b0361-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
