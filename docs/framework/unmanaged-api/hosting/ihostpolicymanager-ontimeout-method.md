---
title: IHostPolicyManager::OnTimeout, méthode
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: fb0f943d710322257d052edc5c16108671622790
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804218"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="ea799-102">IHostPolicyManager::OnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="ea799-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="ea799-103">Avertit l’hôte que le common language runtime (CLR) est sur le point d’exécuter l’action spécifiée par un appel à la méthode [ICLRPolicyManager :: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) en réponse à un délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="ea799-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea799-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea799-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea799-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea799-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="ea799-106">dans L’une des valeurs [EClrOperation](eclroperation-enumeration.md) , indiquant le type d’opération qui a expiré.</span><span class="sxs-lookup"><span data-stu-id="ea799-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="ea799-107">dans L’une des valeurs [EPolicyAction](epolicyaction-enumeration.md) , indiquant l’action que le CLR prend en réponse au délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="ea799-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea799-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea799-108">Return Value</span></span>  
  
|<span data-ttu-id="ea799-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea799-109">HRESULT</span></span>|<span data-ttu-id="ea799-110">Description</span><span class="sxs-lookup"><span data-stu-id="ea799-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea799-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea799-111">S_OK</span></span>|<span data-ttu-id="ea799-112">`OnTimeout`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ea799-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="ea799-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea799-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea799-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="ea799-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea799-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea799-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea799-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ea799-116">The call timed out.</span></span>|  
|<span data-ttu-id="ea799-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea799-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea799-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ea799-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea799-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea799-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea799-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="ea799-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea799-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea799-121">E_FAIL</span></span>|<span data-ttu-id="ea799-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ea799-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea799-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ea799-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea799-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea799-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea799-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ea799-125">Requirements</span></span>  
 <span data-ttu-id="ea799-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea799-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea799-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea799-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea799-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea799-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea799-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea799-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea799-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea799-130">See also</span></span>

- [<span data-ttu-id="ea799-131">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="ea799-131">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="ea799-132">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="ea799-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="ea799-133">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="ea799-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="ea799-134">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="ea799-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
