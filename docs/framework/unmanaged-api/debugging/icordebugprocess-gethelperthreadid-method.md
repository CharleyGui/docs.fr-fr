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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad62b267eb0c49ff8fbefeb45b523c21edc705fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766039"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="4d8a6-102">ICorDebugProcess::GetHelperThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="4d8a6-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="4d8a6-103">Obtient l’ID de thread de système d’exploitation (se) du thread d’assistance interne du débogueur.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d8a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d8a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d8a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4d8a6-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="4d8a6-106">[out] Un pointeur vers le système d’exploitation ID de thread du thread d’assistance interne du débogueur.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d8a6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4d8a6-107">Remarks</span></span>  
 <span data-ttu-id="4d8a6-108">Pendant le débogage managé et, il incombe du débogueur pour vous assurer que le thread avec l’ID spécifié continue de s’exécuter s’il rencontre un point d’arrêt placé par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="4d8a6-109">Un débogueur peut souhaiter également masquer ce thread à partir de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="4d8a6-110">Si aucun thread d’assistance n’existe encore, dans le processus le `GetHelperThreadID` méthode retourne la valeur zéro dans \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="4d8a6-111">Vous ne pouvez pas mettre en cache l’ID de thread du thread d’assistance, car il peut changer au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="4d8a6-112">Vous devez redemander l’ID de thread à chaque événement d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="4d8a6-113">L’ID du thread d’assistance du débogueur est correct sur chaque non managé [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) événement, ce qui permet un débogueur de déterminer l’ID de son thread d’assistance et masquez-la par rapport à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="4d8a6-114">Un thread qui est identifié comme un thread d’assistance pendant une fonction non managée `ICorDebugManagedCallback::CreateThread` événement n’est jamais exécuté le code utilisateur managé.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d8a6-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4d8a6-115">Requirements</span></span>  
 <span data-ttu-id="4d8a6-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d8a6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d8a6-117">**En-tête :** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="4d8a6-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="4d8a6-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d8a6-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="4d8a6-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d8a6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d8a6-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d8a6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
