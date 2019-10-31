---
title: ICorDebugManagedCallback::EditAndContinueRemap, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 3fd1686eb268b9d4e347fe28e067a5321327dbd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137388"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="9c695-102">ICorDebugManagedCallback::EditAndContinueRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="9c695-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="9c695-103">Cette méthode est dépréciée.</span><span class="sxs-lookup"><span data-stu-id="9c695-103">This method has been deprecated.</span></span> <span data-ttu-id="9c695-104">Il informe le débogueur qu’un événement de remappage a été envoyé à l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="9c695-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c695-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c695-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9c695-106">Notes</span><span class="sxs-lookup"><span data-stu-id="9c695-106">Remarks</span></span>  
 <span data-ttu-id="9c695-107">La méthode `EditAndContinueRemap` est appelée lorsque l’exécution du code dans une ancienne version d’une fonction mise à jour a été tentée.</span><span class="sxs-lookup"><span data-stu-id="9c695-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="9c695-108">Le common language runtime appelle la méthode `EditAndContinueRemap` pour envoyer un événement de remappage à l’IDE.</span><span class="sxs-lookup"><span data-stu-id="9c695-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c695-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="9c695-109">Requirements</span></span>  
 <span data-ttu-id="9c695-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c695-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c695-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c695-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c695-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c695-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c695-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c695-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c695-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c695-114">See also</span></span>

- [<span data-ttu-id="9c695-115">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="9c695-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
