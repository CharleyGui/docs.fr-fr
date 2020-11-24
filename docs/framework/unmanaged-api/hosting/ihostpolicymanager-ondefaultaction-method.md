---
title: IHostPolicyManager::OnDefaultAction, méthode
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: a22f16c14514b90ce888fafc0ea554bd9f90cb11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684081"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="cd018-102">IHostPolicyManager::OnDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="cd018-102">IHostPolicyManager::OnDefaultAction Method</span></span>

<span data-ttu-id="cd018-103">Avertit l’hôte que le common language runtime (CLR) est sur le point d’exécuter l’action par défaut qui a été définie par un appel à la méthode [ICLRPolicyManager :: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) en réponse à l’abandon ou au <xref:System.AppDomain> déchargement d’un thread.</span><span class="sxs-lookup"><span data-stu-id="cd018-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd018-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd018-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd018-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd018-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="cd018-106">dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant le type d’événement auquel le CLR répond.</span><span class="sxs-lookup"><span data-stu-id="cd018-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="cd018-107">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action que le CLR prend en réponse à l’événement.</span><span class="sxs-lookup"><span data-stu-id="cd018-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd018-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cd018-108">Return Value</span></span>  
  
|<span data-ttu-id="cd018-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd018-109">HRESULT</span></span>|<span data-ttu-id="cd018-110">Description</span><span class="sxs-lookup"><span data-stu-id="cd018-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd018-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd018-111">S_OK</span></span>|<span data-ttu-id="cd018-112">`OnDefaultAction` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cd018-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="cd018-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd018-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd018-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter l’appel.</span><span class="sxs-lookup"><span data-stu-id="cd018-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="cd018-115">correctement</span><span class="sxs-lookup"><span data-stu-id="cd018-115">successfully</span></span>|  
|<span data-ttu-id="cd018-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd018-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd018-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cd018-117">The call timed out.</span></span>|  
|<span data-ttu-id="cd018-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd018-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd018-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cd018-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd018-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd018-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd018-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="cd018-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd018-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd018-122">E_FAIL</span></span>|<span data-ttu-id="cd018-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cd018-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd018-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cd018-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd018-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd018-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd018-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cd018-126">Requirements</span></span>  

 <span data-ttu-id="cd018-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd018-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd018-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd018-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd018-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd018-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd018-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd018-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd018-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd018-131">See also</span></span>

- [<span data-ttu-id="cd018-132">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="cd018-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="cd018-133">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="cd018-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="cd018-134">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="cd018-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="cd018-135">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="cd018-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
