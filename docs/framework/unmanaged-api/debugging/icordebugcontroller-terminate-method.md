---
title: ICorDebugController::Terminate, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: eade3fd5d946c44ae4a77c571f762709de3cef40
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976562"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="6aea5-102">ICorDebugController::Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="6aea5-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="6aea5-103">Termine le processus avec le code de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="6aea5-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6aea5-104">Cette méthode est un wrapper pour la fonction `TerminateProcess` Win32.</span><span class="sxs-lookup"><span data-stu-id="6aea5-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="6aea5-105">Par conséquent `Terminate` , utilise le code de sortie de la même façon que `TerminateProcess` la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="6aea5-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aea5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6aea5-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aea5-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6aea5-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="6aea5-108">dans Valeur numérique qui est le code de sortie.</span><span class="sxs-lookup"><span data-stu-id="6aea5-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="6aea5-109">Les valeurs numériques valides sont définies dans Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="6aea5-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aea5-110">Notes </span><span class="sxs-lookup"><span data-stu-id="6aea5-110">Remarks</span></span>  
 <span data-ttu-id="6aea5-111">Si le processus est arrêté lorsque `Terminate` est appelé, le processus doit être poursuivi à l’aide de la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) afin que le débogueur reçoive la confirmation de l’arrêt par le biais du rappel [ICorDebugManagedCallback :: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) ou [ICorDebugManagedCallback :: ExitAppDomain,](icordebugmanagedcallback-exitappdomain-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6aea5-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6aea5-112">Cette méthode n’est pas implémentée par un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6aea5-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="6aea5-113">Autrement dit, il n’est pas implémenté au <xref:System.AppDomain> niveau.</span><span class="sxs-lookup"><span data-stu-id="6aea5-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aea5-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6aea5-114">Requirements</span></span>  
 <span data-ttu-id="6aea5-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aea5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aea5-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6aea5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aea5-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aea5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aea5-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aea5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aea5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aea5-119">See also</span></span>
