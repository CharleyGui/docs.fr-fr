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
ms.openlocfilehash: cf9c9d11c4725908fcf7ff4a0c91882b70a80190
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723374"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="2b122-102">ICorDebug::Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="2b122-102">ICorDebug::Terminate Method</span></span>

<span data-ttu-id="2b122-103">Met fin à l' `ICorDebug` objet.</span><span class="sxs-lookup"><span data-stu-id="2b122-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b122-104">`Terminate` ne doit pas être appelé tant qu’un rappel [ICorDebugManagedCallback :: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) n’a pas été reçu pour tous les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="2b122-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b122-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b122-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2b122-106">Notes</span><span class="sxs-lookup"><span data-stu-id="2b122-106">Remarks</span></span>  

 <span data-ttu-id="2b122-107">`Terminate` doit être appelé lorsque l' `ICorDebug` objet n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2b122-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b122-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2b122-108">Requirements</span></span>  

 <span data-ttu-id="2b122-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b122-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b122-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b122-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b122-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b122-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b122-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b122-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b122-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b122-113">See also</span></span>

- [<span data-ttu-id="2b122-114">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="2b122-114">ICorDebug Interface</span></span>](icordebug-interface.md)
