---
title: CorBindToRuntimeEx, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f31ae29efee9b353c2dcc679724db73da5444e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969412"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="427e2-102">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="427e2-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="427e2-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="427e2-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="427e2-104">Les fonctions [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) et `CorBindToRuntimeEx` effectuent la même opération, mais la fonction `CorBindToRuntimeEx` vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="427e2-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="427e2-105">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="427e2-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="427e2-106">Cette fonction prend un ensemble de paramètres qui permettent à un hôte d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="427e2-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="427e2-107">Spécifiez la version du runtime qui sera chargée.</span><span class="sxs-lookup"><span data-stu-id="427e2-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="427e2-108">Indiquez si la build du serveur ou de la station de travail doit être chargée.</span><span class="sxs-lookup"><span data-stu-id="427e2-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="427e2-109">Contrôler si les garbage collection simultanées garbage collection ou non simultanées sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="427e2-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="427e2-110">Le garbage collection simultané n’est pas pris en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="427e2-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="427e2-111">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="427e2-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="427e2-112">Contrôler si les assemblys sont chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="427e2-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="427e2-113">Obtenez un pointeur d’interface vers un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant son démarrage.</span><span class="sxs-lookup"><span data-stu-id="427e2-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="427e2-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="427e2-114">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="427e2-115">Paramètres</span><span class="sxs-lookup"><span data-stu-id="427e2-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="427e2-116">dans Chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="427e2-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="427e2-117">Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="427e2-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="427e2-118">La chaîne transmise `pwszVersion` comme doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="427e2-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="427e2-119">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="427e2-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="427e2-120">Par défaut, le shim de démarrage est `pwszVersion` évalué par rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="427e2-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="427e2-121">Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et à charger la `pwszVersion` version exacte spécifiée dans en `STARTUP_LOADER_SAFEMODE` passant une `startupFlags` valeur pour le paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="427e2-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="427e2-122">Si l’appelant spécifie null `pwszVersion`pour `CorBindToRuntimeEx` , identifie le jeu de runtimes installés dont les numéros de version sont inférieurs au Runtime .NET Framework 4 et charge la version la plus récente du runtime à partir de ce jeu.</span><span class="sxs-lookup"><span data-stu-id="427e2-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="427e2-123">Il ne chargera pas le .NET Framework 4 ou version ultérieure et échouera si aucune version antérieure n’est installée.</span><span class="sxs-lookup"><span data-stu-id="427e2-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="427e2-124">Notez que le passage de la valeur null donne à l’hôte aucun contrôle sur la version du runtime qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="427e2-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="427e2-125">Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="427e2-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="427e2-126">dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="427e2-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="427e2-127">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="427e2-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="427e2-128">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.</span><span class="sxs-lookup"><span data-stu-id="427e2-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="427e2-129">Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="427e2-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="427e2-130">Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail `pwszBuildFlavor` est toujours chargée `svr`, même si a la valeur.</span><span class="sxs-lookup"><span data-stu-id="427e2-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="427e2-131">Toutefois, si `pwszBuildFlavor` a la `svr` valeur et que garbage collection simultané est spécifié ( `startupFlags` Voir la description du paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="427e2-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="427e2-132">dans Combinaison de valeurs de l’énumération [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="427e2-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="427e2-133">Ces indicateurs contrôlent les garbage collection simultanés, le code indépendant du domaine et le `pwszVersion` comportement du paramètre.</span><span class="sxs-lookup"><span data-stu-id="427e2-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="427e2-134">La valeur par défaut est un domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="427e2-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="427e2-135">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="427e2-135">The following values are valid:</span></span>  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 <span data-ttu-id="427e2-136">Pour obtenir une description de ces indicateurs, consultez l’énumération [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="427e2-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="427e2-137">[in] `CLSID` de la coclasse qui implémente l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).</span><span class="sxs-lookup"><span data-stu-id="427e2-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="427e2-138">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="427e2-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="427e2-139">dans De l’interface demandée à partir `rclsid`de. `IID`</span><span class="sxs-lookup"><span data-stu-id="427e2-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="427e2-140">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="427e2-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="427e2-141">à Pointeur d’interface retourné à `riid`.</span><span class="sxs-lookup"><span data-stu-id="427e2-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="427e2-142">Notes</span><span class="sxs-lookup"><span data-stu-id="427e2-142">Remarks</span></span>  
 <span data-ttu-id="427e2-143">Si `pwszVersion` spécifie une version du runtime qui n’existe `CorBindToRuntimeEx` pas, retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="427e2-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="427e2-144">Contexte d’exécution et le workflow de l’identité Windows</span><span class="sxs-lookup"><span data-stu-id="427e2-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="427e2-145">Dans la version 1 du CLR, l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones tels que les nouveaux threads, les pools de threads ou les rappels de minuterie.</span><span class="sxs-lookup"><span data-stu-id="427e2-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="427e2-146">Dans la version 2,0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et le transmet sur n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="427e2-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="427e2-147">De même, l' <xref:System.Security.Principal.WindowsIdentity> objet circule également sur n’importe quel point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="427e2-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="427e2-148">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="427e2-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="427e2-149">Vous pouvez modifier le Flow de deux manières :</span><span class="sxs-lookup"><span data-stu-id="427e2-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="427e2-150">En modifiant les <xref:System.Threading.ExecutionContext> paramètres pour supprimer le workflow pour chaque thread (consultez les <xref:System.Threading.ExecutionContext.SuppressFlow%2A>méthodes, <xref:System.Security.SecurityContext.SuppressFlow%2A>et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="427e2-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="427e2-151">En remplaçant le mode de traitement par défaut par le mode de compatibilité de la <xref:System.Security.Principal.WindowsIdentity> version 1, où l’objet n’est pas transmis sur un <xref:System.Threading.ExecutionContext> point asynchrone, quels que soient les paramètres du thread en cours.</span><span class="sxs-lookup"><span data-stu-id="427e2-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="427e2-152">La façon dont vous modifiez le mode par défaut varie selon que vous utilisez un exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="427e2-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="427e2-153">Pour les exécutables managés, vous `enabled` devez affecter la valeur à `true`l’attribut de l' [ \<élément legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) .</span><span class="sxs-lookup"><span data-stu-id="427e2-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="427e2-154">Pour les interfaces d’hébergement non managées, `STARTUP_LEGACY_IMPERSONATION` définissez l’indicateur `startupFlags` dans le paramètre lors `CorBindToRuntimeEx` de l’appel de la fonction.</span><span class="sxs-lookup"><span data-stu-id="427e2-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="427e2-155">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.</span><span class="sxs-lookup"><span data-stu-id="427e2-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="427e2-156">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="427e2-156">Requirements</span></span>  
 <span data-ttu-id="427e2-157">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="427e2-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="427e2-158">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="427e2-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="427e2-159">**Bibliothèque** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="427e2-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="427e2-160">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="427e2-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427e2-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="427e2-161">See also</span></span>

- [<span data-ttu-id="427e2-162">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="427e2-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="427e2-163">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="427e2-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="427e2-164">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="427e2-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="427e2-165">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="427e2-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="427e2-166">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="427e2-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="427e2-167">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="427e2-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
