---
title: Fonction d'hébergement du CLR déconseillées
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 083d0ff285abb4a99ad05c791bc504ff7f282c6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504366"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="cc5ff-102">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="cc5ff-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="cc5ff-103">Cette section décrit les fonctions statiques globales non managées utilisées par les versions antérieures de l’API d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="cc5ff-104">À l’exception des fonctions d’infrastructure ( `_Cor*` fonctions), qui sont utilisées uniquement par le .NET Framework, ces fonctions ont été dépréciées dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="cc5ff-105">Fonctions d’activation</span><span class="sxs-lookup"><span data-stu-id="cc5ff-105">Activation functions</span></span>  
 [<span data-ttu-id="cc5ff-106">ClrCreateManagedInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="cc5ff-107">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-107">Deprecated.</span></span> <span data-ttu-id="cc5ff-108">Crée une instance du type managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="cc5ff-109">CoInitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="cc5ff-110">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-110">Obsolete.</span></span> <span data-ttu-id="cc5ff-111">Pour initialiser le common language runtime (CLR), utilisez [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="cc5ff-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="cc5ff-112">CoInitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="cc5ff-113">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-113">Deprecated.</span></span> <span data-ttu-id="cc5ff-114">Garantit que le moteur d’exécution du CLR est chargé dans un processus.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="cc5ff-115">Utilisez à la place la méthode [ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cc5ff-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="cc5ff-116">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="cc5ff-117">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-117">Deprecated.</span></span> <span data-ttu-id="cc5ff-118">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="cc5ff-119">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="cc5ff-120">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-120">Deprecated.</span></span> <span data-ttu-id="cc5ff-121">Permet aux hôtes non managés de charger le CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="cc5ff-122">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="cc5ff-123">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-123">Deprecated.</span></span> <span data-ttu-id="cc5ff-124">Charge le CLR dans un processus à l’aide des informations de version lues à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="cc5ff-125">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="cc5ff-126">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-126">Deprecated.</span></span> <span data-ttu-id="cc5ff-127">Permet aux hôtes non managés de charger le CLR dans un processus, et vous permet de définir des indicateurs pour spécifier le comportement du CLR.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="cc5ff-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="cc5ff-129">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-129">Deprecated.</span></span> <span data-ttu-id="cc5ff-130">Permet aux hôtes de charger une version spécifiée du CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="cc5ff-131">GetCORRequiredVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="cc5ff-132">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-132">Deprecated.</span></span> <span data-ttu-id="cc5ff-133">Obtient le numéro de version CLR requis.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="cc5ff-134">GetCORSystemDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="cc5ff-135">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-135">Deprecated.</span></span> <span data-ttu-id="cc5ff-136">Retourne le répertoire d’installation du CLR qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="cc5ff-137">GetRealProcAddress, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="cc5ff-138">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-138">Deprecated.</span></span> <span data-ttu-id="cc5ff-139">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du CLR.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="cc5ff-140">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="cc5ff-141">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-141">Deprecated.</span></span> <span data-ttu-id="cc5ff-142">Obtient les informations de version et de répertoire relatives au CLR demandé par une application.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="cc5ff-143">Fonctions de version du CLR</span><span class="sxs-lookup"><span data-stu-id="cc5ff-143">CLR version functions</span></span>  
 <span data-ttu-id="cc5ff-144">Les fonctions de cette section retournent une version CLR ; ils n’activent pas le CLR.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="cc5ff-145">GetCORVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="cc5ff-146">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-146">Deprecated.</span></span> <span data-ttu-id="cc5ff-147">Retourne le numéro de version du CLR qui s’exécute dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="cc5ff-148">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="cc5ff-149">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-149">Deprecated.</span></span> <span data-ttu-id="cc5ff-150">Obtient les informations de version du CLR du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="cc5ff-151">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="cc5ff-152">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-152">Deprecated.</span></span> <span data-ttu-id="cc5ff-153">Obtient le numéro de version du CLR demandé par l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="cc5ff-154">Si cette version n’est pas installée, obtient la version la plus récente installée avant la version demandée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="cc5ff-155">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="cc5ff-156">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-156">Deprecated.</span></span> <span data-ttu-id="cc5ff-157">Obtient les informations de version CLR appropriées pour la classe avec le CLSID spécifié.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="cc5ff-158">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="cc5ff-159">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-159">Deprecated.</span></span> <span data-ttu-id="cc5ff-160">Obtient le numéro de version du CLR qui est associé au handle de processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="cc5ff-161">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="cc5ff-162">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-162">Deprecated.</span></span> <span data-ttu-id="cc5ff-163">Permet à l’hôte de déterminer la version du CLR qui sera utilisée dans le processus avant d’initialiser explicitement le CLR.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="cc5ff-164">Fonctions d’hébergement</span><span class="sxs-lookup"><span data-stu-id="cc5ff-164">Hosting functions</span></span>  
 [<span data-ttu-id="cc5ff-165">CallFunctionShim, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="cc5ff-166">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-166">Deprecated.</span></span> <span data-ttu-id="cc5ff-167">Effectue un appel à la fonction qui a le nom et les paramètres spécifiés dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="cc5ff-168">CoEEShutDownCOM, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="cc5ff-169">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-169">Deprecated.</span></span> <span data-ttu-id="cc5ff-170">Décharge un assembly COM du processus.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="cc5ff-171">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="cc5ff-172">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-172">Deprecated.</span></span> <span data-ttu-id="cc5ff-173">Arrête le processus non managé actuel.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="cc5ff-174">CorLaunchApplication, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="cc5ff-175">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-175">Deprecated.</span></span> <span data-ttu-id="cc5ff-176">Démarre l’application au chemin d’accès réseau spécifié, à l’aide des manifestes spécifiés et d’autres données d’application.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="cc5ff-177">CorMarkThreadInThreadPool, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="cc5ff-178">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-178">Deprecated.</span></span> <span data-ttu-id="cc5ff-179">Marque le thread du pool de threads en cours d’exécution pour l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="cc5ff-180">À partir de la version 2,0 de .NET Framework, cette fonction n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="cc5ff-181">Elle n’est pas obligatoire et peut être supprimée de votre code.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="cc5ff-182">CoUninitializeCor, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="cc5ff-183">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-183">Obsolete.</span></span> <span data-ttu-id="cc5ff-184">Le CLR ne peut pas être déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="cc5ff-185">CoUninitializeEE, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="cc5ff-186">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="cc5ff-187">CreateDebuggingInterfaceFromVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="cc5ff-188">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-188">Deprecated.</span></span> <span data-ttu-id="cc5ff-189">Crée un objet [ICorDebug](../debugging/icordebug-interface.md) basé sur les informations de version spécifiées.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="cc5ff-190">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="cc5ff-191">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-191">Deprecated.</span></span> <span data-ttu-id="cc5ff-192">Crée un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="cc5ff-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="cc5ff-193">DestroyICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="cc5ff-194">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-194">Deprecated.</span></span> <span data-ttu-id="cc5ff-195">Détruit un objet [ICeeFileGen](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="cc5ff-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="cc5ff-196">FExecuteInAppDomainCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="cc5ff-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="cc5ff-197">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-197">Deprecated.</span></span> <span data-ttu-id="cc5ff-198">Pointe vers une fonction que le CLR appelle pour exécuter du code managé.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="cc5ff-199">FLockClrVersionCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="cc5ff-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="cc5ff-200">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-200">Deprecated.</span></span> <span data-ttu-id="cc5ff-201">Pointe vers une fonction que le CLR appelle pour notifier l’hôte que l’initialisation a démarré ou est terminée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="cc5ff-202">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="cc5ff-203">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-203">Deprecated.</span></span> <span data-ttu-id="cc5ff-204">Obtient un pointeur vers une interface qui permet au CLR de gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="cc5ff-205">LoadLibraryShim, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="cc5ff-206">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-206">Deprecated.</span></span> <span data-ttu-id="cc5ff-207">Charge une version spécifiée d’un .NET Framework DLL.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="cc5ff-208">LoadStringRC, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="cc5ff-209">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-209">Deprecated.</span></span> <span data-ttu-id="cc5ff-210">Convertit une valeur HRESULT en message d’erreur à l’aide de la culture par défaut du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="cc5ff-211">LoadStringRCEx, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="cc5ff-212">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-212">Deprecated.</span></span> <span data-ttu-id="cc5ff-213">Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="cc5ff-214">LPOVERLAPPED_COMPLETION_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="cc5ff-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="cc5ff-215">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-215">Deprecated.</span></span> <span data-ttu-id="cc5ff-216">Pointe vers une fonction qui avertit l’hôte lorsqu’une e/s avec chevauchement (c’est-à-dire, asynchrone) sur un appareil est terminée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="cc5ff-217">LPTHREAD_START_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="cc5ff-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="cc5ff-218">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-218">Deprecated.</span></span> <span data-ttu-id="cc5ff-219">Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="cc5ff-220">RunDll32ShimW, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="cc5ff-221">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-221">Deprecated.</span></span> <span data-ttu-id="cc5ff-222">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="cc5ff-223">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="cc5ff-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="cc5ff-224">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-224">Deprecated.</span></span> <span data-ttu-id="cc5ff-225">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="cc5ff-226">Fonctions d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="cc5ff-226">Infrastructure functions</span></span>  
 <span data-ttu-id="cc5ff-227">Les fonctions de cette section sont destinées à être utilisées par l' .NET Framework uniquement.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="cc5ff-228">_CorDllMain, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="cc5ff-229">Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="cc5ff-230">_CorExeMain, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="cc5ff-231">Initialise le CLR, localise le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="cc5ff-232">_CorExeMain2, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="cc5ff-233">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="cc5ff-234">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="cc5ff-235">_CorImageUnloading, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="cc5ff-236">Notifie le chargeur lorsque les images de modules managés sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="cc5ff-237">_CorValidateImage, fonction</span><span class="sxs-lookup"><span data-stu-id="cc5ff-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="cc5ff-238">Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.</span><span class="sxs-lookup"><span data-stu-id="cc5ff-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc5ff-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc5ff-239">See also</span></span>

- [<span data-ttu-id="cc5ff-240">Fonctions statiques globales de l'hébergement .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="cc5ff-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
