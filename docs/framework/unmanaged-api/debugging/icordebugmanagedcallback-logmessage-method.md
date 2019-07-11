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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14b10b94f66a6b5434befeac1cd9562cb8a0f27f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761554"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="5b3de-102">ICorDebugManagedCallback::LogMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="5b3de-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="5b3de-103">Notifie le débogueur qu’un thread du common language runtime (CLR) géré a appelé une méthode la <xref:System.Diagnostics.EventLog> classe journaliser un événement.</span><span class="sxs-lookup"><span data-stu-id="5b3de-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b3de-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b3de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b3de-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5b3de-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a consigné l’événement.</span><span class="sxs-lookup"><span data-stu-id="5b3de-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5b3de-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="5b3de-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="5b3de-108">[in] Une valeur de la [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) énumération qui indique le niveau de gravité du message descriptif qui a été écrite dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="5b3de-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="5b3de-109">[in] Un pointeur vers le nom du commutateur de suivi.</span><span class="sxs-lookup"><span data-stu-id="5b3de-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="5b3de-110">[in] Pointeur vers le message qui a été écrite dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="5b3de-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b3de-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5b3de-111">Requirements</span></span>  
 <span data-ttu-id="5b3de-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b3de-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b3de-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b3de-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b3de-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b3de-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b3de-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b3de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3de-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b3de-116">See also</span></span>

- [<span data-ttu-id="5b3de-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5b3de-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
