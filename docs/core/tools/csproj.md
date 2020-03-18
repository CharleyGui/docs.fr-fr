---
title: Ajouts au format csproj pour .NET Core
description: Découvrir les différences entre les fichiers csproj existants et les fichiers csproj .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: 2fb00e830380c5c4cbf7b6dcd2c8a585e1617b4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398992"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="cab2b-103">Ajouts au format csproj pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="cab2b-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="cab2b-104">Ce document décrit les modifications qui ont été ajoutées aux fichiers projet dans le cadre du passage de *project.json* à *csproj* et [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="cab2b-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="cab2b-105">Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="cab2b-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="cab2b-106">Références de package implicites</span><span class="sxs-lookup"><span data-stu-id="cab2b-106">Implicit package references</span></span>

<span data-ttu-id="cab2b-107">Les métapackages sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété `<TargetFramework>` ou `<TargetFrameworks>` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="cab2b-108">`<TargetFrameworks>` est ignoré si `<TargetFramework>` est spécifié, indépendamment de l’ordre.</span><span class="sxs-lookup"><span data-stu-id="cab2b-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="cab2b-109">Pour plus d’informations, voir [Paquets, métapackages et cadres](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="cab2b-109">For more information, see [Packages, metapackages, and frameworks](../packages.md).</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="cab2b-110">Recommandations</span><span class="sxs-lookup"><span data-stu-id="cab2b-110">Recommendations</span></span>

<span data-ttu-id="cab2b-111">Comme les métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` sont implicitement référencés, voici les bonnes pratiques que nous recommandons :</span><span class="sxs-lookup"><span data-stu-id="cab2b-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="cab2b-112">Quand vous ciblez .NET Core ou .NET Standard, n’incluez jamais de référence explicite aux métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` via un élément `<PackageReference>` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="cab2b-113">Si vous avez besoin d’une version spécifique du runtime quand vous ciblez .NET Core, vous devez utiliser la propriété `<RuntimeFrameworkVersion>` dans votre projet (par exemple, `1.0.4`) au lieu de référencer le métapackage.</span><span class="sxs-lookup"><span data-stu-id="cab2b-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="cab2b-114">Cela peut se produire si vous utilisez des [déploiements autonomes](../deploying/index.md#publish-self-contained) et que vous devez utiliser une version de correctif spécifique du runtime 1.0.0 LTS, par exemple.</span><span class="sxs-lookup"><span data-stu-id="cab2b-114">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="cab2b-115">Si vous avez besoin d’une version spécifique du métapackage `NETStandard.Library` quand vous ciblez .NET Standard, vous pouvez utiliser la propriété `<NetStandardImplicitPackageVersion>` et définir la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="cab2b-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="cab2b-116">Vous ne devez pas ajouter ni mettre à jour explicitement les références au métapackage `Microsoft.NETCore.App` ou `NETStandard.Library` dans les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cab2b-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="cab2b-117">Si une version de `NETStandard.Library` est nécessaire lors de l’utilisation d’un package NuGet basé sur .NET Standard, NuGet installe automatiquement cette version.</span><span class="sxs-lookup"><span data-stu-id="cab2b-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="cab2b-118">Version implicite pour certaines références de packages</span><span class="sxs-lookup"><span data-stu-id="cab2b-118">Implicit version for some package references</span></span>

<span data-ttu-id="cab2b-119">La plupart [`<PackageReference>`](#packagereference) des utilisations de nécessitent de définir l’attribut `Version` pour spécifier la version du paquet NuGet à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cab2b-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="cab2b-120">Cependant, lorsque vous utilisez .NET Core 2.1 ou 2.2 et référencez [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) ou [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), cet attribut n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cab2b-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="cab2b-121">Le Kit SDK .NET Core peut sélectionner automatiquement la version des packages à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cab2b-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="cab2b-122">Recommandation</span><span class="sxs-lookup"><span data-stu-id="cab2b-122">Recommendation</span></span>

<span data-ttu-id="cab2b-123">Lorsque vous référencez les packages `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All`, ne spécifiez pas leur version.</span><span class="sxs-lookup"><span data-stu-id="cab2b-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="cab2b-124">Si une version est spécifiée, le Kit SDK risque de générer l’avertissement NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="cab2b-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="cab2b-125">Pour résoudre cet avertissement, supprimez la version du package, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cab2b-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="cab2b-126">Problème connu : le Kit SDK .NET Core 2.1 prend uniquement en charge cette syntaxe si le projet utilise également Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="cab2b-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="cab2b-127">Ce problème est résolu dans le SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="cab2b-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="cab2b-128">Ces références aux métapackages ASP.NET Core ont un comportement légèrement différent de celui de la plupart des packages NuGet normaux.</span><span class="sxs-lookup"><span data-stu-id="cab2b-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="cab2b-129">Les [déploiements dépendant du framework](../deploying/index.md#publish-runtime-dependent) d’applications qui utilisent ces métapackages tirent automatiquement parti du framework partagé ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cab2b-129">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="cab2b-130">Quand vous utilisez les métapackages **aucune** des ressources des packages NuGet ASP.NET Core référencés n’est déployée avec l’application — le framework partagé ASP.NET Core contient ces ressources.</span><span class="sxs-lookup"><span data-stu-id="cab2b-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="cab2b-131">Les ressources présentes dans le framework partagé sont optimisées pour la plateforme cible afin d’améliorer la vitesse de démarrage des applications.</span><span class="sxs-lookup"><span data-stu-id="cab2b-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="cab2b-132">Pour plus d’informations sur le framework partagé, consultez [Empaquetage de la distribution de .NET Core](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="cab2b-132">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="cab2b-133">Si une version *est* spécifiée, elle est traitée comme la version *minimale* du framework partagé ASP.NET Core pour les déploiements dépendant du framework, et comme une version *exacte* pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="cab2b-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="cab2b-134">Cela peut avoir les conséquences suivantes :</span><span class="sxs-lookup"><span data-stu-id="cab2b-134">This can have the following consequences:</span></span>

- <span data-ttu-id="cab2b-135">Si la version d’ASP.NET Core installée sur le serveur est inférieure à la version spécifiée sur PackageReference, le processus .NET Core n’est pas lancé.</span><span class="sxs-lookup"><span data-stu-id="cab2b-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="cab2b-136">Les mises à jour du métapackage sont souvent disponibles sur NuGet.org avant que des mises à jour soient publiées dans les environnements d’hébergement comme Azure.</span><span class="sxs-lookup"><span data-stu-id="cab2b-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="cab2b-137">La mise à jour de la version sur PackageReference avec ASP.NET Core peut entraîner l’échec d’une application déployée.</span><span class="sxs-lookup"><span data-stu-id="cab2b-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="cab2b-138">Si l’application est déployée comme un [déploiement autonome](../deploying/index.md#publish-self-contained), cette application ne peut pas contenir les dernières mises à jour de sécurité pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cab2b-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="cab2b-139">Quand une version n’est pas spécifiée, le Kit SDK peut inclure automatiquement la dernière version ASP.NET Core dans le déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="cab2b-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="cab2b-140">Inclusions de compilation par défaut dans les projets .NET Core</span><span class="sxs-lookup"><span data-stu-id="cab2b-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="cab2b-141">Dans le cadre du passage au format *csproj* dans les dernières versions du SDK, nous avons déplacé les inclusions et exclusions par défaut pour les éléments de compilation et les ressources incorporées dans les fichiers de propriétés du SDK.</span><span class="sxs-lookup"><span data-stu-id="cab2b-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="cab2b-142">Cela signifie que vous n’avez plus besoin de spécifier ces éléments dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="cab2b-143">La principale raison de cette modification est de réduire l’encombrement de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="cab2b-144">Les valeurs par défaut qui sont présentes dans le SDK doivent couvrir la plupart des cas d’utilisation courants, il est donc inutile de les répéter dans chaque projet que vous créez.</span><span class="sxs-lookup"><span data-stu-id="cab2b-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="cab2b-145">Il en résulte des fichiers projet moins volumineux qui sont beaucoup plus faciles à comprendre et à modifier à la main, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cab2b-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="cab2b-146">Le tableau suivant montre les éléments et les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le SDK :</span><span class="sxs-lookup"><span data-stu-id="cab2b-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="cab2b-147">Élément</span><span class="sxs-lookup"><span data-stu-id="cab2b-147">Element</span></span>           | <span data-ttu-id="cab2b-148">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="cab2b-148">Include glob</span></span>                              | <span data-ttu-id="cab2b-149">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="cab2b-149">Exclude glob</span></span>                                                  | <span data-ttu-id="cab2b-150">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="cab2b-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="cab2b-151">Compiler</span><span class="sxs-lookup"><span data-stu-id="cab2b-151">Compile</span></span>           | <span data-ttu-id="cab2b-152">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="cab2b-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="cab2b-153">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="cab2b-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="cab2b-154">N/A</span><span class="sxs-lookup"><span data-stu-id="cab2b-154">N/A</span></span>                      |
| <span data-ttu-id="cab2b-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="cab2b-155">EmbeddedResource</span></span>  | <span data-ttu-id="cab2b-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="cab2b-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="cab2b-157">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="cab2b-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="cab2b-158">N/A</span><span class="sxs-lookup"><span data-stu-id="cab2b-158">N/A</span></span>                      |
| <span data-ttu-id="cab2b-159">None</span><span class="sxs-lookup"><span data-stu-id="cab2b-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="cab2b-160">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="cab2b-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="cab2b-161">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="cab2b-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="cab2b-162">**Exclure Glob** exclut toujours les dossiers `./bin` et `./obj`, respectivement représentés par les propriétés MSBuild `$(BaseOutputPath)` et `$(BaseIntermediateOutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="cab2b-163">Dans l’ensemble, toutes les exclusions sont représentées par `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="cab2b-164">Si vous avez des modèles Glob dans votre projet et que vous essayez de le générer à l’aide du dernier SDK, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="cab2b-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="cab2b-165">Des éléments de compilation en double ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="cab2b-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="cab2b-166">Le SDK .NET inclut des éléments de compilation de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="cab2b-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="cab2b-167">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="cab2b-168">Pour contourner cette erreur, vous pouvez supprimer les éléments `Compile` explicites qui correspondent à ceux répertoriés dans le tableau précédent ou vous pouvez définir la propriété `<EnableDefaultCompileItems>` sur `false`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="cab2b-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="cab2b-169">Le fait de définir cette propriété avec la valeur `false` désactive l’inclusion implicite, ce qui rétablit le comportement des SDK précédents dans lesquels vous deviez spécifier les globs par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="cab2b-170">Ce changement ne modifie pas le mécanisme principal des autres inclusions.</span><span class="sxs-lookup"><span data-stu-id="cab2b-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="cab2b-171">Toutefois, si vous voulez, par exemple, spécifier certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes connus dans *csproj* correspondants (par exemple, l’élément `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="cab2b-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="cab2b-172">`<EnableDefaultCompileItems>` désactive uniquement les modèles Glob `Compile`, mais n’affecte pas les autres modèles Glob, comme le modèle Glob implicite `None`, qui s’applique également aux éléments \*.cs.</span><span class="sxs-lookup"><span data-stu-id="cab2b-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="cab2b-173">Par conséquent, **l’Explorateur de solutions** continue d’afficher des éléments \*.cs dans le cadre du projet, inclus en tant qu’éléments `None`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="cab2b-174">De la même façon, vous pouvez affecter à `<EnableDefaultNoneItems>` la valeur false pour désactiver le modèle Glob implicite `None`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="cab2b-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="cab2b-175">Pour désactiver **tous les modèles Glob implicites**, vous pouvez affecter à la propriété `<EnableDefaultItems>` la valeur `false` comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cab2b-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="cab2b-176">Comment afficher la totalité du projet tel qu’il est perçu par MSBuild ?</span><span class="sxs-lookup"><span data-stu-id="cab2b-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="cab2b-177">Même si ces modifications csproj simplifient considérablement les fichiers projet, vous pouvez souhaiter voir le projet entièrement développé tel qu’il est perçu par MSBuild une fois le kit SDK et ses cibles inclus.</span><span class="sxs-lookup"><span data-stu-id="cab2b-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="cab2b-178">Prétraitez le projet avec [le commutateur `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](dotnet-msbuild.md), qui affiche les fichiers qui sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet :</span><span class="sxs-lookup"><span data-stu-id="cab2b-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="cab2b-179">Si le projet comporte plusieurs frameworks cibles, les résultats de la commande ne doivent se concentrer que sur un seul d'entre eux en le spécifiant en tant que propriété MSBuild :</span><span class="sxs-lookup"><span data-stu-id="cab2b-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="cab2b-180">Ajouts</span><span class="sxs-lookup"><span data-stu-id="cab2b-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="cab2b-181">Attribut Sdk</span><span class="sxs-lookup"><span data-stu-id="cab2b-181">Sdk attribute</span></span>

<span data-ttu-id="cab2b-182">L’élément `<Project>` racine du fichier *.csproj* a un nouvel attribut nommé `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="cab2b-183">`Sdk` spécifie le SDK à utiliser par le projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="cab2b-184">Le SDK, comme le décrit le [document de superposition](cli-msbuild-architecture.md), est un ensemble de [tâches](/visualstudio/msbuild/msbuild-tasks) et de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild pouvant générer du code .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cab2b-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="cab2b-185">Les SDK suivants sont disponibles pour .NET Core:</span><span class="sxs-lookup"><span data-stu-id="cab2b-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="cab2b-186">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="cab2b-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="cab2b-187">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="cab2b-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="cab2b-188">Le Kit SDK de la bibliothèque de classes .NET Core Razor avec l’ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="cab2b-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="cab2b-189">Le service de travailleur de `Microsoft.NET.Sdk.Worker` base .NET avec l’ID de (depuis .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="cab2b-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="cab2b-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="cab2b-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="cab2b-191">Vous devez définir l’attribut `Sdk` sur un de ces ID pour l’élément `<Project>` afin d’utiliser les outils .NET Core et générer votre code.</span><span class="sxs-lookup"><span data-stu-id="cab2b-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="cab2b-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="cab2b-192">PackageReference</span></span>

<span data-ttu-id="cab2b-193">Un élément `<PackageReference>` spécifie une [dépendance NuGet dans le projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="cab2b-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="cab2b-194">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="cab2b-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="cab2b-195">Version</span><span class="sxs-lookup"><span data-stu-id="cab2b-195">Version</span></span>

<span data-ttu-id="cab2b-196">L’attribut obligatoire `Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="cab2b-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="cab2b-197">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards).</span><span class="sxs-lookup"><span data-stu-id="cab2b-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="cab2b-198">Le comportement par défaut est une version minimale, match inclusif.</span><span class="sxs-lookup"><span data-stu-id="cab2b-198">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="cab2b-199">Par exemple, `Version="1.2.3"` la spécifation est équivalente à la notation `[1.2.3, )` NuGet et signifie que le paquet résolu aura la version 1.2.3 si disponible ou plus autrement.</span><span class="sxs-lookup"><span data-stu-id="cab2b-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="cab2b-200">Inclure desassets, des exclus et des PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="cab2b-200">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="cab2b-201">L’attribut `IncludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cab2b-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="cab2b-202">Par défaut, toutes les ressources du package sont incluses.</span><span class="sxs-lookup"><span data-stu-id="cab2b-202">By default, all package assets are included.</span></span>

<span data-ttu-id="cab2b-203">L’attribut `ExcludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` ne doivent pas être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cab2b-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="cab2b-204">L’attribut `PrivateAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées, mais sans être reprises dans le projet suivant.</span><span class="sxs-lookup"><span data-stu-id="cab2b-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="cab2b-205">Les ressources `Analyzers`, `Build` et `ContentFiles` sont par défaut privées en l’absence de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="cab2b-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="cab2b-206">`PrivateAssets`est équivalent à l’élément *project.json*/*xproj.* `SuppressParent`</span><span class="sxs-lookup"><span data-stu-id="cab2b-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="cab2b-207">Ces attributs peuvent contenir un ou plusieurs éléments de la liste suivante, séparés par le caractère point-virgule `;` le cas échéant :</span><span class="sxs-lookup"><span data-stu-id="cab2b-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="cab2b-208">`Compile`Le contenu du dossier *lib* est disponible pour compiler contre.</span><span class="sxs-lookup"><span data-stu-id="cab2b-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="cab2b-209">`Runtime`Le contenu du dossier *de l’exécution* est distribué.</span><span class="sxs-lookup"><span data-stu-id="cab2b-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="cab2b-210">`ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.</span><span class="sxs-lookup"><span data-stu-id="cab2b-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="cab2b-211">`Build`Les accessoires/cibles du dossier *de construction* sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="cab2b-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="cab2b-212">`Native`Le contenu des actifs autochtones est copié au dossier *de sortie* pour le temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cab2b-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="cab2b-213">`Analyzers` : Les analyseurs sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="cab2b-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="cab2b-214">Sinon, l’attribut peut contenir :</span><span class="sxs-lookup"><span data-stu-id="cab2b-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="cab2b-215">`None` : Aucune ressource n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="cab2b-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="cab2b-216">`All` : Toutes les ressources sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="cab2b-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="cab2b-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="cab2b-217">DotNetCliToolReference</span></span>

<span data-ttu-id="cab2b-218">Un élément `<DotNetCliToolReference>` spécifie l’outil CLI que l’utilisateur souhaite restaurer dans le contexte du projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="cab2b-219">Il constitue une alternative au nœud `tools` dans *project.json*.</span><span class="sxs-lookup"><span data-stu-id="cab2b-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="cab2b-220">Notez `DotNetCliToolReference` que est [maintenant déprécié](https://github.com/dotnet/announcements/issues/107) en faveur de [.NET Core Local Tools](https://aka.ms/local-tools).</span><span class="sxs-lookup"><span data-stu-id="cab2b-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="cab2b-221">Version</span><span class="sxs-lookup"><span data-stu-id="cab2b-221">Version</span></span>

<span data-ttu-id="cab2b-222">`Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="cab2b-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="cab2b-223">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="cab2b-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="cab2b-224">Le comportement par défaut est une version minimale, match inclusif.</span><span class="sxs-lookup"><span data-stu-id="cab2b-224">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="cab2b-225">Par exemple, `Version="1.2.3"` la spécifation est équivalente à la notation `[1.2.3, )` NuGet et signifie que le paquet résolu aura la version 1.2.3 si disponible ou plus autrement.</span><span class="sxs-lookup"><span data-stu-id="cab2b-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="cab2b-226">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="cab2b-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="cab2b-227">L’élément de propriété `<RuntimeIdentifiers>` vous permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="cab2b-228">Les RID permettent de publier des déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="cab2b-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="cab2b-229">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="cab2b-229">RuntimeIdentifier</span></span>

<span data-ttu-id="cab2b-230">L’élément de propriété `<RuntimeIdentifier>` vous permet de spécifier un seul [identificateur de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="cab2b-231">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="cab2b-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="cab2b-232">Utilisez plutôt `<RuntimeIdentifiers>` (au pluriel) si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="cab2b-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="cab2b-233">`<RuntimeIdentifier>` peut fournir des builds plus rapides quand un seul runtime est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cab2b-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="cab2b-234">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="cab2b-234">PackageTargetFallback</span></span>

<span data-ttu-id="cab2b-235">L’élément de propriété `<PackageTargetFallback>` vous permet de spécifier un jeu de cibles compatibles à utiliser lors de la restauration des packages.</span><span class="sxs-lookup"><span data-stu-id="cab2b-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="cab2b-236">Il est conçu pour permettre aux packages qui utilisent le [moniker du framework cible](/nuget/schema/target-frameworks) dotnet de fonctionner avec les packages qui ne déclarent pas de moniker du framework cible dotnet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="cab2b-237">Si votre projet utilise le moniker du framework cible dotnet, tous les packages dont il dépend doivent également avoir un moniker du framework cible dotnet, sauf si vous ajoutez `<PackageTargetFallback>` à votre projet pour permettre aux plateformes autres que dotnet d’être compatibles avec dotnet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="cab2b-238">L’exemple suivant fournit les solutions de secours pour toutes les cibles dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="cab2b-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="cab2b-239">L’exemple suivant spécifie les solutions de secours uniquement pour la cible `netcoreapp2.1` :</span><span class="sxs-lookup"><span data-stu-id="cab2b-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="cab2b-240">Événements de build</span><span class="sxs-lookup"><span data-stu-id="cab2b-240">Build events</span></span>

<span data-ttu-id="cab2b-241">La façon dont les événements de pré-construction et de post-construction sont spécifiés dans le dossier du projet a changé.</span><span class="sxs-lookup"><span data-stu-id="cab2b-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="cab2b-242">Les propriétés PreBuildEvent et PostBuildEvent ne sont pas recommandées dans le format de projet de style SDK, parce que les macros telles que $(ProjectDir) ne sont pas résolues.</span><span class="sxs-lookup"><span data-stu-id="cab2b-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="cab2b-243">Par exemple, le code suivant n’est plus pris en charge :</span><span class="sxs-lookup"><span data-stu-id="cab2b-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

<span data-ttu-id="cab2b-244">Dans les projets de style SDK, `PreBuild` utilisez `PostBuild` une `BeforeTargets` cible `PreBuild` MSBuild nommée ou et définissez la propriété pour ou la `AfterTargets` propriété pour `PostBuild`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="cab2b-245">Pour l’exemple précédent, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cab2b-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="cab2b-246">Vous pouvez utiliser n’importe quel nom pour les cibles `PreBuild` MSBuild, mais le Visual Studio IDE reconnaît et `PostBuild` cible, donc nous vous recommandons d’utiliser ces noms afin que vous puissiez modifier les commandes dans le Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="cab2b-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="cab2b-247">Propriétés de métadonnées NuGet</span><span class="sxs-lookup"><span data-stu-id="cab2b-247">NuGet metadata properties</span></span>

<span data-ttu-id="cab2b-248">Avec le passage à MSBuild, nous avons déplacé les métadonnées d’entrée qui est utilisé lors de l’emballage d’un paquet NuGet de *project.json* aux fichiers *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="cab2b-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="cab2b-249">Les entrées sont des propriétés MSBuild qui doivent donc être placées dans un groupe `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="cab2b-250">Voici la liste des propriétés qui sont utilisées comme entrées `dotnet pack` pour le `Pack` processus d’emballage lors de l’utilisation de la commande ou de la cible MSBuild qui fait partie du SDK :</span><span class="sxs-lookup"><span data-stu-id="cab2b-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="cab2b-251">IsPackable</span><span class="sxs-lookup"><span data-stu-id="cab2b-251">IsPackable</span></span>

<span data-ttu-id="cab2b-252">Valeur booléenne qui spécifie si le projet peut être compressé.</span><span class="sxs-lookup"><span data-stu-id="cab2b-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="cab2b-253">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="cab2b-254">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="cab2b-254">PackageVersion</span></span>

<span data-ttu-id="cab2b-255">Spécifie la version du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="cab2b-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="cab2b-256">Accepte toutes les formes de la chaîne de version NuGet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="cab2b-257">La valeur par défaut est la valeur de `$(Version)`, autrement dit, de la propriété `Version` dans le projet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="cab2b-258">PackageId</span><span class="sxs-lookup"><span data-stu-id="cab2b-258">PackageId</span></span>

<span data-ttu-id="cab2b-259">Spécifie le nom du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="cab2b-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="cab2b-260">Si non spécifié, l’opération `pack` utilise par défaut le `AssemblyName` ou le nom du répertoire comme nom du package.</span><span class="sxs-lookup"><span data-stu-id="cab2b-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="cab2b-261">Intitulé</span><span class="sxs-lookup"><span data-stu-id="cab2b-261">Title</span></span>

<span data-ttu-id="cab2b-262">Titre convivial du package, généralement utilisé dans les affichages de l’interface utilisateur comme sur nuget.org et dans le gestionnaire de package de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cab2b-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="cab2b-263">Si non spécifié, l’ID de package est utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="cab2b-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="cab2b-264">Auteurs</span><span class="sxs-lookup"><span data-stu-id="cab2b-264">Authors</span></span>

<span data-ttu-id="cab2b-265">Une liste d’auteurs de paquets séquelon-séparé, correspondant aux noms de profil sur nuget.org. Ceux-ci sont affichés dans la Galerie NuGet sur nuget.org et sont utilisés pour les paquets de référence croisée par les mêmes auteurs.</span><span class="sxs-lookup"><span data-stu-id="cab2b-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="cab2b-266">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="cab2b-266">PackageDescription</span></span>

<span data-ttu-id="cab2b-267">Description longue du package pour l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cab2b-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="cab2b-268">Description</span><span class="sxs-lookup"><span data-stu-id="cab2b-268">Description</span></span>

<span data-ttu-id="cab2b-269">Description longue de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="cab2b-269">A long description for the assembly.</span></span> <span data-ttu-id="cab2b-270">Si `PackageDescription` elle n’est pas spécifiée, cette propriété est également utilisée comme description de l’emballage.</span><span class="sxs-lookup"><span data-stu-id="cab2b-270">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="cab2b-271">copyright</span><span class="sxs-lookup"><span data-stu-id="cab2b-271">Copyright</span></span>

<span data-ttu-id="cab2b-272">Détails de copyright pour le package.</span><span class="sxs-lookup"><span data-stu-id="cab2b-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="cab2b-273">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="cab2b-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="cab2b-274">Valeur booléenne qui spécifie si le client doit inviter l’utilisateur à accepter la licence du package avant d’installer le package.</span><span class="sxs-lookup"><span data-stu-id="cab2b-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="cab2b-275">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-275">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="cab2b-276">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="cab2b-276">DevelopmentDependency</span></span>

<span data-ttu-id="cab2b-277">Une valeur Boolean qui précise si le paquet est marqué comme une dépendance au développement seulement, ce qui empêche le paquet d’être inclus comme une dépendance dans d’autres paquets.</span><span class="sxs-lookup"><span data-stu-id="cab2b-277">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="cab2b-278">Avec PackageReference (NuGet 4.8), ce drapeau signifie également que les actifs de compilation sont exclus de la compilation.</span><span class="sxs-lookup"><span data-stu-id="cab2b-278">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="cab2b-279">Pour plus d'informations, voir [Prise en charge de DevelopmentDependency pour PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="cab2b-279">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="cab2b-280">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="cab2b-280">PackageLicenseExpression</span></span>

<span data-ttu-id="cab2b-281">[Identificateur de licence SPDX](https://spdx.org/licenses/) ou expression.</span><span class="sxs-lookup"><span data-stu-id="cab2b-281">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="cab2b-282">Par exemple : `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-282">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="cab2b-283">Voici la liste complète des [identificateurs de licence SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="cab2b-283">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="cab2b-284">NuGet.org n’accepte que les licences approuvées OSI et FSF avec une expression de type licence.</span><span class="sxs-lookup"><span data-stu-id="cab2b-284">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="cab2b-285">La syntaxe exacte des expressions de licence est décrite ci-dessous dans [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="cab2b-285">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="cab2b-286">Il n’est pas possible de spécifier plusieurs des éléments suivants à la fois : `PackageLicenseExpression`, `PackageLicenseFile` et `PackageLicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-286">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="cab2b-287">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="cab2b-287">PackageLicenseFile</span></span>

<span data-ttu-id="cab2b-288">Chemin d’un fichier de licence du package, si la licence utilisée n’a pas été attribuée à un identificateur SPDX, ou il s’agit d’une licence personnalisée (sinon, `PackageLicenseExpression` est recommandé).</span><span class="sxs-lookup"><span data-stu-id="cab2b-288">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="cab2b-289">Remplace `PackageLicenseUrl`, ne peut pas `PackageLicenseExpression`être combiné avec , et nécessite Visual Studio version 15.9.4 et .NET SDK 2.1.502 ou 2.2.101 ou plus récent.</span><span class="sxs-lookup"><span data-stu-id="cab2b-289">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="cab2b-290">Vérifiez que le fichier de licence est empaqueté en l’ajoutant explicitement au projet ; voici un exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="cab2b-290">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="cab2b-291">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="cab2b-291">PackageLicenseUrl</span></span>

<span data-ttu-id="cab2b-292">Une URL de la licence qui s’applique au paquet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-292">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="cab2b-293">(_Déconseillé depuis Visual Studio 15.9.4, le kit SDK .NET 2.1.502 et 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="cab2b-293">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="cab2b-294">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="cab2b-294">PackageIconUrl</span></span>

<span data-ttu-id="cab2b-295">URL d’une image 64 x 64 avec un arrière-plan transparent à utiliser comme icône pour le package dans l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cab2b-295">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="cab2b-296">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="cab2b-296">PackageReleaseNotes</span></span>

<span data-ttu-id="cab2b-297">Notes de publication du package.</span><span class="sxs-lookup"><span data-stu-id="cab2b-297">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="cab2b-298">PackageTags</span><span class="sxs-lookup"><span data-stu-id="cab2b-298">PackageTags</span></span>

<span data-ttu-id="cab2b-299">Liste de balises séparées par un point-virgule qui désigne le package.</span><span class="sxs-lookup"><span data-stu-id="cab2b-299">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="cab2b-300">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="cab2b-300">PackageOutputPath</span></span>

<span data-ttu-id="cab2b-301">Détermine le chemin de sortie dans lequel le package compressé est déposé.</span><span class="sxs-lookup"><span data-stu-id="cab2b-301">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="cab2b-302">La valeur par défaut est `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-302">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="cab2b-303">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="cab2b-303">IncludeSymbols</span></span>
<span data-ttu-id="cab2b-304">Cette valeur booléenne indique si le package doit créer un package de symboles supplémentaire quand le projet est compressé.</span><span class="sxs-lookup"><span data-stu-id="cab2b-304">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="cab2b-305">Le format du package de symboles est contrôlé par la propriété `SymbolPackageFormat`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-305">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="cab2b-306">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="cab2b-306">SymbolPackageFormat</span></span>
<span data-ttu-id="cab2b-307">Spécifie le format du package de symboles.</span><span class="sxs-lookup"><span data-stu-id="cab2b-307">Specifies the format of the symbols package.</span></span> <span data-ttu-id="cab2b-308">Si la valeur est « symbols.nupkg », un package de symboles hérité est créé avec une extension *.symbols.nupkg* contenant des fichiers PDB, DLL et d’autres fichiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="cab2b-308">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="cab2b-309">Si la valeur est « snupkg », un package de symboles snupkg est créé, contenant les fichiers PDB portables.</span><span class="sxs-lookup"><span data-stu-id="cab2b-309">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="cab2b-310">La valeur par défaut est « symbols.nupkg ».</span><span class="sxs-lookup"><span data-stu-id="cab2b-310">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="cab2b-311">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="cab2b-311">IncludeSource</span></span>

<span data-ttu-id="cab2b-312">Cette valeur booléenne indique si le processus de compression doit créer un package source.</span><span class="sxs-lookup"><span data-stu-id="cab2b-312">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="cab2b-313">Le package source contient le code source de la bibliothèque ainsi que les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="cab2b-313">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="cab2b-314">Les fichiers sources sont placés dans le répertoire `src/ProjectName` dans le fichier de package obtenu.</span><span class="sxs-lookup"><span data-stu-id="cab2b-314">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="cab2b-315">IsTool</span><span class="sxs-lookup"><span data-stu-id="cab2b-315">IsTool</span></span>

<span data-ttu-id="cab2b-316">Spécifie si tous les fichiers de sortie sont copiés dans le dossier *tools* au lieu du dossier *lib*.</span><span class="sxs-lookup"><span data-stu-id="cab2b-316">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="cab2b-317">Ceci est différent `DotNetCliTool`d’un , `PackageType` qui est spécifié en définissant le dans le fichier *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="cab2b-317">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="cab2b-318">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="cab2b-318">RepositoryUrl</span></span>

<span data-ttu-id="cab2b-319">Spécifie l’URL du dépôt où réside le code source du package et/ou à partir de laquelle il est généré.</span><span class="sxs-lookup"><span data-stu-id="cab2b-319">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="cab2b-320">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="cab2b-320">RepositoryType</span></span>

<span data-ttu-id="cab2b-321">Spécifie le type de dépôt.</span><span class="sxs-lookup"><span data-stu-id="cab2b-321">Specifies the type of the repository.</span></span> <span data-ttu-id="cab2b-322">La valeur par défaut est « git ».</span><span class="sxs-lookup"><span data-stu-id="cab2b-322">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="cab2b-323">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="cab2b-323">RepositoryBranch</span></span>
<span data-ttu-id="cab2b-324">Précise le nom de la branche source dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="cab2b-324">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="cab2b-325">Lorsque le projet est emballé dans un paquet NuGet, il est ajouté aux métadonnées du paquet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-325">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="cab2b-326">DépôtCommit</span><span class="sxs-lookup"><span data-stu-id="cab2b-326">RepositoryCommit</span></span>
<span data-ttu-id="cab2b-327">Dépositaire optionnel commit ou changeet pour indiquer à quelle source le paquet a été construit contre.</span><span class="sxs-lookup"><span data-stu-id="cab2b-327">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="cab2b-328">`RepositoryUrl`doit également être spécifié pour que cette propriété soit incluse.</span><span class="sxs-lookup"><span data-stu-id="cab2b-328">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="cab2b-329">Lorsque le projet est emballé dans un paquet NuGet, cette validation ou modification est ajoutée aux métadonnées du paquet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-329">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="cab2b-330">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="cab2b-330">NoPackageAnalysis</span></span>

<span data-ttu-id="cab2b-331">Spécifie que le pack ne doit pas exécuter d’analyse du package après sa génération.</span><span class="sxs-lookup"><span data-stu-id="cab2b-331">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="cab2b-332">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="cab2b-332">MinClientVersion</span></span>

<span data-ttu-id="cab2b-333">Spécifie la version minimale du client NuGet qui peut installer ce package, appliquée par nuget.exe et le gestionnaire de package Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cab2b-333">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="cab2b-334">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="cab2b-334">IncludeBuildOutput</span></span>

<span data-ttu-id="cab2b-335">Cette valeur Boolean précise si les assemblages de sortie de construction doivent être emballés dans le fichier *.nupkg* ou non.</span><span class="sxs-lookup"><span data-stu-id="cab2b-335">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="cab2b-336">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="cab2b-336">IncludeContentInPack</span></span>

<span data-ttu-id="cab2b-337">Cette valeur booléenne indique si tous les éléments qui ont un type `Content` sont automatiquement inclus dans le package obtenu.</span><span class="sxs-lookup"><span data-stu-id="cab2b-337">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="cab2b-338">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-338">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="cab2b-339">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="cab2b-339">BuildOutputTargetFolder</span></span>

<span data-ttu-id="cab2b-340">Spécifie le dossier où placer les assemblys de sortie.</span><span class="sxs-lookup"><span data-stu-id="cab2b-340">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="cab2b-341">Les assemblys de sortie (et les autres fichiers de sortie) sont copiés dans les dossiers de leur framework respectif.</span><span class="sxs-lookup"><span data-stu-id="cab2b-341">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="cab2b-342">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="cab2b-342">ContentTargetFolders</span></span>

<span data-ttu-id="cab2b-343">Cette propriété spécifie l’emplacement par défaut où placer tous les fichiers de contenu si `PackagePath` n’est pas spécifié pour eux.</span><span class="sxs-lookup"><span data-stu-id="cab2b-343">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="cab2b-344">La valeur par défaut est « content;contentFiles ».</span><span class="sxs-lookup"><span data-stu-id="cab2b-344">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="cab2b-345">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="cab2b-345">NuspecFile</span></span>

<span data-ttu-id="cab2b-346">Chemin relatif ou absolu du fichier *.nuspec* utilisé pour la compression.</span><span class="sxs-lookup"><span data-stu-id="cab2b-346">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="cab2b-347">Si le fichier *.nuspec* est spécifié, il est utilisé **exclusivement** pour les informations de packaging et toutes les informations non utilisées dans les projets.</span><span class="sxs-lookup"><span data-stu-id="cab2b-347">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="cab2b-348">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="cab2b-348">NuspecBasePath</span></span>

<span data-ttu-id="cab2b-349">Chemin de base pour le fichier *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="cab2b-349">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="cab2b-350">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="cab2b-350">NuspecProperties</span></span>

<span data-ttu-id="cab2b-351">Liste de paires clé=valeur séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="cab2b-351">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="cab2b-352">Propriétés AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="cab2b-352">AssemblyInfo properties</span></span>

<span data-ttu-id="cab2b-353">Les [attributs d’assembly](../../standard/assembly/set-attributes.md) qui figurent généralement dans un fichier *AssemblyInfo* désormais générés automatiquement à partir des propriétés.</span><span class="sxs-lookup"><span data-stu-id="cab2b-353">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="cab2b-354">Propriétés par attribut</span><span class="sxs-lookup"><span data-stu-id="cab2b-354">Properties per attribute</span></span>

<span data-ttu-id="cab2b-355">Comme le montre le tableau suivant, chaque attribut a une propriété qui contrôle son contenu et une autre qui désactive sa génération :</span><span class="sxs-lookup"><span data-stu-id="cab2b-355">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="cab2b-356">Attribut</span><span class="sxs-lookup"><span data-stu-id="cab2b-356">Attribute</span></span>                                                      | <span data-ttu-id="cab2b-357">Propriété</span><span class="sxs-lookup"><span data-stu-id="cab2b-357">Property</span></span>               | <span data-ttu-id="cab2b-358">Propriété permettant de désactiver</span><span class="sxs-lookup"><span data-stu-id="cab2b-358">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="cab2b-359">Remarques :</span><span class="sxs-lookup"><span data-stu-id="cab2b-359">Notes:</span></span>

- <span data-ttu-id="cab2b-360">Le comportement par défaut de `AssemblyVersion` et `FileVersion` consiste à prendre la valeur de `$(Version)` sans suffixe.</span><span class="sxs-lookup"><span data-stu-id="cab2b-360">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="cab2b-361">Par exemple, si `$(Version)` est `1.2.3-beta.4`, alors la valeur serait `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-361">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="cab2b-362">`InformationalVersion` utilise par défaut la valeur de `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-362">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="cab2b-363">`$(SourceRevisionId)` est ajouté à `InformationalVersion` si la propriété est présente.</span><span class="sxs-lookup"><span data-stu-id="cab2b-363">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="cab2b-364">Cela peut être désactivé à l’aide de `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-364">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="cab2b-365">Les propriétés `Copyright` et `Description` sont également utilisées pour les métadonnées NuGet.</span><span class="sxs-lookup"><span data-stu-id="cab2b-365">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="cab2b-366">`Configuration` est partagé avec le processus de génération et défini par le biais du paramètre `--configuration` des commandes `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-366">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="cab2b-367">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="cab2b-367">GenerateAssemblyInfo</span></span>

<span data-ttu-id="cab2b-368">Valeur booléenne qui active ou désactive la génération AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="cab2b-368">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="cab2b-369">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="cab2b-369">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="cab2b-370">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="cab2b-370">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="cab2b-371">Chemin d’accès du fichier d’informations sur l’assembly généré.</span><span class="sxs-lookup"><span data-stu-id="cab2b-371">The path of the generated assembly info file.</span></span> <span data-ttu-id="cab2b-372">Utilise par défaut un fichier dans le répertoire `$(IntermediateOutputPath)` (obj).</span><span class="sxs-lookup"><span data-stu-id="cab2b-372">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
