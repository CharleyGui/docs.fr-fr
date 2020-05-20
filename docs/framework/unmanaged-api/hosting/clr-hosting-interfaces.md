---
title: Interfaces d'hébergement du CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616838"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="597af-102">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="597af-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="597af-103">Cette section décrit les interfaces que les hôtes non managés peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="597af-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="597af-104">Les informations se rapportent à la version 2,0 de .NET Framework et aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="597af-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="597af-105">Ces interfaces permettent à l’hôte de contrôler beaucoup plus d’aspects du runtime que ce qui était possible dans les versions 1,0 et 1,1, et offrent une intégration plus étroite entre le CLR et le modèle d’exécution de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="597af-106">Dans les versions 1,0 et 1,1 de .NET Framework, le modèle d’hébergement permettait à un hôte non géré de charger le CLR dans un processus, de configurer certains paramètres et de recevoir des notifications d’événements.</span><span class="sxs-lookup"><span data-stu-id="597af-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="597af-107">Toutefois, en général, l’hôte et le CLR s’exécutaient indépendamment dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="597af-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="597af-108">Dans la .NET Framework version 2,0 et les versions ultérieures, les nouvelles couches d’abstraction permettent à l’hôte de fournir un grand nombre des ressources actuellement fournies par les types dans l’assembly Win32, et d’étendre l’ensemble de fonctionnalités que l’hôte peut configurer.</span><span class="sxs-lookup"><span data-stu-id="597af-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="597af-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="597af-109">In This Section</span></span>  
 [<span data-ttu-id="597af-110">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="597af-110">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="597af-111">Fournit une méthode qui exécute un rappel pour un événement inscrit.</span><span class="sxs-lookup"><span data-stu-id="597af-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="597af-112">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="597af-112">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="597af-113">Fournit des méthodes pour effectuer des rappels dans un cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="597af-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="597af-114">IAppDomainBinding, interface</span><span class="sxs-lookup"><span data-stu-id="597af-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="597af-115">Fournit des méthodes pour définir la configuration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="597af-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="597af-116">ICatalogServices, interface</span><span class="sxs-lookup"><span data-stu-id="597af-116">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="597af-117">Fournit des méthodes pour les services de catalogage.</span><span class="sxs-lookup"><span data-stu-id="597af-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="597af-118">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)</span><span class="sxs-lookup"><span data-stu-id="597af-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="597af-119">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="597af-120">Fournit des méthodes qui prennent en charge la communication entre l’hôte et le CLR sur les assemblys.</span><span class="sxs-lookup"><span data-stu-id="597af-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="597af-121">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="597af-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="597af-122">Gère une liste d’assemblys qui sont chargés par le CLR et non par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="597af-123">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="597af-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="597af-124">Fournit des méthodes pour que l’hôte ait accès à et configure divers aspects de, le CLR.</span><span class="sxs-lookup"><span data-stu-id="597af-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="597af-125">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="597af-126">Fournit des méthodes qui permettent à un hôte d’associer un ensemble de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="597af-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="597af-127">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-127">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="597af-128">Fournit des méthodes qui permettent à l’hôte de configurer des dumps de tas personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="597af-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="597af-129">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-129">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="597af-130">Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du CLR.</span><span class="sxs-lookup"><span data-stu-id="597af-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="597af-131">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-131">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="597af-132">Fournit des méthodes pour que l’hôte évalue et communique les modifications apportées aux informations de stratégie pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="597af-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="597af-133">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-133">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="597af-134">Permet à l’hôte de bloquer des classes, des méthodes, des propriétés et des champs managés spécifiques de s’exécuter dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="597af-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="597af-135">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="597af-136">Implémente une méthode de rappel qui permet à l’hôte de notifier le CLR de l’état des demandes d’e/s spécifiées.</span><span class="sxs-lookup"><span data-stu-id="597af-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="597af-137">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="597af-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="597af-138">Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de la `CreateMemoryResourceNotification` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="597af-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="597af-139">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="597af-140">Fournit des méthodes qui permettent à l’hôte d’inscrire et d’annuler l’enregistrement des rappels pour les événements CLR.</span><span class="sxs-lookup"><span data-stu-id="597af-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="597af-141">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="597af-142">Fournit des méthodes qui permettent à l’hôte de spécifier des actions de stratégie à prendre en cas d’échecs et de délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="597af-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="597af-143">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="597af-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="597af-144">Fournit des méthodes qui permettent à l’hôte d’accéder aux identités de détection d’un assembly à l’aide des informations d’identité de l’assembly qui sont internes au CLR, sans avoir à créer ou à comprendre cette identité.</span><span class="sxs-lookup"><span data-stu-id="597af-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="597af-145">ICLRReferenceAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="597af-145">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="597af-146">Fournit des méthodes qui permettent à l’hôte de manipuler l’ensemble d’assemblys référencés par un fichier ou un flux à l’aide de données d’identité d’assembly qui sont internes au CLR, sans avoir à créer ou à comprendre ces identités.</span><span class="sxs-lookup"><span data-stu-id="597af-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="597af-147">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="597af-147">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="597af-148">Fournit des fonctionnalités similaires à [ICorRuntimeHost](icorruntimehost-interface.md), avec une méthode supplémentaire pour définir l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-148">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="597af-149">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-149">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="597af-150">Fournit des méthodes permettant à l’hôte d’obtenir des informations sur les tâches demandées et de détecter les interblocages dans son implémentation de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="597af-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="597af-151">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="597af-151">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="597af-152">Fournit des méthodes qui permettent à l’hôte d’effectuer des demandes du CLR ou de fournir une notification au CLR sur la tâche associée.</span><span class="sxs-lookup"><span data-stu-id="597af-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="597af-153">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="597af-154">Fournit des méthodes qui permettent à l’hôte de demander explicitement que le CLR crée une nouvelle tâche, d’obtenir la tâche en cours d’exécution et de définir la langue géographique et la culture de la tâche.</span><span class="sxs-lookup"><span data-stu-id="597af-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="597af-155">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="597af-155">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="597af-156">Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.</span><span class="sxs-lookup"><span data-stu-id="597af-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="597af-157">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="597af-157">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="597af-158">Fournit des méthodes pour configurer le CLR.</span><span class="sxs-lookup"><span data-stu-id="597af-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="597af-159">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="597af-159">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="597af-160">Fournit des méthodes pour accéder au pool de threads.</span><span class="sxs-lookup"><span data-stu-id="597af-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="597af-161">IDebuggerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="597af-161">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="597af-162">Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.</span><span class="sxs-lookup"><span data-stu-id="597af-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="597af-163">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="597af-163">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="597af-164">Fournit des méthodes pour notifier l’hôte concernant le blocage et le déblocage de threads par les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="597af-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="597af-165">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="597af-165">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="597af-166">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et pour contrôler certains aspects de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="597af-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="597af-167">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="597af-167">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="597af-168">Fournit la méthode [setgcstartuplimitsex,](igchost2-setgcstartuplimitsex-method.md) qui permet à un hôte de définir la taille du segment garbage collection et la taille maximale de la génération zéro du système garbage collection sur des valeurs supérieures à `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="597af-168">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="597af-169">IGCHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="597af-169">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="597af-170">Fournit une méthode qui permet au garbage collector de demander à l’hôte de modifier les limites de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="597af-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="597af-171">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="597af-171">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="597af-172">Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="597af-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="597af-173">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-173">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="597af-174">Fournit des méthodes qui permettent à un hôte de spécifier des jeux d’assemblys qui doivent être chargés par le CLR ou par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="597af-175">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="597af-175">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="597af-176">Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du CLR.</span><span class="sxs-lookup"><span data-stu-id="597af-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="597af-177">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="597af-177">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="597af-178">Fournit une représentation d’un événement de réinitialisation automatique implémenté par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="597af-179">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="597af-179">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="597af-180">Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.</span><span class="sxs-lookup"><span data-stu-id="597af-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="597af-181">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="597af-181">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="597af-182">Sert de représentation de l’hôte d’une section critique pour le Threading.</span><span class="sxs-lookup"><span data-stu-id="597af-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="597af-183">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-183">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="597af-184">Fournit des méthodes qui notifient l’hôte d’événements dans le mécanisme de garbage collection implémenté par le CLR.</span><span class="sxs-lookup"><span data-stu-id="597af-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="597af-185">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-185">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="597af-186">Fournit des méthodes qui permettent au CLR d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="597af-187">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="597af-187">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="597af-188">Fournit des méthodes pour que le CLR demande des allocations affinées à partir du tas par le biais de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="597af-189">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="597af-189">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="597af-190">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="597af-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="597af-191">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-191">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="597af-192">Fournit des méthodes pour que le CLR effectue des demandes de mémoire virtuelle par le biais de l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="597af-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="597af-193">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-193">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="597af-194">Fournit des méthodes qui notifient l’hôte des actions exécutées par le CLR en cas d’abandons, de délais d’attente ou d’échecs.</span><span class="sxs-lookup"><span data-stu-id="597af-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="597af-195">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="597af-195">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="597af-196">Permet au CLR de conserver les informations de contexte de sécurité implémentées par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="597af-197">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-197">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="597af-198">Fournit des méthodes qui permettent d’accéder au contexte de sécurité du thread en cours d’exécution et de le contrôler.</span><span class="sxs-lookup"><span data-stu-id="597af-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="597af-199">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="597af-199">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="597af-200">Fournit une représentation d’un sémaphore implémenté par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="597af-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="597af-201">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-201">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="597af-202">Fournit des méthodes pour que le CLR crée des primitives de synchronisation en appelant l’hôte, au lieu d’utiliser les fonctions de synchronisation Win32.</span><span class="sxs-lookup"><span data-stu-id="597af-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="597af-203">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="597af-203">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="597af-204">Fournit des méthodes qui permettent au CLR de communiquer avec l’hôte pour gérer des tâches.</span><span class="sxs-lookup"><span data-stu-id="597af-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="597af-205">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-205">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="597af-206">Fournit des méthodes qui permettent au CLR d’utiliser des tâches via l’hôte au lieu d’utiliser le thread de système d’exploitation standard ou les fonctions Fiber.</span><span class="sxs-lookup"><span data-stu-id="597af-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="597af-207">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="597af-207">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="597af-208">Fournit des méthodes permettant au CLR de configurer le pool de threads et de mettre en file d’attente des éléments de travail dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="597af-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="597af-209">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="597af-209">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="597af-210">Fournit des méthodes pour contrôler un objet managé.</span><span class="sxs-lookup"><span data-stu-id="597af-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="597af-211">IObjectHandle</span><span class="sxs-lookup"><span data-stu-id="597af-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="597af-212">Fournit une méthode pour désencapsuler les objets marshalés par valeur à partir de l’indirection.</span><span class="sxs-lookup"><span data-stu-id="597af-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="597af-213">ITypeName, interface</span><span class="sxs-lookup"><span data-stu-id="597af-213">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="597af-214">Fournit des méthodes pour obtenir des informations de nom de type.</span><span class="sxs-lookup"><span data-stu-id="597af-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="597af-215">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)</span><span class="sxs-lookup"><span data-stu-id="597af-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="597af-216">ITypeNameBuilder, interface</span><span class="sxs-lookup"><span data-stu-id="597af-216">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="597af-217">Fournit des méthodes pour la génération d’un nom de type.</span><span class="sxs-lookup"><span data-stu-id="597af-217">Provides methods for building a type name.</span></span> <span data-ttu-id="597af-218">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)</span><span class="sxs-lookup"><span data-stu-id="597af-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="597af-219">ITypeNameFactory, interface</span><span class="sxs-lookup"><span data-stu-id="597af-219">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="597af-220">Fournit des méthodes pour décomposer un nom de type.</span><span class="sxs-lookup"><span data-stu-id="597af-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="597af-221">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)</span><span class="sxs-lookup"><span data-stu-id="597af-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="597af-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="597af-222">"IValidator"</span></span>  
 <span data-ttu-id="597af-223">Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.</span><span class="sxs-lookup"><span data-stu-id="597af-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="597af-224">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="597af-224">Related Sections</span></span>  
 [<span data-ttu-id="597af-225">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="597af-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="597af-226">Contient des rubriques qui décrivent les interfaces d’hébergement fournies dans le .NET Framework version 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="597af-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="597af-227">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="597af-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="597af-228">Contient des rubriques qui décrivent les interfaces d’hébergement fournies dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="597af-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
