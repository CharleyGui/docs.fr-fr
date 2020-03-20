---
title: CorBindToRuntimeHost, fonction
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176485"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="5338d-102">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="5338d-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="5338d-103">Permet aux hôtes de charger une version spécifiée de l’heure d’exécution de la langue commune (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="5338d-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="5338d-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="5338d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5338d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5338d-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,
    [in] LPCWSTR       pwszBuildFlavor,
    [in] LPCWSTR       pwszHostConfigFile,
    [in] VOID*         pReserved,
    [in] DWORD         startupFlags,
    [in] REFCLSID      rclsid,
    [in] REFIID        riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5338d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5338d-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="5338d-107">[dans] Une chaîne qui décrit la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="5338d-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="5338d-108">Un numéro de version dans le cadre .NET se compose de quatre parties séparées par des périodes: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="5338d-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="5338d-109">La chaîne `pwszVersion` est passée comme il faut commencer par le personnage "v" suivi des trois premières parties du numéro de version (par exemple, "v1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="5338d-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="5338d-110">Certaines versions du CLR sont installées avec un énoncé de politique qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="5338d-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="5338d-111">Par défaut, le cale de démarrage évalue par rapport aux énoncés `pwszVersion` de politique et charge la dernière version du temps d’exécution qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="5338d-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="5338d-112">Un hôte peut forcer le cale à sauter `pwszVersion` l’évaluation de la politique et `startupFlags` charger la version exacte spécifiée en passant une valeur de STARTUP_LOADER_SAFEMODE pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="5338d-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="5338d-113">Si `pwszVersion` `null,` c’est la méthode ne charge aucune version du CLR.</span><span class="sxs-lookup"><span data-stu-id="5338d-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="5338d-114">Au lieu de cela, il retourne CLR_E_SHIM_RUNTIMELOAD, ce qui indique qu’il n’a pas réussi à charger le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5338d-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="5338d-115">[dans] Une chaîne qui précise s’il faut charger le serveur ou la construction du poste de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="5338d-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="5338d-116">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="5338d-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="5338d-117">La construction du serveur est optimisée pour tirer parti de plusieurs processeurs pour les collectes d’ordures, et la construction du poste de travail est optimisée pour les applications client fonctionnant sur une machine à processeur unique.</span><span class="sxs-lookup"><span data-stu-id="5338d-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="5338d-118">S’il `pwszBuildFlavor` est réglé pour annuler, la construction du poste de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="5338d-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="5338d-119">Lorsque vous exécutez sur une machine à processeur unique, `pwszBuildFlavor` la `svr`construction du poste de travail est toujours chargée, même si elle est réglée à .</span><span class="sxs-lookup"><span data-stu-id="5338d-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="5338d-120">Toutefois, `pwszBuildFlavor` si la `svr` collecte des ordures est définie et `startupFlags` concomitante (voir la description du paramètre), la construction du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="5338d-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5338d-121">La collecte simultanée des ordures n’est pas prise en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="5338d-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="5338d-122">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, voir [Exécution des applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="5338d-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="5338d-123">[dans] Le nom d’un fichier de configuration hôte qui spécifie la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="5338d-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="5338d-124">Si le nom du fichier n’inclut pas un chemin entièrement qualifié, le fichier est supposé être dans le même répertoire que l’exécutable qui fait l’appel.</span><span class="sxs-lookup"><span data-stu-id="5338d-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="5338d-125">[dans] Réservé à l’extensibility future.</span><span class="sxs-lookup"><span data-stu-id="5338d-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="5338d-126">[dans] Un ensemble de drapeaux qui contrôle la collecte simultanée des `pwszVersion` ordures, le code neutre sur le domaine et le comportement du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5338d-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="5338d-127">La valeur par défaut est un domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="5338d-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="5338d-128">Pour une liste de valeurs soutenues, voir le [STARTUP_FLAGS énumération](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5338d-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="5338d-129">[dans] La `CLSID` coclasse qui met en œuvre soit [l’interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [l’interface ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="5338d-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="5338d-130">Les valeurs soutenues sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="5338d-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="5338d-131">[dans] L’interface `IID` que vous demandez.</span><span class="sxs-lookup"><span data-stu-id="5338d-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="5338d-132">Les valeurs soutenues sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="5338d-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="5338d-133">[out] Un pointeur d’interface à la version du temps d’exécution qui a été chargé.</span><span class="sxs-lookup"><span data-stu-id="5338d-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5338d-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5338d-134">Requirements</span></span>  
 <span data-ttu-id="5338d-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5338d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5338d-136">**En-tête:** MSCorEE.idl MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="5338d-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5338d-137">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="5338d-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5338d-138">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5338d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5338d-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5338d-139">See also</span></span>

- [<span data-ttu-id="5338d-140">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="5338d-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="5338d-141">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="5338d-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="5338d-142">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="5338d-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="5338d-143">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="5338d-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="5338d-144">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="5338d-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="5338d-145">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="5338d-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
