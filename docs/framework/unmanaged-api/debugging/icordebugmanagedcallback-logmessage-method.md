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
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788365"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="7aa6f-102">ICorDebugManagedCallback::LogMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="7aa6f-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="7aa6f-103">Notifie le débogueur qu’un thread managé common language runtime (CLR) a appelé une méthode dans la classe <xref:System.Diagnostics.EventLog> pour enregistrer un événement.</span><span class="sxs-lookup"><span data-stu-id="7aa6f-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aa6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aa6f-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aa6f-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7aa6f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7aa6f-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a enregistré l’événement.</span><span class="sxs-lookup"><span data-stu-id="7aa6f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="7aa6f-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="7aa6f-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="7aa6f-108">dans Valeur de l’énumération [LoggingLevelEnum,](logginglevelenum-enumeration.md) qui indique le niveau de gravité du message descriptif écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7aa6f-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="7aa6f-109">dans Pointeur vers le nom du commutateur de traçage.</span><span class="sxs-lookup"><span data-stu-id="7aa6f-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="7aa6f-110">dans Pointeur vers le message qui a été écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="7aa6f-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aa6f-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7aa6f-111">Requirements</span></span>  
 <span data-ttu-id="7aa6f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aa6f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aa6f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7aa6f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aa6f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aa6f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aa6f-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aa6f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aa6f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aa6f-116">See also</span></span>

- [<span data-ttu-id="7aa6f-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7aa6f-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
