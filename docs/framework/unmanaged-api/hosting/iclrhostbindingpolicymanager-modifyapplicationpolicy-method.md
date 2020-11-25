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
ms.openlocfilehash: 8da9c9fea5cf5b3a27eeb9d0222f0845c832b7da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714196"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="b75b5-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="b75b5-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>

<span data-ttu-id="b75b5-103">Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="b75b5-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b75b5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b75b5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b75b5-105">Parameters</span></span>  

 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="b75b5-106">dans Identité de l’assembly à modifier.</span><span class="sxs-lookup"><span data-stu-id="b75b5-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="b75b5-107">dans Nouvelle identité de l’assembly modifié.</span><span class="sxs-lookup"><span data-stu-id="b75b5-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="b75b5-108">dans Pointeur vers une mémoire tampon qui contient les données de stratégie de liaison de l’assembly à modifier.</span><span class="sxs-lookup"><span data-stu-id="b75b5-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="b75b5-109">dans Taille de la stratégie de liaison à remplacer.</span><span class="sxs-lookup"><span data-stu-id="b75b5-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="b75b5-110">dans Combinaison logique ou de valeurs [EHostBindingPolicyModifyFlags,](ehostbindingpolicymodifyflags-enumeration.md) indiquant le contrôle de la redirection.</span><span class="sxs-lookup"><span data-stu-id="b75b5-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="b75b5-111">à Pointeur vers une mémoire tampon qui contient les nouvelles données de stratégie de liaison.</span><span class="sxs-lookup"><span data-stu-id="b75b5-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="b75b5-112">[in, out] Pointeur vers la taille de la nouvelle mémoire tampon de stratégie de liaison.</span><span class="sxs-lookup"><span data-stu-id="b75b5-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b75b5-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b75b5-113">Return Value</span></span>  
  
|<span data-ttu-id="b75b5-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b75b5-114">HRESULT</span></span>|<span data-ttu-id="b75b5-115">Description</span><span class="sxs-lookup"><span data-stu-id="b75b5-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b75b5-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="b75b5-116">S_OK</span></span>|<span data-ttu-id="b75b5-117">La stratégie a été modifiée avec succès.</span><span class="sxs-lookup"><span data-stu-id="b75b5-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="b75b5-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b75b5-118">E_INVALIDARG</span></span>|<span data-ttu-id="b75b5-119">`pwzSourceAssemblyIdentity` ou `pwzTargetAssemblyIdentity` était une référence null.</span><span class="sxs-lookup"><span data-stu-id="b75b5-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="b75b5-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b75b5-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b75b5-121">`pbNewApplicationPolicy` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="b75b5-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="b75b5-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b75b5-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b75b5-123">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b75b5-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b75b5-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b75b5-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b75b5-125">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b75b5-125">The call timed out.</span></span>|  
|<span data-ttu-id="b75b5-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b75b5-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b75b5-127">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b75b5-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b75b5-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b75b5-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b75b5-129">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b75b5-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b75b5-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b75b5-130">E_FAIL</span></span>|<span data-ttu-id="b75b5-131">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b75b5-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b75b5-132">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b75b5-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b75b5-133">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b75b5-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b75b5-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="b75b5-134">Remarks</span></span>  

 <span data-ttu-id="b75b5-135">La `ModifyApplicationPolicy` méthode peut être appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="b75b5-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="b75b5-136">Le premier appel doit fournir une valeur null pour le `pbNewApplicationPolicy` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b75b5-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="b75b5-137">Cet appel retourne la valeur nécessaire pour `pcbNewAppPolicySize` .</span><span class="sxs-lookup"><span data-stu-id="b75b5-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="b75b5-138">Le deuxième appel doit fournir cette valeur pour `pcbNewAppPolicySize` et pointer vers une mémoire tampon de cette taille pour `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="b75b5-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b75b5-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b75b5-139">Requirements</span></span>  

 <span data-ttu-id="b75b5-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75b5-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b75b5-141">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b75b5-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b75b5-142">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b75b5-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b75b5-143">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b75b5-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75b5-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b75b5-144">See also</span></span>

- [<span data-ttu-id="b75b5-145">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="b75b5-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
