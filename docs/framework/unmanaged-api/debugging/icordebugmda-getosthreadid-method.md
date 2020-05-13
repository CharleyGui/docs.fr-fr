---
title: ICorDebugMDA::GetOSThreadId, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: c7ab77e9316023a97d2eafe8bcccc2b45e240cd0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207821"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="fb25b-102">ICorDebugMDA::GetOSThreadId, méthode</span><span class="sxs-lookup"><span data-stu-id="fb25b-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="fb25b-103">Obtient l’identificateur de thread du système d’exploitation sur lequel l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](icordebugmda-interface.md) est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="fb25b-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb25b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb25b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb25b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb25b-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="fb25b-106">à Pointeur vers l’identificateur du thread du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="fb25b-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb25b-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="fb25b-107">Remarks</span></span>  
 <span data-ttu-id="fb25b-108">Le thread de système d’exploitation est utilisé à la place d’un ICorDebugThread pour tenir compte des situations dans lesquelles un Assistant Débogage managé est déclenché sur un thread natif ou sur un thread managé qui n’a pas encore entré du code managé.</span><span class="sxs-lookup"><span data-stu-id="fb25b-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb25b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fb25b-109">Requirements</span></span>  
 <span data-ttu-id="fb25b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb25b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb25b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb25b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb25b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb25b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb25b-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb25b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb25b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb25b-114">See also</span></span>

- [<span data-ttu-id="fb25b-115">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="fb25b-115">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="fb25b-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="fb25b-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
