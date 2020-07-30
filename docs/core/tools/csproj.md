---
title: Ajouts au format csproj pour .NET Core
description: Découvrir les différences entre les fichiers csproj existants et les fichiers csproj .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: a0cbead27e52af3114d9c44fd19c966e665a2850
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87427006"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="abd63-103">Ajouts au format csproj pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="abd63-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="abd63-104">Ce document décrit les modifications qui ont été ajoutées aux fichiers projet dans le cadre du passage de *project.json* à *csproj* et [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="abd63-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="abd63-105">Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).</span><span class="sxs-lookup"><span data-stu-id="abd63-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="abd63-106">Références de package implicites</span><span class="sxs-lookup"><span data-stu-id="abd63-106">Implicit package references</span></span>

<span data-ttu-id="abd63-107">Les métapackages sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété `<TargetFramework>` ou `<TargetFrameworks>` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="abd63-108">`<TargetFrameworks>` est ignoré si `<TargetFramework>` est spécifié, indépendamment de l’ordre.</span><span class="sxs-lookup"><span data-stu-id="abd63-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="abd63-109">Recommandations</span><span class="sxs-lookup"><span data-stu-id="abd63-109">Recommendations</span></span>

<span data-ttu-id="abd63-110">Comme les métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` sont implicitement référencés, voici les bonnes pratiques que nous recommandons :</span><span class="sxs-lookup"><span data-stu-id="abd63-110">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="abd63-111">Quand vous ciblez .NET Core ou .NET Standard, n’incluez jamais de référence explicite aux métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` via un élément `<PackageReference>` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="abd63-112">Si vous avez besoin d’une version spécifique du runtime quand vous ciblez .NET Core, vous devez utiliser la propriété `<RuntimeFrameworkVersion>` dans votre projet (par exemple, `1.0.4`) au lieu de référencer le métapackage.</span><span class="sxs-lookup"><span data-stu-id="abd63-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="abd63-113">Cela peut se produire si vous utilisez des [déploiements autonomes](../deploying/index.md#publish-self-contained) et que vous devez utiliser une version de correctif spécifique du runtime 1.0.0 LTS, par exemple.</span><span class="sxs-lookup"><span data-stu-id="abd63-113">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="abd63-114">Si vous avez besoin d’une version spécifique du métapackage `NETStandard.Library` quand vous ciblez .NET Standard, vous pouvez utiliser la propriété `<NetStandardImplicitPackageVersion>` et définir la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="abd63-114">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="abd63-115">Vous ne devez pas ajouter ni mettre à jour explicitement les références au métapackage `Microsoft.NETCore.App` ou `NETStandard.Library` dans les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abd63-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="abd63-116">Si une version de `NETStandard.Library` est nécessaire lors de l’utilisation d’un package NuGet basé sur .NET Standard, NuGet installe automatiquement cette version.</span><span class="sxs-lookup"><span data-stu-id="abd63-116">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="abd63-117">Version implicite pour certaines références de packages</span><span class="sxs-lookup"><span data-stu-id="abd63-117">Implicit version for some package references</span></span>

<span data-ttu-id="abd63-118">La plupart des utilisations de [`<PackageReference>`](#packagereference) requièrent la définition de l' `Version` attribut pour spécifier la version de package NuGet à utiliser.</span><span class="sxs-lookup"><span data-stu-id="abd63-118">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="abd63-119">Cependant, lorsque vous utilisez .NET Core 2.1 ou 2.2 et référencez [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) ou [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), cet attribut n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="abd63-119">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="abd63-120">Le Kit SDK .NET Core peut sélectionner automatiquement la version des packages à utiliser.</span><span class="sxs-lookup"><span data-stu-id="abd63-120">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="abd63-121">Recommandation</span><span class="sxs-lookup"><span data-stu-id="abd63-121">Recommendation</span></span>

<span data-ttu-id="abd63-122">Lorsque vous référencez les packages `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All`, ne spécifiez pas leur version.</span><span class="sxs-lookup"><span data-stu-id="abd63-122">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="abd63-123">Si une version est spécifiée, le Kit SDK risque de générer l’avertissement NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="abd63-123">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="abd63-124">Pour résoudre cet avertissement, supprimez la version du package, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="abd63-124">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="abd63-125">Problème connu : le Kit SDK .NET Core 2.1 prend uniquement en charge cette syntaxe si le projet utilise également Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="abd63-125">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="abd63-126">Ce problème est résolu dans le SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="abd63-126">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="abd63-127">Ces références aux métapackages ASP.NET Core ont un comportement légèrement différent de celui de la plupart des packages NuGet normaux.</span><span class="sxs-lookup"><span data-stu-id="abd63-127">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="abd63-128">Les [déploiements dépendant du framework](../deploying/index.md#publish-runtime-dependent) d’applications qui utilisent ces métapackages tirent automatiquement parti du framework partagé ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="abd63-128">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="abd63-129">Quand vous utilisez les métapackages **aucune** des ressources des packages NuGet ASP.NET Core référencés n’est déployée avec l’application — le framework partagé ASP.NET Core contient ces ressources.</span><span class="sxs-lookup"><span data-stu-id="abd63-129">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="abd63-130">Les ressources présentes dans le framework partagé sont optimisées pour la plateforme cible afin d’améliorer la vitesse de démarrage des applications.</span><span class="sxs-lookup"><span data-stu-id="abd63-130">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="abd63-131">Pour plus d’informations sur le framework partagé, consultez [Empaquetage de la distribution de .NET Core](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="abd63-131">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="abd63-132">Si une version *est* spécifiée, elle est traitée comme la version *minimale* du framework partagé ASP.NET Core pour les déploiements dépendant du framework, et comme une version *exacte* pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="abd63-132">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="abd63-133">Cela peut avoir les conséquences suivantes :</span><span class="sxs-lookup"><span data-stu-id="abd63-133">This can have the following consequences:</span></span>

- <span data-ttu-id="abd63-134">Si la version d’ASP.NET Core installée sur le serveur est inférieure à la version spécifiée sur PackageReference, le processus .NET Core n’est pas lancé.</span><span class="sxs-lookup"><span data-stu-id="abd63-134">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="abd63-135">Les mises à jour du métapackage sont souvent disponibles sur NuGet.org avant que des mises à jour soient publiées dans les environnements d’hébergement comme Azure.</span><span class="sxs-lookup"><span data-stu-id="abd63-135">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="abd63-136">La mise à jour de la version sur PackageReference avec ASP.NET Core peut entraîner l’échec d’une application déployée.</span><span class="sxs-lookup"><span data-stu-id="abd63-136">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="abd63-137">Si l’application est déployée comme un [déploiement autonome](../deploying/index.md#publish-self-contained), cette application ne peut pas contenir les dernières mises à jour de sécurité pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="abd63-137">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="abd63-138">Quand une version n’est pas spécifiée, le Kit SDK peut inclure automatiquement la dernière version ASP.NET Core dans le déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="abd63-138">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="abd63-139">Inclusions de compilation par défaut dans les projets .NET Core</span><span class="sxs-lookup"><span data-stu-id="abd63-139">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="abd63-140">Dans le cadre du passage au format *csproj* dans les dernières versions du SDK, nous avons déplacé les inclusions et exclusions par défaut pour les éléments de compilation et les ressources incorporées dans les fichiers de propriétés du SDK.</span><span class="sxs-lookup"><span data-stu-id="abd63-140">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="abd63-141">Cela signifie que vous n’avez plus besoin de spécifier ces éléments dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-141">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="abd63-142">La principale raison de cette modification est de réduire l’encombrement de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-142">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="abd63-143">Les valeurs par défaut qui sont présentes dans le SDK doivent couvrir la plupart des cas d’utilisation courants, il est donc inutile de les répéter dans chaque projet que vous créez.</span><span class="sxs-lookup"><span data-stu-id="abd63-143">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="abd63-144">Il en résulte des fichiers projet moins volumineux qui sont beaucoup plus faciles à comprendre et à modifier à la main, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="abd63-144">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="abd63-145">Le tableau suivant montre les éléments et les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le SDK :</span><span class="sxs-lookup"><span data-stu-id="abd63-145">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="abd63-146">Élément</span><span class="sxs-lookup"><span data-stu-id="abd63-146">Element</span></span>           | <span data-ttu-id="abd63-147">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="abd63-147">Include glob</span></span>                              | <span data-ttu-id="abd63-148">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="abd63-148">Exclude glob</span></span>                                                  | <span data-ttu-id="abd63-149">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="abd63-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="abd63-150">Compiler</span><span class="sxs-lookup"><span data-stu-id="abd63-150">Compile</span></span>           | <span data-ttu-id="abd63-151">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="abd63-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="abd63-152">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="abd63-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="abd63-153">N/A</span><span class="sxs-lookup"><span data-stu-id="abd63-153">N/A</span></span>                      |
| <span data-ttu-id="abd63-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="abd63-154">EmbeddedResource</span></span>  | <span data-ttu-id="abd63-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="abd63-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="abd63-156">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="abd63-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="abd63-157">N/A</span><span class="sxs-lookup"><span data-stu-id="abd63-157">N/A</span></span>                      |
| <span data-ttu-id="abd63-158">None</span><span class="sxs-lookup"><span data-stu-id="abd63-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="abd63-159">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="abd63-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="abd63-160">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="abd63-160">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="abd63-161">**Exclure Glob** exclut toujours les dossiers `./bin` et `./obj`, respectivement représentés par les propriétés MSBuild `$(BaseOutputPath)` et `$(BaseIntermediateOutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="abd63-161">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="abd63-162">Dans l’ensemble, toutes les exclusions sont représentées par `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="abd63-162">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="abd63-163">Si vous avez des modèles Glob dans votre projet et que vous essayez de le générer à l’aide du dernier SDK, vous obtenez l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="abd63-163">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="abd63-164">Des éléments de compilation en double ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="abd63-164">Duplicate Compile items were included.</span></span> <span data-ttu-id="abd63-165">Le SDK .NET inclut des éléments de compilation de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="abd63-165">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="abd63-166">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-166">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="abd63-167">Pour contourner cette erreur, vous pouvez supprimer les éléments `Compile` explicites qui correspondent à ceux répertoriés dans le tableau précédent ou vous pouvez définir la propriété `<EnableDefaultCompileItems>` sur `false`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="abd63-167">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="abd63-168">Le fait de définir cette propriété avec la valeur `false` désactive l’inclusion implicite, ce qui rétablit le comportement des SDK précédents dans lesquels vous deviez spécifier les globs par défaut dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-168">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="abd63-169">Ce changement ne modifie pas le mécanisme principal des autres inclusions.</span><span class="sxs-lookup"><span data-stu-id="abd63-169">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="abd63-170">Toutefois, si vous voulez, par exemple, spécifier certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes connus dans *csproj* correspondants (par exemple, l’élément `<Content>`).</span><span class="sxs-lookup"><span data-stu-id="abd63-170">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="abd63-171">`<EnableDefaultCompileItems>` désactive uniquement les modèles Glob `Compile`, mais n’affecte pas les autres modèles Glob, comme le modèle Glob implicite `None`, qui s’applique également aux éléments \*.cs.</span><span class="sxs-lookup"><span data-stu-id="abd63-171">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="abd63-172">Par conséquent, **l’Explorateur de solutions** continue d’afficher des éléments \*.cs dans le cadre du projet, inclus en tant qu’éléments `None`.</span><span class="sxs-lookup"><span data-stu-id="abd63-172">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="abd63-173">De la même façon, vous pouvez affecter à `<EnableDefaultNoneItems>` la valeur false pour désactiver le modèle Glob implicite `None`, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="abd63-173">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="abd63-174">Pour désactiver **tous les modèles Glob implicites**, vous pouvez affecter à la propriété `<EnableDefaultItems>` la valeur `false` comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="abd63-174">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="abd63-175">Comment afficher la totalité du projet tel qu’il est perçu par MSBuild ?</span><span class="sxs-lookup"><span data-stu-id="abd63-175">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="abd63-176">Même si ces modifications csproj simplifient considérablement les fichiers projet, vous pouvez souhaiter voir le projet entièrement développé tel qu’il est perçu par MSBuild une fois le kit SDK et ses cibles inclus.</span><span class="sxs-lookup"><span data-stu-id="abd63-176">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="abd63-177">Prétraitez le projet avec [le commutateur `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](dotnet-msbuild.md), qui affiche les fichiers qui sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet :</span><span class="sxs-lookup"><span data-stu-id="abd63-177">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="abd63-178">Si le projet comporte plusieurs frameworks cibles, les résultats de la commande ne doivent se concentrer que sur un seul d'entre eux en le spécifiant en tant que propriété MSBuild :</span><span class="sxs-lookup"><span data-stu-id="abd63-178">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="abd63-179">Ajouts</span><span class="sxs-lookup"><span data-stu-id="abd63-179">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="abd63-180">Attribut Sdk</span><span class="sxs-lookup"><span data-stu-id="abd63-180">Sdk attribute</span></span>

<span data-ttu-id="abd63-181">L’élément `<Project>` racine du fichier *.csproj* a un nouvel attribut nommé `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="abd63-181">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="abd63-182">`Sdk` spécifie le SDK à utiliser par le projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-182">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="abd63-183">Le SDK, comme le décrit le [document de superposition](cli-msbuild-architecture.md), est un ensemble de [tâches](/visualstudio/msbuild/msbuild-tasks) et de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild pouvant générer du code .NET Core.</span><span class="sxs-lookup"><span data-stu-id="abd63-183">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="abd63-184">Les kits de développement logiciel (SDK) suivants sont disponibles pour .NET Core :</span><span class="sxs-lookup"><span data-stu-id="abd63-184">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="abd63-185">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="abd63-185">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="abd63-186">Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="abd63-186">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="abd63-187">Le Kit SDK de la bibliothèque de classes .NET Core Razor avec l’ID `Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="abd63-187">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="abd63-188">Service Worker .NET Core avec l’ID de `Microsoft.NET.Sdk.Worker` (depuis .net core 3,0)</span><span class="sxs-lookup"><span data-stu-id="abd63-188">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="abd63-189">Le WinForms .NET Core et WPF avec l’ID de `Microsoft.NET.Sdk.WindowsDesktop` (depuis .net core 3,0)</span><span class="sxs-lookup"><span data-stu-id="abd63-189">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="abd63-190">Vous devez définir l’attribut `Sdk` sur un de ces ID pour l’élément `<Project>` afin d’utiliser les outils .NET Core et générer votre code.</span><span class="sxs-lookup"><span data-stu-id="abd63-190">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="abd63-191">PackageReference</span><span class="sxs-lookup"><span data-stu-id="abd63-191">PackageReference</span></span>

<span data-ttu-id="abd63-192">Un élément `<PackageReference>` spécifie une [dépendance NuGet dans le projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="abd63-192">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="abd63-193">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="abd63-193">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="abd63-194">Version</span><span class="sxs-lookup"><span data-stu-id="abd63-194">Version</span></span>

<span data-ttu-id="abd63-195">L’attribut obligatoire `Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="abd63-195">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="abd63-196">L’attribut respecte les règles du schéma de la [plage de versions NuGet](/nuget/concepts/package-versioning#version-ranges) .</span><span class="sxs-lookup"><span data-stu-id="abd63-196">The attribute respects the rules of the [NuGet version range](/nuget/concepts/package-versioning#version-ranges) scheme.</span></span> <span data-ttu-id="abd63-197">Le comportement par défaut est une version minimale et une correspondance inclusive.</span><span class="sxs-lookup"><span data-stu-id="abd63-197">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="abd63-198">Par exemple, la spécification de `Version="1.2.3"` est équivalente à la notation NuGet `[1.2.3, )` et signifie que le package résolu aura la version 1.2.3 si elle est disponible ou supérieure dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="abd63-198">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="abd63-199">IncludeAssets, ExcludeAssets et PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="abd63-199">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="abd63-200">L’attribut `IncludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="abd63-200">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="abd63-201">Par défaut, toutes les ressources du package sont incluses.</span><span class="sxs-lookup"><span data-stu-id="abd63-201">By default, all package assets are included.</span></span>

<span data-ttu-id="abd63-202">L’attribut `ExcludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` ne doivent pas être utilisées.</span><span class="sxs-lookup"><span data-stu-id="abd63-202">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="abd63-203">L’attribut `PrivateAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées, mais sans être reprises dans le projet suivant.</span><span class="sxs-lookup"><span data-stu-id="abd63-203">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="abd63-204">Les ressources `Analyzers`, `Build` et `ContentFiles` sont par défaut privées en l’absence de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="abd63-204">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="abd63-205">`PrivateAssets`équivaut au *project.jssur*l' / élément*xproj* `SuppressParent` .</span><span class="sxs-lookup"><span data-stu-id="abd63-205">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="abd63-206">Ces attributs peuvent contenir un ou plusieurs éléments de la liste suivante, séparés par le caractère point-virgule `;` le cas échéant :</span><span class="sxs-lookup"><span data-stu-id="abd63-206">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="abd63-207">`Compile`: le contenu du dossier *lib* est disponible pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="abd63-207">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="abd63-208">`Runtime`: le contenu du dossier *Runtime* est distribué.</span><span class="sxs-lookup"><span data-stu-id="abd63-208">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="abd63-209">`ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.</span><span class="sxs-lookup"><span data-stu-id="abd63-209">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="abd63-210">`Build`: les propriétés/cibles du dossier de *génération* sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="abd63-210">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="abd63-211">`Native`: le contenu des ressources natives est copié dans le dossier de *sortie* pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="abd63-211">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="abd63-212">`Analyzers` : Les analyseurs sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="abd63-212">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="abd63-213">Sinon, l’attribut peut contenir :</span><span class="sxs-lookup"><span data-stu-id="abd63-213">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="abd63-214">`None` : Aucune ressource n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="abd63-214">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="abd63-215">`All` : Toutes les ressources sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="abd63-215">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="abd63-216">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="abd63-216">DotNetCliToolReference</span></span>

<span data-ttu-id="abd63-217">Un élément `<DotNetCliToolReference>` spécifie l’outil CLI que l’utilisateur souhaite restaurer dans le contexte du projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-217">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="abd63-218">Il constitue une alternative au nœud `tools` dans *project.json*.</span><span class="sxs-lookup"><span data-stu-id="abd63-218">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="abd63-219">Notez que `DotNetCliToolReference` est [désormais déconseillé](https://github.com/dotnet/announcements/issues/107) en faveur des [Outils locaux .net Core](./global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="abd63-219">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](./global-tools.md#install-a-local-tool).</span></span>

#### <a name="version"></a><span data-ttu-id="abd63-220">Version</span><span class="sxs-lookup"><span data-stu-id="abd63-220">Version</span></span>

<span data-ttu-id="abd63-221">`Version` spécifie la version du package à restaurer.</span><span class="sxs-lookup"><span data-stu-id="abd63-221">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="abd63-222">L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="abd63-222">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="abd63-223">Le comportement par défaut est une version minimale et une correspondance inclusive.</span><span class="sxs-lookup"><span data-stu-id="abd63-223">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="abd63-224">Par exemple, la spécification de `Version="1.2.3"` est équivalente à la notation NuGet `[1.2.3, )` et signifie que le package résolu aura la version 1.2.3 si elle est disponible ou supérieure dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="abd63-224">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="abd63-225">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="abd63-225">RuntimeIdentifiers</span></span>

<span data-ttu-id="abd63-226">L’élément de propriété `<RuntimeIdentifiers>` vous permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-226">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="abd63-227">Les RID permettent de publier des déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="abd63-227">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="abd63-228">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="abd63-228">RuntimeIdentifier</span></span>

<span data-ttu-id="abd63-229">L’élément de propriété `<RuntimeIdentifier>` vous permet de spécifier un seul [identificateur de runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-229">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="abd63-230">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="abd63-230">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="abd63-231">Utilisez plutôt `<RuntimeIdentifiers>` (au pluriel) si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="abd63-231">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="abd63-232">`<RuntimeIdentifier>` peut fournir des builds plus rapides quand un seul runtime est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="abd63-232">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="abd63-233">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="abd63-233">PackageTargetFallback</span></span>

<span data-ttu-id="abd63-234">L’élément de propriété `<PackageTargetFallback>` vous permet de spécifier un jeu de cibles compatibles à utiliser lors de la restauration des packages.</span><span class="sxs-lookup"><span data-stu-id="abd63-234">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="abd63-235">Il est conçu pour permettre aux packages qui utilisent le [moniker du framework cible](/nuget/schema/target-frameworks) dotnet de fonctionner avec les packages qui ne déclarent pas de moniker du framework cible dotnet.</span><span class="sxs-lookup"><span data-stu-id="abd63-235">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="abd63-236">Si votre projet utilise le moniker du framework cible dotnet, tous les packages dont il dépend doivent également avoir un moniker du framework cible dotnet, sauf si vous ajoutez `<PackageTargetFallback>` à votre projet pour permettre aux plateformes autres que dotnet d’être compatibles avec dotnet.</span><span class="sxs-lookup"><span data-stu-id="abd63-236">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="abd63-237">L’exemple suivant fournit les solutions de secours pour toutes les cibles dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="abd63-237">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="abd63-238">L’exemple suivant spécifie les solutions de secours uniquement pour la cible `netcoreapp2.1` :</span><span class="sxs-lookup"><span data-stu-id="abd63-238">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="abd63-239">Événements de build</span><span class="sxs-lookup"><span data-stu-id="abd63-239">Build events</span></span>

<span data-ttu-id="abd63-240">La façon dont les événements pré-build et postérieurs à la génération sont spécifiés dans le fichier projet a changé.</span><span class="sxs-lookup"><span data-stu-id="abd63-240">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="abd63-241">Les propriétés PreBuildEvent et PostBuildEvent ne sont pas recommandées dans le format de projet de type SDK, car les macros telles que $ (ProjectDir) ne sont pas résolues.</span><span class="sxs-lookup"><span data-stu-id="abd63-241">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="abd63-242">Par exemple, le code suivant n’est plus pris en charge :</span><span class="sxs-lookup"><span data-stu-id="abd63-242">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="abd63-243">Dans les projets de type SDK, utilisez une cible MSBuild nommée `PreBuild` ou `PostBuild` et définissez la `BeforeTargets` propriété pour `PreBuild` ou `AfterTargets` pour la propriété de `PostBuild` .</span><span class="sxs-lookup"><span data-stu-id="abd63-243">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="abd63-244">Pour l’exemple précédent, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="abd63-244">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="abd63-245">Vous pouvez utiliser n’importe quel nom pour les cibles MSBuild, mais l’IDE de Visual Studio reconnaît `PreBuild` et `PostBuild` cible. nous vous recommandons donc d’utiliser ces noms pour pouvoir modifier les commandes dans l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="abd63-245">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="abd63-246">Propriétés de métadonnées NuGet</span><span class="sxs-lookup"><span data-stu-id="abd63-246">NuGet metadata properties</span></span>

<span data-ttu-id="abd63-247">Avec le passage à MSBuild, nous avons déplacé les métadonnées d’entrée utilisées lors de la compression d’un package NuGet à partir de *project.jssur des* fichiers *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="abd63-247">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="abd63-248">Les entrées sont des propriétés MSBuild qui doivent donc être placées dans un groupe `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="abd63-248">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="abd63-249">Voici la liste des propriétés utilisées comme entrées dans le processus de compression lors de l’utilisation de la `dotnet pack` commande ou de la `Pack` cible MSBuild qui fait partie du kit de développement logiciel (SDK) :</span><span class="sxs-lookup"><span data-stu-id="abd63-249">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="abd63-250">IsPackable</span><span class="sxs-lookup"><span data-stu-id="abd63-250">IsPackable</span></span>

<span data-ttu-id="abd63-251">Valeur booléenne qui spécifie si le projet peut être compressé.</span><span class="sxs-lookup"><span data-stu-id="abd63-251">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="abd63-252">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="abd63-252">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="abd63-253">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="abd63-253">PackageVersion</span></span>

<span data-ttu-id="abd63-254">Spécifie la version du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="abd63-254">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="abd63-255">Accepte toutes les formes de la chaîne de version NuGet.</span><span class="sxs-lookup"><span data-stu-id="abd63-255">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="abd63-256">La valeur par défaut est la valeur de `$(Version)`, autrement dit, de la propriété `Version` dans le projet.</span><span class="sxs-lookup"><span data-stu-id="abd63-256">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="abd63-257">PackageId</span><span class="sxs-lookup"><span data-stu-id="abd63-257">PackageId</span></span>

<span data-ttu-id="abd63-258">Spécifie le nom du package obtenu.</span><span class="sxs-lookup"><span data-stu-id="abd63-258">Specifies the name for the resulting package.</span></span> <span data-ttu-id="abd63-259">Si non spécifié, l’opération `pack` utilise par défaut le `AssemblyName` ou le nom du répertoire comme nom du package.</span><span class="sxs-lookup"><span data-stu-id="abd63-259">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="abd63-260">Titre</span><span class="sxs-lookup"><span data-stu-id="abd63-260">Title</span></span>

<span data-ttu-id="abd63-261">Titre convivial du package, généralement utilisé dans les affichages de l’interface utilisateur comme sur nuget.org et dans le gestionnaire de package de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="abd63-261">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="abd63-262">Si non spécifié, l’ID de package est utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="abd63-262">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="abd63-263">Auteurs</span><span class="sxs-lookup"><span data-stu-id="abd63-263">Authors</span></span>

<span data-ttu-id="abd63-264">Liste délimitée par des points-virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org. Ceux-ci sont affichés dans la galerie NuGet sur nuget.org et sont utilisés pour faire référence croisée aux packages par les mêmes auteurs.</span><span class="sxs-lookup"><span data-stu-id="abd63-264">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="abd63-265">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="abd63-265">PackageDescription</span></span>

<span data-ttu-id="abd63-266">Description longue du package pour l’affichage de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="abd63-266">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="abd63-267">Description</span><span class="sxs-lookup"><span data-stu-id="abd63-267">Description</span></span>

<span data-ttu-id="abd63-268">Description longue de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="abd63-268">A long description for the assembly.</span></span> <span data-ttu-id="abd63-269">Si `PackageDescription` n’est pas spécifié, cette propriété est également utilisée comme description du package.</span><span class="sxs-lookup"><span data-stu-id="abd63-269">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="abd63-270">Copyright</span><span class="sxs-lookup"><span data-stu-id="abd63-270">Copyright</span></span>

<span data-ttu-id="abd63-271">Détails de copyright pour le package.</span><span class="sxs-lookup"><span data-stu-id="abd63-271">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="abd63-272">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="abd63-272">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="abd63-273">Valeur booléenne qui spécifie si le client doit inviter l’utilisateur à accepter la licence du package avant d’installer le package.</span><span class="sxs-lookup"><span data-stu-id="abd63-273">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="abd63-274">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="abd63-274">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="abd63-275">DevelopmentDependency</span><span class="sxs-lookup"><span data-stu-id="abd63-275">DevelopmentDependency</span></span>

<span data-ttu-id="abd63-276">Valeur booléenne qui spécifie si le package est marqué en tant que dépendance de développement uniquement, ce qui empêche l’inclusion du package en tant que dépendance dans d’autres packages.</span><span class="sxs-lookup"><span data-stu-id="abd63-276">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="abd63-277">Avec PackageReference (NuGet 4.8 +), cet indicateur signifie également que les éléments multimédias de compilation sont exclus de la compilation.</span><span class="sxs-lookup"><span data-stu-id="abd63-277">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="abd63-278">Pour plus d'informations, voir [Prise en charge de DevelopmentDependency pour PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="abd63-278">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="abd63-279">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="abd63-279">PackageLicenseExpression</span></span>

<span data-ttu-id="abd63-280">[Identificateur de licence SPDX](https://spdx.org/licenses/) ou expression.</span><span class="sxs-lookup"><span data-stu-id="abd63-280">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="abd63-281">Par exemple : `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="abd63-281">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="abd63-282">Voici la liste complète des [identificateurs de licence SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="abd63-282">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="abd63-283">NuGet.org n’accepte que les licences approuvées OSI et FSF avec une expression de type licence.</span><span class="sxs-lookup"><span data-stu-id="abd63-283">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="abd63-284">La syntaxe exacte des expressions de licence est décrite ci-dessous dans [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="abd63-284">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="abd63-285">Il n’est pas possible de spécifier plusieurs des éléments suivants à la fois : `PackageLicenseExpression`, `PackageLicenseFile` et `PackageLicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="abd63-285">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="abd63-286">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="abd63-286">PackageLicenseFile</span></span>

<span data-ttu-id="abd63-287">Chemin d’un fichier de licence du package, si la licence utilisée n’a pas été attribuée à un identificateur SPDX, ou il s’agit d’une licence personnalisée (sinon, `PackageLicenseExpression` est recommandé).</span><span class="sxs-lookup"><span data-stu-id="abd63-287">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="abd63-288">Remplace `PackageLicenseUrl` , ne peut pas être combiné avec `PackageLicenseExpression` et nécessite Visual Studio version 15.9.4 et le kit de développement logiciel (SDK) .NET 2.1.502 ou 2.2.101 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="abd63-288">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="abd63-289">Vérifiez que le fichier de licence est empaqueté en l’ajoutant explicitement au projet ; voici un exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="abd63-289">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="abd63-290">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="abd63-290">PackageLicenseUrl</span></span>

<span data-ttu-id="abd63-291">URL de la licence applicable au package.</span><span class="sxs-lookup"><span data-stu-id="abd63-291">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="abd63-292">(_Déconseillé depuis Visual Studio 15.9.4, le kit SDK .NET 2.1.502 et 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="abd63-292">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageicon"></a><span data-ttu-id="abd63-293">PackageIcon</span><span class="sxs-lookup"><span data-stu-id="abd63-293">PackageIcon</span></span>

<span data-ttu-id="abd63-294">Chemin d’accès à une image dans le package à utiliser comme icône de package.</span><span class="sxs-lookup"><span data-stu-id="abd63-294">A path to an image in the package to use as a package icon.</span></span> <span data-ttu-id="abd63-295">En savoir plus sur les [ `icon` métadonnées](/nuget/reference/nuspec#icon).</span><span class="sxs-lookup"><span data-stu-id="abd63-295">Read more about [`icon` metadata](/nuget/reference/nuspec#icon).</span></span> <span data-ttu-id="abd63-296">[PackageIconUrl est déconseillé](/nuget/reference/msbuild-targets#packageiconurl) en faveur de PackageIcon.</span><span class="sxs-lookup"><span data-stu-id="abd63-296">[PackageIconUrl is deprecated](/nuget/reference/msbuild-targets#packageiconurl) in favor of PackageIcon.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="abd63-297">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="abd63-297">PackageReleaseNotes</span></span>

<span data-ttu-id="abd63-298">Notes de publication du package.</span><span class="sxs-lookup"><span data-stu-id="abd63-298">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="abd63-299">PackageTags</span><span class="sxs-lookup"><span data-stu-id="abd63-299">PackageTags</span></span>

<span data-ttu-id="abd63-300">Liste de balises séparées par un point-virgule qui désigne le package.</span><span class="sxs-lookup"><span data-stu-id="abd63-300">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="abd63-301">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="abd63-301">PackageOutputPath</span></span>

<span data-ttu-id="abd63-302">Détermine le chemin de sortie dans lequel le package compressé est déposé.</span><span class="sxs-lookup"><span data-stu-id="abd63-302">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="abd63-303">La valeur par défaut est `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="abd63-303">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="abd63-304">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="abd63-304">IncludeSymbols</span></span>
<span data-ttu-id="abd63-305">Cette valeur booléenne indique si le package doit créer un package de symboles supplémentaire quand le projet est compressé.</span><span class="sxs-lookup"><span data-stu-id="abd63-305">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="abd63-306">Le format du package de symboles est contrôlé par la propriété `SymbolPackageFormat`.</span><span class="sxs-lookup"><span data-stu-id="abd63-306">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="abd63-307">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="abd63-307">SymbolPackageFormat</span></span>
<span data-ttu-id="abd63-308">Spécifie le format du package de symboles.</span><span class="sxs-lookup"><span data-stu-id="abd63-308">Specifies the format of the symbols package.</span></span> <span data-ttu-id="abd63-309">Si la valeur est « symbols.nupkg », un package de symboles hérité est créé avec une extension *.symbols.nupkg* contenant des fichiers PDB, DLL et d’autres fichiers de sortie.</span><span class="sxs-lookup"><span data-stu-id="abd63-309">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="abd63-310">Si la valeur est « snupkg », un package de symboles snupkg est créé, contenant les fichiers PDB portables.</span><span class="sxs-lookup"><span data-stu-id="abd63-310">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="abd63-311">La valeur par défaut est « symbols.nupkg ».</span><span class="sxs-lookup"><span data-stu-id="abd63-311">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="abd63-312">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="abd63-312">IncludeSource</span></span>

<span data-ttu-id="abd63-313">Cette valeur booléenne indique si le processus de compression doit créer un package source.</span><span class="sxs-lookup"><span data-stu-id="abd63-313">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="abd63-314">Le package source contient le code source de la bibliothèque ainsi que les fichiers PDB.</span><span class="sxs-lookup"><span data-stu-id="abd63-314">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="abd63-315">Les fichiers sources sont placés dans le répertoire `src/ProjectName` dans le fichier de package obtenu.</span><span class="sxs-lookup"><span data-stu-id="abd63-315">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="abd63-316">IsTool</span><span class="sxs-lookup"><span data-stu-id="abd63-316">IsTool</span></span>

<span data-ttu-id="abd63-317">Spécifie si tous les fichiers de sortie sont copiés dans le dossier *tools* au lieu du dossier *lib*.</span><span class="sxs-lookup"><span data-stu-id="abd63-317">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="abd63-318">Cela est différent d’un `DotNetCliTool` , qui est spécifié en définissant `PackageType` dans le fichier *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="abd63-318">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="abd63-319">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="abd63-319">RepositoryUrl</span></span>

<span data-ttu-id="abd63-320">Spécifie l’URL du dépôt où réside le code source du package et/ou à partir de laquelle il est généré.</span><span class="sxs-lookup"><span data-stu-id="abd63-320">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="abd63-321">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="abd63-321">RepositoryType</span></span>

<span data-ttu-id="abd63-322">Spécifie le type de dépôt.</span><span class="sxs-lookup"><span data-stu-id="abd63-322">Specifies the type of the repository.</span></span> <span data-ttu-id="abd63-323">La valeur par défaut est « git ».</span><span class="sxs-lookup"><span data-stu-id="abd63-323">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="abd63-324">RepositoryBranch</span><span class="sxs-lookup"><span data-stu-id="abd63-324">RepositoryBranch</span></span>
<span data-ttu-id="abd63-325">Spécifie le nom de la branche source dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="abd63-325">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="abd63-326">Lorsque le projet est empaqueté dans un package NuGet, il est ajouté aux métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="abd63-326">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="abd63-327">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="abd63-327">RepositoryCommit</span></span>
<span data-ttu-id="abd63-328">Validation ou ensemble de modifications de référentiel facultatif pour indiquer la source à partir de laquelle le package a été généré.</span><span class="sxs-lookup"><span data-stu-id="abd63-328">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="abd63-329">`RepositoryUrl`doit également être spécifié pour que cette propriété soit incluse.</span><span class="sxs-lookup"><span data-stu-id="abd63-329">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="abd63-330">Lorsque le projet est empaqueté dans un package NuGet, cette validation ou cet ensemble de modifications est ajouté aux métadonnées du package.</span><span class="sxs-lookup"><span data-stu-id="abd63-330">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="abd63-331">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="abd63-331">NoPackageAnalysis</span></span>

<span data-ttu-id="abd63-332">Spécifie que le pack ne doit pas exécuter d’analyse du package après sa génération.</span><span class="sxs-lookup"><span data-stu-id="abd63-332">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="abd63-333">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="abd63-333">MinClientVersion</span></span>

<span data-ttu-id="abd63-334">Spécifie la version minimale du client NuGet qui peut installer ce package, appliquée par nuget.exe et le gestionnaire de package Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="abd63-334">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="abd63-335">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="abd63-335">IncludeBuildOutput</span></span>

<span data-ttu-id="abd63-336">Cette valeur booléenne spécifie si les assemblys de sortie de la génération doivent être empaquetés dans le fichier *. nupkg* ou non.</span><span class="sxs-lookup"><span data-stu-id="abd63-336">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="abd63-337">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="abd63-337">IncludeContentInPack</span></span>

<span data-ttu-id="abd63-338">Cette valeur booléenne indique si tous les éléments qui ont un type `Content` sont automatiquement inclus dans le package obtenu.</span><span class="sxs-lookup"><span data-stu-id="abd63-338">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="abd63-339">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="abd63-339">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="abd63-340">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="abd63-340">BuildOutputTargetFolder</span></span>

<span data-ttu-id="abd63-341">Spécifie le dossier où placer les assemblys de sortie.</span><span class="sxs-lookup"><span data-stu-id="abd63-341">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="abd63-342">Les assemblys de sortie (et les autres fichiers de sortie) sont copiés dans les dossiers de leur framework respectif.</span><span class="sxs-lookup"><span data-stu-id="abd63-342">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="abd63-343">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="abd63-343">ContentTargetFolders</span></span>

<span data-ttu-id="abd63-344">Cette propriété spécifie l’emplacement par défaut où placer tous les fichiers de contenu si `PackagePath` n’est pas spécifié pour eux.</span><span class="sxs-lookup"><span data-stu-id="abd63-344">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="abd63-345">La valeur par défaut est « content;contentFiles ».</span><span class="sxs-lookup"><span data-stu-id="abd63-345">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="abd63-346">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="abd63-346">NuspecFile</span></span>

<span data-ttu-id="abd63-347">Chemin relatif ou absolu du fichier *.nuspec* utilisé pour la compression.</span><span class="sxs-lookup"><span data-stu-id="abd63-347">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="abd63-348">Si le fichier *.nuspec* est spécifié, il est utilisé **exclusivement** pour les informations de packaging et toutes les informations non utilisées dans les projets.</span><span class="sxs-lookup"><span data-stu-id="abd63-348">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="abd63-349">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="abd63-349">NuspecBasePath</span></span>

<span data-ttu-id="abd63-350">Chemin de base pour le fichier *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="abd63-350">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="abd63-351">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="abd63-351">NuspecProperties</span></span>

<span data-ttu-id="abd63-352">Liste de paires clé=valeur séparées par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="abd63-352">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="abd63-353">Propriétés AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="abd63-353">AssemblyInfo properties</span></span>

<span data-ttu-id="abd63-354">Les [attributs d’assembly](../../standard/assembly/set-attributes.md) qui figurent généralement dans un fichier *AssemblyInfo* désormais générés automatiquement à partir des propriétés.</span><span class="sxs-lookup"><span data-stu-id="abd63-354">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="abd63-355">Propriétés par attribut</span><span class="sxs-lookup"><span data-stu-id="abd63-355">Properties per attribute</span></span>

<span data-ttu-id="abd63-356">Comme indiqué dans le tableau suivant, chaque attribut a une propriété qui contrôle son contenu et un autre qui désactive sa génération :</span><span class="sxs-lookup"><span data-stu-id="abd63-356">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="abd63-357">Attribut</span><span class="sxs-lookup"><span data-stu-id="abd63-357">Attribute</span></span>                                                      | <span data-ttu-id="abd63-358">Propriété</span><span class="sxs-lookup"><span data-stu-id="abd63-358">Property</span></span>               | <span data-ttu-id="abd63-359">Propriété permettant de désactiver</span><span class="sxs-lookup"><span data-stu-id="abd63-359">Property to disable</span></span>                             |
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

<span data-ttu-id="abd63-360">Remarques :</span><span class="sxs-lookup"><span data-stu-id="abd63-360">Notes:</span></span>

- <span data-ttu-id="abd63-361">Le comportement par défaut de `AssemblyVersion` et `FileVersion` consiste à prendre la valeur de `$(Version)` sans suffixe.</span><span class="sxs-lookup"><span data-stu-id="abd63-361">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="abd63-362">Par exemple, si `$(Version)` est `1.2.3-beta.4`, alors la valeur serait `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="abd63-362">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="abd63-363">`InformationalVersion` utilise par défaut la valeur de `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="abd63-363">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="abd63-364">`$(SourceRevisionId)` est ajouté à `InformationalVersion` si la propriété est présente.</span><span class="sxs-lookup"><span data-stu-id="abd63-364">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="abd63-365">Cela peut être désactivé à l’aide de `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="abd63-365">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="abd63-366">Les propriétés `Copyright` et `Description` sont également utilisées pour les métadonnées NuGet.</span><span class="sxs-lookup"><span data-stu-id="abd63-366">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="abd63-367">`Configuration` est partagé avec le processus de génération et défini par le biais du paramètre `--configuration` des commandes `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="abd63-367">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="abd63-368">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="abd63-368">GenerateAssemblyInfo</span></span>

<span data-ttu-id="abd63-369">Valeur booléenne qui active ou désactive la génération AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="abd63-369">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="abd63-370">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="abd63-370">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="abd63-371">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="abd63-371">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="abd63-372">Chemin d’accès du fichier d’informations sur l’assembly généré.</span><span class="sxs-lookup"><span data-stu-id="abd63-372">The path of the generated assembly info file.</span></span> <span data-ttu-id="abd63-373">Utilise par défaut un fichier dans le répertoire `$(IntermediateOutputPath)` (obj).</span><span class="sxs-lookup"><span data-stu-id="abd63-373">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
