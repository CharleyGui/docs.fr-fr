---
title: Informations de référence sur les API non managées
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: f7dd78b889129998dee31a22f5dd23325613b8ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092027"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="0a221-102">Informations de référence sur les API non managées</span><span class="sxs-lookup"><span data-stu-id="0a221-102">Unmanaged API Reference</span></span>
<span data-ttu-id="0a221-103">Cette section contient des informations sur les API non managées qui peuvent être utilisées par les applications associées à du code managé, comme les hôtes de runtime, les compilateurs, les désassembleurs, les obscurcisseurs, les débogueurs et les profileurs.</span><span class="sxs-lookup"><span data-stu-id="0a221-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a221-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0a221-104">In This Section</span></span>  
 [<span data-ttu-id="0a221-105">Types de données communs</span><span class="sxs-lookup"><span data-stu-id="0a221-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="0a221-106">Répertorie les types de données courants qui sont utilisés, en particulier dans les API de profilage et de débogage non managées.</span><span class="sxs-lookup"><span data-stu-id="0a221-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="0a221-107">ALink</span><span class="sxs-lookup"><span data-stu-id="0a221-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="0a221-108">Décrit une API ALink, qui prend en charge la création d'assemblys et de modules indépendants .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a221-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="0a221-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0a221-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="0a221-110">Prend en charge le module de création et de vérification des licences XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="0a221-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="0a221-111">Constantes</span><span class="sxs-lookup"><span data-stu-id="0a221-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="0a221-112">Décrit les constantes définies dans CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="0a221-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="0a221-113">[Attributs d'interface personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0a221-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="0a221-114">Décrit les attributs de l'interface personnalisée COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="0a221-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="0a221-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="0a221-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="0a221-116">Décrit l'API de débogage, qui permet à un débogueur de déboguer du code qui s'exécute dans un environnement CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="0a221-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="0a221-117">Magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="0a221-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="0a221-118">Décrit l'API du magasin de symboles des diagnostics, qui permet à un compilateur de générer des informations de symbole utilisables par un débogueur.</span><span class="sxs-lookup"><span data-stu-id="0a221-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="0a221-119">Fusion</span><span class="sxs-lookup"><span data-stu-id="0a221-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="0a221-120">Décrit l'API de fusion, qui permet à un hôte de runtime d'accéder aux propriétés des ressources d'une application pour pouvoir localiser les versions correctes de ces ressources pour l'application.</span><span class="sxs-lookup"><span data-stu-id="0a221-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="0a221-121">Hébergement</span><span class="sxs-lookup"><span data-stu-id="0a221-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="0a221-122">Décrit l'API d'hébergement, qui permet à des hôtes non managés d'intégrer le CLR dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="0a221-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="0a221-123">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="0a221-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="0a221-124">Décrit l'API de métadonnées, qui permet à un client comme un compilateur de générer les métadonnées d'un composant ou d'y accéder sans que les types soient chargés par le CLR.</span><span class="sxs-lookup"><span data-stu-id="0a221-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="0a221-125">Profilage</span><span class="sxs-lookup"><span data-stu-id="0a221-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="0a221-126">Décrit l'API de profilage, qui permet à un profileur de surveiller l'exécution d'un programme par le CLR.</span><span class="sxs-lookup"><span data-stu-id="0a221-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="0a221-127">Utilisation de noms forts</span><span class="sxs-lookup"><span data-stu-id="0a221-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="0a221-128">Décrit l'API de nommage fort, qui permet à un client d'administrer la signature par noms forts pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="0a221-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="0a221-129">WMI et compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="0a221-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="0a221-130">Décrit les API qui encapsulent des appels aux bibliothèques de Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="0a221-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="0a221-131">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="0a221-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="0a221-132">Décrit les deux fonctions et l'interface d'assistance utilisées par l'exportateur de bibliothèques de types (Tlbexp.exe) lors du processus de conversion « assembly vers bibliothèque de types ».</span><span class="sxs-lookup"><span data-stu-id="0a221-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a221-133">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="0a221-133">Related Sections</span></span>  
 [<span data-ttu-id="0a221-134">Guide de développement</span><span class="sxs-lookup"><span data-stu-id="0a221-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
