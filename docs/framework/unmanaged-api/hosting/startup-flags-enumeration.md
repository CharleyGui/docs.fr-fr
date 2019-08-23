---
title: STARTUP_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f39608b39be7d5c25b916fb20877aa73d6e5a8bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916234"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="5f6dc-102">STARTUP_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="5f6dc-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="5f6dc-103">Contient des valeurs qui indiquent le comportement de démarrage du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5f6dc-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="5f6dc-104">Par défaut, garbage collection n’est pas simultanée et seule la bibliothèque de classes de base est chargée dans la zone indépendante du domaine.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f6dc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f6dc-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5f6dc-106">Membres</span><span class="sxs-lookup"><span data-stu-id="5f6dc-106">Members</span></span>  
  
|<span data-ttu-id="5f6dc-107">Membre</span><span class="sxs-lookup"><span data-stu-id="5f6dc-107">Member</span></span>|<span data-ttu-id="5f6dc-108">Description</span><span class="sxs-lookup"><span data-stu-id="5f6dc-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="5f6dc-109">Spécifie que les garbage collection simultanées doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="5f6dc-110">Si l’appelant demande la build du serveur et garbage collection simultané sur un ordinateur à un seul processeur, la build de la station de travail et les garbage collection non simultanés sont exécutés à la place.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="5f6dc-111">**Remarque :**  Le garbage collection simultané n’est pas pris en charge dans les applications qui exécutent l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64).</span><span class="sxs-lookup"><span data-stu-id="5f6dc-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="5f6dc-112">Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="5f6dc-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="5f6dc-113">Spécifie que l’optimisation du chargeur doit se produire.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="5f6dc-114">Spécifie qu’aucun assembly n’est chargé comme indépendant du domaine.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="5f6dc-115">Spécifie que tous les assemblys sont chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="5f6dc-116">Spécifie que tous les assemblys avec nom fort sont chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="5f6dc-117">Spécifie que la stratégie de version du CLR ne sera pas appliquée à la version passée.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="5f6dc-118">La version exacte spécifiée du CLR sera chargée.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="5f6dc-119">Le shim n’évalue pas la stratégie pour déterminer la dernière version compatible.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="5f6dc-120">Spécifie que le runtime préféré sera défini, mais pas réellement démarré.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="5f6dc-121">Spécifie que le serveur garbage collection sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="5f6dc-122">Spécifie que garbage collection conserve l’adresse virtuelle utilisée.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="5f6dc-123">Spécifie que la combinaison d’une interface d’hébergement ne sera pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="5f6dc-124">Spécifie que l’emprunt d’identité ne doit pas être transmis entre des points asynchrones par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="5f6dc-125">Spécifie que la pile de threads complète ne doit pas être validée lorsque le thread commence à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="5f6dc-126">Spécifie que les emprunts d’identité et les emprunts d’identité managés obtenus via l’appel de code non managé sont transmis entre des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="5f6dc-127">Par défaut, seuls les emprunts d’identité managés sont transmis entre des points asynchrones.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="5f6dc-128">Spécifie que garbage collection utilise un espace moins validé lorsque la mémoire système est insuffisante.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="5f6dc-129">Voir `gcTrimCommitOnLowMemory` dans [optimisation de l’hébergement Web partagé](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="5f6dc-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="5f6dc-130">Spécifie que le suivi d’événements pour Windows (ETW) est activé pour les événements de common language runtime.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="5f6dc-131">À partir de Windows Vista, le suivi d’événements est toujours activé, donc cet indicateur n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="5f6dc-132">Consultez [contrôle](../../../../docs/framework/performance/controlling-logging.md)de la journalisation des .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="5f6dc-133">Spécifie que l’analyse des ressources du domaine d’application est activée.</span><span class="sxs-lookup"><span data-stu-id="5f6dc-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="5f6dc-134">Consultez l' <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> élément Property et [ \<appDomainResourceMonitoring >](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="5f6dc-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f6dc-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5f6dc-135">Requirements</span></span>  
 <span data-ttu-id="5f6dc-136">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f6dc-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f6dc-137">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f6dc-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f6dc-138">**Bibliothèque** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5f6dc-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f6dc-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f6dc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f6dc-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f6dc-140">See also</span></span>

- [<span data-ttu-id="5f6dc-141">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5f6dc-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
