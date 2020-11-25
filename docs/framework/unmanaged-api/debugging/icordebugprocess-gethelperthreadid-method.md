---
title: ICorDebugProcess::GetHelperThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: 77cc658e28c7a69d8c4aeeed2f3e7ea40f0d2af6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724570"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="508e8-102">ICorDebugProcess::GetHelperThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="508e8-102">ICorDebugProcess::GetHelperThreadID Method</span></span>

<span data-ttu-id="508e8-103">Obtient l’ID de thread (se) du système d’exploitation du thread d’assistance interne du débogueur.</span><span class="sxs-lookup"><span data-stu-id="508e8-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="508e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="508e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="508e8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="508e8-105">Parameters</span></span>  

 `pThreadID`  
 <span data-ttu-id="508e8-106">à Pointeur vers l’ID de thread de système d’exploitation du thread d’assistance interne du débogueur.</span><span class="sxs-lookup"><span data-stu-id="508e8-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="508e8-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="508e8-107">Remarks</span></span>  

 <span data-ttu-id="508e8-108">Lors du débogage managé et non managé, il incombe au débogueur de s’assurer que le thread avec l’ID spécifié reste en cours d’exécution s’il atteint un point d’arrêt placé par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="508e8-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="508e8-109">Un débogueur peut également souhaiter masquer ce thread à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="508e8-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="508e8-110">Si aucun thread d’assistance n’existe encore dans le processus, la `GetHelperThreadID` méthode retourne zéro dans \* `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="508e8-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="508e8-111">Vous ne pouvez pas mettre en cache l’ID de thread du thread d’assistance, car il peut changer au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="508e8-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="508e8-112">Vous devez relancer l’interrogation de l’ID de thread à chaque événement d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="508e8-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="508e8-113">L’ID de thread du thread d’assistance du débogueur est correct sur chaque événement [ICorDebugManagedCallback :: CreateThread](icordebugmanagedcallback-createthread-method.md) non managé, ce qui permet à un débogueur de déterminer l’ID de thread de son thread d’assistance et de le masquer à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="508e8-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="508e8-114">Un thread identifié comme un thread d’assistance pendant un événement non managé `ICorDebugManagedCallback::CreateThread` n’exécutera jamais le code utilisateur managé.</span><span class="sxs-lookup"><span data-stu-id="508e8-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="508e8-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="508e8-115">Requirements</span></span>  

 <span data-ttu-id="508e8-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508e8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508e8-117">**En-tête :** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="508e8-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="508e8-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="508e8-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="508e8-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="508e8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="508e8-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="508e8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
