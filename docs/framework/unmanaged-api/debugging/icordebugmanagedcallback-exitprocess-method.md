---
title: ICorDebugManagedCallback::ExitProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 7a49bd6626518179c9b5ef008fca28d304537cc8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205263"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="73d65-102">ICorDebugManagedCallback::ExitProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="73d65-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="73d65-103">Notifie le débogueur qu’un processus s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="73d65-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73d65-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73d65-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73d65-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="73d65-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="73d65-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73d65-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="73d65-107">Remarks</span></span>  
 <span data-ttu-id="73d65-108">Vous ne pouvez pas continuer à partir d’un `ExitProcess` événement.</span><span class="sxs-lookup"><span data-stu-id="73d65-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="73d65-109">Cet événement peut se déclencher de manière asynchrone vers d’autres événements pendant que le processus semble être arrêté.</span><span class="sxs-lookup"><span data-stu-id="73d65-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="73d65-110">Cela peut se produire si le processus se termine alors qu’il est arrêté, généralement en raison d’une force externe.</span><span class="sxs-lookup"><span data-stu-id="73d65-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="73d65-111">Si le common language runtime (CLR) est déjà en cours de distribution d’un rappel managé, cet événement est retardé jusqu’à ce que le rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="73d65-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="73d65-112">L' `ExitProcess` événement est le seul événement de sortie/déchargement qui est garanti pour être appelé lors de l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="73d65-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73d65-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="73d65-113">Requirements</span></span>  
 <span data-ttu-id="73d65-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73d65-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d65-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73d65-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73d65-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73d65-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73d65-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d65-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d65-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73d65-118">See also</span></span>

- [<span data-ttu-id="73d65-119">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="73d65-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
