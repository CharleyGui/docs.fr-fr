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
ms.openlocfilehash: 52594c36c54c74941371f9950fbc6fb543b86de0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493550"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="48f9d-102">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="48f9d-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="48f9d-103">Permet aux hôtes non managés de charger le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="48f9d-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="48f9d-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="48f9d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f9d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48f9d-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48f9d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48f9d-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="48f9d-107">dans Chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="48f9d-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="48f9d-108">Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="48f9d-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="48f9d-109">La chaîne transmise comme `pwszVersion` doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="48f9d-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="48f9d-110">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="48f9d-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="48f9d-111">Par défaut, le shim de démarrage est évalué par `pwszVersion` rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="48f9d-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="48f9d-112">Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et à charger la version exacte spécifiée dans `pwszVersion` en passant une valeur `STARTUP_LOADER_SAFEMODE` pour le `flags` paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="48f9d-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="48f9d-113">Si l’appelant spécifie null pour `pwszVersion` , la version la plus récente du runtime est chargée.</span><span class="sxs-lookup"><span data-stu-id="48f9d-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="48f9d-114">Le passage de la valeur null donne à l’hôte aucun contrôle sur la version du runtime qui est chargée.</span><span class="sxs-lookup"><span data-stu-id="48f9d-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="48f9d-115">Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="48f9d-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="48f9d-116">dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="48f9d-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="48f9d-117">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="48f9d-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="48f9d-118">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.</span><span class="sxs-lookup"><span data-stu-id="48f9d-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="48f9d-119">Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="48f9d-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="48f9d-120">Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail est toujours chargée, même si `pwszBuildFlavor` a la valeur `svr` .</span><span class="sxs-lookup"><span data-stu-id="48f9d-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="48f9d-121">Toutefois, si `pwszBuildFlavor` a la valeur `svr` et que garbage collection simultané est spécifié (voir la description du `flags` paramètre), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="48f9d-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="48f9d-122">dans `CLSID`De la coclasse qui implémente l’interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="48f9d-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="48f9d-123">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="48f9d-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="48f9d-124">dans `IID`De l’interface demandée à partir de `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="48f9d-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="48f9d-125">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="48f9d-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="48f9d-126">à Pointeur d’interface retourné à `riid` .</span><span class="sxs-lookup"><span data-stu-id="48f9d-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48f9d-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="48f9d-127">Remarks</span></span>  
 <span data-ttu-id="48f9d-128">Si `pwszVersion` spécifie une version du runtime qui n’existe pas, `CorBindToRuntimeEx` retourne une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="48f9d-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="48f9d-129">Contexte d’exécution et le workflow de l’identité Windows</span><span class="sxs-lookup"><span data-stu-id="48f9d-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="48f9d-130">Dans la version 1 du CLR, l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis entre des points asynchrones tels que les nouveaux threads, les pools de threads ou les rappels de minuterie.</span><span class="sxs-lookup"><span data-stu-id="48f9d-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="48f9d-131">Dans la version 2,0 du CLR, un <xref:System.Threading.ExecutionContext> objet encapsule des informations sur le thread en cours d’exécution et le transmet sur n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="48f9d-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="48f9d-132">De même, l' <xref:System.Security.Principal.WindowsIdentity> objet circule également sur n’importe quel point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="48f9d-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="48f9d-133">Par conséquent, l’emprunt d’identité actuel sur le thread, le cas échéant, est également transmis.</span><span class="sxs-lookup"><span data-stu-id="48f9d-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="48f9d-134">Vous pouvez modifier le Flow de deux manières :</span><span class="sxs-lookup"><span data-stu-id="48f9d-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="48f9d-135">En modifiant les <xref:System.Threading.ExecutionContext> paramètres pour supprimer le workflow pour chaque thread (consultez les <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> méthodes, et <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).</span><span class="sxs-lookup"><span data-stu-id="48f9d-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="48f9d-136">En remplaçant le mode de traitement par défaut par le mode de compatibilité de la version 1, où l' <xref:System.Security.Principal.WindowsIdentity> objet n’est pas transmis sur un point asynchrone, quels que soient les <xref:System.Threading.ExecutionContext> paramètres du thread en cours.</span><span class="sxs-lookup"><span data-stu-id="48f9d-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="48f9d-137">La façon dont vous modifiez le mode par défaut varie selon que vous utilisez un exécutable managé ou une interface d’hébergement non managée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="48f9d-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="48f9d-138">Pour les exécutables managés, vous devez affecter `enabled` à l’attribut de l’élément la valeur [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="48f9d-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="48f9d-139">Pour les interfaces d’hébergement non managées, définissez l' `STARTUP_LEGACY_IMPERSONATION` indicateur dans le `flags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.</span><span class="sxs-lookup"><span data-stu-id="48f9d-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="48f9d-140">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.</span><span class="sxs-lookup"><span data-stu-id="48f9d-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48f9d-141">Remarques</span><span class="sxs-lookup"><span data-stu-id="48f9d-141">Remarks</span></span>  
 <span data-ttu-id="48f9d-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) et `CorBindToRuntime` effectuent la même opération, mais la `CorBindToRuntimeEx` fonction vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="48f9d-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f9d-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="48f9d-143">Requirements</span></span>  
 <span data-ttu-id="48f9d-144">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48f9d-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f9d-145">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="48f9d-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48f9d-146">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48f9d-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48f9d-147">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48f9d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48f9d-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48f9d-148">See also</span></span>

- [<span data-ttu-id="48f9d-149">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="48f9d-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="48f9d-150">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="48f9d-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="48f9d-151">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="48f9d-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="48f9d-152">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="48f9d-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="48f9d-153">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="48f9d-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="48f9d-154">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="48f9d-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
