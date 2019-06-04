---
title: CorBindToRuntime, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3af11b3d2170e13bf216aec64f2bff88cc015f41
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490599"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="9225a-102">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="9225a-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="9225a-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="9225a-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="9225a-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9225a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9225a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9225a-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9225a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9225a-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="9225a-107">[in] Une chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="9225a-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="9225a-108">Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="9225a-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="9225a-109">La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="9225a-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="9225a-110">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="9225a-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="9225a-111">Par défaut, le shim de démarrage évalue `pwszVersion` contre les instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="9225a-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="9225a-112">Un hôte peut obliger le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en transmettant une valeur de `STARTUP_LOADER_SAFEMODE` pour le `flags` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9225a-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="9225a-113">Si l’appelant spécifie null pour `pwszVersion`, la dernière version du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="9225a-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="9225a-114">Passage de null ne donne à l’hôte aucun contrôle sur lequel la version du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="9225a-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="9225a-115">Bien que cette approche peut être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="9225a-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="9225a-116">[in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="9225a-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="9225a-117">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="9225a-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="9225a-118">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="9225a-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="9225a-119">Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="9225a-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="9225a-120">Lors de l’exécution sur un ordinateur monoprocesseur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` est défini sur `svr`.</span><span class="sxs-lookup"><span data-stu-id="9225a-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="9225a-121">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `flags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="9225a-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9225a-122">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9225a-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9225a-123">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9225a-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9225a-124">[in] Le `IID` de l’interface demandée à partir de `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="9225a-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="9225a-125">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9225a-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9225a-126">[out] Le pointeur d’interface retourné à `riid`.</span><span class="sxs-lookup"><span data-stu-id="9225a-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9225a-127">Notes</span><span class="sxs-lookup"><span data-stu-id="9225a-127">Remarks</span></span>  
 <span data-ttu-id="9225a-128">Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="9225a-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="9225a-129">Contexte d’exécution et les flux d’identité de Windows</span><span class="sxs-lookup"><span data-stu-id="9225a-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="9225a-130">Dans la version 1 du CLR, le <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmise entre des points asynchrones telles que les nouveaux threads, pools de threads ou rappels de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="9225a-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="9225a-131">Dans la version 2.0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et il transite d’un point asynchrone, mais pas entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="9225a-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="9225a-132">De même, le <xref:System.Security.Principal.WindowsIdentity> objet transmis d’un point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9225a-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="9225a-133">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="9225a-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="9225a-134">Vous pouvez modifier le flux de deux manières :</span><span class="sxs-lookup"><span data-stu-id="9225a-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="9225a-135">En modifiant le <xref:System.Threading.ExecutionContext> paramètres afin de supprimer le flux sur un thread par thread (voir la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).</span><span class="sxs-lookup"><span data-stu-id="9225a-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="9225a-136">En modifiant le mode par défaut de processus en mode de compatibilité de la version 1, où le <xref:System.Security.Principal.WindowsIdentity> objet ne transmet pas d’un point asynchrone, quel que soit le <xref:System.Threading.ExecutionContext> paramètres sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="9225a-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="9225a-137">Comment vous modifier le mode par défaut varie selon que vous utilisez un fichier exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="9225a-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="9225a-138">Pour les fichiers exécutables managés, vous devez définir le `enabled` attribut de la [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément à `true`.</span><span class="sxs-lookup"><span data-stu-id="9225a-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="9225a-139">Pour les interfaces d’hébergement non managées, définissez le `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `flags` paramètre lors de l’appel le `CorBindToRuntimeEx` (fonction).</span><span class="sxs-lookup"><span data-stu-id="9225a-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="9225a-140">Le mode de compatibilité de version 1 s’applique à l’ensemble du processus et tous les domaines d’application dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9225a-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9225a-141">Notes</span><span class="sxs-lookup"><span data-stu-id="9225a-141">Remarks</span></span>  
 <span data-ttu-id="9225a-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et `CorBindToRuntime` effectuer la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="9225a-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9225a-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9225a-143">Requirements</span></span>  
 <span data-ttu-id="9225a-144">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9225a-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9225a-145">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9225a-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9225a-146">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9225a-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9225a-147">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9225a-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9225a-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9225a-148">See also</span></span>

- [<span data-ttu-id="9225a-149">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="9225a-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9225a-150">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="9225a-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9225a-151">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="9225a-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9225a-152">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="9225a-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9225a-153">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="9225a-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9225a-154">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="9225a-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
