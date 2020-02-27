---
title: Vue d’ensemble du SDK de projet .NET Core
description: En savoir plus sur les kits de développement logiciel (SDK) de projet .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: c41b25bf7933e7b1f6cb50da5e52dc0b312f5c74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626248"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="b9b80-103">Kits de développement logiciel (SDK) de projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="b9b80-103">.NET Core project SDKs</span></span>

<span data-ttu-id="b9b80-104">Les projets .NET Core sont associés à un kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="b9b80-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="b9b80-105">Chaque kit de développement logiciel (SDK) de projet est un ensemble de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild et de [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication de code.</span><span class="sxs-lookup"><span data-stu-id="b9b80-105">Each project SDK is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="b9b80-106">Kits de développement logiciel disponibles</span><span class="sxs-lookup"><span data-stu-id="b9b80-106">Available SDKs</span></span>

<span data-ttu-id="b9b80-107">Les kits de développement logiciel (SDK) suivants sont disponibles pour .NET Core :</span><span class="sxs-lookup"><span data-stu-id="b9b80-107">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="b9b80-108">id</span><span class="sxs-lookup"><span data-stu-id="b9b80-108">ID</span></span> | <span data-ttu-id="b9b80-109">Description</span><span class="sxs-lookup"><span data-stu-id="b9b80-109">Description</span></span> | <span data-ttu-id="b9b80-110">Référentiel</span><span class="sxs-lookup"><span data-stu-id="b9b80-110">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="b9b80-111">Kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="b9b80-111">The .NET Core SDK</span></span> | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="b9b80-112">Le kit de [développement logiciel (SDK) Web](/aspnet/core/razor-pages/web-sdk) .net Core</span><span class="sxs-lookup"><span data-stu-id="b9b80-112">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="b9b80-113">Le kit de [développement logiciel (SDK)](/aspnet/core/razor-pages/sdk) .net Core Razor</span><span class="sxs-lookup"><span data-stu-id="b9b80-113">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="b9b80-114">Kit de développement logiciel (SDK) .NET Core Worker service</span><span class="sxs-lookup"><span data-stu-id="b9b80-114">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="b9b80-115">Le kit de développement logiciel (SDK) .NET Core WinForms et WPF</span><span class="sxs-lookup"><span data-stu-id="b9b80-115">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="b9b80-116">Le kit SDK .NET Core est le kit de développement logiciel (SDK) de base pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9b80-116">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="b9b80-117">Les autres kits de développement logiciel (SDK) référencent les kit SDK .NET Core, et les propriétés de kit SDK .NET Core associées aux autres kits de développement logiciel (SDK) sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="b9b80-117">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="b9b80-118">Le kit de développement logiciel (SDK) Web, par exemple, dépend à la fois du kit SDK .NET Core et du kit de développement logiciel (SDK) Razor.</span><span class="sxs-lookup"><span data-stu-id="b9b80-118">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="b9b80-119">Vous pouvez également créer votre propre kit de développement logiciel (SDK) qui peut être distribué via NuGet.</span><span class="sxs-lookup"><span data-stu-id="b9b80-119">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="b9b80-120">Fichiers projet</span><span class="sxs-lookup"><span data-stu-id="b9b80-120">Project files</span></span>

<span data-ttu-id="b9b80-121">Les projets .NET Core sont basés sur le format [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="b9b80-121">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="b9b80-122">Les fichiers projet, qui ont des extensions telles que C# *. csproj* pour les projets F# et *. fsproj* pour les projets, sont au format XML.</span><span class="sxs-lookup"><span data-stu-id="b9b80-122">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="b9b80-123">L’élément racine d’un fichier projet MSBuild est l’élément de [projet](/visualstudio/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="b9b80-123">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="b9b80-124">L’élément `Project` a un attribut `Sdk` facultatif qui spécifie le kit de développement logiciel (SDK) et la version à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b9b80-124">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="b9b80-125">Pour utiliser les outils .NET Core et générer votre code, affectez à l’attribut `Sdk` l’un des ID figurant dans le tableau kits de développement logiciel ( [SDK) disponibles](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="b9b80-125">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="b9b80-126">Pour spécifier un kit de développement logiciel (SDK) qui provient de NuGet, incluez la version à la fin du nom, ou spécifiez le nom et la version dans le fichier *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="b9b80-126">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="b9b80-127">Vous pouvez également spécifier le kit de développement logiciel (SDK) à l’aide de l’élément [SDK](/visualstudio/msbuild/sdk-element-msbuild) de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="b9b80-127">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="b9b80-128">Le référencement d’un kit de développement logiciel (SDK) de l’une de ces manières simplifie grandement les fichiers projet pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9b80-128">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="b9b80-129">Lors de l’évaluation du projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du fichier projet et `Sdk.targets` en bas.</span><span class="sxs-lookup"><span data-stu-id="b9b80-129">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="b9b80-130">Sur un ordinateur Windows, les fichiers *SDK. props* et *SDK. targets* se trouvent dans le dossier *%ProgramFiles%\dotnet\sdk\\[version] \Sdks\Microsoft.net.Sdk\Sdk*</span><span class="sxs-lookup"><span data-stu-id="b9b80-130">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="b9b80-131">Prétraiter le fichier projet</span><span class="sxs-lookup"><span data-stu-id="b9b80-131">Preprocess the project file</span></span>

<span data-ttu-id="b9b80-132">Vous pouvez voir le projet entièrement développé, car MSBuild le voit après l’inclusion du kit de développement logiciel (SDK) et de ses cibles à l’aide de la commande `dotnet msbuild -preprocess`.</span><span class="sxs-lookup"><span data-stu-id="b9b80-132">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="b9b80-133">Le commutateur de [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](../tools/dotnet-msbuild.md) indique quels fichiers sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet.</span><span class="sxs-lookup"><span data-stu-id="b9b80-133">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="b9b80-134">Si le projet comporte plusieurs frameworks cibles, vous ne concentrez les résultats de la commande que sur un Framework en le spécifiant en tant que propriété MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b9b80-134">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="b9b80-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b9b80-135">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="b9b80-136">La compilation par défaut comprend</span><span class="sxs-lookup"><span data-stu-id="b9b80-136">Default compilation includes</span></span>

<span data-ttu-id="b9b80-137">Les inclusions et les exclusions par défaut pour les éléments de compilation et les ressources incorporées sont définies dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="b9b80-137">The default includes and excludes for compile items and embedded resources are defined in the SDK.</span></span> <span data-ttu-id="b9b80-138">Contrairement aux projets de .NET Framework non SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier projet, car les valeurs par défaut couvrent les cas d’utilisation les plus courants.</span><span class="sxs-lookup"><span data-stu-id="b9b80-138">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="b9b80-139">Cela donne lieu à des fichiers de projet plus petits qui sont plus faciles à comprendre et à modifier manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b9b80-139">This leads to smaller project files that are easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="b9b80-140">Le tableau suivant indique l’élément et les [modèles glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le kit SDK .net Core :</span><span class="sxs-lookup"><span data-stu-id="b9b80-140">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="b9b80-141">Élément</span><span class="sxs-lookup"><span data-stu-id="b9b80-141">Element</span></span>           | <span data-ttu-id="b9b80-142">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="b9b80-142">Include glob</span></span>                              | <span data-ttu-id="b9b80-143">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="b9b80-143">Exclude glob</span></span>                                                  | <span data-ttu-id="b9b80-144">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="b9b80-144">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="b9b80-145">Compiler</span><span class="sxs-lookup"><span data-stu-id="b9b80-145">Compile</span></span>           | <span data-ttu-id="b9b80-146">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="b9b80-146">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="b9b80-147">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b9b80-147">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="b9b80-148">N/A</span><span class="sxs-lookup"><span data-stu-id="b9b80-148">N/A</span></span>                      |
| <span data-ttu-id="b9b80-149">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="b9b80-149">EmbeddedResource</span></span>  | <span data-ttu-id="b9b80-150">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b9b80-150">\*\*/\*.resx</span></span>                              | <span data-ttu-id="b9b80-151">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b9b80-151">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b9b80-152">N/A</span><span class="sxs-lookup"><span data-stu-id="b9b80-152">N/A</span></span>                      |
| <span data-ttu-id="b9b80-153">None</span><span class="sxs-lookup"><span data-stu-id="b9b80-153">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="b9b80-154">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b9b80-154">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b9b80-155">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b9b80-155">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="b9b80-156">Les dossiers `./bin` et `./obj`, représentés par les propriétés `$(BaseOutputPath)` et `$(BaseIntermediateOutputPath)` MSBuild, sont exclus du modèles glob par défaut.</span><span class="sxs-lookup"><span data-stu-id="b9b80-156">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="b9b80-157">Les exclusions sont représentées par la propriété `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="b9b80-157">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="b9b80-158">Si vous définissez explicitement ces éléments dans votre fichier projet, vous risquez de recevoir l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="b9b80-158">If you explicitly define these items in your project file, you're likely to get the following error:</span></span>

<span data-ttu-id="b9b80-159">**Des éléments de compilation en double ont été inclus. Le kit de développement logiciel (SDK) .NET comprend les éléments de compilation de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété’EnableDefaultCompileItems’sur’false’si vous souhaitez les inclure explicitement dans votre fichier projet.**</span><span class="sxs-lookup"><span data-stu-id="b9b80-159">**Duplicate Compile items were included. The .NET SDK includes Compile items from your project directory by default. You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.**</span></span>

<span data-ttu-id="b9b80-160">Pour résoudre l’erreur, supprimez les éléments de `Compile` explicites qui correspondent aux éléments implicites figurant dans le tableau précédent, ou affectez à la propriété `EnableDefaultCompileItems` la valeur `false`, ce qui désactive l’inclusion implicite :</span><span class="sxs-lookup"><span data-stu-id="b9b80-160">To resolve the error, either remove the explicit `Compile` items that match the implicit ones listed on the previous table, or set the `EnableDefaultCompileItems` property to `false`, which disables implicit inclusion:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="b9b80-161">Si vous souhaitez spécifier, par exemple, certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l’élément `Content`.</span><span class="sxs-lookup"><span data-stu-id="b9b80-161">If you want to specify, for example, some files to get published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

<span data-ttu-id="b9b80-162">`EnableDefaultCompileItems` désactive uniquement `Compile` modèles glob, mais n’affecte pas les autres modèles glob, comme le Glob implicite `None` qui s’applique également aux éléments \*. cs.</span><span class="sxs-lookup"><span data-stu-id="b9b80-162">`EnableDefaultCompileItems` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob that also applies to \*.cs items.</span></span> <span data-ttu-id="b9b80-163">Pour cette raison, Explorateur de solutions dans Visual Studio affiche les éléments \*. cs dans le cadre du projet, inclus en tant qu’éléments de `None`.</span><span class="sxs-lookup"><span data-stu-id="b9b80-163">Because of that, Solution Explorer in Visual Studio shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="b9b80-164">Pour désactiver la glob implicite `None`, définissez `EnableDefaultNoneItems` sur `false`:</span><span class="sxs-lookup"><span data-stu-id="b9b80-164">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="b9b80-165">Pour désactiver *toutes les* modèles glob implicites, affectez à la propriété `EnableDefaultItems` la valeur `false`:</span><span class="sxs-lookup"><span data-stu-id="b9b80-165">To disable *all* implicit globs, set the `EnableDefaultItems` property to `false`:</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a><span data-ttu-id="b9b80-166">Personnaliser la Build</span><span class="sxs-lookup"><span data-stu-id="b9b80-166">Customize the build</span></span>

<span data-ttu-id="b9b80-167">Il existe plusieurs façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="b9b80-167">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="b9b80-168">Vous souhaiterez peut-être substituer une propriété en la passant comme argument à une commande [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="b9b80-168">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="b9b80-169">Vous pouvez également ajouter la propriété au fichier projet ou à un fichier *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="b9b80-169">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="b9b80-170">Pour obtenir la liste des propriétés utiles pour les projets .NET Core, consultez [propriétés MSBuild pour les projets kit SDK .net Core](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="b9b80-170">For a list of useful properties for .NET Core projects, see [MSBuild properties for .NET Core SDK projects](msbuild-props.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9b80-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9b80-171">See also</span></span>

- [<span data-ttu-id="b9b80-172">Installez .NET Core</span><span class="sxs-lookup"><span data-stu-id="b9b80-172">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="b9b80-173">Comment utiliser les kits de développement logiciel (SDK) de projet MSBuild</span><span class="sxs-lookup"><span data-stu-id="b9b80-173">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
