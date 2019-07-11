---
title: ICLRRuntimeHost::ExecuteApplication, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8db6fd1296420011dcbfbbb0e5682f8a484dc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768812"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="fb3de-102">ICLRRuntimeHost::ExecuteApplication, méthode</span><span class="sxs-lookup"><span data-stu-id="fb3de-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="fb3de-103">Utilisé dans les scénarios de déploiement ClickOnce basée sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="fb3de-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="fb3de-104">Pour plus d’informations sur ces scénarios, consultez [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="fb3de-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb3de-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb3de-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb3de-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="fb3de-107">[in] Le nom complet de l’application, tel que défini pour <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="fb3de-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="fb3de-108">[in] Le nombre de chaînes contenues dans le `ppwzManifestPaths` tableau.</span><span class="sxs-lookup"><span data-stu-id="fb3de-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="fb3de-109">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="fb3de-109">[in] Optional.</span></span> <span data-ttu-id="fb3de-110">Tableau de chaînes qui contient les chemins d’accès de manifestes pour l’application.</span><span class="sxs-lookup"><span data-stu-id="fb3de-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="fb3de-111">[in] Le nombre de chaînes contenues dans le `ppwzActivationData` tableau.</span><span class="sxs-lookup"><span data-stu-id="fb3de-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="fb3de-112">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="fb3de-112">[in] Optional.</span></span> <span data-ttu-id="fb3de-113">Un tableau de chaînes qui contient des données de l’activation de l’application, comme la partie de chaîne de requête de l’URL pour les applications déployées sur le Web.</span><span class="sxs-lookup"><span data-stu-id="fb3de-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="fb3de-114">[out] La valeur retournée par le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="fb3de-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb3de-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fb3de-115">Return Value</span></span>  
  
|<span data-ttu-id="fb3de-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb3de-116">HRESULT</span></span>|<span data-ttu-id="fb3de-117">Description</span><span class="sxs-lookup"><span data-stu-id="fb3de-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb3de-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb3de-118">S_OK</span></span>|<span data-ttu-id="fb3de-119">`ExecuteApplication` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="fb3de-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="fb3de-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb3de-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb3de-121">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="fb3de-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb3de-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb3de-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb3de-123">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="fb3de-123">The call timed out.</span></span>|  
|<span data-ttu-id="fb3de-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb3de-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb3de-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="fb3de-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb3de-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb3de-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb3de-127">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="fb3de-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb3de-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb3de-128">E_FAIL</span></span>|<span data-ttu-id="fb3de-129">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="fb3de-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb3de-130">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="fb3de-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb3de-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb3de-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb3de-132">Notes</span><span class="sxs-lookup"><span data-stu-id="fb3de-132">Remarks</span></span>  
 <span data-ttu-id="fb3de-133">`ExecuteApplication` est utilisé pour activer des applications ClickOnce dans un domaine d’application nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="fb3de-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="fb3de-134">Le `pReturnValue` paramètre de sortie est défini sur la valeur retournée par l’application.</span><span class="sxs-lookup"><span data-stu-id="fb3de-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="fb3de-135">Si vous fournissez une valeur NULL pour `pReturnValue`, `ExecuteApplication` n’échoue pas, mais il ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="fb3de-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb3de-136">N’appelez pas la [méthode Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode avant d’appeler le `ExecuteApplication` méthode permettant d’activer une application basée sur un manifeste.</span><span class="sxs-lookup"><span data-stu-id="fb3de-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="fb3de-137">Si le `Start` méthode est appelée en premier, le `ExecuteApplication` appel de méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="fb3de-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb3de-138">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fb3de-138">Requirements</span></span>  
 <span data-ttu-id="fb3de-139">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb3de-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb3de-140">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb3de-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb3de-141">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb3de-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb3de-142">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb3de-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3de-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb3de-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="fb3de-144">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="fb3de-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="fb3de-145">SetAppDomainManager, méthode</span><span class="sxs-lookup"><span data-stu-id="fb3de-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="fb3de-146">Procédure pas à pas : téléchargement d'assemblys à la demande avec l'API du déploiement ClickOnce à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="fb3de-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
