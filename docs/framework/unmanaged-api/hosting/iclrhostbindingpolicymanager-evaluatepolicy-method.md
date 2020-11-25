---
title: ICLRHostBindingPolicyManager::EvaluatePolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
ms.openlocfilehash: 9840217abdf8b3e1d0917b7447572b6860c181c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720306"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="706a6-102">ICLRHostBindingPolicyManager::EvaluatePolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="706a6-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>

<span data-ttu-id="706a6-103">Évalue la stratégie de liaison pour le compte de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="706a6-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="706a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="706a6-104">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="706a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="706a6-105">Parameters</span></span>  

 `pwzReferenceIdentity`  
 <span data-ttu-id="706a6-106">dans Référence à l’assembly avant l’évaluation de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="706a6-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="706a6-107">dans Pointeur vers une mémoire tampon qui contient les données de stratégie.</span><span class="sxs-lookup"><span data-stu-id="706a6-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="706a6-108">dans Taille de la `pbApplicationPolicy` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="706a6-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="706a6-109">à Référence à l’assembly après l’évaluation des nouvelles données de stratégie.</span><span class="sxs-lookup"><span data-stu-id="706a6-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="706a6-110">[in, out] Pointeur vers la taille de la mémoire tampon de référence de l’identité de l’assembly après l’évaluation des nouvelles données de stratégie.</span><span class="sxs-lookup"><span data-stu-id="706a6-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="706a6-111">à Pointeur vers une combinaison logique ou de valeurs [EBindPolicyLevels,](ebindpolicylevels-enumeration.md) , indiquant les stratégies qui ont été appliquées.</span><span class="sxs-lookup"><span data-stu-id="706a6-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="706a6-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="706a6-112">Return Value</span></span>  
  
|<span data-ttu-id="706a6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="706a6-113">HRESULT</span></span>|<span data-ttu-id="706a6-114">Description</span><span class="sxs-lookup"><span data-stu-id="706a6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="706a6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="706a6-115">S_OK</span></span>|<span data-ttu-id="706a6-116">L’évaluation s’est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="706a6-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="706a6-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="706a6-117">E_INVALIDARG</span></span>|<span data-ttu-id="706a6-118">`pwzReferenceIdentity`Ou `pbApplicationPolicy` est une référence null.</span><span class="sxs-lookup"><span data-stu-id="706a6-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="706a6-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="706a6-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="706a6-120">`cbAppPolicySize` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="706a6-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="706a6-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="706a6-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="706a6-122">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="706a6-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="706a6-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="706a6-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="706a6-124">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="706a6-124">The call timed out.</span></span>|  
|<span data-ttu-id="706a6-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="706a6-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="706a6-126">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="706a6-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="706a6-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="706a6-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="706a6-128">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="706a6-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="706a6-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="706a6-129">E_FAIL</span></span>|<span data-ttu-id="706a6-130">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="706a6-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="706a6-131">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="706a6-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="706a6-132">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="706a6-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="706a6-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="706a6-133">Remarks</span></span>  

 <span data-ttu-id="706a6-134">La `EvaluatePolicy` méthode permet à l’hôte d’influencer la stratégie de liaison pour tenir à jour les exigences en matière de contrôle de version des assemblys spécifiques à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="706a6-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="706a6-135">Le moteur de stratégie lui-même reste à l’intérieur du CLR.</span><span class="sxs-lookup"><span data-stu-id="706a6-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="706a6-136">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="706a6-136">Requirements</span></span>  

 <span data-ttu-id="706a6-137">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="706a6-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="706a6-138">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="706a6-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="706a6-139">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="706a6-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="706a6-140">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="706a6-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706a6-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="706a6-141">See also</span></span>

- [<span data-ttu-id="706a6-142">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="706a6-142">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
