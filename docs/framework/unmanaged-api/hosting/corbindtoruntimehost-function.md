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
ms.openlocfilehash: a6d9708e7281a72c88ba28012006784f7b0ee9d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124358"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="a3472-102">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="a3472-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="a3472-103">Permet aux hôtes de charger une version spécifiée du common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="a3472-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="a3472-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a3472-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3472-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3472-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a3472-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a3472-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="a3472-107">dans Chaîne qui décrit la version du CLR que vous souhaitez charger.</span><span class="sxs-lookup"><span data-stu-id="a3472-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="a3472-108">Un numéro de version dans le .NET Framework se compose de quatre parties séparées par des points : *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="a3472-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="a3472-109">La chaîne transmise en tant que `pwszVersion` doit commencer par le caractère « v » suivi des trois premières parties du numéro de version (par exemple, « v 1.0.1529 »).</span><span class="sxs-lookup"><span data-stu-id="a3472-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="a3472-110">Certaines versions du CLR sont installées avec une instruction de stratégie qui spécifie la compatibilité avec les versions précédentes du CLR.</span><span class="sxs-lookup"><span data-stu-id="a3472-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="a3472-111">Par défaut, le shim de démarrage évalue `pwszVersion` par rapport aux instructions de stratégie et charge la version la plus récente du runtime qui est compatible avec la version demandée.</span><span class="sxs-lookup"><span data-stu-id="a3472-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="a3472-112">Un hôte peut forcer le shim à ignorer l’évaluation de la stratégie et charger la version exacte spécifiée dans `pwszVersion` en passant une valeur de STARTUP_LOADER_SAFEMODE pour le paramètre `startupFlags`.</span><span class="sxs-lookup"><span data-stu-id="a3472-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="a3472-113">Si `pwszVersion` est `null,` la méthode ne charge pas de version du CLR.</span><span class="sxs-lookup"><span data-stu-id="a3472-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="a3472-114">Au lieu de cela, elle retourne CLR_E_SHIM_RUNTIMELOAD, ce qui indique qu’elle n’a pas pu charger le Runtime.</span><span class="sxs-lookup"><span data-stu-id="a3472-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="a3472-115">dans Chaîne qui spécifie s’il faut charger le serveur ou la build de station de travail du CLR.</span><span class="sxs-lookup"><span data-stu-id="a3472-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="a3472-116">Les valeurs valides sont `svr` et `wks`.</span><span class="sxs-lookup"><span data-stu-id="a3472-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="a3472-117">La build du serveur est optimisée pour tirer parti de plusieurs processeurs pour les nettoyages de la mémoire, et la build de la station de travail est optimisée pour les applications clientes exécutées sur un ordinateur à un seul processeur.</span><span class="sxs-lookup"><span data-stu-id="a3472-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="a3472-118">Si `pwszBuildFlavor` a la valeur null, la build de station de travail est chargée.</span><span class="sxs-lookup"><span data-stu-id="a3472-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="a3472-119">Lors de l’exécution sur un ordinateur à un seul processeur, la build de station de travail est toujours chargée, même si `pwszBuildFlavor` est défini sur `svr`.</span><span class="sxs-lookup"><span data-stu-id="a3472-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="a3472-120">Toutefois, si `pwszBuildFlavor` est défini sur `svr` et que garbage collection simultané est spécifié (voir la description du paramètre `startupFlags`), la build du serveur est chargée.</span><span class="sxs-lookup"><span data-stu-id="a3472-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3472-121">Le garbage collection simultané n’est pas pris en charge dans les applications exécutant l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="a3472-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="a3472-122">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="a3472-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="a3472-123">dans Nom d’un fichier de configuration d’hôte qui spécifie la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="a3472-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="a3472-124">Si le nom de fichier n’inclut pas de chemin d’accès qualifié complet, le fichier est supposé être dans le même répertoire que l’exécutable qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="a3472-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="a3472-125">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="a3472-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a3472-126">dans Jeu d’indicateurs qui contrôle les garbage collection simultanées, le code indépendant du domaine et le comportement du paramètre `pwszVersion`.</span><span class="sxs-lookup"><span data-stu-id="a3472-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="a3472-127">La valeur par défaut est un domaine unique si aucun indicateur n’est défini.</span><span class="sxs-lookup"><span data-stu-id="a3472-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="a3472-128">Pour obtenir la liste des valeurs prises en charge, consultez l' [énumération STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a3472-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a3472-129">dans `CLSID` de la coclasse qui implémente l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a3472-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a3472-130">Les valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a3472-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a3472-131">dans `IID` de l’interface que vous demandez.</span><span class="sxs-lookup"><span data-stu-id="a3472-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="a3472-132">Les valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a3472-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a3472-133">à Pointeur d’interface vers la version du runtime qui a été chargée.</span><span class="sxs-lookup"><span data-stu-id="a3472-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3472-134">spécifications</span><span class="sxs-lookup"><span data-stu-id="a3472-134">Requirements</span></span>  
 <span data-ttu-id="a3472-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3472-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3472-136">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="a3472-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a3472-137">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3472-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3472-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3472-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3472-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3472-139">See also</span></span>

- [<span data-ttu-id="a3472-140">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="a3472-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="a3472-141">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="a3472-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="a3472-142">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="a3472-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="a3472-143">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="a3472-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="a3472-144">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a3472-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="a3472-145">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="a3472-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
