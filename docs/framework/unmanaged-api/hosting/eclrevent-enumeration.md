---
title: EClrEvent, énumération
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 3ecaebb9d943a3cdbb231307012b5dc3aaf000f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493385"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="b42f0-102">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="b42f0-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="b42f0-103">Décrit les événements common language runtime (CLR) pour lesquels l’hôte peut inscrire des rappels.</span><span class="sxs-lookup"><span data-stu-id="b42f0-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b42f0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="b42f0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b42f0-105">Members</span></span>  
  
|<span data-ttu-id="b42f0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b42f0-106">Member</span></span>|<span data-ttu-id="b42f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="b42f0-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="b42f0-108">Spécifie une erreur CLR irrécupérable.</span><span class="sxs-lookup"><span data-stu-id="b42f0-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="b42f0-109">Spécifie le déchargement d’un particulier <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="b42f0-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="b42f0-110">Spécifie qu’un message de l’Assistant Débogage managé (MDA) a été généré.</span><span class="sxs-lookup"><span data-stu-id="b42f0-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="b42f0-111">Spécifie qu’une erreur de dépassement de capacité de la pile s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b42f0-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b42f0-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="b42f0-112">Remarks</span></span>  
 <span data-ttu-id="b42f0-113">L’hôte peut enregistrer des rappels pour tous les types d’événements décrits par `EClrEvent` en appelant des méthodes de l’interface [ICLROnEventManager](iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b42f0-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="b42f0-114">L’hôte obtient un pointeur vers cette interface en appelant la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b42f0-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="b42f0-115">Les `Event_CLRDisabled` `Event_DomainUnload` événements et peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.</span><span class="sxs-lookup"><span data-stu-id="b42f0-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="b42f0-116">L' `Event_MDAFired` événement déclenche la création d’une instance [MDAInfo](mdainfo-structure.md) qui contient les détails du message de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="b42f0-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="b42f0-117">Pour plus d’informations sur les MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="b42f0-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42f0-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b42f0-118">Requirements</span></span>  
 <span data-ttu-id="b42f0-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b42f0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b42f0-120">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b42f0-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b42f0-121">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b42f0-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b42f0-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b42f0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42f0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b42f0-123">See also</span></span>

- [<span data-ttu-id="b42f0-124">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="b42f0-124">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="b42f0-125">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="b42f0-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b42f0-126">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="b42f0-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
