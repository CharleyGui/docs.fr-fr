---
title: ICorDebug::Terminate, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 78838e9002cb3f5263395af9de255c54de47b6ae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134018"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="af5fc-102">ICorDebug::Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="af5fc-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="af5fc-103">Met fin à l’objet `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="af5fc-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af5fc-104">`Terminate` ne doit pas être appelée tant qu’un rappel [ICorDebugManagedCallback :: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) n’a pas été reçu pour tous les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="af5fc-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af5fc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af5fc-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="af5fc-106">Notes</span><span class="sxs-lookup"><span data-stu-id="af5fc-106">Remarks</span></span>  
 <span data-ttu-id="af5fc-107">`Terminate` doit être appelée lorsque l’objet `ICorDebug` n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="af5fc-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af5fc-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="af5fc-108">Requirements</span></span>  
 <span data-ttu-id="af5fc-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af5fc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af5fc-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af5fc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af5fc-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af5fc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af5fc-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af5fc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5fc-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af5fc-113">See also</span></span>

- [<span data-ttu-id="af5fc-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="af5fc-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
