---
title: WAIT_OPTION, énumération
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 2f83bc5b114b746958f936c311efa823d88441d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503885"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="7efdf-102">WAIT_OPTION, énumération</span><span class="sxs-lookup"><span data-stu-id="7efdf-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="7efdf-103">Contient des valeurs qui indiquent l’action qu’un hôte doit effectuer si une opération demandée par le common language runtime (CLR) se bloque.</span><span class="sxs-lookup"><span data-stu-id="7efdf-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7efdf-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="7efdf-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7efdf-105">Members</span></span>  
  
|<span data-ttu-id="7efdf-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7efdf-106">Member</span></span>|<span data-ttu-id="7efdf-107">Description</span><span class="sxs-lookup"><span data-stu-id="7efdf-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="7efdf-108">Avertit l’hôte que la tâche doit être réutilisée si le CLR appelle la méthode [IHostTask :: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7efdf-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="7efdf-109">Indique à l’hôte qu’il doit pomper les messages sur le thread de système d’exploitation actuel si le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="7efdf-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="7efdf-110">Le runtime spécifie cette valeur uniquement sur un <xref:System.Threading.ApartmentState.STA> thread.</span><span class="sxs-lookup"><span data-stu-id="7efdf-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="7efdf-111">Indique à l’hôte que la demande de synchronisation spécifiée ne peut pas être interrompue par un hôte.</span><span class="sxs-lookup"><span data-stu-id="7efdf-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="7efdf-112">Autrement dit, l’hôte ne peut pas retourner `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="7efdf-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7efdf-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="7efdf-113">Remarks</span></span>  
 <span data-ttu-id="7efdf-114">Les méthodes [IHostTaskManager :: Sleep](ihosttaskmanager-sleep-method.md) et [IHostTaskManager :: SwitchToTask,](ihosttaskmanager-switchtotask-method.md) prennent toutes deux un paramètre de ce type.</span><span class="sxs-lookup"><span data-stu-id="7efdf-114">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7efdf-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7efdf-115">Requirements</span></span>  
 <span data-ttu-id="7efdf-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7efdf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7efdf-117">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7efdf-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7efdf-118">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7efdf-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7efdf-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7efdf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efdf-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7efdf-120">See also</span></span>

- [<span data-ttu-id="7efdf-121">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="7efdf-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
