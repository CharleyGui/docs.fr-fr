---
title: LoggingLevelEnum, énumération
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 62ea982f30a6a73648d9bf36722c0b5a49a68896
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420745"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="65b23-102">LoggingLevelEnum, énumération</span><span class="sxs-lookup"><span data-stu-id="65b23-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="65b23-103">Indique le niveau de gravité d'un message de description qui est écrit dans le journal des événements quand un thread managé consigne un événement.</span><span class="sxs-lookup"><span data-stu-id="65b23-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65b23-104">Syntax</span></span>  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="65b23-105">Membres</span><span class="sxs-lookup"><span data-stu-id="65b23-105">Members</span></span>  
  
|<span data-ttu-id="65b23-106">Membre</span><span class="sxs-lookup"><span data-stu-id="65b23-106">Member</span></span>|<span data-ttu-id="65b23-107">Description</span><span class="sxs-lookup"><span data-stu-id="65b23-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="65b23-108">Le message est un niveau de trace 0.</span><span class="sxs-lookup"><span data-stu-id="65b23-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="65b23-109">Le message est un niveau de trace 1.</span><span class="sxs-lookup"><span data-stu-id="65b23-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="65b23-110">Le message est un niveau de trace 2.</span><span class="sxs-lookup"><span data-stu-id="65b23-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="65b23-111">Le message est un niveau de trace 3.</span><span class="sxs-lookup"><span data-stu-id="65b23-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="65b23-112">Le message est un niveau de trace 4.</span><span class="sxs-lookup"><span data-stu-id="65b23-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="65b23-113">Le message est un niveau d’État 0.</span><span class="sxs-lookup"><span data-stu-id="65b23-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="65b23-114">Le message est un niveau d’État 1.</span><span class="sxs-lookup"><span data-stu-id="65b23-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="65b23-115">Le message est un niveau d’État 2.</span><span class="sxs-lookup"><span data-stu-id="65b23-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="65b23-116">Le message est au niveau d’État 3.</span><span class="sxs-lookup"><span data-stu-id="65b23-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="65b23-117">Le message a le niveau d’État 4.</span><span class="sxs-lookup"><span data-stu-id="65b23-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="65b23-118">Le message est un niveau d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="65b23-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="65b23-119">Le message est un niveau d’erreur.</span><span class="sxs-lookup"><span data-stu-id="65b23-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="65b23-120">Le message est un niveau de panique.</span><span class="sxs-lookup"><span data-stu-id="65b23-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65b23-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="65b23-121">Remarks</span></span>  
 <span data-ttu-id="65b23-122">Le common language runtime (CLR) appelle la méthode [ICorDebugManagedCallback :: LogMessage](icordebugmanagedcallback-logmessage-method.md) pour notifier au débogueur qu’un thread managé a consigné un événement.</span><span class="sxs-lookup"><span data-stu-id="65b23-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="65b23-123">Le CLR passe une valeur de l' `LoggingLevelEnum` énumération pour indiquer le niveau de gravité du message que le thread managé a écrit dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="65b23-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b23-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="65b23-124">Requirements</span></span>  
 <span data-ttu-id="65b23-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b23-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b23-126">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65b23-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65b23-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65b23-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65b23-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b23-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b23-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65b23-129">See also</span></span>

- <xref:System.Diagnostics.EventLog>
- [<span data-ttu-id="65b23-130">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="65b23-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
