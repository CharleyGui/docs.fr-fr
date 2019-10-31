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
ms.openlocfilehash: 9ecfb551b55551e5f6cc7e7e9ffb55e5a96259ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141519"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="63fb0-102">WAIT_OPTION, énumération</span><span class="sxs-lookup"><span data-stu-id="63fb0-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="63fb0-103">Contient des valeurs qui indiquent l’action qu’un hôte doit effectuer si une opération demandée par le common language runtime (CLR) se bloque.</span><span class="sxs-lookup"><span data-stu-id="63fb0-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63fb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63fb0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="63fb0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="63fb0-105">Members</span></span>  
  
|<span data-ttu-id="63fb0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="63fb0-106">Member</span></span>|<span data-ttu-id="63fb0-107">Description</span><span class="sxs-lookup"><span data-stu-id="63fb0-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="63fb0-108">Avertit l’hôte que la tâche doit être réutilisée si le CLR appelle la méthode [IHostTask :: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="63fb0-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="63fb0-109">Indique à l’hôte qu’il doit pomper les messages sur le thread de système d’exploitation actuel si le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="63fb0-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="63fb0-110">Le runtime spécifie cette valeur uniquement sur un thread <xref:System.Threading.ApartmentState.STA>.</span><span class="sxs-lookup"><span data-stu-id="63fb0-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="63fb0-111">Indique à l’hôte que la demande de synchronisation spécifiée ne peut pas être interrompue par un hôte.</span><span class="sxs-lookup"><span data-stu-id="63fb0-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="63fb0-112">Autrement dit, l’hôte ne peut pas retourner `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="63fb0-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63fb0-113">Notes</span><span class="sxs-lookup"><span data-stu-id="63fb0-113">Remarks</span></span>  
 <span data-ttu-id="63fb0-114">Les méthodes [IHostTaskManager :: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) et [IHostTaskManager :: SwitchToTask,](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) prennent toutes deux un paramètre de ce type.</span><span class="sxs-lookup"><span data-stu-id="63fb0-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63fb0-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="63fb0-115">Requirements</span></span>  
 <span data-ttu-id="63fb0-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63fb0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63fb0-117">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63fb0-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63fb0-118">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63fb0-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63fb0-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63fb0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63fb0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63fb0-120">See also</span></span>

- [<span data-ttu-id="63fb0-121">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="63fb0-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
