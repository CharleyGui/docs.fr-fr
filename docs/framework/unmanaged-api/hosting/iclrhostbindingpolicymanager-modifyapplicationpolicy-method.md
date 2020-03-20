---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178098"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="c7e76-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="c7e76-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="c7e76-103">Modifie la politique contraignante pour l’assemblage spécifié et crée une nouvelle version de la politique.</span><span class="sxs-lookup"><span data-stu-id="c7e76-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7e76-104">Syntax</span></span>  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7e76-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="c7e76-106">[dans] L’identité de l’assemblage à modifier.</span><span class="sxs-lookup"><span data-stu-id="c7e76-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="c7e76-107">[dans] La nouvelle identité de l’assemblage modifié.</span><span class="sxs-lookup"><span data-stu-id="c7e76-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="c7e76-108">[dans] Pointeur d’un tampon qui contient les données de stratégie contraignantes que l’assemblage doit modifier.</span><span class="sxs-lookup"><span data-stu-id="c7e76-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="c7e76-109">[dans] L’ampleur de la politique contraignante à remplacer.</span><span class="sxs-lookup"><span data-stu-id="c7e76-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="c7e76-110">[dans] Une combinaison de produits [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) logique, indiquant le contrôle de la redirection.</span><span class="sxs-lookup"><span data-stu-id="c7e76-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="c7e76-111">[out] Un pointeur vers un tampon qui contient les nouvelles données de stratégie contraignantes.</span><span class="sxs-lookup"><span data-stu-id="c7e76-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="c7e76-112">[dans, dehors] Un pointeur sur la taille du nouveau tampon de politique contraignante.</span><span class="sxs-lookup"><span data-stu-id="c7e76-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7e76-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c7e76-113">Return Value</span></span>  
  
|<span data-ttu-id="c7e76-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7e76-114">HRESULT</span></span>|<span data-ttu-id="c7e76-115">Description</span><span class="sxs-lookup"><span data-stu-id="c7e76-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7e76-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7e76-116">S_OK</span></span>|<span data-ttu-id="c7e76-117">La politique a été modifiée avec succès.</span><span class="sxs-lookup"><span data-stu-id="c7e76-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="c7e76-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c7e76-118">E_INVALIDARG</span></span>|<span data-ttu-id="c7e76-119">`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` était une référence nulle.</span><span class="sxs-lookup"><span data-stu-id="c7e76-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="c7e76-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c7e76-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c7e76-121">`pbNewApplicationPolicy` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="c7e76-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="c7e76-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7e76-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7e76-123">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c7e76-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7e76-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7e76-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7e76-125">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="c7e76-125">The call timed out.</span></span>|  
|<span data-ttu-id="c7e76-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7e76-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7e76-127">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="c7e76-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7e76-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7e76-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7e76-129">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c7e76-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7e76-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7e76-130">E_FAIL</span></span>|<span data-ttu-id="c7e76-131">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c7e76-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7e76-132">Une fois qu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c7e76-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7e76-133">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c7e76-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7e76-134">Notes </span><span class="sxs-lookup"><span data-stu-id="c7e76-134">Remarks</span></span>  
 <span data-ttu-id="c7e76-135">La `ModifyApplicationPolicy` méthode peut être appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="c7e76-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="c7e76-136">Le premier appel doit fournir `pbNewApplicationPolicy` une valeur nulle pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c7e76-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="c7e76-137">Cet appel sera de retour `pcbNewAppPolicySize`avec la valeur nécessaire pour .</span><span class="sxs-lookup"><span data-stu-id="c7e76-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="c7e76-138">Le deuxième appel devrait `pcbNewAppPolicySize`fournir cette valeur pour , `pbNewApplicationPolicy`et pointer vers un tampon de cette taille pour .</span><span class="sxs-lookup"><span data-stu-id="c7e76-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e76-139">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7e76-139">Requirements</span></span>  
 <span data-ttu-id="c7e76-140">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7e76-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e76-141">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="c7e76-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7e76-142">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7e76-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7e76-143">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e76-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e76-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7e76-144">See also</span></span>

- [<span data-ttu-id="c7e76-145">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="c7e76-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
