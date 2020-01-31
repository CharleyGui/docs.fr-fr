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
ms.openlocfilehash: 9b96c0a2eca543b9e01ccf92b271b1aa7003c5c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781949"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="d03fc-102">ICorDebugManagedCallback::DebuggerError, méthode</span><span class="sxs-lookup"><span data-stu-id="d03fc-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="d03fc-103">Notifie le débogueur qu’une erreur s’est produite lors de la tentative de gestion d’un événement à partir du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d03fc-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d03fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d03fc-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d03fc-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d03fc-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d03fc-106">dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel l’événement s’est produit.</span><span class="sxs-lookup"><span data-stu-id="d03fc-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="d03fc-107">dans Valeur HRESULT qui a été retournée par le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d03fc-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="d03fc-108">dans Entier qui spécifie l’erreur CLR.</span><span class="sxs-lookup"><span data-stu-id="d03fc-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d03fc-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d03fc-109">Remarks</span></span>  
 <span data-ttu-id="d03fc-110">Le processus peut être placé en mode de transfert, en fonction de la nature de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="d03fc-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="d03fc-111">Le rappel de `DebugError` indique que les services de débogage ont été désactivés en raison d’une erreur. les débogueurs doivent donc mettre le message d’erreur à la disposition de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d03fc-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="d03fc-112">[ICorDebugProcess :: GetId](icordebugprocess-getid-method.md) peut être appelée sans risque, mais toutes les autres méthodes, y compris [ICorDebug :: Terminate](icordebug-terminate-method.md), ne doivent pas être appelées.</span><span class="sxs-lookup"><span data-stu-id="d03fc-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="d03fc-113">Le débogueur doit utiliser des fonctionnalités de système d’exploitation pour terminer les processus.</span><span class="sxs-lookup"><span data-stu-id="d03fc-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d03fc-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d03fc-114">Requirements</span></span>  
 <span data-ttu-id="d03fc-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d03fc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d03fc-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d03fc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d03fc-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d03fc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d03fc-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d03fc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03fc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d03fc-119">See also</span></span>

- [<span data-ttu-id="d03fc-120">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d03fc-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
