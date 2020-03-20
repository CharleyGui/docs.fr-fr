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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176498"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="cbb79-102">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="cbb79-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="cbb79-103">Permet aux hôtes non gérés de charger l’heure d’exécution de la langue commune (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="cbb79-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="cbb79-104">Le [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) et `CorBindToRuntimeEx` les fonctions effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des drapeaux pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="cbb79-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="cbb79-105">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="cbb79-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="cbb79-106">Cette fonction prend un ensemble de paramètres qui permettent à un hôte de faire ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="cbb79-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="cbb79-107">Spécifier la version de l’exécution qui sera chargée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="cbb79-108">Indiquez si la construction du serveur ou du poste de travail doit être chargée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="cbb79-109">Contrôlez si la collecte simultanée des ordures ou la collecte non simultanée des ordures est effectuée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbb79-110">La collecte simultanée des ordures n’est pas prise en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="cbb79-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="cbb79-111">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, voir [Exécution des applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="cbb79-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="cbb79-112">Contrôlez si les assemblages sont chargés comme neutres sur le plan de domaine.</span><span class="sxs-lookup"><span data-stu-id="cbb79-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="cbb79-113">Obtenez un pointeur d’interface à un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant qu’il ne soit commencé.</span><span class="sxs-lookup"><span data-stu-id="cbb79-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb79-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbb79-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cbb79-115">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbb79-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="cbb79-116">[dans] Une chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="cbb79-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="cbb79-117">Un numéro de version dans le cadre .NET se compose de quatre parties séparées par des périodes: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="cbb79-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="cbb79-118">La chaîne `pwszVersion` est passée comme il faut commencer par le personnage "v" suivi des trois premières parties du numéro de version (par exemple, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="cbb79-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="cbb79-119">Certaines versions du CLR sont installées avec un énoncé de politique qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="cbb79-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="cbb79-120">Par défaut, le cale de démarrage évalue par rapport aux énoncés `pwszVersion` de politique et charge la dernière version du temps d’exécution qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="cbb79-121">Un hôte peut forcer le cale à sauter `pwszVersion` l’évaluation de `STARTUP_LOADER_SAFEMODE` la `startupFlags` politique et charger la version exacte spécifiée en passant une valeur de pour le paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="cbb79-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="cbb79-122">Si l’appelant spécifie nulle pour `pwszVersion`, `CorBindToRuntimeEx` identifie l’ensemble de temps d’exécution installés dont les numéros de version sont inférieurs à la .NET Framework 4 runtime, et charge la dernière version de l’exécution de cet ensemble.</span><span class="sxs-lookup"><span data-stu-id="cbb79-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="cbb79-123">Il ne chargera pas le cadre .NET 4 ou plus tard, et échoue si aucune version antérieure n’est installée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="cbb79-124">Notez que le passage nul ne donne à l’hôte aucun contrôle sur la version du temps d’exécution est chargée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="cbb79-125">Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="cbb79-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="cbb79-126">[dans] Une chaîne qui précise s’il faut charger le serveur ou la construction du poste de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="cbb79-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="cbb79-127">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="cbb79-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="cbb79-128">La construction du serveur est optimisée pour tirer parti de plusieurs processeurs pour les collectes d’ordures, et la construction du poste de travail est optimisée pour les applications client fonctionnant sur une machine à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="cbb79-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="cbb79-129">S’il `pwszBuildFlavor` est réglé pour annuler, la construction du poste de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="cbb79-130">Lorsque vous exécutez sur une machine à processeur unique, `pwszBuildFlavor` la `svr`construction du poste de travail est toujours chargée, même si elle est réglée à .</span><span class="sxs-lookup"><span data-stu-id="cbb79-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="cbb79-131">Toutefois, `pwszBuildFlavor` si la `svr` collecte des ordures est définie et `startupFlags` concomitante (voir la description du paramètre), la construction du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="cbb79-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="cbb79-132">[dans] Une combinaison de valeurs de [l’STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="cbb79-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="cbb79-133">Ces drapeaux contrôlent la collecte simultanée des ordures, le code neutre en matière de domaine et le comportement du `pwszVersion` paramètre.</span><span class="sxs-lookup"><span data-stu-id="cbb79-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="cbb79-134">La valeur par défaut est un domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="cbb79-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="cbb79-135">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="cbb79-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="cbb79-136">Pour les descriptions de ces drapeaux, voir le [recensement STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="cbb79-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="cbb79-137">[dans] La `CLSID` coclasse qui met en œuvre soit [l’interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [l’interface ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="cbb79-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="cbb79-138">Les valeurs soutenues sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="cbb79-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="cbb79-139">[dans] L’interface `IID` demandée `rclsid`de .</span><span class="sxs-lookup"><span data-stu-id="cbb79-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="cbb79-140">Les valeurs soutenues sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="cbb79-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="cbb79-141">[out] Le pointeur `riid`d’interface retourné à .</span><span class="sxs-lookup"><span data-stu-id="cbb79-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbb79-142">Notes </span><span class="sxs-lookup"><span data-stu-id="cbb79-142">Remarks</span></span>  
 <span data-ttu-id="cbb79-143">Si `pwszVersion` spécifie une version de `CorBindToRuntimeEx` temps d’exécution qui n’existe pas, renvoie une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="cbb79-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="cbb79-144">Contexte d’exécution et flux de l’identité de Windows</span><span class="sxs-lookup"><span data-stu-id="cbb79-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="cbb79-145">Dans la version 1 du <xref:System.Security.Principal.WindowsIdentity> CLR, l’objet ne circule pas à travers des points asynchrones tels que de nouveaux fils, des pools de threads ou des rappels de minuterie.</span><span class="sxs-lookup"><span data-stu-id="cbb79-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="cbb79-146">Dans la version 2.0 du <xref:System.Threading.ExecutionContext> CLR, un objet enveloppe certaines informations sur le thread qui exécute actuellement et le fait couler à travers n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="cbb79-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="cbb79-147">De même, l’objet <xref:System.Security.Principal.WindowsIdentity> s’écoule également à travers n’importe quel point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="cbb79-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="cbb79-148">Par conséquent, l’usurpation d’identité actuelle sur le fil, le cas échéant, coule aussi.</span><span class="sxs-lookup"><span data-stu-id="cbb79-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="cbb79-149">Vous pouvez modifier le flux de deux façons :</span><span class="sxs-lookup"><span data-stu-id="cbb79-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="cbb79-150">En modifiant <xref:System.Threading.ExecutionContext> les paramètres pour supprimer le flux par <xref:System.Threading.ExecutionContext.SuppressFlow%2A>fil <xref:System.Security.SecurityContext.SuppressFlow%2A>(voir le , , et les <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).</span><span class="sxs-lookup"><span data-stu-id="cbb79-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="cbb79-151">En changeant le mode par défaut de processus au <xref:System.Security.Principal.WindowsIdentity> mode de compatibilité de la version 1, lorsque l’objet ne circule pas sur un point asynchrone, indépendamment des <xref:System.Threading.ExecutionContext> paramètres du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="cbb79-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="cbb79-152">La façon dont vous modifiez le mode par défaut dépend si vous utilisez une interface d’hébergement exécutable gérée ou non gérée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="cbb79-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="cbb79-153">Pour les exécutables `enabled` gérés, vous devez définir l’attribut de [ \<l’héritageImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément à `true`.</span><span class="sxs-lookup"><span data-stu-id="cbb79-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="cbb79-154">Pour les interfaces d’hébergement `STARTUP_LEGACY_IMPERSONATION` non gestion, définissez le drapeau dans le `startupFlags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.</span><span class="sxs-lookup"><span data-stu-id="cbb79-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="cbb79-155">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.</span><span class="sxs-lookup"><span data-stu-id="cbb79-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbb79-156">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cbb79-156">Requirements</span></span>  
 <span data-ttu-id="cbb79-157">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb79-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb79-158">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="cbb79-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbb79-159">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="cbb79-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbb79-160">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb79-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb79-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbb79-161">See also</span></span>

- [<span data-ttu-id="cbb79-162">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="cbb79-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="cbb79-163">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="cbb79-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="cbb79-164">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="cbb79-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="cbb79-165">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="cbb79-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="cbb79-166">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="cbb79-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="cbb79-167">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="cbb79-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
