---
title: vue d’ensemble du projet SDK de base de NET
description: En savoir plus sur le projet .NET Core SDKs.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399174"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="f9159-103">.NET Core projet SDKs</span><span class="sxs-lookup"><span data-stu-id="f9159-103">.NET Core project SDKs</span></span>

<span data-ttu-id="f9159-104">.NET Les projets de base sont associés à un kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="f9159-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="f9159-105">Chaque projet SDK est un ensemble [d’objectifs](/visualstudio/msbuild/msbuild-targets) MSBuild et [de tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’emballage et de la publication du code.</span><span class="sxs-lookup"><span data-stu-id="f9159-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="f9159-106">SDKs disponibles</span><span class="sxs-lookup"><span data-stu-id="f9159-106">Available SDKs</span></span>

<span data-ttu-id="f9159-107">Les SDK suivants sont disponibles pour .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f9159-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="f9159-108">id</span><span class="sxs-lookup"><span data-stu-id="f9159-108">ID</span></span> | <span data-ttu-id="f9159-109">Description</span><span class="sxs-lookup"><span data-stu-id="f9159-109">Description</span></span> | <span data-ttu-id="f9159-110">Repo</span><span class="sxs-lookup"><span data-stu-id="f9159-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="f9159-111">Le SDK core .NET</span><span class="sxs-lookup"><span data-stu-id="f9159-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="f9159-112">Le .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="f9159-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="f9159-113">Le rasoir de base .NET [SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="f9159-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="f9159-114">Le service de travailleurs de base .NET SDK</span><span class="sxs-lookup"><span data-stu-id="f9159-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="f9159-115">Les WinForms de base de .NET et WPF SDK</span><span class="sxs-lookup"><span data-stu-id="f9159-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="f9159-116">Le .NET Core SDK est la base SDK pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9159-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="f9159-117">Les autres SDK font référence à la SDK Core .NET, et les projets qui sont associés aux autres SDK ont toutes les propriétés SDK de base .NET à leur disposition.</span><span class="sxs-lookup"><span data-stu-id="f9159-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="f9159-118">Le Web SDK, par exemple, dépend à la fois du .NET Core SDK et du Razor SDK.</span><span class="sxs-lookup"><span data-stu-id="f9159-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="f9159-119">Vous pouvez également écrire votre propre SDK qui peut être distribué via NuGet.</span><span class="sxs-lookup"><span data-stu-id="f9159-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="f9159-120">Fichiers projet</span><span class="sxs-lookup"><span data-stu-id="f9159-120">Project files</span></span>

<span data-ttu-id="f9159-121">.NET Les projets de base sont basés sur le format [MSBuild.](/visualstudio/msbuild/msbuild)</span><span class="sxs-lookup"><span data-stu-id="f9159-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="f9159-122">Les fichiers de projet, qui ont des extensions comme *.csproj* pour les projets C et *.fsproj* pour les projets F, sont en format XML.</span><span class="sxs-lookup"><span data-stu-id="f9159-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="f9159-123">L’élément racine d’un fichier de projet MSBuild est l’élément [projet.](/visualstudio/msbuild/project-element-msbuild)</span><span class="sxs-lookup"><span data-stu-id="f9159-123">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="f9159-124">L’élément `Project` a `Sdk` un attribut facultatif qui spécifie ce SDK (et la version) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f9159-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="f9159-125">Pour utiliser les outils .NET Core et `Sdk` construire votre code, définissez l’attribut à l’un des DI dans la table [SDKs disponible.](#available-sdks)</span><span class="sxs-lookup"><span data-stu-id="f9159-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="f9159-126">Pour spécifier un SDK qui vient de NuGet, inclure la version à la fin du nom, ou spécifier le nom et la version dans le fichier *global.json.*</span><span class="sxs-lookup"><span data-stu-id="f9159-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="f9159-127">Une autre façon de spécifier le SDK est avec l’élément [Sdk](/visualstudio/msbuild/sdk-element-msbuild) de haut niveau:</span><span class="sxs-lookup"><span data-stu-id="f9159-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="f9159-128">Le référencement d’un SDK de l’une de ces façons simplifie grandement les fichiers de projets pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9159-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="f9159-129">Tout en évaluant le projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du dossier du projet et `Sdk.targets` en bas.</span><span class="sxs-lookup"><span data-stu-id="f9159-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="f9159-130">Sur une machine Windows, les fichiers *Sdk.props* et *Sdk.targets* peuvent être trouvés dans le dossier *%ProgramFiles%'dotnet’sdk\\[version] -Sdks-Microsoft.NET.Sdk-Sdk.*</span><span class="sxs-lookup"><span data-stu-id="f9159-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="f9159-131">Prétraiter le dossier du projet</span><span class="sxs-lookup"><span data-stu-id="f9159-131">Preprocess the project file</span></span>

<span data-ttu-id="f9159-132">Vous pouvez voir le projet entièrement élargi comme MSBuild le voit après `dotnet msbuild -preprocess` le SDK et ses cibles sont inclus en utilisant la commande.</span><span class="sxs-lookup"><span data-stu-id="f9159-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="f9159-133">Le commutateur de [`dotnet msbuild`](../tools/dotnet-msbuild.md) [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande montre quels fichiers sont importés, leurs sources, et leurs contributions à la construction sans réellement construire le projet.</span><span class="sxs-lookup"><span data-stu-id="f9159-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="f9159-134">Si le projet a plusieurs cadres cibles, concentrez les résultats de la commande sur un seul cadre en le spécifiant comme propriété MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f9159-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="f9159-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f9159-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="f9159-136">La compilation par défaut comprend</span><span class="sxs-lookup"><span data-stu-id="f9159-136">Default compilation includes</span></span>

<span data-ttu-id="f9159-137">La valeur par défaut comprend et exclut pour les éléments de compilation et les ressources intégrées sont définis dans le SDK.</span><span class="sxs-lookup"><span data-stu-id="f9159-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="f9159-138">Contrairement aux projets cadres .NET non-SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier de projet, car les défauts couvrent la plupart des cas d’utilisation courants.</span><span class="sxs-lookup"><span data-stu-id="f9159-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="f9159-139">Cela conduit à de plus petits fichiers de projet qui sont plus faciles à comprendre ainsi que modifier à la main, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f9159-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="f9159-140">Le tableau suivant montre quel élément et quels [globs](https://en.wikipedia.org/wiki/Glob_(programming)) sont inclus et exclus dans le SDK core .NET:</span><span class="sxs-lookup"><span data-stu-id="f9159-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="f9159-141">Élément</span><span class="sxs-lookup"><span data-stu-id="f9159-141">Element</span></span>           | <span data-ttu-id="f9159-142">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="f9159-142">Include glob</span></span>                              | <span data-ttu-id="f9159-143">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="f9159-143">Exclude glob</span></span>                                                  | <span data-ttu-id="f9159-144">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="f9159-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="f9159-145">Compiler</span><span class="sxs-lookup"><span data-stu-id="f9159-145">Compile</span></span>           | <span data-ttu-id="f9159-146">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="f9159-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="f9159-147">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f9159-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="f9159-148">N/A</span><span class="sxs-lookup"><span data-stu-id="f9159-148">N/A</span></span>                      |
| <span data-ttu-id="f9159-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="f9159-149">EmbeddedResource</span></span>  | <span data-ttu-id="f9159-150">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f9159-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="f9159-151">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f9159-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f9159-152">N/A</span><span class="sxs-lookup"><span data-stu-id="f9159-152">N/A</span></span>                      |
| <span data-ttu-id="f9159-153">None</span><span class="sxs-lookup"><span data-stu-id="f9159-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="f9159-154">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="f9159-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="f9159-155">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="f9159-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="f9159-156">Les `./bin` `./obj` dossiers, qui sont représentés `$(BaseIntermediateOutputPath)` par les propriétés et MSBuild, `$(BaseOutputPath)` sont exclus des globs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9159-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="f9159-157">Les exclus sont représentés par le bien `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="f9159-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="f9159-158">Si vous définissez explicitement ces éléments dans votre fichier de projet, vous êtes susceptible d’obtenir l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="f9159-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="f9159-159">**Des éléments de compiles en double ont été inclus. Le .NET SDK inclut les éléments de compilation de votre répertoire de projet par défaut. Vous pouvez soit supprimer ces éléments de votre dossier de projet, soit définir la propriété 'EnableDefaultCompileItems' à 'faux' si vous souhaitez les inclure explicitement dans votre dossier de projet.**</span><span class="sxs-lookup"><span data-stu-id="f9159-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="f9159-160">Pour résoudre l’erreur, `Compile` soit supprimez les éléments explicites qui correspondent `EnableDefaultCompileItems` aux `false`éléments implicites énumérés sur le tableau précédent, ou définissez la propriété à , ce qui désactive l’inclusion implicite:</span><span class="sxs-lookup"><span data-stu-id="f9159-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="f9159-161">Si vous souhaitez spécifier, par exemple, certains fichiers pour être publiés avec votre application, vous `Content` pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l’élément.</span><span class="sxs-lookup"><span data-stu-id="f9159-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="f9159-162">`EnableDefaultCompileItems`ne désactive que les `Compile` globs, mais n’affecte pas d’autres globs, comme le glob implicite `None` qui s’applique également aux \*articles .cs.</span><span class="sxs-lookup"><span data-stu-id="f9159-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="f9159-163">Pour cette raison, Solution Explorer \*dans Visual Studio montre .cs `None` articles dans le cadre du projet, inclus comme éléments.</span><span class="sxs-lookup"><span data-stu-id="f9159-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="f9159-164">Pour désactiver le `None` glob `EnableDefaultNoneItems` implicite, réglé sur `false`:</span><span class="sxs-lookup"><span data-stu-id="f9159-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="f9159-165">Pour désactiver *tous les* globs `EnableDefaultItems` implicites, définissez la propriété à `false`:</span><span class="sxs-lookup"><span data-stu-id="f9159-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="f9159-166">Personnaliser la construction</span><span class="sxs-lookup"><span data-stu-id="f9159-166">Customize the build</span></span>

<span data-ttu-id="f9159-167">Il existe différentes façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="f9159-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="f9159-168">Vous pouvez remplacer une propriété en la passant comme argument à une commande [de msbuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="f9159-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="f9159-169">Vous pouvez également ajouter la propriété au fichier du projet ou à un fichier *Directory.Build.props.*</span><span class="sxs-lookup"><span data-stu-id="f9159-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="f9159-170">Pour une liste de propriétés utiles pour les projets .NET Core, voir [propriétés MSBuild pour .NET Core SDK projets](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="f9159-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="f9159-171">Cibles personnalisées</span><span class="sxs-lookup"><span data-stu-id="f9159-171">Custom targets</span></span>

<span data-ttu-id="f9159-172">.NET Les projets de base peuvent emballer des cibles et des propriétés MSBuild personnalisées pour les utiliser par les projets qui consomment le paquet.</span><span class="sxs-lookup"><span data-stu-id="f9159-172">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="f9159-173">Utilisez ce type d’extéabilité lorsque vous voulez :</span><span class="sxs-lookup"><span data-stu-id="f9159-173">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="f9159-174">Étendre le processus de construction.</span><span class="sxs-lookup"><span data-stu-id="f9159-174">Extend the build process.</span></span>
- <span data-ttu-id="f9159-175">Accédez aux artefacts du processus de construction, tels que les fichiers générés.</span><span class="sxs-lookup"><span data-stu-id="f9159-175">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="f9159-176">Inspectez la configuration sous laquelle la construction est invoquée.</span><span class="sxs-lookup"><span data-stu-id="f9159-176">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="f9159-177">Vous ajoutez des cibles ou des propriétés `<package_id>.props` de construction `Contoso.Utility.UsefulStuff.targets`personnalisées en plaçant des fichiers sous la forme `<package_id>.targets` ou (par exemple) dans le dossier de *construction* du projet.</span><span class="sxs-lookup"><span data-stu-id="f9159-177">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="f9159-178">Le XML suivant est un extrait d’un fichier *.csproj* qui indique à la [`dotnet pack`](../tools/dotnet-pack.md) commande ce qu’il faut emballer.</span><span class="sxs-lookup"><span data-stu-id="f9159-178">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="f9159-179">L’élément `<ItemGroup Label="dotnet pack instructions">` place les fichiers cibles dans le dossier *de construction* à l’intérieur du paquet.</span><span class="sxs-lookup"><span data-stu-id="f9159-179">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="f9159-180">L’élément `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` place les assemblages et les fichiers *.json* dans le dossier *de construction.*</span><span class="sxs-lookup"><span data-stu-id="f9159-180">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="f9159-181">Pour consommer une cible personnalisée dans `PackageReference` votre projet, ajoutez un élément qui indique le package et sa version.</span><span class="sxs-lookup"><span data-stu-id="f9159-181">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="f9159-182">Contrairement aux outils, l’ensemble de cibles personnalisées est inclus dans la fermeture de la dépendance du projet de consommation.</span><span class="sxs-lookup"><span data-stu-id="f9159-182">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="f9159-183">Vous pouvez configurer comment utiliser la cible personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f9159-183">You can configure how to use the custom target.</span></span> <span data-ttu-id="f9159-184">Puisqu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible `dotnet msbuild -t:<target-name>` donnée, courir après une autre cible, ou être invoquée manuellement en utilisant la commande.</span><span class="sxs-lookup"><span data-stu-id="f9159-184">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="f9159-185">Toutefois, pour offrir une meilleure expérience utilisateur, vous pouvez combiner des outils par projet et des cibles personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f9159-185">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="f9159-186">Dans ce scénario, l’outil par projet accepte tous les paramètres [`dotnet msbuild`](../tools/dotnet-msbuild.md) nécessaires et traduit cela dans l’invocation requise qui exécute la cible.</span><span class="sxs-lookup"><span data-stu-id="f9159-186">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="f9159-187">Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="f9159-187">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9159-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9159-188">See also</span></span>

- [<span data-ttu-id="f9159-189">Installez .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9159-189">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="f9159-190">Comment utiliser msBuild projet SDKs</span><span class="sxs-lookup"><span data-stu-id="f9159-190">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="f9159-191">Forfait personnalisé cibles et accessoires MSBuild avec NuGet</span><span class="sxs-lookup"><span data-stu-id="f9159-191">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
