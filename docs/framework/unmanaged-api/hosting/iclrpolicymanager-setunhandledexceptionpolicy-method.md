---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 1088374c9df18ded38b44384be44de245f0bd403
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728951"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="e08a5-102">ICLRPolicyManager::SetUnhandledExceptionPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="e08a5-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>

<span data-ttu-id="e08a5-103">Spécifie le comportement du common language runtime (CLR) lorsqu’une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="e08a5-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e08a5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e08a5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e08a5-105">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="e08a5-106">dans L’une des valeurs [EClrUnhandledException,](eclrunhandledexception-enumeration.md) , indiquant si le comportement est défini par le CLR ou l’hôte.</span><span class="sxs-lookup"><span data-stu-id="e08a5-106">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e08a5-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e08a5-107">Return Value</span></span>  
  
|<span data-ttu-id="e08a5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e08a5-108">HRESULT</span></span>|<span data-ttu-id="e08a5-109">Description</span><span class="sxs-lookup"><span data-stu-id="e08a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e08a5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e08a5-110">S_OK</span></span>|<span data-ttu-id="e08a5-111">`SetUnhandledExceptionPolicy` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e08a5-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="e08a5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e08a5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e08a5-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e08a5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e08a5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e08a5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e08a5-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e08a5-115">The call timed out.</span></span>|  
|<span data-ttu-id="e08a5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e08a5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e08a5-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e08a5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e08a5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e08a5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e08a5-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e08a5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e08a5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e08a5-120">E_FAIL</span></span>|<span data-ttu-id="e08a5-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e08a5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e08a5-122">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e08a5-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e08a5-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e08a5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e08a5-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="e08a5-124">Remarks</span></span>  

 <span data-ttu-id="e08a5-125">Par défaut, le CLR est le gestionnaire final pour toutes les exceptions non gérées, et son comportement par défaut consiste à détruire le processus.</span><span class="sxs-lookup"><span data-stu-id="e08a5-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="e08a5-126">L’hôte peut modifier ce comportement en définissant la `policy` valeur sur eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="e08a5-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="e08a5-127">Cette valeur permet à l’hôte d’implémenter son propre comportement par défaut, comme avec les versions antérieures du CLR.</span><span class="sxs-lookup"><span data-stu-id="e08a5-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08a5-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e08a5-128">Requirements</span></span>  

 <span data-ttu-id="e08a5-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e08a5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e08a5-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e08a5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e08a5-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e08a5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e08a5-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e08a5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08a5-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e08a5-133">See also</span></span>

- [<span data-ttu-id="e08a5-134">EClrUnhandledException, énumération</span><span class="sxs-lookup"><span data-stu-id="e08a5-134">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="e08a5-135">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="e08a5-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e08a5-136">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="e08a5-136">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="e08a5-137">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="e08a5-137">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
