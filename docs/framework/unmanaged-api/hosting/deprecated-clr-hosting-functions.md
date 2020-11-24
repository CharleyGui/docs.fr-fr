---
title: Fonction d'hébergement du CLR déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 9e19502672973f292991b72c7ea9b4fdc17f5707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673122"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="924e6-102">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="924e6-102">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="924e6-103">Cette section décrit les fonctions statiques globales non managées utilisées par les versions antérieures de l’API d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="924e6-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="924e6-104">À l’exception des fonctions d’infrastructure ( `_Cor*` fonctions), qui sont utilisées uniquement par le .NET Framework, ces fonctions ont été dépréciées dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="924e6-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="924e6-105">Fonctions d’activation</span><span class="sxs-lookup"><span data-stu-id="924e6-105">Activation functions</span></span>  

 [<span data-ttu-id="924e6-106">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="924e6-107">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-107">Deprecated.</span></span> <span data-ttu-id="924e6-108">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="924e6-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="924e6-109">CoInitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="924e6-110">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-110">Obsolete.</span></span> <span data-ttu-id="924e6-111">Pour initialiser le common language runtime (CLR), utilisez [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="924e6-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="924e6-112">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="924e6-113">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-113">Deprecated.</span></span> <span data-ttu-id="924e6-114">Garantit que le moteur d’exécution du CLR est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="924e6-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="924e6-115">Utilisez à la place la méthode [ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="924e6-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="924e6-116">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="924e6-117">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-117">Deprecated.</span></span> <span data-ttu-id="924e6-118">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="924e6-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="924e6-119">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="924e6-120">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-120">Deprecated.</span></span> <span data-ttu-id="924e6-121">Permet aux hôtes non managés de charger le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="924e6-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="924e6-122">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="924e6-123">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-123">Deprecated.</span></span> <span data-ttu-id="924e6-124">Charge le CLR dans un processus à l’aide des informations de version lues à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="924e6-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="924e6-125">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="924e6-126">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-126">Deprecated.</span></span> <span data-ttu-id="924e6-127">Permet aux hôtes non managés de charger le CLR dans un processus, et vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="924e6-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="924e6-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="924e6-129">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-129">Deprecated.</span></span> <span data-ttu-id="924e6-130">Permet aux hôtes de charger une version spécifiée du CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="924e6-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="924e6-131">GetCORRequiredVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="924e6-132">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-132">Deprecated.</span></span> <span data-ttu-id="924e6-133">Obtient le numéro de version CLR requis.</span><span class="sxs-lookup"><span data-stu-id="924e6-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="924e6-134">GetCORSystemDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="924e6-135">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-135">Deprecated.</span></span> <span data-ttu-id="924e6-136">Retourne le répertoire d’installation du CLR qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="924e6-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="924e6-137">GetRealProcAddress, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="924e6-138">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-138">Deprecated.</span></span> <span data-ttu-id="924e6-139">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du CLR.</span><span class="sxs-lookup"><span data-stu-id="924e6-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="924e6-140">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="924e6-141">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-141">Deprecated.</span></span> <span data-ttu-id="924e6-142">Obtient les informations de version et de répertoire relatives au CLR demandé par une application.</span><span class="sxs-lookup"><span data-stu-id="924e6-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="924e6-143">Fonctions de version du CLR</span><span class="sxs-lookup"><span data-stu-id="924e6-143">CLR version functions</span></span>  

 <span data-ttu-id="924e6-144">Les fonctions de cette section retournent une version CLR ; ils n’activent pas le CLR.</span><span class="sxs-lookup"><span data-stu-id="924e6-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="924e6-145">GetCORVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="924e6-146">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-146">Deprecated.</span></span> <span data-ttu-id="924e6-147">Retourne le numéro de version du CLR qui s’exécute dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="924e6-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="924e6-148">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="924e6-149">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-149">Deprecated.</span></span> <span data-ttu-id="924e6-150">Obtient les informations de version du CLR du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="924e6-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="924e6-151">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="924e6-152">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-152">Deprecated.</span></span> <span data-ttu-id="924e6-153">Obtient le numéro de version du CLR demandé par l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="924e6-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="924e6-154">Si cette version n’est pas installée, obtient la version la plus récente installée avant la version demandée.</span><span class="sxs-lookup"><span data-stu-id="924e6-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="924e6-155">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="924e6-156">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-156">Deprecated.</span></span> <span data-ttu-id="924e6-157">Obtient les informations de version CLR appropriées pour la classe avec le CLSID spécifié.</span><span class="sxs-lookup"><span data-stu-id="924e6-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="924e6-158">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="924e6-159">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-159">Deprecated.</span></span> <span data-ttu-id="924e6-160">Obtient le numéro de version du CLR qui est associé au handle de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="924e6-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="924e6-161">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="924e6-162">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-162">Deprecated.</span></span> <span data-ttu-id="924e6-163">Permet à l’hôte de déterminer la version du CLR qui sera utilisée dans le processus avant d’initialiser explicitement le CLR.</span><span class="sxs-lookup"><span data-stu-id="924e6-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="924e6-164">Fonctions d’hébergement</span><span class="sxs-lookup"><span data-stu-id="924e6-164">Hosting functions</span></span>  

 [<span data-ttu-id="924e6-165">CallFunctionShim, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="924e6-166">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-166">Deprecated.</span></span> <span data-ttu-id="924e6-167">Effectue un appel à la fonction qui a le nom et les paramètres spécifiés dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="924e6-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="924e6-168">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="924e6-169">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-169">Deprecated.</span></span> <span data-ttu-id="924e6-170">Décharge un assembly COM du processus.</span><span class="sxs-lookup"><span data-stu-id="924e6-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="924e6-171">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="924e6-172">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-172">Deprecated.</span></span> <span data-ttu-id="924e6-173">Arrête le processus non managé actuel.</span><span class="sxs-lookup"><span data-stu-id="924e6-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="924e6-174">CorLaunchApplication, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="924e6-175">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-175">Deprecated.</span></span> <span data-ttu-id="924e6-176">Démarre l’application au chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et d’autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="924e6-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="924e6-177">CorMarkThreadInThreadPool, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="924e6-178">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-178">Deprecated.</span></span> <span data-ttu-id="924e6-179">Marque le thread du pool de threads en cours d’exécution pour l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="924e6-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="924e6-180">À partir de la version 2,0 de .NET Framework, cette fonction n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="924e6-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="924e6-181">Elle n’est pas obligatoire et peut être supprimée de votre code.</span><span class="sxs-lookup"><span data-stu-id="924e6-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="924e6-182">CoUninitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="924e6-183">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-183">Obsolete.</span></span> <span data-ttu-id="924e6-184">Le CLR ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="924e6-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="924e6-185">CoUninitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="924e6-186">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="924e6-187">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="924e6-188">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-188">Deprecated.</span></span> <span data-ttu-id="924e6-189">Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.</span><span class="sxs-lookup"><span data-stu-id="924e6-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="924e6-190">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="924e6-191">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-191">Deprecated.</span></span> <span data-ttu-id="924e6-192">Crée un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="924e6-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="924e6-193">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="924e6-194">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-194">Deprecated.</span></span> <span data-ttu-id="924e6-195">Détruit un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="924e6-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="924e6-196">FExecuteInAppDomainCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="924e6-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="924e6-197">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-197">Deprecated.</span></span> <span data-ttu-id="924e6-198">Pointe vers une fonction que le CLR appelle pour exécuter du code managé.</span><span class="sxs-lookup"><span data-stu-id="924e6-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="924e6-199">FLockClrVersionCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="924e6-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="924e6-200">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-200">Deprecated.</span></span> <span data-ttu-id="924e6-201">Pointe vers une fonction que le CLR appelle pour notifier l’hôte que l’initialisation a démarré ou est terminée.</span><span class="sxs-lookup"><span data-stu-id="924e6-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="924e6-202">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="924e6-203">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-203">Deprecated.</span></span> <span data-ttu-id="924e6-204">Obtient un pointeur vers une interface qui permet au CLR de gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="924e6-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="924e6-205">LoadLibraryShim, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="924e6-206">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-206">Deprecated.</span></span> <span data-ttu-id="924e6-207">Charge une version spécifiée d’un .NET Framework DLL.</span><span class="sxs-lookup"><span data-stu-id="924e6-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="924e6-208">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="924e6-209">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-209">Deprecated.</span></span> <span data-ttu-id="924e6-210">Convertit une valeur HRESULT en message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="924e6-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="924e6-211">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="924e6-212">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-212">Deprecated.</span></span> <span data-ttu-id="924e6-213">Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="924e6-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="924e6-214">LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="924e6-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="924e6-215">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-215">Deprecated.</span></span> <span data-ttu-id="924e6-216">Pointe vers une fonction qui avertit l’hôte lorsqu’une e/s avec chevauchement (c’est-à-dire, asynchrone) sur un appareil est terminée.</span><span class="sxs-lookup"><span data-stu-id="924e6-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="924e6-217">LPTHREAD_START_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="924e6-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="924e6-218">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-218">Deprecated.</span></span> <span data-ttu-id="924e6-219">Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="924e6-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="924e6-220">RunDll32ShimW, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="924e6-221">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-221">Deprecated.</span></span> <span data-ttu-id="924e6-222">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="924e6-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="924e6-223">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="924e6-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="924e6-224">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="924e6-224">Deprecated.</span></span> <span data-ttu-id="924e6-225">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="924e6-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="924e6-226">Fonctions d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="924e6-226">Infrastructure functions</span></span>  

 <span data-ttu-id="924e6-227">Les fonctions de cette section sont destinées à être utilisées par l' .NET Framework uniquement.</span><span class="sxs-lookup"><span data-stu-id="924e6-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="924e6-228">_CorDllMain, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="924e6-229">Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="924e6-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="924e6-230">_CorExeMain, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="924e6-231">Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="924e6-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="924e6-232">_CorExeMain2, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="924e6-233">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="924e6-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="924e6-234">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="924e6-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="924e6-235">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="924e6-236">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="924e6-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="924e6-237">_CorValidateImage, fonction</span><span class="sxs-lookup"><span data-stu-id="924e6-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="924e6-238">Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.</span><span class="sxs-lookup"><span data-stu-id="924e6-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924e6-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="924e6-239">See also</span></span>

- [<span data-ttu-id="924e6-240">Fonctions statiques globales de l'hébergement .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="924e6-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
