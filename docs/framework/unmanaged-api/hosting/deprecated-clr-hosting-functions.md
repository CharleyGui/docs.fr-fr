---
title: Fonction d'hébergement du CLR déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 8925278bdf4d48efc9e589ffc4e181d904444e6b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616422"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="4fc7f-102">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="4fc7f-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="4fc7f-103">Cette section décrit les fonctions statiques globales non managées utilisées par les versions antérieures de l’API d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="4fc7f-104">À l’exception des fonctions d’infrastructure ( `_Cor*` fonctions), qui sont utilisées uniquement par le .NET Framework, ces fonctions ont été dépréciées dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="4fc7f-105">Fonctions d’activation</span><span class="sxs-lookup"><span data-stu-id="4fc7f-105">Activation functions</span></span>  
 [<span data-ttu-id="4fc7f-106">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="4fc7f-107">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-107">Deprecated.</span></span> <span data-ttu-id="4fc7f-108">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="4fc7f-109">CoInitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="4fc7f-110">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-110">Obsolete.</span></span> <span data-ttu-id="4fc7f-111">Pour initialiser le common language runtime (CLR), utilisez [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="4fc7f-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="4fc7f-112">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="4fc7f-113">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-113">Deprecated.</span></span> <span data-ttu-id="4fc7f-114">Garantit que le moteur d’exécution du CLR est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="4fc7f-115">Utilisez à la place la méthode [ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4fc7f-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="4fc7f-116">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="4fc7f-117">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-117">Deprecated.</span></span> <span data-ttu-id="4fc7f-118">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="4fc7f-119">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="4fc7f-120">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-120">Deprecated.</span></span> <span data-ttu-id="4fc7f-121">Permet aux hôtes non managés de charger le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="4fc7f-122">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="4fc7f-123">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-123">Deprecated.</span></span> <span data-ttu-id="4fc7f-124">Charge le CLR dans un processus à l’aide des informations de version lues à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="4fc7f-125">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="4fc7f-126">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-126">Deprecated.</span></span> <span data-ttu-id="4fc7f-127">Permet aux hôtes non managés de charger le CLR dans un processus, et vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="4fc7f-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="4fc7f-129">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-129">Deprecated.</span></span> <span data-ttu-id="4fc7f-130">Permet aux hôtes de charger une version spécifiée du CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="4fc7f-131">GetCORRequiredVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="4fc7f-132">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-132">Deprecated.</span></span> <span data-ttu-id="4fc7f-133">Obtient le numéro de version CLR requis.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="4fc7f-134">GetCORSystemDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="4fc7f-135">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-135">Deprecated.</span></span> <span data-ttu-id="4fc7f-136">Retourne le répertoire d’installation du CLR qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="4fc7f-137">GetRealProcAddress, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="4fc7f-138">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-138">Deprecated.</span></span> <span data-ttu-id="4fc7f-139">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du CLR.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="4fc7f-140">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="4fc7f-141">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-141">Deprecated.</span></span> <span data-ttu-id="4fc7f-142">Obtient les informations de version et de répertoire relatives au CLR demandé par une application.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="4fc7f-143">Fonctions de version du CLR</span><span class="sxs-lookup"><span data-stu-id="4fc7f-143">CLR version functions</span></span>  
 <span data-ttu-id="4fc7f-144">Les fonctions de cette section retournent une version CLR ; ils n’activent pas le CLR.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="4fc7f-145">GetCORVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="4fc7f-146">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-146">Deprecated.</span></span> <span data-ttu-id="4fc7f-147">Retourne le numéro de version du CLR qui s’exécute dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="4fc7f-148">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="4fc7f-149">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-149">Deprecated.</span></span> <span data-ttu-id="4fc7f-150">Obtient les informations de version du CLR du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="4fc7f-151">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="4fc7f-152">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-152">Deprecated.</span></span> <span data-ttu-id="4fc7f-153">Obtient le numéro de version du CLR demandé par l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="4fc7f-154">Si cette version n’est pas installée, obtient la version la plus récente installée avant la version demandée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="4fc7f-155">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="4fc7f-156">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-156">Deprecated.</span></span> <span data-ttu-id="4fc7f-157">Obtient les informations de version CLR appropriées pour la classe avec le CLSID spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="4fc7f-158">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="4fc7f-159">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-159">Deprecated.</span></span> <span data-ttu-id="4fc7f-160">Obtient le numéro de version du CLR qui est associé au handle de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="4fc7f-161">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="4fc7f-162">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-162">Deprecated.</span></span> <span data-ttu-id="4fc7f-163">Permet à l’hôte de déterminer la version du CLR qui sera utilisée dans le processus avant d’initialiser explicitement le CLR.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="4fc7f-164">Fonctions d’hébergement</span><span class="sxs-lookup"><span data-stu-id="4fc7f-164">Hosting functions</span></span>  
 [<span data-ttu-id="4fc7f-165">CallFunctionShim, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="4fc7f-166">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-166">Deprecated.</span></span> <span data-ttu-id="4fc7f-167">Effectue un appel à la fonction qui a le nom et les paramètres spécifiés dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="4fc7f-168">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="4fc7f-169">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-169">Deprecated.</span></span> <span data-ttu-id="4fc7f-170">Décharge un assembly COM du processus.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="4fc7f-171">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="4fc7f-172">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-172">Deprecated.</span></span> <span data-ttu-id="4fc7f-173">Arrête le processus non managé actuel.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="4fc7f-174">CorLaunchApplication, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="4fc7f-175">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-175">Deprecated.</span></span> <span data-ttu-id="4fc7f-176">Démarre l’application au chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et d’autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="4fc7f-177">CorMarkThreadInThreadPool, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="4fc7f-178">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-178">Deprecated.</span></span> <span data-ttu-id="4fc7f-179">Marque le thread du pool de threads en cours d’exécution pour l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="4fc7f-180">À partir de la version 2,0 de .NET Framework, cette fonction n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="4fc7f-181">Elle n’est pas obligatoire et peut être supprimée de votre code.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="4fc7f-182">CoUninitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="4fc7f-183">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-183">Obsolete.</span></span> <span data-ttu-id="4fc7f-184">Le CLR ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="4fc7f-185">CoUninitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="4fc7f-186">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="4fc7f-187">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="4fc7f-188">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-188">Deprecated.</span></span> <span data-ttu-id="4fc7f-189">Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="4fc7f-190">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="4fc7f-191">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-191">Deprecated.</span></span> <span data-ttu-id="4fc7f-192">Crée un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4fc7f-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="4fc7f-193">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="4fc7f-194">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-194">Deprecated.</span></span> <span data-ttu-id="4fc7f-195">Détruit un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4fc7f-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="4fc7f-196">FExecuteInAppDomainCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4fc7f-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="4fc7f-197">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-197">Deprecated.</span></span> <span data-ttu-id="4fc7f-198">Pointe vers une fonction que le CLR appelle pour exécuter du code managé.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="4fc7f-199">FLockClrVersionCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4fc7f-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="4fc7f-200">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-200">Deprecated.</span></span> <span data-ttu-id="4fc7f-201">Pointe vers une fonction que le CLR appelle pour notifier l’hôte que l’initialisation a démarré ou est terminée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="4fc7f-202">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="4fc7f-203">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-203">Deprecated.</span></span> <span data-ttu-id="4fc7f-204">Obtient un pointeur vers une interface qui permet au CLR de gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="4fc7f-205">LoadLibraryShim, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="4fc7f-206">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-206">Deprecated.</span></span> <span data-ttu-id="4fc7f-207">Charge une version spécifiée d’un .NET Framework DLL.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="4fc7f-208">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="4fc7f-209">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-209">Deprecated.</span></span> <span data-ttu-id="4fc7f-210">Convertit une valeur HRESULT en message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="4fc7f-211">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="4fc7f-212">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-212">Deprecated.</span></span> <span data-ttu-id="4fc7f-213">Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="4fc7f-214">LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4fc7f-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="4fc7f-215">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-215">Deprecated.</span></span> <span data-ttu-id="4fc7f-216">Pointe vers une fonction qui avertit l’hôte lorsqu’une e/s avec chevauchement (c’est-à-dire, asynchrone) sur un appareil est terminée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="4fc7f-217">LPTHREAD_START_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4fc7f-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="4fc7f-218">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-218">Deprecated.</span></span> <span data-ttu-id="4fc7f-219">Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="4fc7f-220">RunDll32ShimW, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="4fc7f-221">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-221">Deprecated.</span></span> <span data-ttu-id="4fc7f-222">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="4fc7f-223">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4fc7f-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="4fc7f-224">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-224">Deprecated.</span></span> <span data-ttu-id="4fc7f-225">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="4fc7f-226">Fonctions d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="4fc7f-226">Infrastructure functions</span></span>  
 <span data-ttu-id="4fc7f-227">Les fonctions de cette section sont destinées à être utilisées par l' .NET Framework uniquement.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="4fc7f-228">_CorDllMain, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="4fc7f-229">Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="4fc7f-230">_CorExeMain, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="4fc7f-231">Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="4fc7f-232">_CorExeMain2, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="4fc7f-233">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="4fc7f-234">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="4fc7f-235">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="4fc7f-236">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="4fc7f-237">_CorValidateImage, fonction</span><span class="sxs-lookup"><span data-stu-id="4fc7f-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="4fc7f-238">Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.</span><span class="sxs-lookup"><span data-stu-id="4fc7f-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc7f-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fc7f-239">See also</span></span>

- [<span data-ttu-id="4fc7f-240">Fonctions statiques globales de l'hébergement .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="4fc7f-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
