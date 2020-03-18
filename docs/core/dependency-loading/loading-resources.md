---
title: Algorithme de chargement d’assemblage satellite - .NET Core
description: Description des détails de l’algorithme de chargement d’assemblage par satellite dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70234634"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="0573a-103">Algorithme de chargement d’assemblage par satellite</span><span class="sxs-lookup"><span data-stu-id="0573a-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="0573a-104">Les assemblages satellitaires sont utilisés pour stocker des ressources localisées personnalisées pour la langue et la culture.</span><span class="sxs-lookup"><span data-stu-id="0573a-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="0573a-105">Les assemblages de satellites utilisent un algorithme de chargement différent de celui des assemblages gérés en général.</span><span class="sxs-lookup"><span data-stu-id="0573a-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="0573a-106">Quand les assemblages satellites sont-ils chargés?</span><span class="sxs-lookup"><span data-stu-id="0573a-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="0573a-107">Les assemblages satellitaires sont chargés lors du chargement d’une ressource localisée.</span><span class="sxs-lookup"><span data-stu-id="0573a-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="0573a-108">L’API de base pour <xref:System.Resources.ResourceManager?displayProperty=fullName> charger les ressources localisées est la classe.</span><span class="sxs-lookup"><span data-stu-id="0573a-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="0573a-109">En <xref:System.Resources.ResourceManager> fin de <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> compte, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>la classe appellera la méthode pour chacun .</span><span class="sxs-lookup"><span data-stu-id="0573a-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="0573a-110">Les API de niveau supérieur peuvent extraire l’API de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="0573a-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="0573a-111">Algorithm</span><span class="sxs-lookup"><span data-stu-id="0573a-111">Algorithm</span></span>

<span data-ttu-id="0573a-112">Le processus de secours pour les ressources .NET Core comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0573a-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="0573a-113">Déterminez `active` <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance.</span><span class="sxs-lookup"><span data-stu-id="0573a-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="0573a-114">Dans tous les `active` cas, l’exemple <xref:System.Runtime.Loader.AssemblyLoadContext>est celui de l’assemblée d’exécution .</span><span class="sxs-lookup"><span data-stu-id="0573a-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="0573a-115">L’instance `active` tente de charger un assemblage satellite pour la culture demandée dans l’ordre prioritaire par :</span><span class="sxs-lookup"><span data-stu-id="0573a-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="0573a-116">Vérification de son cache.</span><span class="sxs-lookup"><span data-stu-id="0573a-116">Checking its cache.</span></span>
    - <span data-ttu-id="0573a-117">Vérification de l’annuaire de l’assemblage actuellement exécutant pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> une `es-MX`sous-direction qui correspond à la demande (par exemple ).</span><span class="sxs-lookup"><span data-stu-id="0573a-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="0573a-118">Cette fonctionnalité n’a pas été implémentée dans .NET Core avant 3.0.</span><span class="sxs-lookup"><span data-stu-id="0573a-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="0573a-119">Sur Linux et macOS, la sous-direction est sensible aux cas et doit soit:</span><span class="sxs-lookup"><span data-stu-id="0573a-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="0573a-120">Exactement cas de match.</span><span class="sxs-lookup"><span data-stu-id="0573a-120">Exactly match case.</span></span>
        > - <span data-ttu-id="0573a-121">Soyez dans le cas inférieur.</span><span class="sxs-lookup"><span data-stu-id="0573a-121">Be in lower case.</span></span>

    - <span data-ttu-id="0573a-122">Si `active` c’est le <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> cas, en exécutant la logique [d’analyse par satellite par défaut (ressource).](default-probing.md#satellite-resource-assembly-probing)</span><span class="sxs-lookup"><span data-stu-id="0573a-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="0573a-123">Appel <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> de la fonction.</span><span class="sxs-lookup"><span data-stu-id="0573a-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="0573a-124">Élever <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> l’événement.</span><span class="sxs-lookup"><span data-stu-id="0573a-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="0573a-125">Élever <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement.</span><span class="sxs-lookup"><span data-stu-id="0573a-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="0573a-126">Si un assemblage satellite est chargé :</span><span class="sxs-lookup"><span data-stu-id="0573a-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="0573a-127">L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="0573a-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="0573a-128">L’assemblage est recherché pour la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="0573a-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="0573a-129">Si le temps d’exécution trouve la ressource dans l’assemblage, il l’utilise.</span><span class="sxs-lookup"><span data-stu-id="0573a-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="0573a-130">S’il ne trouve pas la ressource, il continue la recherche.</span><span class="sxs-lookup"><span data-stu-id="0573a-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0573a-131">Pour trouver une ressource dans l’assembly satellite, le runtime recherche le fichier de ressources demandé par <xref:System.Resources.ResourceManager> pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0573a-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0573a-132">Dans le fichier des ressources, il recherche le nom de ressource demandé.</span><span class="sxs-lookup"><span data-stu-id="0573a-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="0573a-133">En cas d’échec, la ressource est traitée comme introuvable.</span><span class="sxs-lookup"><span data-stu-id="0573a-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="0573a-134">Le temps d’exécution recherche ensuite les assemblées de la culture des parents à travers de nombreux niveaux potentiels, chaque fois répéter les étapes 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="0573a-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="0573a-135">Chaque culture n’a qu’un <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> seul parent, qui est défini par la propriété.</span><span class="sxs-lookup"><span data-stu-id="0573a-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="0573a-136">La recherche de cultures parentales <xref:System.Globalization.CultureInfo.Parent%2A> s’arrête lorsque la propriété d’une culture est <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0573a-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="0573a-137">Pour <xref:System.Globalization.CultureInfo.InvariantCulture>le , nous ne revenons pas aux étapes 2 & 3, mais plutôt continuer avec l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="0573a-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="0573a-138">Si la ressource n’est toujours pas trouvée, la ressource pour la culture par défaut (repli) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0573a-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="0573a-139">En règle générale, les ressources de la culture par défaut sont incluses dans l’assembly d’application principal.</span><span class="sxs-lookup"><span data-stu-id="0573a-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="0573a-140">Toutefois, vous <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> pouvez <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> spécifier pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="0573a-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0573a-141">Cette valeur indique que l’emplacement de repli ultime pour les ressources est un assemblage satellite plutôt que l’assemblage principal.</span><span class="sxs-lookup"><span data-stu-id="0573a-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0573a-142">La culture par défaut est le repli ultime.</span><span class="sxs-lookup"><span data-stu-id="0573a-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="0573a-143">Par conséquent, nous vous recommandons d’inclure toujours un ensemble exhaustif de ressources dans le fichier des ressources par défaut.</span><span class="sxs-lookup"><span data-stu-id="0573a-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="0573a-144">Vous empêchez ainsi la levée d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="0573a-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="0573a-145">En ayant un ensemble exhaustif, vous fournissez un repli pour toutes les ressources et assurez-vous qu’au moins une ressource est toujours présente pour l’utilisateur, même si elle n’est pas culturellement spécifique.</span><span class="sxs-lookup"><span data-stu-id="0573a-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="0573a-146">Enfin,</span><span class="sxs-lookup"><span data-stu-id="0573a-146">Finally,</span></span>
   - <span data-ttu-id="0573a-147">Si le temps d’exécution ne trouve pas de fichier de <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> ressources pour une culture par défaut (repli), une ou une exception est lancée.</span><span class="sxs-lookup"><span data-stu-id="0573a-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="0573a-148">Si le fichier de ressources est trouvé mais que `null`la ressource demandée n’est pas présente, la demande revient .</span><span class="sxs-lookup"><span data-stu-id="0573a-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
