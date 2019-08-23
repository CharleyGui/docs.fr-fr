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
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965356"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="9dc8a-102">ICLRRuntimeHost::ExecuteApplication, méthode</span><span class="sxs-lookup"><span data-stu-id="9dc8a-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="9dc8a-103">Utilisé dans les scénarios de déploiement ClickOnce basés sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="9dc8a-104">Pour plus d’informations sur ces scénarios, consultez [sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="9dc8a-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc8a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc8a-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9dc8a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9dc8a-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="9dc8a-107">dans Nom complet de l’application, tel que défini pour <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="9dc8a-108">dans Nombre de chaînes contenues dans le `ppwzManifestPaths` tableau.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="9dc8a-109">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-109">[in] Optional.</span></span> <span data-ttu-id="9dc8a-110">Tableau de chaînes qui contient des chemins d’accès de manifeste pour l’application.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="9dc8a-111">dans Nombre de chaînes contenues dans le `ppwzActivationData` tableau.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="9dc8a-112">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-112">[in] Optional.</span></span> <span data-ttu-id="9dc8a-113">Tableau de chaînes qui contient les données d’activation de l’application, telles que la partie de la chaîne de requête de l’URL pour les applications déployées sur le Web.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="9dc8a-114">à Valeur retournée par le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dc8a-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9dc8a-115">Return Value</span></span>  
  
|<span data-ttu-id="9dc8a-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dc8a-116">HRESULT</span></span>|<span data-ttu-id="9dc8a-117">Description</span><span class="sxs-lookup"><span data-stu-id="9dc8a-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9dc8a-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="9dc8a-118">S_OK</span></span>|<span data-ttu-id="9dc8a-119">`ExecuteApplication`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="9dc8a-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9dc8a-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9dc8a-121">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9dc8a-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9dc8a-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9dc8a-123">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-123">The call timed out.</span></span>|  
|<span data-ttu-id="9dc8a-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dc8a-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9dc8a-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9dc8a-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9dc8a-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9dc8a-127">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9dc8a-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9dc8a-128">E_FAIL</span></span>|<span data-ttu-id="9dc8a-129">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9dc8a-130">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9dc8a-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dc8a-132">Notes</span><span class="sxs-lookup"><span data-stu-id="9dc8a-132">Remarks</span></span>  
 <span data-ttu-id="9dc8a-133">`ExecuteApplication`est utilisé pour activer des applications ClickOnce dans un domaine d’application nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="9dc8a-134">Le paramètre de sortie est défini sur la valeur retournée par l’application. `pReturnValue`</span><span class="sxs-lookup"><span data-stu-id="9dc8a-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="9dc8a-135">Si vous spécifiez une valeur null pour `pReturnValue`, `ExecuteApplication` n’échoue pas, mais elle ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9dc8a-136">N’appelez pas la méthode [Start méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) avant d’appeler `ExecuteApplication` la méthode pour activer une application basée sur un manifeste.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="9dc8a-137">Si la `Start` méthode est appelée en premier, `ExecuteApplication` l’appel de la méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="9dc8a-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc8a-138">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9dc8a-138">Requirements</span></span>  
 <span data-ttu-id="9dc8a-139">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc8a-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc8a-140">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9dc8a-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9dc8a-141">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9dc8a-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dc8a-142">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc8a-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc8a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dc8a-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="9dc8a-144">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="9dc8a-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="9dc8a-145">SetAppDomainManager, méthode</span><span class="sxs-lookup"><span data-stu-id="9dc8a-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="9dc8a-146">Procédure pas à pas : téléchargement d'assemblys à la demande avec l'API du déploiement ClickOnce à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="9dc8a-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
