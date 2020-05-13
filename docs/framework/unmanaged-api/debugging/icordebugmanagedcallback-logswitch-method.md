---
title: ICorDebugManagedCallback::LogSwitch, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: f095bc0272e0e6f16467b9758d5e392d371139dd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212683"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="3df7a-102">ICorDebugManagedCallback::LogSwitch, méthode</span><span class="sxs-lookup"><span data-stu-id="3df7a-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="3df7a-103">Notifie le débogueur qu’un thread managé common language runtime (CLR) a appelé une méthode dans la <xref:System.Diagnostics.Switch> classe pour créer, modifier ou supprimer un commutateur de débogage/traçage.</span><span class="sxs-lookup"><span data-stu-id="3df7a-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3df7a-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df7a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3df7a-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="3df7a-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a créé, modifié ou supprimé un commutateur de débogage/traçage.</span><span class="sxs-lookup"><span data-stu-id="3df7a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="3df7a-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="3df7a-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="3df7a-108">dans Valeur qui indique le niveau de gravité du message descriptif qui a été écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="3df7a-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="3df7a-109">dans Valeur de l’énumération [LogSwitchCallReason,](logswitchcallreason-enumeration.md) qui indique l’opération effectuée sur le commutateur de débogage/traçage.</span><span class="sxs-lookup"><span data-stu-id="3df7a-109">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="3df7a-110">dans Pointeur vers le nom du commutateur de débogage/traçage.</span><span class="sxs-lookup"><span data-stu-id="3df7a-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="3df7a-111">dans Pointeur vers le nom du parent du commutateur de débogage/traçage.</span><span class="sxs-lookup"><span data-stu-id="3df7a-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df7a-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3df7a-112">Requirements</span></span>  
 <span data-ttu-id="3df7a-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df7a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df7a-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3df7a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3df7a-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3df7a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3df7a-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df7a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df7a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3df7a-117">See also</span></span>

- [<span data-ttu-id="3df7a-118">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3df7a-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
