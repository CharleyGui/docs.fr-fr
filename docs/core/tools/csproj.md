---
title: Ajouts au format csproj pour .NET Core
description: Découvrir les différences entre les fichiers csproj existants et les fichiers csproj .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: a9b1caf6068a7161258a6825ed16894ac41b3be7
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397538"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="0ca7d-103">Ajouts au format csproj pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ca7d-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="0ca7d-104">Ce document décrit les modifications qui ont été ajoutées aux fichiers projet dans le cadre du passage de *project.json* à *csproj* et [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="0ca7d-105">Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="0ca7d-106">Références de package implicites</span><span class="sxs-lookup"><span data-stu-id="0ca7d-106">Implicit package references</span></span>

<span data-ttu-id="0ca7d-107">Les métapackages sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété `<TargetFramework>` ou `<TargetFrameworks>` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="0ca7d-108">`<TargetFrameworks>` est ignoré si `<TargetFramework>` est spécifié, indépendamment de l’ordre.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="0ca7d-109">Pour plus d’informations, consultez [Packages, métapackages et frameworks](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-109">For more information, see [Packages, metapackages and frameworks](../packages.md).</span></span> 

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

### <a name="recommendations"></a><span data-ttu-id="0ca7d-110">Recommandations</span><span class="sxs-lookup"><span data-stu-id="0ca7d-110">Recommendations</span></span>

<span data-ttu-id="0ca7d-111">Comme les métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` sont implicitement référencés, voici les bonnes pratiques que nous recommandons :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="0ca7d-112">Quand vous ciblez .NET Core ou .NET Standard, n’incluez jamais de référence explicite aux métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` via un élément `<PackageReference>` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="0ca7d-113">Si vous avez besoin d’une version spécifique du runtime quand vous ciblez .NET Core, vous devez utiliser la propriété `<RuntimeFrameworkVersion>` dans votre projet (par exemple, `1.0.4`) au lieu de référencer le métapackage.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="0ca7d-114">Cela peut se produire si vous utilisez des [déploiements autonomes](../deploying/index.md#self-contained-deployments-scd) et que vous devez utiliser une version de correctif spécifique du runtime 1.0.0 LTS, par exemple.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="0ca7d-115">Si vous avez besoin d’une version spécifique du métapackage `NETStandard.Library` quand vous ciblez .NET Standard, vous pouvez utiliser la propriété `<NetStandardImplicitPackageVersion>` et définir la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="0ca7d-116">Vous ne devez pas ajouter ni mettre à jour explicitement les références au métapackage `Microsoft.NETCore.App` ou `NETStandard.Library` dans les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="0ca7d-117">Si une version de `NETStandard.Library` est nécessaire lors de l’utilisation d’un package NuGet basé sur .NET Standard, NuGet installe automatiquement cette version.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="0ca7d-118">Version implicite pour certaines références de packages</span><span class="sxs-lookup"><span data-stu-id="0ca7d-118">Implicit version for some package references</span></span>

<span data-ttu-id="0ca7d-119">La plupart des utilisations de [ `<PackageReference>` ](#packagereference) nécessitent de définir l’attribut `Version` pour spécifier la version du package NuGet à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="0ca7d-120">Cependant, lorsque vous utilisez .NET Core 2.1 ou 2.2 et référencez [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) ou [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), cet attribut n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="0ca7d-121">Le Kit SDK .NET Core peut sélectionner automatiquement la version des packages à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="0ca7d-122">Recommandation</span><span class="sxs-lookup"><span data-stu-id="0ca7d-122">Recommendation</span></span>

<span data-ttu-id="0ca7d-123">Lorsque vous référencez les packages `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All`, ne spécifiez pas leur version.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="0ca7d-124">Si une version est spécifiée, le Kit SDK risque de générer l’avertissement NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="0ca7d-125">Pour résoudre cet avertissement, supprimez la version du package, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="0ca7d-126">Problème connu : le Kit SDK .NET Core 2.1 prend uniquement en charge cette syntaxe si le projet utilise également Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="0ca7d-127">Ce problème est résolu dans le SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="0ca7d-128">Ces références aux métapackages ASP.NET Core ont un comportement légèrement différent de celui de la plupart des packages NuGet normaux.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="0ca7d-129">Les [déploiements dépendant du framework](../deploying/index.md#framework-dependent-deployments-fdd) d’applications qui utilisent ces métapackages tirent automatiquement parti du framework partagé ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-129">[Framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="0ca7d-130">Quand vous utilisez les métapackages **aucune** des ressources des packages NuGet ASP.NET Core référencés n’est déployée avec l’application — le framework partagé ASP.NET Core contient ces ressources.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="0ca7d-131">Les ressources présentes dans le framework partagé sont optimisées pour la plateforme cible afin d’améliorer la vitesse de démarrage des applications.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="0ca7d-132">Pour plus d’informations sur le framework partagé, consultez [Empaquetage de la distribution de .NET Core](../build/distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-132">For more information about shared framework, see [.NET Core distribution packaging](../build/distribution-packaging.md).</span></span>

<span data-ttu-id="0ca7d-133">Si une version *est* spécifiée, elle est traitée comme la version *minimale* du framework partagé ASP.NET Core pour les déploiements dépendant du framework, et comme une version *exacte* pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="0ca7d-134">Cela peut avoir les conséquences suivantes :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-134">This can have the following consequences:</span></span>

* <span data-ttu-id="0ca7d-135">Si la version d’ASP.NET Core installée sur le serveur est inférieure à la version spécifiée sur PackageReference, le processus .NET Core n’est pas lancé.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="0ca7d-136">Les mises à jour du métapackage sont souvent disponibles sur NuGet.org avant que des mises à jour soient publiées dans les environnements d’hébergement comme Azure.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="0ca7d-137">La mise à jour de la version sur PackageReference avec ASP.NET Core peut entraîner l’échec d’une application déployée.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
* <span data-ttu-id="0ca7d-138">Si l’application est déployée comme un [déploiement autonome](../deploying/index.md#self-contained-deployments-scd), cette application ne peut pas contenir les dernières mises à jour de sécurité pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="0ca7d-139">Quand une version n’est pas spécifiée, le Kit SDK peut inclure automatiquement la dernière version ASP.NET Core dans le déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="0ca7d-140">Inclusions de compilation par défaut dans les projets .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ca7d-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="0ca7d-141">Dans le cadre du passage au format *csproj* dans les dernières versions du SDK, nous avons déplacé les inclusions et exclusions par défaut pour les éléments de compilation et les ressources incorporées dans les fichiers de propriétés du SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="0ca7d-142">Cela signifie que vous n’avez plus besoin de spécifier ces éléments dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="0ca7d-143">La principale raison de cette modification est de réduire l’encombrement de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="0ca7d-144">Les valeurs par défaut qui sont présentes dans le SDK doivent couvrir la plupart des cas d’utilisation courants, il est donc inutile de les répéter dans chaque projet que vous créez.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="0ca7d-145">Il en résulte des fichiers projet moins volumineux qui sont beaucoup plus faciles à comprendre et à modifier à la main, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="0ca7d-146">Le tableau suivant montre les éléments et les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le SDK :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="0ca7d-147">Élément</span><span class="sxs-lookup"><span data-stu-id="0ca7d-147">Element</span></span>           | <span data-ttu-id="0ca7d-148">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="0ca7d-148">Include glob</span></span>                              | <span data-ttu-id="0ca7d-149">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="0ca7d-149">Exclude glob</span></span>                                                  | <span data-ttu-id="0ca7d-150">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="0ca7d-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="0ca7d-151">Compile</span><span class="sxs-lookup"><span data-stu-id="0ca7d-151">Compile</span></span>           | <span data-ttu-id="0ca7d-152">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="0ca7d-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="0ca7d-153">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0ca7d-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="0ca7d-154">N/A</span><span class="sxs-lookup"><span data-stu-id="0ca7d-154">N/A</span></span>                      |
| <span data-ttu-id="0ca7d-155">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="0ca7d-155">EmbeddedResource</span></span>  | <span data-ttu-id="0ca7d-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0ca7d-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="0ca7d-157">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0ca7d-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0ca7d-158">N/A</span><span class="sxs-lookup"><span data-stu-id="0ca7d-158">N/A</span></span>                      |
| <span data-ttu-id="0ca7d-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="0ca7d-160">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="0ca7d-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="0ca7d-161">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="0ca7d-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="0ca7d-162">**Exclure Glob** exclut toujours les dossiers `./bin` et `./obj`, respectivement représentés par les propriétés MSBuild `$(BaseOutputPath)` et `$(BaseIntermediateOutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="0ca7d-163">Dans l’ensemble, toutes les exclusions sont représentées par `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="0ca7d-164">Si vous avez des modèles Glob dans votre projet et que vous essayez de le générer à l’aide du dernier SDK, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="0ca7d-165">Des éléments de compilation en double ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="0ca7d-166">Le SDK .NET inclut des éléments de compilation de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="0ca7d-167">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="0ca7d-168">Pour contourner cette erreur, vous pouvez supprimer les éléments `Compile` explicites qui correspondent à ceux répertoriés dans le tableau précédent ou vous pouvez définir la propriété `<EnableDefaultCompileItems>` sur `false`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="0ca7d-169">Le fait de définir cette propriété avec la valeur `false` désactive l’inclusion implicite, ce qui rétablit le comportement des SDK précédents dans lesquels vous deviez spécifier les globs par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="0ca7d-170">Ce changement ne modifie pas le mécanisme principal des autres inclusions.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="0ca7d-171">Toutefois, si vous voulez, par exemple, spécifier certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes connus dans *csproj* correspondants (par exemple, l’élément `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="0ca7d-172">`<EnableDefaultCompileItems>` désactive uniquement les modèles Glob `Compile`, mais n’affecte pas les autres modèles Glob, comme le modèle Glob implicite `None`, qui s’applique également aux éléments \*.cs.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="0ca7d-173">Par conséquent, **l’Explorateur de solutions** continue d’afficher des éléments \*.cs dans le cadre du projet, inclus en tant qu’éléments `None`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="0ca7d-174">De la même façon, vous pouvez affecter à `<EnableDefaultNoneItems>` la valeur false pour désactiver le modèle Glob implicite `None`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="0ca7d-175">Pour désactiver **tous les modèles Glob implicites**, vous pouvez affecter à la propriété `<EnableDefaultItems>` la valeur `false` comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="0ca7d-176">Comment afficher la totalité du projet tel qu’il est perçu par MSBuild ?</span><span class="sxs-lookup"><span data-stu-id="0ca7d-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="0ca7d-177">Même si ces modifications csproj simplifient considérablement les fichiers projet, vous pouvez souhaiter voir le projet entièrement développé tel qu’il est perçu par MSBuild une fois le kit SDK et ses cibles inclus.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="0ca7d-178">Prétraitez le projet avec [le commutateur `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](dotnet-msbuild.md), qui affiche les fichiers qui sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="0ca7d-179">Si le projet comporte plusieurs frameworks cibles, les résultats de la commande ne doivent se concentrer que sur un seul d'entre eux en le spécifiant en tant que propriété MSBuild :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="0ca7d-180">Ajouts</span><span class="sxs-lookup"><span data-stu-id="0ca7d-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="0ca7d-181">Attribut Sdk</span><span class="sxs-lookup"><span data-stu-id="0ca7d-181">Sdk attribute</span></span>

<span data-ttu-id="0ca7d-182">L’élément `<Project>` racine du fichier *.csproj* a un nouvel attribut nommé `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="0ca7d-183">`Sdk` spécifie le SDK à utiliser par le projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="0ca7d-184">Le SDK, comme le décrit le [document de superposition](cli-msbuild-architecture.md), est un ensemble de [tâches](/visualstudio/msbuild/msbuild-tasks) et de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild pouvant générer du code .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="0ca7d-185">Trois SDK principaux sont fournis avec les outils .NET Core, et deux autres SDK sont fournis lors de l’utilisation de la préversion de .NET Core 3.0 :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-185">We ship three main SDKs with the .NET Core tools and an additional two SDKs when using .NET Core 3.0 Preview:</span></span>

1. <span data-ttu-id="0ca7d-186">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="0ca7d-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="0ca7d-187">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="0ca7d-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="0ca7d-188">Le Kit SDK de la bibliothèque de classes .NET Core Razor avec l’ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="0ca7d-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="0ca7d-189">Le Service Worker .NET Core avec l’ID `Microsoft.NET.Sdk.Worker` (préversion de .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="0ca7d-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 Preview)</span></span>
5. <span data-ttu-id="0ca7d-190">WinForms et WPF .NET Core avec l’ID `Microsoft.NET.Sdk.WindowsDesktop` (préversion de .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="0ca7d-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 Preview)</span></span>

<span data-ttu-id="0ca7d-191">Vous devez définir l’attribut `Sdk` sur un de ces ID pour l’élément `<Project>` afin d’utiliser les outils .NET Core et générer votre code.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="0ca7d-192">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0ca7d-192">PackageReference</span></span>

<span data-ttu-id="0ca7d-193">Un élément `<PackageReference>` spécifie une [dépendance NuGet dans le projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="0ca7d-194">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="0ca7d-195">Version</span><span class="sxs-lookup"><span data-stu-id="0ca7d-195">Version</span></span>

<span data-ttu-id="0ca7d-196">L’attribut obligatoire `Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="0ca7d-197">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="0ca7d-198">Le comportement par défaut est une correspondance exacte entre les versions.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="0ca7d-199">Par exemple, la spécification `Version="1.2.3"` est équivalente à la notation `[1.2.3]` de NuGet pour la version du package 1.2.3 précisément.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="0ca7d-200">IncludeAssets, ExcludeAssets et PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="0ca7d-200">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

<span data-ttu-id="0ca7d-201">L’attribut `IncludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="0ca7d-202">Par défaut, toutes les ressources du package sont incluses.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-202">By default, all package assets are included.</span></span>

<span data-ttu-id="0ca7d-203">L’attribut `ExcludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` ne doivent pas être utilisées.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="0ca7d-204">L’attribut `PrivateAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées, mais sans être reprises dans le projet suivant.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="0ca7d-205">Les ressources `Analyzers`, `Build` et `ContentFiles` sont par défaut privées en l’absence de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="0ca7d-206">`PrivateAssets` est équivalent à l’élément *project.json*/*xproj* `SuppressParent`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="0ca7d-207">Ces attributs peuvent contenir un ou plusieurs éléments de la liste suivante, séparés par le caractère point-virgule `;` le cas échéant :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* <span data-ttu-id="0ca7d-208">`Compile` : Le contenu du dossier lib est disponible pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-208">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="0ca7d-209">`Runtime` : Le contenu du dossier runtime est distribué.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-209">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="0ca7d-210">`ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="0ca7d-211">`Build` : Les propriétés/cibles du dossier de génération sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-211">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="0ca7d-212">`Native` : Le contenu des ressources natives est copié dans le dossier de sortie de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-212">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="0ca7d-213">`Analyzers` : Les analyseurs sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="0ca7d-214">Sinon, l’attribut peut contenir :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-214">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="0ca7d-215">`None` : Aucune ressource n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-215">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="0ca7d-216">`All` : Toutes les ressources sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="0ca7d-217">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="0ca7d-217">DotNetCliToolReference</span></span>
<span data-ttu-id="0ca7d-218">Un élément `<DotNetCliToolReference>` spécifie l’outil CLI que l’utilisateur souhaite restaurer dans le contexte du projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="0ca7d-219">Il constitue une alternative au nœud `tools` dans *project.json*.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="0ca7d-220">Version</span><span class="sxs-lookup"><span data-stu-id="0ca7d-220">Version</span></span>

<span data-ttu-id="0ca7d-221">`Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="0ca7d-222">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="0ca7d-223">Le comportement par défaut est une correspondance exacte entre les versions.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-223">The default behavior is an exact version match.</span></span> <span data-ttu-id="0ca7d-224">Par exemple, la spécification `Version="1.2.3"` est équivalente à la notation `[1.2.3]` de NuGet pour la version du package 1.2.3 précisément.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="0ca7d-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0ca7d-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="0ca7d-226">L’élément de propriété `<RuntimeIdentifiers>` vous permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="0ca7d-227">Les RID permettent de publier des déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="0ca7d-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0ca7d-228">RuntimeIdentifier</span></span>

<span data-ttu-id="0ca7d-229">L’élément de propriété `<RuntimeIdentifier>` vous permet de spécifier un seul [identificateur de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0ca7d-230">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="0ca7d-231">Utilisez plutôt `<RuntimeIdentifiers>` (au pluriel) si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="0ca7d-232">`<RuntimeIdentifier>` peut fournir des builds plus rapides quand un seul runtime est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="0ca7d-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="0ca7d-233">PackageTargetFallback</span></span>

<span data-ttu-id="0ca7d-234">L’élément de propriété `<PackageTargetFallback>` vous permet de spécifier un jeu de cibles compatibles à utiliser lors de la restauration des packages.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="0ca7d-235">Il est conçu pour permettre aux packages qui utilisent le [moniker du framework cible](/nuget/schema/target-frameworks) dotnet de fonctionner avec les packages qui ne déclarent pas de moniker du framework cible dotnet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="0ca7d-236">Si votre projet utilise le moniker du framework cible dotnet, tous les packages dont il dépend doivent également avoir un moniker du framework cible dotnet, sauf si vous ajoutez `<PackageTargetFallback>` à votre projet pour permettre aux plateformes autres que dotnet d’être compatibles avec dotnet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="0ca7d-237">L’exemple suivant fournit les solutions de secours pour toutes les cibles dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="0ca7d-238">L’exemple suivant spécifie les solutions de secours uniquement pour la cible `netcoreapp2.1` :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="0ca7d-239">Propriétés de métadonnées NuGet</span><span class="sxs-lookup"><span data-stu-id="0ca7d-239">NuGet metadata properties</span></span>

<span data-ttu-id="0ca7d-240">Avec le passage à MSBuild, nous avons transféré les métadonnées d’entrée utilisées lors de la compression d’un package NuGet des fichiers *project.json* vers les fichiers *csproj*.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-240">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="0ca7d-241">Les entrées sont des propriétés MSBuild qui doivent donc être placées dans un groupe `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-241">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="0ca7d-242">Voici la liste des propriétés qui sont utilisées comme entrées dans le processus de compression lors de l’utilisation de la commande `dotnet pack` ou de la cible MSBuild `Pack` qui fait partie du SDK.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-242">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="0ca7d-243">IsPackable</span><span class="sxs-lookup"><span data-stu-id="0ca7d-243">IsPackable</span></span>

<span data-ttu-id="0ca7d-244">Valeur booléenne qui spécifie si le projet peut être compressé.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-244">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="0ca7d-245">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-245">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="0ca7d-246">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="0ca7d-246">PackageVersion</span></span>

<span data-ttu-id="0ca7d-247">Spécifie la version du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-247">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="0ca7d-248">Accepte toutes les formes de la chaîne de version NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-248">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="0ca7d-249">La valeur par défaut est la valeur de `$(Version)`, autrement dit, de la propriété `Version` dans le projet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-249">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="0ca7d-250">PackageId</span><span class="sxs-lookup"><span data-stu-id="0ca7d-250">PackageId</span></span>

<span data-ttu-id="0ca7d-251">Spécifie le nom du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-251">Specifies the name for the resulting package.</span></span> <span data-ttu-id="0ca7d-252">Si non spécifié, l’opération `pack` utilise par défaut le `AssemblyName` ou le nom du répertoire comme nom du package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-252">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="0ca7d-253">Titre</span><span class="sxs-lookup"><span data-stu-id="0ca7d-253">Title</span></span>

<span data-ttu-id="0ca7d-254">Titre convivial du package, généralement utilisé dans les affichages de l’interface utilisateur comme sur nuget.org et dans le gestionnaire de package de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-254">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="0ca7d-255">Si non spécifié, l’ID de package est utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-255">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="0ca7d-256">Auteurs</span><span class="sxs-lookup"><span data-stu-id="0ca7d-256">Authors</span></span>

<span data-ttu-id="0ca7d-257">Liste séparée par des points-virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org. Ceux-ci sont affichés dans la galerie NuGet sur nuget.org et servent à croiser les références des packages de mêmes auteurs.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-257">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="0ca7d-258">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="0ca7d-258">PackageDescription</span></span>

<span data-ttu-id="0ca7d-259">Description longue du package pour l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-259">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="0ca7d-260">Description</span><span class="sxs-lookup"><span data-stu-id="0ca7d-260">Description</span></span>

<span data-ttu-id="0ca7d-261">Description longue de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-261">A long description for the assembly.</span></span> <span data-ttu-id="0ca7d-262">Si `PackageDescription` n’est pas spécifié, cette propriété est également utilisée comme description du package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-262">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="0ca7d-263">Copyright</span><span class="sxs-lookup"><span data-stu-id="0ca7d-263">Copyright</span></span>

<span data-ttu-id="0ca7d-264">Détails de copyright pour le package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-264">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="0ca7d-265">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="0ca7d-265">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="0ca7d-266">Valeur booléenne qui spécifie si le client doit inviter l’utilisateur à accepter la licence du package avant d’installer le package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-266">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="0ca7d-267">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-267">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="0ca7d-268">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="0ca7d-268">PackageLicenseExpression</span></span>

<span data-ttu-id="0ca7d-269">[Identificateur de licence SPDX](https://spdx.org/licenses/) ou expression.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-269">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="0ca7d-270">Par exemple, `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-270">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="0ca7d-271">Voici la liste complète des [identificateurs de licence SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-271">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="0ca7d-272">NuGet.org n’accepte que les licences approuvées OSI et FSF avec une expression de type licence.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-272">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="0ca7d-273">La syntaxe exacte des expressions de licence est décrite ci-dessous dans [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-273">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```cli
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
> <span data-ttu-id="0ca7d-274">Il n’est pas possible de spécifier plusieurs des éléments suivants à la fois : `PackageLicenseExpression`, `PackageLicenseFile` et `PackageLicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-274">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="0ca7d-275">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="0ca7d-275">PackageLicenseFile</span></span>

<span data-ttu-id="0ca7d-276">Chemin d’un fichier de licence du package, si la licence utilisée n’a pas été attribuée à un identificateur SPDX, ou il s’agit d’une licence personnalisée (sinon, `PackageLicenseExpression` est recommandé).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-276">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="0ca7d-277">Remplace `PackageLicenseUrl`, n’est pas combinable avec `PackageLicenseExpression` et exige Visual Studio 15.9.4, le kit SDK .NET 2.1.502 ou 2.2.101, ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-277">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="0ca7d-278">Vérifiez que le fichier de licence est empaqueté en l’ajoutant explicitement au projet ; voici un exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-278">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="0ca7d-279">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="0ca7d-279">PackageLicenseUrl</span></span>

<span data-ttu-id="0ca7d-280">URL vers la licence applicable au package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-280">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="0ca7d-281">(_Déconseillé depuis Visual Studio 15.9.4, le kit SDK .NET 2.1.502 et 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="0ca7d-281">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="0ca7d-282">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="0ca7d-282">PackageIconUrl</span></span>

<span data-ttu-id="0ca7d-283">URL d’une image 64 x 64 avec un arrière-plan transparent à utiliser comme icône pour le package dans l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-283">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="0ca7d-284">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="0ca7d-284">PackageReleaseNotes</span></span>

<span data-ttu-id="0ca7d-285">Notes de publication du package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-285">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="0ca7d-286">PackageTags</span><span class="sxs-lookup"><span data-stu-id="0ca7d-286">PackageTags</span></span>

<span data-ttu-id="0ca7d-287">Liste de balises séparées par un point-virgule qui désigne le package.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-287">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="0ca7d-288">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="0ca7d-288">PackageOutputPath</span></span>

<span data-ttu-id="0ca7d-289">Détermine le chemin de sortie dans lequel le package compressé est déposé.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-289">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="0ca7d-290">La valeur par défaut est `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-290">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="0ca7d-291">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="0ca7d-291">IncludeSymbols</span></span>
<span data-ttu-id="0ca7d-292">Cette valeur booléenne indique si le package doit créer un package de symboles supplémentaire quand le projet est compressé.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-292">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="0ca7d-293">Le format du package de symboles est contrôlé par la propriété `SymbolPackageFormat`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-293">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="0ca7d-294">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="0ca7d-294">SymbolPackageFormat</span></span>
<span data-ttu-id="0ca7d-295">Spécifie le format du package de symboles.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-295">Specifies the format of the symbols package.</span></span> <span data-ttu-id="0ca7d-296">Si la valeur est « symbols.nupkg », un package de symboles hérité est créé avec une extension *.symbols.nupkg* contenant des fichiers PDB, DLL et d’autres fichiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-296">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="0ca7d-297">Si la valeur est « snupkg », un package de symboles snupkg est créé, contenant les fichiers PDB portables.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-297">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="0ca7d-298">La valeur par défaut est « symbols.nupkg ».</span><span class="sxs-lookup"><span data-stu-id="0ca7d-298">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="0ca7d-299">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="0ca7d-299">IncludeSource</span></span>

<span data-ttu-id="0ca7d-300">Cette valeur booléenne indique si le processus de compression doit créer un package source.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-300">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="0ca7d-301">Le package source contient le code source de la bibliothèque ainsi que les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-301">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="0ca7d-302">Les fichiers sources sont placés dans le répertoire `src/ProjectName` dans le fichier de package obtenu.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-302">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="0ca7d-303">IsTool</span><span class="sxs-lookup"><span data-stu-id="0ca7d-303">IsTool</span></span>

<span data-ttu-id="0ca7d-304">Spécifie si tous les fichiers de sortie sont copiés dans le dossier *tools* au lieu du dossier *lib*.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-304">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="0ca7d-305">Notez que cela est différent d’un `DotNetCliTool` qui est spécifié en définissant `PackageType` dans le fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-305">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="0ca7d-306">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="0ca7d-306">RepositoryUrl</span></span>

<span data-ttu-id="0ca7d-307">Spécifie l’URL du dépôt où réside le code source du package et/ou à partir de laquelle il est généré.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-307">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="0ca7d-308">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="0ca7d-308">RepositoryType</span></span>

<span data-ttu-id="0ca7d-309">Spécifie le type de dépôt.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-309">Specifies the type of the repository.</span></span> <span data-ttu-id="0ca7d-310">La valeur par défaut est « git ».</span><span class="sxs-lookup"><span data-stu-id="0ca7d-310">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="0ca7d-311">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="0ca7d-311">NoPackageAnalysis</span></span>

<span data-ttu-id="0ca7d-312">Spécifie que le pack ne doit pas exécuter d’analyse du package après sa génération.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-312">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="0ca7d-313">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="0ca7d-313">MinClientVersion</span></span>

<span data-ttu-id="0ca7d-314">Spécifie la version minimale du client NuGet qui peut installer ce package, appliquée par nuget.exe et le gestionnaire de package Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-314">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="0ca7d-315">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="0ca7d-315">IncludeBuildOutput</span></span>

<span data-ttu-id="0ca7d-316">Ces valeurs booléennes spécifient si les assemblys de sortie de génération doivent être compressés dans le fichier *.nupkg* ou non.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-316">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="0ca7d-317">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="0ca7d-317">IncludeContentInPack</span></span>

<span data-ttu-id="0ca7d-318">Cette valeur booléenne indique si tous les éléments qui ont un type `Content` sont automatiquement inclus dans le package obtenu.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-318">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="0ca7d-319">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-319">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="0ca7d-320">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="0ca7d-320">BuildOutputTargetFolder</span></span>

<span data-ttu-id="0ca7d-321">Spécifie le dossier où placer les assemblys de sortie.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-321">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="0ca7d-322">Les assemblys de sortie (et les autres fichiers de sortie) sont copiés dans les dossiers de leur framework respectif.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-322">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="0ca7d-323">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="0ca7d-323">ContentTargetFolders</span></span>

<span data-ttu-id="0ca7d-324">Cette propriété spécifie l’emplacement par défaut où placer tous les fichiers de contenu si `PackagePath` n’est pas spécifié pour eux.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-324">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="0ca7d-325">La valeur par défaut est « content;contentFiles ».</span><span class="sxs-lookup"><span data-stu-id="0ca7d-325">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="0ca7d-326">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="0ca7d-326">NuspecFile</span></span>

<span data-ttu-id="0ca7d-327">Chemin relatif ou absolu du fichier *.nuspec* utilisé pour la compression.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-327">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="0ca7d-328">Si le fichier *.nuspec* est spécifié, il est utilisé **exclusivement** pour les informations de packaging et toutes les informations non utilisées dans les projets.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-328">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="0ca7d-329">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="0ca7d-329">NuspecBasePath</span></span>

<span data-ttu-id="0ca7d-330">Chemin de base pour le fichier *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-330">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="0ca7d-331">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="0ca7d-331">NuspecProperties</span></span>

<span data-ttu-id="0ca7d-332">Liste de paires clé=valeur séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-332">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="0ca7d-333">Propriétés AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="0ca7d-333">AssemblyInfo properties</span></span>

<span data-ttu-id="0ca7d-334">Les [attributs d’assembly](../../framework/app-domains/set-assembly-attributes.md) qui figurent généralement dans un fichier *AssemblyInfo* désormais générés automatiquement à partir des propriétés.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-334">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="0ca7d-335">Propriétés par attribut</span><span class="sxs-lookup"><span data-stu-id="0ca7d-335">Properties per attribute</span></span>

<span data-ttu-id="0ca7d-336">Chaque attribut a une propriété qui contrôle son contenu et une autre pour désactiver sa génération, comme indiqué dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-336">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="0ca7d-337">Attribut</span><span class="sxs-lookup"><span data-stu-id="0ca7d-337">Attribute</span></span>                                                      | <span data-ttu-id="0ca7d-338">Property</span><span class="sxs-lookup"><span data-stu-id="0ca7d-338">Property</span></span>               | <span data-ttu-id="0ca7d-339">Propriété permettant de désactiver</span><span class="sxs-lookup"><span data-stu-id="0ca7d-339">Property to disable</span></span>                             |
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

<span data-ttu-id="0ca7d-340">Remarques :</span><span class="sxs-lookup"><span data-stu-id="0ca7d-340">Notes:</span></span>

* <span data-ttu-id="0ca7d-341">Le comportement par défaut de `AssemblyVersion` et `FileVersion` consiste à prendre la valeur de `$(Version)` sans suffixe.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-341">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="0ca7d-342">Par exemple, si `$(Version)` est `1.2.3-beta.4`, alors la valeur serait `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-342">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="0ca7d-343">`InformationalVersion` utilise par défaut la valeur de `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-343">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="0ca7d-344">`$(SourceRevisionId)` est ajouté à `InformationalVersion` si la propriété est présente.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-344">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="0ca7d-345">Cela peut être désactivé à l’aide de `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-345">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="0ca7d-346">Les propriétés `Copyright` et `Description` sont également utilisées pour les métadonnées NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-346">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="0ca7d-347">`Configuration` est partagé avec le processus de génération et défini par le biais du paramètre `--configuration` des commandes `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-347">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="0ca7d-348">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="0ca7d-348">GenerateAssemblyInfo</span></span>

<span data-ttu-id="0ca7d-349">Valeur booléenne qui active ou désactive la génération AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-349">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="0ca7d-350">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-350">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="0ca7d-351">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="0ca7d-351">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="0ca7d-352">Chemin d’accès du fichier d’informations sur l’assembly généré.</span><span class="sxs-lookup"><span data-stu-id="0ca7d-352">The path of the generated assembly info file.</span></span> <span data-ttu-id="0ca7d-353">Utilise par défaut un fichier dans le répertoire `$(IntermediateOutputPath)` (obj).</span><span class="sxs-lookup"><span data-stu-id="0ca7d-353">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
