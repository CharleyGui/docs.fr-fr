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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176511"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="1bbf5-102">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="1bbf5-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="1bbf5-103">Permet aux hôtes non gérés de charger l’heure d’exécution de la langue commune (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="1bbf5-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bbf5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bbf5-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bbf5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bbf5-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="1bbf5-107">[dans] Une chaîne décrivant la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="1bbf5-108">Un numéro de version dans le cadre .NET se compose de quatre parties séparées par des périodes: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="1bbf5-109">La chaîne `pwszVersion` est passée comme il faut commencer par le personnage "v" suivi des trois premières parties du numéro de version (par exemple, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="1bbf5-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="1bbf5-110">Certaines versions du CLR sont installées avec un énoncé de politique qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="1bbf5-111">Par défaut, le cale de démarrage évalue par rapport aux énoncés `pwszVersion` de politique et charge la dernière version du temps d’exécution qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="1bbf5-112">Un hôte peut forcer le cale à sauter `pwszVersion` l’évaluation de `STARTUP_LOADER_SAFEMODE` la `flags` politique et charger la version exacte spécifiée en passant une valeur de pour le paramètre, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="1bbf5-113">Si l’appelant spécifie nulle pour `pwszVersion`, la dernière version de l’heure d’exécution est chargée.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="1bbf5-114">Passer nul ne donne à l’hôte aucun contrôle sur la version du temps d’exécution est chargée.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="1bbf5-115">Bien que cette approche puisse être appropriée dans certains scénarios, il est fortement recommandé que l’hôte fournisse une version spécifique à charger.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="1bbf5-116">[dans] Une chaîne qui précise s’il faut charger le serveur ou la construction du poste de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="1bbf5-117">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="1bbf5-118">La construction du serveur est optimisée pour tirer parti de plusieurs processeurs pour les collectes d’ordures, et la construction du poste de travail est optimisée pour les applications client fonctionnant sur une machine à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="1bbf5-119">S’il `pwszBuildFlavor` est réglé pour annuler, la construction du poste de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="1bbf5-120">Lorsque vous exécutez sur une machine à processeur unique, `pwszBuildFlavor` la `svr`construction du poste de travail est toujours chargée, même si elle est réglée à .</span><span class="sxs-lookup"><span data-stu-id="1bbf5-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="1bbf5-121">Toutefois, `pwszBuildFlavor` si la `svr` collecte des ordures est définie et `flags` concomitante (voir la description du paramètre), la construction du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="1bbf5-122">[dans] La `CLSID` coclasse qui met en œuvre soit [l’interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [l’interface ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="1bbf5-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="1bbf5-123">Les valeurs soutenues sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="1bbf5-124">[dans] L’interface `IID` demandée `rclsid`de .</span><span class="sxs-lookup"><span data-stu-id="1bbf5-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="1bbf5-125">Les valeurs soutenues sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="1bbf5-126">[out] Le pointeur `riid`d’interface retourné à .</span><span class="sxs-lookup"><span data-stu-id="1bbf5-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bbf5-127">Notes </span><span class="sxs-lookup"><span data-stu-id="1bbf5-127">Remarks</span></span>  
 <span data-ttu-id="1bbf5-128">Si `pwszVersion` spécifie une version de `CorBindToRuntimeEx` temps d’exécution qui n’existe pas, renvoie une valeur HRESULT de CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="1bbf5-129">Contexte d’exécution et flux de l’identité de Windows</span><span class="sxs-lookup"><span data-stu-id="1bbf5-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="1bbf5-130">Dans la version 1 du <xref:System.Security.Principal.WindowsIdentity> CLR, l’objet ne circule pas à travers des points asynchrones tels que de nouveaux fils, des pools de threads ou des rappels de minuterie.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="1bbf5-131">Dans la version 2.0 du <xref:System.Threading.ExecutionContext> CLR, un objet enveloppe certaines informations sur le thread qui exécute actuellement et le fait couler à travers n’importe quel point asynchrone, mais pas au-delà des limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="1bbf5-132">De même, l’objet <xref:System.Security.Principal.WindowsIdentity> s’écoule également à travers n’importe quel point asynchrone.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="1bbf5-133">Par conséquent, l’usurpation d’identité actuelle sur le fil, le cas échéant, coule aussi.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="1bbf5-134">Vous pouvez modifier le flux de deux façons :</span><span class="sxs-lookup"><span data-stu-id="1bbf5-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="1bbf5-135">En modifiant <xref:System.Threading.ExecutionContext> les paramètres pour supprimer le flux par <xref:System.Threading.ExecutionContext.SuppressFlow%2A>fil <xref:System.Security.SecurityContext.SuppressFlow%2A>(voir le , , et les <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> méthodes).</span><span class="sxs-lookup"><span data-stu-id="1bbf5-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="1bbf5-136">En changeant le mode par défaut de processus au <xref:System.Security.Principal.WindowsIdentity> mode de compatibilité de la version 1, lorsque l’objet ne circule pas sur un point asynchrone, indépendamment des <xref:System.Threading.ExecutionContext> paramètres du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="1bbf5-137">La façon dont vous modifiez le mode par défaut dépend si vous utilisez une interface d’hébergement exécutable gérée ou non gérée pour charger le CLR :</span><span class="sxs-lookup"><span data-stu-id="1bbf5-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="1bbf5-138">Pour les exécutables `enabled` gérés, vous devez définir l’attribut de [ \<l’héritageImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) élément à `true`.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="1bbf5-139">Pour les interfaces d’hébergement `STARTUP_LEGACY_IMPERSONATION` non gestion, définissez le drapeau dans le `flags` paramètre lors de l’appel de la `CorBindToRuntimeEx` fonction.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="1bbf5-140">Le mode de compatibilité de la version 1 s’applique à l’ensemble du processus et à tous les domaines d’application du processus.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bbf5-141">Notes </span><span class="sxs-lookup"><span data-stu-id="1bbf5-141">Remarks</span></span>  
 <span data-ttu-id="1bbf5-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` et effectuer la même `CorBindToRuntimeEx` opération, mais la fonction vous permet de définir des drapeaux pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="1bbf5-142">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bbf5-143">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1bbf5-143">Requirements</span></span>  
 <span data-ttu-id="1bbf5-144">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bbf5-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bbf5-145">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="1bbf5-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bbf5-146">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="1bbf5-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bbf5-147">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bbf5-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbf5-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bbf5-148">See also</span></span>

- [<span data-ttu-id="1bbf5-149">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="1bbf5-149">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="1bbf5-150">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="1bbf5-150">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="1bbf5-151">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="1bbf5-151">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="1bbf5-152">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="1bbf5-152">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="1bbf5-153">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="1bbf5-153">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="1bbf5-154">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="1bbf5-154">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
