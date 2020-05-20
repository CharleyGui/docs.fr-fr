---
title: Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: a524c0b0e01fbde95ce2341874511960b3e5738e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616851"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="81560-102">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="81560-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="81560-103">Cette section décrit les interfaces que les hôtes non gérés peuvent utiliser pour intégrer le common language runtime (CLR) des .NET Framework 4, .NET Framework 4,5 et versions ultérieures dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="81560-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="81560-104">Ces interfaces fournissent des méthodes permettant à un hôte de configurer et de charger le runtime dans un processus.</span><span class="sxs-lookup"><span data-stu-id="81560-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="81560-105">À partir du .NET Framework 4, toutes les interfaces d’hébergement présentent les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="81560-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="81560-106">Ils utilisent la gestion de la durée de vie ( `AddRef` et `Release` ), l’encapsulation (contexte implicite) et `QueryInterface` à partir de com.</span><span class="sxs-lookup"><span data-stu-id="81560-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="81560-107">Ils n’utilisent pas les types COM tels que `BSTR` , `SAFEARRAY` ou `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="81560-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="81560-108">Il n’existe pas de modèles cloisonnés, d’agrégation ou d’activation du Registre qui utilisent la [fonction CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span><span class="sxs-lookup"><span data-stu-id="81560-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81560-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="81560-109">In This Section</span></span>  
 [<span data-ttu-id="81560-110">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="81560-110">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="81560-111">Fournit des méthodes qui inspectent la mémoire et l’utilisation de l’UC d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="81560-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="81560-112">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="81560-112">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="81560-113">Permet à l’hôte de spécifier le gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="81560-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="81560-114">ICLRGCManager2, interface</span><span class="sxs-lookup"><span data-stu-id="81560-114">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="81560-115">Fournit la méthode [setgcstartuplimitsex,](iclrgcmanager2-setgcstartuplimitsex-method.md) , qui permet à un hôte de définir la taille du segment garbage collection et la taille maximale de la génération 0 du système garbage collection à des valeurs supérieures à `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="81560-115">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="81560-116">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="81560-116">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="81560-117">Fournit des méthodes qui retournent une version spécifique du CLR, répertorient tous les CLR installés, répertorient tous les runtimes in-process, retournent l’interface d’activation et découvrent la version CLR utilisée pour compiler un assembly.</span><span class="sxs-lookup"><span data-stu-id="81560-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="81560-118">ICLRMetaHostPolicy, interface</span><span class="sxs-lookup"><span data-stu-id="81560-118">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="81560-119">Fournit la méthode [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) qui fournit une interface CLR basée sur des critères de stratégie, un assembly managé, une version et un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="81560-119">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="81560-120">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="81560-120">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="81560-121">Fournit des méthodes qui retournent des informations sur un Runtime spécifique, y compris la version, le répertoire et l’état de chargement.</span><span class="sxs-lookup"><span data-stu-id="81560-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="81560-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="81560-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="81560-123">Fournit des fonctions statiques globales de base pour la signature d’assemblys avec des noms forts.</span><span class="sxs-lookup"><span data-stu-id="81560-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="81560-124">Toutes les méthodes [ICLRStrongName](iclrstrongname-interface.md) retournent des valeurs HRESULT com standard.</span><span class="sxs-lookup"><span data-stu-id="81560-124">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="81560-125">ICLRStrongName2, interface</span><span class="sxs-lookup"><span data-stu-id="81560-125">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="81560-126">Offre la possibilité de créer des noms forts à l’aide du groupe SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).</span><span class="sxs-lookup"><span data-stu-id="81560-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="81560-127">ICLRTask2, interface</span><span class="sxs-lookup"><span data-stu-id="81560-127">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="81560-128">Fournit toutes les fonctionnalités de l' [interface ICLRTask](iclrtask-interface.md); en outre, fournit des méthodes qui permettent de retarder les abandons de thread sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="81560-128">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="81560-129">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="81560-129">Related Sections</span></span>  
 [<span data-ttu-id="81560-130">Interfaces d'hébergement du CLR et coclasses déconseillées</span><span class="sxs-lookup"><span data-stu-id="81560-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="81560-131">Décrit les interfaces d’hébergement fournies avec les versions de .NET Framework 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="81560-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="81560-132">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="81560-132">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="81560-133">Décrit les interfaces d’hébergement fournies avec les versions .NET Framework 2,0, 3,0 et 3,5.</span><span class="sxs-lookup"><span data-stu-id="81560-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="81560-134">Hébergement</span><span class="sxs-lookup"><span data-stu-id="81560-134">Hosting</span></span>](index.md)  
 <span data-ttu-id="81560-135">Présente l’hébergement dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81560-135">Introduces hosting in the .NET Framework.</span></span>
