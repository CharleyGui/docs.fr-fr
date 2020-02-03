---
title: Dépendances et bibliothèques .NET
description: Meilleures pratiques suggérées pour la gestion des dépendances NuGet dans les bibliothèques .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731478"
---
# <a name="dependencies"></a><span data-ttu-id="72928-103">Dépendances</span><span class="sxs-lookup"><span data-stu-id="72928-103">Dependencies</span></span>

<span data-ttu-id="72928-104">Le principal moyen d’ajouter des dépendances à une bibliothèque .NET est de référencer des packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="72928-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="72928-105">Les références de packages NuGet vous permettent de réutiliser rapidement des fonctionnalités déjà écrites et d’en tirer parti , mais elles sont une source courante de friction pour les développeurs .NET.</span><span class="sxs-lookup"><span data-stu-id="72928-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="72928-106">La gestion correcte des dépendances est importante pour empêcher des modifications dans d’autres bibliothèques .NET d’arrêter votre bibliothèque .NET et vice versa !</span><span class="sxs-lookup"><span data-stu-id="72928-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="72928-107">Dépendances en losange</span><span class="sxs-lookup"><span data-stu-id="72928-107">Diamond dependencies</span></span>

<span data-ttu-id="72928-108">Il est courant qu’un projet .NET ait plusieurs versions d’un package dans son arborescence des dépendances.</span><span class="sxs-lookup"><span data-stu-id="72928-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="72928-109">Par exemple, une application dépend de deux packages NuGet dont chacun dépend de différentes versions du même package.</span><span class="sxs-lookup"><span data-stu-id="72928-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="72928-110">Il y a désormais une dépendance en losange dans le graphique de dépendance de l’application.</span><span class="sxs-lookup"><span data-stu-id="72928-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="72928-111">![Dépendance Diamond](./media/dependencies/diamond-dependency.png "Dépendance Diamond")</span><span class="sxs-lookup"><span data-stu-id="72928-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="72928-112">Lors du build, NuGet analyse tous les packages dont dépend un projet, y compris les dépendances de dépendances.</span><span class="sxs-lookup"><span data-stu-id="72928-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="72928-113">Lorsque plusieurs versions d’un package sont détectées, les règles sont évaluées pour en choisir une.</span><span class="sxs-lookup"><span data-stu-id="72928-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="72928-114">L’unification des packages est nécessaire, car l’exécution côte à côte des versions d’un assembly dans la même application est problématique dans .NET.</span><span class="sxs-lookup"><span data-stu-id="72928-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="72928-115">La plupart des dépendances en losange sont facilement résolues ; toutefois, elles peuvent créer des problèmes dans certaines circonstances :</span><span class="sxs-lookup"><span data-stu-id="72928-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="72928-116">**Les conflits de références de packages NuGet** empêchent la résolution d’une version pendant la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="72928-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="72928-117">**Des modifications importantes entre les versions** provoquent des bogues et des exceptions lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="72928-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="72928-118">**Un nom fort est attribué à l’assembly de package**, la version d’assembly est modifiée et l’application exécutée sur .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72928-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="72928-119">Des redirection des liaisons d'assembly sont requises.</span><span class="sxs-lookup"><span data-stu-id="72928-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="72928-120">Il n’est pas possible de savoir quels packages seront utilisées en même temps que le vôtre.</span><span class="sxs-lookup"><span data-stu-id="72928-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="72928-121">Un bon moyen de réduire la probabilité d’une dépendance en losange avec arrêt de votre bibliothèque consiste à limiter le nombre de packages dont vous dépendez.</span><span class="sxs-lookup"><span data-stu-id="72928-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="72928-122">✔️ Examinez votre bibliothèque .NET pour rechercher les dépendances inutiles.</span><span class="sxs-lookup"><span data-stu-id="72928-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="72928-123">Plages de versions de dépendances de NuGet</span><span class="sxs-lookup"><span data-stu-id="72928-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="72928-124">Une référence de package spécifie la plage de packages valides autorisés.</span><span class="sxs-lookup"><span data-stu-id="72928-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="72928-125">Généralement, la version de référence de package dans le fichier projet est la version minimale et il n’y a pas de maximum.</span><span class="sxs-lookup"><span data-stu-id="72928-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="72928-126">Les règles que NuGet utilise lors de la résolution des dépendances sont [complexes](/nuget/consume-packages/dependency-resolution), mais il recherche toujours la version la plus ancienne applicable.</span><span class="sxs-lookup"><span data-stu-id="72928-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="72928-127">NuGet préfère la version la plus ancienne applicable à la plus récente disponible, car la plus ancienne aura moins de problèmes de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="72928-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="72928-128">En raison de la règle de la version la plus ancienne applicable de NuGet, il n’est pas nécessaire de placer une version supérieure ou une plage exacte sur les références de package pour éviter d’obtenir la dernière version.</span><span class="sxs-lookup"><span data-stu-id="72928-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="72928-129">NuGet essaie déjà de trouver de la version la plus ancienne et la plus compatible pour vous.</span><span class="sxs-lookup"><span data-stu-id="72928-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="72928-130">Des limites de versions supérieures entraîneront l’échec de NuGet en cas de conflit.</span><span class="sxs-lookup"><span data-stu-id="72928-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="72928-131">Par exemple, une bibliothèque accepte exactement 1.0, tandis qu’une autre bibliothèque requiert 2.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="72928-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="72928-132">Alors que les modifications importantes peuvent avoir été introduites dans la version 2.0, une dépendance de version stricte ou supérieure d’une limite garantit une erreur.</span><span class="sxs-lookup"><span data-stu-id="72928-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="72928-133">![Conflit de dépendances Diamond](./media/dependencies/diamond-dependency-conflict.png "Conflit de dépendances Diamond")</span><span class="sxs-lookup"><span data-stu-id="72928-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="72928-134">❌ n’avez pas de références de package NuGet sans version minimale.</span><span class="sxs-lookup"><span data-stu-id="72928-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="72928-135">❌ éviter les références de package NuGet qui demandent une version exacte.</span><span class="sxs-lookup"><span data-stu-id="72928-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="72928-136">❌ éviter les références de package NuGet avec une limite supérieure de version.</span><span class="sxs-lookup"><span data-stu-id="72928-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="72928-137">Packages NuGet à code source partagé</span><span class="sxs-lookup"><span data-stu-id="72928-137">NuGet shared source packages</span></span>

<span data-ttu-id="72928-138">Une manière de réduire les dépendances externes de packages NuGet externes consiste à référencer les packages à code source partagé.</span><span class="sxs-lookup"><span data-stu-id="72928-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="72928-139">Un package à code source partagé contient des [fichiers de code source](/nuget/reference/nuspec#including-content-files) qui sont inclus dans un projet référencé.</span><span class="sxs-lookup"><span data-stu-id="72928-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="72928-140">Comme vous incluez uniquement des fichiers de code source compilés avec le reste de votre projet, il n’y a aucune dépendance externe ni risque de conflit.</span><span class="sxs-lookup"><span data-stu-id="72928-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="72928-141">Les packages à code source partagée sont l’idéal pour inclure de petits éléments de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="72928-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="72928-142">Par exemple, un package à source partagée de méthodes d’assistance pour les appels HTTP.</span><span class="sxs-lookup"><span data-stu-id="72928-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="72928-143">![Package source partagé](./media/dependencies/shared-source-package.png "Package source partagé")</span><span class="sxs-lookup"><span data-stu-id="72928-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="72928-144">![Projet source partagé](./media/dependencies/shared-source-project.png "Projet source partagé")</span><span class="sxs-lookup"><span data-stu-id="72928-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="72928-145">Les packages à code source partagé ont certaines limitations.</span><span class="sxs-lookup"><span data-stu-id="72928-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="72928-146">Ils ne peuvent être référencés que par `PackageReference`, ce qui exclut les projets `packages.config` plus anciens.</span><span class="sxs-lookup"><span data-stu-id="72928-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="72928-147">Par ailleurs, les packages à code source partagé ne peuvent être utilisés que par des projets ayant le même type de langage.</span><span class="sxs-lookup"><span data-stu-id="72928-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="72928-148">En raison de ces limitations, les packages à code source partagé sont très bien adaptés au partage d’une fonctionnalité au sein d’un projet open source.</span><span class="sxs-lookup"><span data-stu-id="72928-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="72928-149">✔️ envisagez de faire référence à des packages source partagés pour de petites parties de fonctionnalités internes.</span><span class="sxs-lookup"><span data-stu-id="72928-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="72928-150">✔️ envisagez de faire de votre package un package source partagé s’il fournit de petits éléments de fonctionnalité internes.</span><span class="sxs-lookup"><span data-stu-id="72928-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="72928-151">✔️ FAITES référence à des packages source partagés avec `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="72928-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="72928-152">Ce paramètre indique à NuGet que le package ne doit être utilisée que lors du développement et ne doit pas être exposé en tant que dépendance publique.</span><span class="sxs-lookup"><span data-stu-id="72928-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="72928-153">❌ n’avez pas de types de packages sources partagés dans votre API publique.</span><span class="sxs-lookup"><span data-stu-id="72928-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="72928-154">Les types à code source partagé sont compilés dans l’assembly de référencement et ne peuvent pas être échangés au-delà des limites de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="72928-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="72928-155">Par exemple, un type de `IRepository` à code source partagé dans un projet est un type distinct du même `IRepository` à code source partagé dans un autre projet.</span><span class="sxs-lookup"><span data-stu-id="72928-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="72928-156">Les types de packages à code source partagé doivent avoir une visibilité `internal`.</span><span class="sxs-lookup"><span data-stu-id="72928-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="72928-157">❌ ne publiez pas de packages source partagés sur NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="72928-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="72928-158">Les packages à code source partagé contiennent du code source et ne peuvent être utilisés que par des projets ayant le même type de langage.</span><span class="sxs-lookup"><span data-stu-id="72928-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="72928-159">Par exemple, un package à code source partagé C# ne peut pas être utilisé par une application F#.</span><span class="sxs-lookup"><span data-stu-id="72928-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="72928-160">Publier des packages à code source partagé sur un [flux local ou MyGet](./publish-nuget-package.md) pour les utiliser en interne au sein de votre projet.</span><span class="sxs-lookup"><span data-stu-id="72928-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72928-161">[Précédent](nuget.md)
>[Suivant](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="72928-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
