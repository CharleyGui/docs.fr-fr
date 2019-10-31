---
title: ICorDebugManagedCallback::LogMessage, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: d95662167dbc8fcda049fb6a7b3e6ff1dfb6e736
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130706"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="17391-102">ICorDebugManagedCallback::LogMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="17391-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="17391-103">Notifie le débogueur qu’un thread managé common language runtime (CLR) a appelé une méthode dans la classe <xref:System.Diagnostics.EventLog> pour enregistrer un événement.</span><span class="sxs-lookup"><span data-stu-id="17391-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17391-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17391-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17391-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17391-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="17391-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a enregistré l’événement.</span><span class="sxs-lookup"><span data-stu-id="17391-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="17391-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="17391-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="17391-108">dans Valeur de l’énumération [LoggingLevelEnum,](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) qui indique le niveau de gravité du message descriptif écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="17391-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="17391-109">dans Pointeur vers le nom du commutateur de traçage.</span><span class="sxs-lookup"><span data-stu-id="17391-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="17391-110">dans Pointeur vers le message qui a été écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="17391-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17391-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="17391-111">Requirements</span></span>  
 <span data-ttu-id="17391-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17391-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17391-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17391-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17391-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17391-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17391-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17391-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17391-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17391-116">See also</span></span>

- [<span data-ttu-id="17391-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="17391-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
