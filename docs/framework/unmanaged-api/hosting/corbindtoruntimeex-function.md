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
ms.openlocfilehash: 84e4c70c973fb19be6800d2cbaf76ea137f58b28
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767951"
---
# <a name="corbindtoruntimeex-function"></a><span data-ttu-id="a4403-102">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="a4403-102">CorBindToRuntimeEx Function</span></span>
<span data-ttu-id="a4403-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="a4403-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span> <span data-ttu-id="a4403-104">Le [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) et `CorBindToRuntimeEx` fonctions effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="a4403-104">The [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) and `CorBindToRuntimeEx` functions perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 <span data-ttu-id="a4403-105">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a4403-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="a4403-106">Cette fonction accepte un ensemble de paramètres qui permettent à un hôte effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4403-106">This function takes a set of parameters that allow a host to do the following:</span></span>  
  
- <span data-ttu-id="a4403-107">Spécifiez la version du runtime qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="a4403-107">Specify the version of the runtime that will be loaded.</span></span>  
  
- <span data-ttu-id="a4403-108">Indiquer si la build du serveur ou station de travail doit être chargée.</span><span class="sxs-lookup"><span data-stu-id="a4403-108">Indicate whether the server or workstation build should be loaded.</span></span>  
  
- <span data-ttu-id="a4403-109">Contrôler si le garbage collection simultané ou le garbage collection non simultané est effectué.</span><span class="sxs-lookup"><span data-stu-id="a4403-109">Control whether concurrent garbage collection or non-concurrent garbage collection is done.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4403-110">Le garbage collection simultané n’est pas pris en charge dans les applications en cours d’exécution WOW64 x86 émulateur sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="a4403-110">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="a4403-111">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [Applications en cours d’exécution de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="a4403-111">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
- <span data-ttu-id="a4403-112">Contrôler si les assemblys sont chargés comme indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="a4403-112">Control whether assemblies are loaded as domain-neutral.</span></span>  
  
- <span data-ttu-id="a4403-113">Obtenir un pointeur d’interface vers un [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) qui peut être utilisé pour définir des options supplémentaires pour configurer une instance du CLR avant son démarrage.</span><span class="sxs-lookup"><span data-stu-id="a4403-113">Obtain an interface pointer to an [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) that can be used to set additional options for configuring an instance of the CLR before it is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4403-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4403-114">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a4403-115">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4403-115">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="a4403-116">[in] Une chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="a4403-116">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="a4403-117">Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="a4403-117">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="a4403-118">La chaîne passée en tant que `pwszVersion` doit commencer par le caractère « v », suivi par les trois premières parties du numéro de version (par exemple, « v1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="a4403-118">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="a4403-119">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="a4403-119">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="a4403-120">Par défaut, le shim de démarrage évalue `pwszVersion` contre les instructions de stratégie et charge la dernière version du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="a4403-120">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="a4403-121">Un hôte peut obliger le shim à ignorer l’évaluation de stratégie et charger la version exacte spécifiée dans `pwszVersion` en transmettant une valeur de `STARTUP_LOADER_SAFEMODE` pour le `startupFlags` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a4403-121">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `startupFlags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="a4403-122">Si l’appelant spécifie null pour `pwszVersion`, `CorBindToRuntimeEx` identifie l’ensemble des runtimes installés, dont les numéros de version sont inférieurs à ceux de l’exécution de .NET Framework 4 et chargement la dernière version du runtime à partir de cet ensemble.</span><span class="sxs-lookup"><span data-stu-id="a4403-122">If the caller specifies null for `pwszVersion`, `CorBindToRuntimeEx` identifies the set of installed runtimes whose version numbers are lower than the .NET Framework 4 runtime, and loads the latest version of the runtime from that set.</span></span> <span data-ttu-id="a4403-123">Il ne charge pas le .NET Framework 4 ou version ultérieure et échoue si aucune version antérieure n’est installée.</span><span class="sxs-lookup"><span data-stu-id="a4403-123">It won't load the .NET Framework 4 or later, and fails if no earlier version is installed.</span></span> <span data-ttu-id="a4403-124">Notez que passer une valeur null ne donne à l’hôte aucun contrôle sur lequel la version du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="a4403-124">Note that passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="a4403-125">Bien que cette approche peut être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="a4403-125">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="a4403-126">[in] Chaîne qui spécifie s’il faut charger le serveur de build ou de la station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="a4403-126">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="a4403-127">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="a4403-127">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="a4403-128">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les garbage collection, et la génération de la station de travail est optimisée pour les applications clientes s’exécutant sur un ordinateur à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="a4403-128">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="a4403-129">Si `pwszBuildFlavor` a la valeur null, la build de la station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="a4403-129">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="a4403-130">Lors de l’exécution sur un ordinateur monoprocesseur, la build de la station de travail est toujours chargée, même si `pwszBuildFlavor` est défini sur `svr`.</span><span class="sxs-lookup"><span data-stu-id="a4403-130">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="a4403-131">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et le garbage collection simultané est spécifié (consultez la description de le `startupFlags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="a4403-131">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a4403-132">[in] Une combinaison de valeurs de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="a4403-132">[in] A combination of values of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span> <span data-ttu-id="a4403-133">Ces indicateurs contrôlent le garbage collection simultané, code indépendant du domaine et le comportement de le `pwszVersion` paramètre.</span><span class="sxs-lookup"><span data-stu-id="a4403-133">These flags control concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="a4403-134">La valeur par défaut est le domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="a4403-134">The default is single domain if no flag is set.</span></span> <span data-ttu-id="a4403-135">Les valeurs suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="a4403-135">The following values are valid:</span></span>  
  
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
  
 <span data-ttu-id="a4403-136">Pour obtenir une description de ces indicateurs, consultez la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="a4403-136">For descriptions of these flags, see the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a4403-137">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a4403-137">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a4403-138">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a4403-138">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a4403-139">[in] Le `IID` de l’interface demandée à partir de `rclsid`.</span><span class="sxs-lookup"><span data-stu-id="a4403-139">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="a4403-140">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a4403-140">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a4403-141">[out] Le pointeur d’interface retourné à `riid`.</span><span class="sxs-lookup"><span data-stu-id="a4403-141">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4403-142">Notes</span><span class="sxs-lookup"><span data-stu-id="a4403-142">Remarks</span></span>  
 <span data-ttu-id="a4403-143">Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="a4403-143">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="a4403-144">Contexte d’exécution et les flux d’identité de Windows</span><span class="sxs-lookup"><span data-stu-id="a4403-144">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="a4403-145">Dans la version 1 du CLR, le <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmise entre des points asynchrones telles que les nouveaux threads, pools de threads ou rappels de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="a4403-145">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="a4403-146">Dans la version 2.0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et il transite d’un point asynchrone, mais pas entre les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="a4403-146">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="a4403-147">De même, le <xref:System.Security.Principal.WindowsIdentity> objet transmis d’un point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a4403-147">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="a4403-148">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="a4403-148">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="a4403-149">Vous pouvez modifier le flux de deux manières :</span><span class="sxs-lookup"><span data-stu-id="a4403-149">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="a4403-150">En modifiant le <xref:System.Threading.ExecutionContext> paramètres afin de supprimer le flux sur un thread par thread (voir la <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).</span><span class="sxs-lookup"><span data-stu-id="a4403-150">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="a4403-151">En modifiant le mode par défaut de processus en mode de compatibilité de la version 1, où le <xref:System.Security.Principal.WindowsIdentity> objet ne transmet pas d’un point asynchrone, quel que soit le <xref:System.Threading.ExecutionContext> paramètres sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="a4403-151">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="a4403-152">Comment vous modifier le mode par défaut varie selon que vous utilisez un fichier exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="a4403-152">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="a4403-153">Pour les fichiers exécutables managés, vous devez définir le `enabled` attribut de la [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément à `true`.</span><span class="sxs-lookup"><span data-stu-id="a4403-153">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="a4403-154">Pour les interfaces d’hébergement non managées, définissez le `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `startupFlags` paramètre lors de l’appel le `CorBindToRuntimeEx` (fonction).</span><span class="sxs-lookup"><span data-stu-id="a4403-154">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `startupFlags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="a4403-155">Le mode de compatibilité de version 1 s’applique à l’ensemble du processus et tous les domaines d’application dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a4403-155">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4403-156">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4403-156">Requirements</span></span>  
 <span data-ttu-id="a4403-157">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4403-157">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4403-158">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4403-158">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4403-159">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4403-159">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4403-160">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4403-160">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4403-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4403-161">See also</span></span>

- [<span data-ttu-id="a4403-162">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="a4403-162">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="a4403-163">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="a4403-163">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="a4403-164">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="a4403-164">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="a4403-165">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="a4403-165">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="a4403-166">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a4403-166">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="a4403-167">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="a4403-167">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
