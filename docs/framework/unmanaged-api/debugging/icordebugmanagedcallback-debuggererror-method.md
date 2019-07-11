---
title: ICorDebugManagedCallback::DebuggerError, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6abc4893ac99c5ce93a409a8120f090250be57c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759667"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="81870-102">ICorDebugManagedCallback::DebuggerError, méthode</span><span class="sxs-lookup"><span data-stu-id="81870-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="81870-103">Notifie le débogueur qu’une erreur s’est produite lors de la tentative gérer un événement dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="81870-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81870-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81870-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81870-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81870-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="81870-106">[in] Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel l’événement s’est produite.</span><span class="sxs-lookup"><span data-stu-id="81870-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="81870-107">[in] La valeur HRESULT qui a été retournée par le Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="81870-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="81870-108">[in] Entier qui spécifie l’erreur CLR.</span><span class="sxs-lookup"><span data-stu-id="81870-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81870-109">Notes</span><span class="sxs-lookup"><span data-stu-id="81870-109">Remarks</span></span>  
 <span data-ttu-id="81870-110">Le processus peut être placé en mode Pass-through, selon la nature de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="81870-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="81870-111">Le `DebugError` rappel indique que les services de débogage ont été désactivés en raison d’une erreur, donc les débogueurs doivent proposer le message d’erreur à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="81870-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="81870-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) sera sécurisé à l’appel, mais toutes les autres méthodes, y compris [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), ne doit pas être appelée.</span><span class="sxs-lookup"><span data-stu-id="81870-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="81870-113">Le débogueur doit utiliser les installations de système d’exploitation pour terminer les processus.</span><span class="sxs-lookup"><span data-stu-id="81870-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81870-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81870-114">Requirements</span></span>  
 <span data-ttu-id="81870-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81870-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81870-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81870-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81870-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81870-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81870-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81870-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81870-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81870-119">See also</span></span>

- [<span data-ttu-id="81870-120">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="81870-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
