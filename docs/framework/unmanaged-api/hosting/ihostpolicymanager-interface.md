---
title: IHostPolicyManager, interface
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804327"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="4c0c5-102">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="4c0c5-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="4c0c5-103">Fournit des méthodes qui notifient l’hôte des actions que le common language runtime (CLR) effectue en cas d’abandons, de délais d’attente ou d’échecs.</span><span class="sxs-lookup"><span data-stu-id="4c0c5-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c0c5-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4c0c5-104">Methods</span></span>  
  
|<span data-ttu-id="4c0c5-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4c0c5-105">Method</span></span>|<span data-ttu-id="4c0c5-106">Description</span><span class="sxs-lookup"><span data-stu-id="4c0c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c0c5-107">OnDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="4c0c5-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="4c0c5-108">Avertit l’hôte que le CLR va prendre l’action par défaut spécifiée par un appel à [ICLRPolicyManager :: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) en réponse à l’abandon ou au <xref:System.AppDomain> déchargement d’un thread.</span><span class="sxs-lookup"><span data-stu-id="4c0c5-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="4c0c5-109">OnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="4c0c5-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="4c0c5-110">Avertit l’hôte que le CLR est sur le point d’exécuter l’action spécifiée par un appel à [ICLRPolicyManager :: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) en réponse à une allocation de ressource ou à un échec de récupération.</span><span class="sxs-lookup"><span data-stu-id="4c0c5-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="4c0c5-111">OnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="4c0c5-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="4c0c5-112">Avertit l’hôte que le CLR va prendre l’action spécifiée par un appel à [ICLRPolicyManager :: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) en réponse à un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="4c0c5-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c0c5-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c0c5-113">Requirements</span></span>  
 <span data-ttu-id="4c0c5-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c0c5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0c5-115">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4c0c5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c0c5-116">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c0c5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c0c5-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0c5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c0c5-118">See also</span></span>

- [<span data-ttu-id="4c0c5-119">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="4c0c5-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="4c0c5-120">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="4c0c5-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="4c0c5-121">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="4c0c5-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="4c0c5-122">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="4c0c5-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="4c0c5-123">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="4c0c5-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
