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
ms.openlocfilehash: dcf2ce8bdb7cec1f567e548ff3314e160fffe9fd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616630"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="504c3-102">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="504c3-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="504c3-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="504c3-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="504c3-104">Les fonctions [CorBindToRuntime](corbindtoruntime-function.md) et `CorBindToRuntimeEx` effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="504c3-104">The [CorBindToRuntime](corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="504c3-105">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="504c3-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="504c3-106">Cette fonction prend un ensemble de paramètres qui permettent à un hôte d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="504c3-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="504c3-107">Spécifiez la version du runtime qui sera chargée.</span><span class="sxs-lookup"><span data-stu-id="504c3-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="504c3-108">Indiquez si la build du serveur ou de la station de travail doit être chargée.</span><span class="sxs-lookup"><span data-stu-id="504c3-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="504c3-109">Contrôler si les garbage collection simultanées garbage collection ou non simultanées sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="504c3-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="504c3-110">Le garbage collection simultané n’est pas pris en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="504c3-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="504c3-111">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="504c3-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="504c3-112">Contrôler si les assemblys sont chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="504c3-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="504c3-113">Obtenez un pointeur d’interface vers un [ICorRuntimeHost](icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant son démarrage.</span><span class="sxs-lookup"><span data-stu-id="504c3-113">Obtain an interface pointer to an [ICorRuntimeHost](icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504c3-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="504c3-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="504c3-115">Paramètres</span><span class="sxs-lookup"><span data-stu-id="504c3-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="504c3-116">dans Chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="504c3-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="504c3-117">Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="504c3-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="504c3-118">La chaîne transmise comme `pwszVersion` doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="504c3-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="504c3-119">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="504c3-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="504c3-120">Par défaut, le shim de démarrage est évalué par `pwszVersion` rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="504c3-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="504c3-121">Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et à charger la version exacte spécifiée dans `pwszVersion` en passant une valeur `STARTUP_LOADER_SAFEMODE` pour le `startupFlags` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="504c3-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="504c3-122">Si l’appelant spécifie null pour `pwszVersion` , `CorBindToRuntimeEx` identifie le jeu de runtimes installés dont les numéros de version sont inférieurs au Runtime .NET Framework 4 et charge la version la plus récente du runtime à partir de ce jeu.</span><span class="sxs-lookup"><span data-stu-id="504c3-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="504c3-123">Il ne chargera pas le .NET Framework 4 ou version ultérieure et échouera si aucune version antérieure n’est installée.</span><span class="sxs-lookup"><span data-stu-id="504c3-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="504c3-124">Notez que le passage de la valeur null donne à l’hôte aucun contrôle sur la version du runtime qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="504c3-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="504c3-125">Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="504c3-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="504c3-126">dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="504c3-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="504c3-127">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="504c3-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="504c3-128">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.</span><span class="sxs-lookup"><span data-stu-id="504c3-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="504c3-129">Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="504c3-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="504c3-130">Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr` .</span><span class="sxs-lookup"><span data-stu-id="504c3-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="504c3-131">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et que garbage collection simultané est spécifié (voir la description du `startupFlags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="504c3-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="504c3-132">dans Combinaison de valeurs de l’énumération [STARTUP_FLAGS](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="504c3-132">[in] A combination of values of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="504c3-133">Ces indicateurs contrôlent les garbage collection simultanés, le code indépendant du domaine et le comportement du `pwszVersion` paramètre.</span><span class="sxs-lookup"><span data-stu-id="504c3-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="504c3-134">La valeur par défaut est un domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="504c3-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="504c3-135">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="504c3-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="504c3-136">Pour obtenir une description de ces indicateurs, consultez l’énumération [STARTUP_FLAGS](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="504c3-136">For descriptions of these flags, see the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="504c3-137">dans `CLSID`De la coclasse qui implémente l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="504c3-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="504c3-138">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="504c3-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="504c3-139">dans `IID`De l’interface demandée à partir de `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="504c3-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="504c3-140">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="504c3-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="504c3-141">à Pointeur d’interface retourné à `riid` .</span><span class="sxs-lookup"><span data-stu-id="504c3-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="504c3-142">Notes</span><span class="sxs-lookup"><span data-stu-id="504c3-142">Remarks</span></span>  
 <span data-ttu-id="504c3-143">Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="504c3-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="504c3-144">Contexte d’exécution et le workflow de l’identité Windows</span><span class="sxs-lookup"><span data-stu-id="504c3-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="504c3-145">Dans la version 1 du CLR, l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones tels que les nouveaux threads, les pools de threads ou les rappels de minuterie.</span><span class="sxs-lookup"><span data-stu-id="504c3-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="504c3-146">Dans la version 2,0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et le transmet sur n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="504c3-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="504c3-147">De même, l' <xref:System.Security.Principal.WindowsIdentity> objet circule également sur n’importe quel point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="504c3-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="504c3-148">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="504c3-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="504c3-149">Vous pouvez modifier le Flow de deux manières :</span><span class="sxs-lookup"><span data-stu-id="504c3-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="504c3-150">En modifiant les <xref:System.Threading.ExecutionContext> paramètres pour supprimer le workflow pour chaque thread (consultez les <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> méthodes, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="504c3-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="504c3-151">En remplaçant le mode de traitement par défaut par le mode de compatibilité de la version 1, où l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis sur un point asynchrone, quels que soient les <xref:System.Threading.ExecutionContext> paramètres du thread en cours.</span><span class="sxs-lookup"><span data-stu-id="504c3-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="504c3-152">La façon dont vous modifiez le mode par défaut varie selon que vous utilisez un exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="504c3-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="504c3-153">Pour les exécutables managés, vous devez affecter la valeur `enabled` à l’attribut de l’élément [ \< legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="504c3-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="504c3-154">Pour les interfaces d’hébergement non managées, définissez l' `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `startupFlags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.</span><span class="sxs-lookup"><span data-stu-id="504c3-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="504c3-155">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.</span><span class="sxs-lookup"><span data-stu-id="504c3-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="504c3-156">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="504c3-156">Requirements</span></span>  
 <span data-ttu-id="504c3-157">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="504c3-157">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="504c3-158">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="504c3-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="504c3-159">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="504c3-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="504c3-160">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="504c3-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="504c3-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="504c3-161">See also</span></span>

- [<span data-ttu-id="504c3-162">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="504c3-162">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="504c3-163">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="504c3-163">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="504c3-164">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="504c3-164">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="504c3-165">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="504c3-165">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="504c3-166">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="504c3-166">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="504c3-167">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="504c3-167">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
