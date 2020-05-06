---
title: Algorithme de chargement d’assembly satellite-.NET Core
description: Description des détails de l’algorithme de chargement d’assembly satellite dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 17f29a9aca79019daa91736e586bf1b6b753a9ec
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859531"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="6fe8f-103">Algorithme de chargement d’assembly satellite</span><span class="sxs-lookup"><span data-stu-id="6fe8f-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="6fe8f-104">Les assemblys satellites sont utilisés pour stocker les ressources localisées personnalisées pour la langue et la culture.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="6fe8f-105">Les assemblys satellites utilisent un algorithme de chargement différent des assemblys managés généraux.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="6fe8f-106">Quand les assemblys satellites sont-ils chargés ?</span><span class="sxs-lookup"><span data-stu-id="6fe8f-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="6fe8f-107">Les assemblys satellites sont chargés lors du chargement d’une ressource localisée.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="6fe8f-108">L’API de base pour charger des ressources localisées <xref:System.Resources.ResourceManager?displayProperty=fullName> est la classe.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="6fe8f-109">Finalement, <xref:System.Resources.ResourceManager> la classe appellera la <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> méthode pour chaque <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6fe8f-110">Les API de niveau supérieur peuvent faire abstraction de l’API de bas niveau.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="6fe8f-111">Algorithm</span><span class="sxs-lookup"><span data-stu-id="6fe8f-111">Algorithm</span></span>

<span data-ttu-id="6fe8f-112">Le processus de secours pour les ressources .NET Core comprend les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6fe8f-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="6fe8f-113">Déterminez `active` <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="6fe8f-114">Dans tous les cas, `active` l’instance est le de l’assembly en cours d' <xref:System.Runtime.Loader.AssemblyLoadContext>exécution.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="6fe8f-115">L' `active` instance tente de charger un assembly satellite pour la culture demandée par ordre de priorité en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="6fe8f-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="6fe8f-116">Vérification de son cache.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-116">Checking its cache.</span></span>
    - <span data-ttu-id="6fe8f-117">Vérification du répertoire de l’assembly en cours d’exécution pour un sous-répertoire qui correspond <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> au demandé ( `es-MX`par exemple).</span><span class="sxs-lookup"><span data-stu-id="6fe8f-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="6fe8f-118">Cette fonctionnalité n’a pas été implémentée dans .NET Core avant 3,0.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="6fe8f-119">Sur Linux et macOS, le sous-répertoire est sensible à la casse et doit être :</span><span class="sxs-lookup"><span data-stu-id="6fe8f-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        >
        > - <span data-ttu-id="6fe8f-120">Respecter exactement la casse.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-120">Exactly match case.</span></span>
        > - <span data-ttu-id="6fe8f-121">Être en minuscules.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-121">Be in lower case.</span></span>

    - <span data-ttu-id="6fe8f-122">Si `active` est l' <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance de, en exécutant la logique de sondage de l' [assembly satellite (ressource) par défaut](default-probing.md#satellite-resource-assembly-probing) .</span><span class="sxs-lookup"><span data-stu-id="6fe8f-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="6fe8f-123">Appel de <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> la fonction.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="6fe8f-124">Déclenchement de <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> l’événement.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="6fe8f-125">Déclenchement de <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="6fe8f-126">Si un assembly satellite est chargé :</span><span class="sxs-lookup"><span data-stu-id="6fe8f-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="6fe8f-127">L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="6fe8f-128">La ressource demandée est recherchée dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="6fe8f-129">Si le runtime trouve la ressource dans l’assembly, il l’utilise.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="6fe8f-130">S’il ne trouve pas la ressource, il continue la recherche.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fe8f-131">Pour trouver une ressource dans l’assembly satellite, le runtime recherche le fichier de ressources demandé par <xref:System.Resources.ResourceManager> pour <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6fe8f-132">Dans le fichier de ressources, il recherche le nom de ressource demandé.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="6fe8f-133">En cas d’échec, la ressource est traitée comme introuvable.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="6fe8f-134">Le Runtime effectue ensuite une recherche dans les assemblys de culture parents par le biais de nombreux niveaux potentiels, en répétant les étapes 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="6fe8f-135">Chaque culture n’a qu’un seul parent, qui est défini <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> par la propriété.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="6fe8f-136">La recherche de cultures parentes s’arrête quand la <xref:System.Globalization.CultureInfo.Parent%2A> propriété d' <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>une culture est.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="6fe8f-137">Pour le <xref:System.Globalization.CultureInfo.InvariantCulture>, nous ne revenons pas aux étapes 2 & 3, mais nous continuons à l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="6fe8f-138">Si la ressource est toujours introuvable, la ressource de la culture par défaut (de secours) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="6fe8f-139">En règle générale, les ressources de la culture par défaut sont incluses dans l’assembly d’application principal.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="6fe8f-140">Toutefois, vous pouvez spécifier <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> pour la <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6fe8f-141">Cette valeur indique que l’emplacement de secours ultime pour les ressources est un assembly satellite plutôt que l’assembly principal.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fe8f-142">La culture par défaut est le secours ultime.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="6fe8f-143">Par conséquent, nous vous recommandons de toujours inclure un ensemble exhaustif de ressources dans le fichier de ressources par défaut.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="6fe8f-144">Vous empêchez ainsi la levée d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="6fe8f-145">En ayant un ensemble exhaustif, vous fournissez une solution de secours pour toutes les ressources et vous vous assurez qu’au moins une ressource est toujours présente pour l’utilisateur, même si elle n’est pas spécifique à la culture.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="6fe8f-146">Enfin,</span><span class="sxs-lookup"><span data-stu-id="6fe8f-146">Finally,</span></span>
   - <span data-ttu-id="6fe8f-147">Si le runtime ne trouve pas de fichier de ressources pour une culture par défaut (de <xref:System.Resources.MissingManifestResourceException> secours <xref:System.Resources.MissingSatelliteAssemblyException> ), une exception ou est levée.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="6fe8f-148">Si le fichier de ressources est trouvé mais que la ressource demandée n’est pas présente `null`, la demande est retournée.</span><span class="sxs-lookup"><span data-stu-id="6fe8f-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
