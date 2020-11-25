---
title: ICorDebugProcess::IsOSSuspended, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: fffa61d8e406162251b0934a9846e5a813422798
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724583"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="80316-102">ICorDebugProcess::IsOSSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="80316-102">ICorDebugProcess::IsOSSuspended Method</span></span>

<span data-ttu-id="80316-103">Obtient une valeur qui indique si le thread spécifié a été suspendu suite à l’arrêt de ce processus par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="80316-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80316-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80316-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80316-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="80316-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="80316-106">dans ID du thread en question.</span><span class="sxs-lookup"><span data-stu-id="80316-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="80316-107">à Pointeur vers une valeur booléenne qui est `true` si le thread spécifié a été interrompu ; sinon, \* `pbSuspended` est `false` .</span><span class="sxs-lookup"><span data-stu-id="80316-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80316-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="80316-108">Remarks</span></span>  

 <span data-ttu-id="80316-109">Lorsque le thread spécifié a été suspendu à la suite de l’arrêt de ce processus par le débogueur, le nombre de suspensions Win32 du thread spécifié est incrémenté d’une unité.</span><span class="sxs-lookup"><span data-stu-id="80316-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="80316-110">L’interface utilisateur du débogueur peut prendre en compte ces informations si le nombre de suspensions du système d’exploitation du thread est affiché pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="80316-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="80316-111">La `IsOSSuspended` méthode est logique uniquement dans le contexte du débogage non managé.</span><span class="sxs-lookup"><span data-stu-id="80316-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="80316-112">Pendant le débogage managé, les threads sont suspendus de manière coopérative plutôt que d’être suspendus par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="80316-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80316-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="80316-113">Requirements</span></span>  

 <span data-ttu-id="80316-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80316-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80316-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80316-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80316-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80316-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80316-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80316-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
