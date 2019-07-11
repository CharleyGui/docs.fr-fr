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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755459"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="139ba-102">ICorDebugProcess::IsOSSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="139ba-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="139ba-103">Obtient une valeur qui indique si le thread spécifié a été interrompu suite à l’arrêt de ce processus de débogueur.</span><span class="sxs-lookup"><span data-stu-id="139ba-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="139ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="139ba-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="139ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="139ba-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="139ba-106">[in] L’ID du thread en question.</span><span class="sxs-lookup"><span data-stu-id="139ba-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="139ba-107">[out] Un pointeur vers une valeur booléenne qui est `true` si le thread spécifié a été suspendue ; sinon \*`pbSuspended` est `false`.</span><span class="sxs-lookup"><span data-stu-id="139ba-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="139ba-108">Notes</span><span class="sxs-lookup"><span data-stu-id="139ba-108">Remarks</span></span>  
 <span data-ttu-id="139ba-109">Quand le thread spécifié a été suspendu suite à l’arrêt de ce processus de débogueur, le compteur de suspension Win32 du thread spécifié est incrémenté d’un.</span><span class="sxs-lookup"><span data-stu-id="139ba-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="139ba-110">L’interface utilisateur (IU) du débogueur souhaiterez peut-être prendre en compte ces informations si elle affiche le système d’exploitation (OS) compteur de suspension du thread à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="139ba-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="139ba-111">Le `IsOSSuspended` méthode est pertinent uniquement dans le contexte de débogage non managé.</span><span class="sxs-lookup"><span data-stu-id="139ba-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="139ba-112">Pendant le débogage managé, les threads sont coopération suspendu plutôt que du système d’exploitation suspendu.</span><span class="sxs-lookup"><span data-stu-id="139ba-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="139ba-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="139ba-113">Requirements</span></span>  
 <span data-ttu-id="139ba-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="139ba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="139ba-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="139ba-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="139ba-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="139ba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="139ba-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="139ba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
