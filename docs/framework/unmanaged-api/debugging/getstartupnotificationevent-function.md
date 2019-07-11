---
title: Fonction GetStartupNotificationEvent
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67f3ef57b4996eb4a956c596b76fb94b1bdfd7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738889"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="7e104-102">Fonction GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="7e104-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="7e104-103">Crée ou ouvre un gestionnaire d'événements qui sera signalé par un Common Language Runtime (CLR) qui est chargé dans le processus cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="7e104-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e104-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e104-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e104-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e104-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="7e104-106">[in] Identificateur du processus cible à partir duquel les notifications de démarrage du CLR sont reçues.</span><span class="sxs-lookup"><span data-stu-id="7e104-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="7e104-107">[out] Pointeur vers un handle qui sera signalé par un CLR au démarrage.</span><span class="sxs-lookup"><span data-stu-id="7e104-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e104-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7e104-108">Return Value</span></span>  
 <span data-ttu-id="7e104-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e104-109">S_OK</span></span>  
 <span data-ttu-id="7e104-110">Le handle de l'événement de notification de démarrage a été obtenu.</span><span class="sxs-lookup"><span data-stu-id="7e104-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="7e104-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7e104-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="7e104-112">`phStartupEvent` est null ou `debuggeePID` ne fait pas référence à un processus en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="7e104-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="7e104-113">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="7e104-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7e104-114">Impossible d'obtenir le handle de l'événement de notification de démarrage.</span><span class="sxs-lookup"><span data-stu-id="7e104-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e104-115">Notes</span><span class="sxs-lookup"><span data-stu-id="7e104-115">Remarks</span></span>  
 <span data-ttu-id="7e104-116">Sur le système d'exploitation Windows, `debuggeePID` est mappé à un identificateur de processus du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="7e104-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="7e104-117">L'événement est signalé avant l'exécution de code managé par le CLR ayant signalé l'événement.</span><span class="sxs-lookup"><span data-stu-id="7e104-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e104-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e104-118">Requirements</span></span>  
 <span data-ttu-id="7e104-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e104-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e104-120">**En-tête :** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="7e104-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7e104-121">**Bibliothèque :** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="7e104-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7e104-122">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7e104-122">**.NET Framework Versions:** 3.5 SP1</span></span>
