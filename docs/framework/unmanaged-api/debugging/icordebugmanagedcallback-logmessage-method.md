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
ms.openlocfilehash: 92b2a7f7f1dd98f0d847119a6431e3816c16d5da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679570"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="086e8-102">ICorDebugManagedCallback::LogMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="086e8-102">ICorDebugManagedCallback::LogMessage Method</span></span>

<span data-ttu-id="086e8-103">Notifie le débogueur qu’un thread managé common language runtime (CLR) a appelé une méthode dans la <xref:System.Diagnostics.EventLog> classe pour enregistrer un événement.</span><span class="sxs-lookup"><span data-stu-id="086e8-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="086e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="086e8-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="086e8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="086e8-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="086e8-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a enregistré l’événement.</span><span class="sxs-lookup"><span data-stu-id="086e8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="086e8-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="086e8-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="086e8-108">dans Valeur de l’énumération [LoggingLevelEnum,](logginglevelenum-enumeration.md) qui indique le niveau de gravité du message descriptif écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="086e8-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="086e8-109">dans Pointeur vers le nom du commutateur de traçage.</span><span class="sxs-lookup"><span data-stu-id="086e8-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="086e8-110">dans Pointeur vers le message qui a été écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="086e8-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="086e8-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="086e8-111">Requirements</span></span>  

 <span data-ttu-id="086e8-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="086e8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="086e8-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="086e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="086e8-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="086e8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="086e8-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="086e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="086e8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="086e8-116">See also</span></span>

- [<span data-ttu-id="086e8-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="086e8-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
