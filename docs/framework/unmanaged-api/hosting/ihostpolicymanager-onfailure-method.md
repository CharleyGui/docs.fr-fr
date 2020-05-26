---
title: IHostPolicyManager::OnFailure, méthode
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 8ad4943aa9bf1b66b34bcd83a5422a977b16518d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804230"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="b1f22-102">IHostPolicyManager::OnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="b1f22-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="b1f22-103">Avertit l’hôte que le common language runtime (CLR) est sur le point d’exécuter l’action spécifiée par un appel à la méthode [ICLRPolicyManager :: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) en réponse à une allocation de ressource ou à un échec de récupération.</span><span class="sxs-lookup"><span data-stu-id="b1f22-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1f22-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1f22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1f22-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="b1f22-106">dans Une des valeurs [EClrFailure](eclrfailure-enumeration.md) , indiquant le type d’échec auquel le CLR répond.</span><span class="sxs-lookup"><span data-stu-id="b1f22-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="b1f22-107">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action que le CLR prend en charge `failure` .</span><span class="sxs-lookup"><span data-stu-id="b1f22-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1f22-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b1f22-108">Return Value</span></span>  
  
|<span data-ttu-id="b1f22-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1f22-109">HRESULT</span></span>|<span data-ttu-id="b1f22-110">Description</span><span class="sxs-lookup"><span data-stu-id="b1f22-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1f22-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1f22-111">S_OK</span></span>|<span data-ttu-id="b1f22-112">`OnFailure`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b1f22-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b1f22-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1f22-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1f22-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b1f22-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1f22-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1f22-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1f22-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b1f22-116">The call timed out.</span></span>|  
|<span data-ttu-id="b1f22-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1f22-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1f22-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b1f22-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1f22-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1f22-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1f22-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b1f22-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1f22-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1f22-121">E_FAIL</span></span>|<span data-ttu-id="b1f22-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b1f22-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1f22-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b1f22-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1f22-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1f22-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1f22-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b1f22-125">Requirements</span></span>  
 <span data-ttu-id="b1f22-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1f22-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1f22-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1f22-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1f22-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1f22-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1f22-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1f22-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f22-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1f22-130">See also</span></span>

- [<span data-ttu-id="b1f22-131">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="b1f22-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b1f22-132">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="b1f22-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="b1f22-133">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="b1f22-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b1f22-134">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="b1f22-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
