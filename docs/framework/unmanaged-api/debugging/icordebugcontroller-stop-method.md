---
title: ICorDebugController::Stop, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: 11cc6e4108a2064a8a9fcefa760bf3c3411d63fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679856"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="9fd5a-102">ICorDebugController::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="9fd5a-102">ICorDebugController::Stop Method</span></span>

<span data-ttu-id="9fd5a-103">Exécute un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fd5a-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fd5a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fd5a-105">Parameters</span></span>  

 `dwTimeoutIgnored`  
 <span data-ttu-id="9fd5a-106">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fd5a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9fd5a-107">Remarks</span></span>  

 <span data-ttu-id="9fd5a-108">`Stop` exécute un arrêt coopératif sur tous les threads exécutant du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="9fd5a-109">Pendant une session de débogage managée uniquement, les threads non managés peuvent continuer à s’exécuter (mais ils seront bloqués lors de la tentative d’appel de code managé).</span><span class="sxs-lookup"><span data-stu-id="9fd5a-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="9fd5a-110">Pendant une session de débogage d’interopérabilité, les threads non managés sont également arrêtés.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="9fd5a-111">La `dwTimeoutIgnored` valeur est actuellement ignorée et traitée comme INfinie (-1).</span><span class="sxs-lookup"><span data-stu-id="9fd5a-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="9fd5a-112">Si l’arrêt coopératif échoue en raison d’un blocage, tous les threads sont suspendus et E_TIMEOUT est retourné.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fd5a-113">`Stop` est la seule méthode synchrone de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="9fd5a-114">Lorsque `Stop` retourne S_OK, le processus est arrêté.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="9fd5a-115">Aucun rappel n’est fourni pour notifier les écouteurs de l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="9fd5a-116">Le débogueur doit appeler [ICorDebugController :: continue](icordebugcontroller-continue-method.md) pour permettre au processus de reprendre.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-116">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="9fd5a-117">Le débogueur gère un compteur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="9fd5a-118">Lorsque le compteur atteint zéro, le contrôleur reprend.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="9fd5a-119">Chaque appel à `Stop` ou à chaque rappel distribué incrémente le compteur.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="9fd5a-120">Chaque appel à `ICorDebugController::Continue` décrémente le compteur.</span><span class="sxs-lookup"><span data-stu-id="9fd5a-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fd5a-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9fd5a-121">Requirements</span></span>  

 <span data-ttu-id="9fd5a-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fd5a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fd5a-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fd5a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fd5a-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fd5a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fd5a-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fd5a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd5a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fd5a-126">See also</span></span>
