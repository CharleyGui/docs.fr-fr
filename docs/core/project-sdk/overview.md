---
title: Vue d’ensemble du SDK de projet .NET Core
titleSuffix: ''
description: En savoir plus sur les kits de développement logiciel (SDK) de projet .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 873c06007307c5892c4828f987486b4dd98dc9ae
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187922"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="d8119-103">Kits de développement logiciel (SDK) de projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8119-103">.NET Core project SDKs</span></span>

<span data-ttu-id="d8119-104">Les projets .NET Core sont associés à un kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="d8119-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="d8119-105">Chaque *Kit de développement logiciel (SDK) de projet* est un ensemble de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild et de [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication de code.</span><span class="sxs-lookup"><span data-stu-id="d8119-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="d8119-106">Un projet qui fait référence à un kit de développement logiciel (SDK) de projet est parfois appelé *projet de style SDK*.</span><span class="sxs-lookup"><span data-stu-id="d8119-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="d8119-107">Kits de développement logiciel disponibles</span><span class="sxs-lookup"><span data-stu-id="d8119-107">Available SDKs</span></span>

<span data-ttu-id="d8119-108">Les kits de développement logiciel (SDK) suivants sont disponibles pour .NET Core :</span><span class="sxs-lookup"><span data-stu-id="d8119-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="d8119-109">id</span><span class="sxs-lookup"><span data-stu-id="d8119-109">ID</span></span> | <span data-ttu-id="d8119-110">Description</span><span class="sxs-lookup"><span data-stu-id="d8119-110">Description</span></span> | <span data-ttu-id="d8119-111">Dépôt</span><span class="sxs-lookup"><span data-stu-id="d8119-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="d8119-112">Kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8119-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="d8119-113">Le kit de [développement logiciel (SDK) Web](/aspnet/core/razor-pages/web-sdk) .net Core</span><span class="sxs-lookup"><span data-stu-id="d8119-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="d8119-114">Le kit de [développement logiciel (SDK)](/aspnet/core/razor-pages/sdk) .net Core Razor</span><span class="sxs-lookup"><span data-stu-id="d8119-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="d8119-115">Kit de développement logiciel (SDK) .NET Core Worker service</span><span class="sxs-lookup"><span data-stu-id="d8119-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="d8119-116">Le kit de développement logiciel (SDK) .NET Core WinForms et WPF</span><span class="sxs-lookup"><span data-stu-id="d8119-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="d8119-117">Le kit SDK .NET Core est le kit de développement logiciel (SDK) de base pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8119-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="d8119-118">Les autres kits de développement logiciel (SDK) référencent les kit SDK .NET Core, et les propriétés de kit SDK .NET Core associées aux autres kits de développement logiciel (SDK) sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="d8119-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="d8119-119">Le kit de développement logiciel (SDK) Web, par exemple, dépend à la fois du kit SDK .NET Core et du kit de développement logiciel (SDK) Razor.</span><span class="sxs-lookup"><span data-stu-id="d8119-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="d8119-120">Vous pouvez également créer votre propre kit de développement logiciel (SDK) qui peut être distribué via NuGet.</span><span class="sxs-lookup"><span data-stu-id="d8119-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="d8119-121">Fichiers projet</span><span class="sxs-lookup"><span data-stu-id="d8119-121">Project files</span></span>

<span data-ttu-id="d8119-122">Les projets .NET Core sont basés sur le format [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="d8119-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="d8119-123">Les fichiers projet, qui ont des extensions telles que *. csproj* pour les projets C# et *. fsproj* pour les projets F #, sont au format XML.</span><span class="sxs-lookup"><span data-stu-id="d8119-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="d8119-124">L’élément racine d’un fichier projet MSBuild est l’élément de [projet](/visualstudio/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="d8119-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="d8119-125">L' `Project` élément possède un `Sdk` attribut facultatif qui spécifie le kit de développement logiciel (SDK) (et la version) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="d8119-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="d8119-126">Pour utiliser les outils .NET Core et générer votre code, affectez `Sdk` à l’attribut l’un des ID figurant dans la table kits de développement logiciel ( [SDK) disponibles](#available-sdks) .</span><span class="sxs-lookup"><span data-stu-id="d8119-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="d8119-127">Pour spécifier un kit de développement logiciel (SDK) qui provient de NuGet, incluez la version à la fin du nom, ou spécifiez le nom et la version dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="d8119-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="d8119-128">Vous pouvez également spécifier le kit de développement logiciel (SDK) à l’aide de l’élément [SDK](/visualstudio/msbuild/sdk-element-msbuild) de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="d8119-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="d8119-129">Le référencement d’un kit de développement logiciel (SDK) de l’une de ces manières simplifie grandement les fichiers projet pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8119-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="d8119-130">Lors de l’évaluation du projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du fichier projet et `Sdk.targets` en bas.</span><span class="sxs-lookup"><span data-stu-id="d8119-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="d8119-131">Sur un ordinateur Windows, les fichiers *SDK. props* et *SDK. targets* se trouvent dans le dossier *%ProgramFiles%\dotnet\sdk \\ [version] \Sdks\Microsoft.net.Sdk\Sdk*</span><span class="sxs-lookup"><span data-stu-id="d8119-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="d8119-132">Prétraiter le fichier projet</span><span class="sxs-lookup"><span data-stu-id="d8119-132">Preprocess the project file</span></span>

<span data-ttu-id="d8119-133">Vous pouvez voir le projet entièrement développé, car MSBuild le voit après l’inclusion du kit de développement logiciel (SDK) et de ses cibles à l’aide de la `dotnet msbuild -preprocess` commande.</span><span class="sxs-lookup"><span data-stu-id="d8119-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="d8119-134">Le commutateur de [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la [`dotnet msbuild`](../tools/dotnet-msbuild.md) commande indique quels fichiers sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet.</span><span class="sxs-lookup"><span data-stu-id="d8119-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="d8119-135">Si le projet comporte plusieurs frameworks cibles, vous ne concentrez les résultats de la commande que sur un Framework en le spécifiant en tant que propriété MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d8119-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="d8119-136">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d8119-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="d8119-137">La compilation par défaut comprend</span><span class="sxs-lookup"><span data-stu-id="d8119-137">Default compilation includes</span></span>

<span data-ttu-id="d8119-138">Les éléments include et Exclude par défaut pour les éléments de compilation, les ressources incorporées et `None` les éléments sont définis dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="d8119-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="d8119-139">Contrairement aux projets de .NET Framework non SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier projet, car les valeurs par défaut couvrent les cas d’utilisation les plus courants.</span><span class="sxs-lookup"><span data-stu-id="d8119-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="d8119-140">Cela rend le fichier projet plus petit et plus facile à comprendre et à modifier manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d8119-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="d8119-141">Le tableau suivant indique les éléments et les [modèles glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le kit SDK .net Core :</span><span class="sxs-lookup"><span data-stu-id="d8119-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="d8119-142">Élément</span><span class="sxs-lookup"><span data-stu-id="d8119-142">Element</span></span>           | <span data-ttu-id="d8119-143">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="d8119-143">Include glob</span></span>                              | <span data-ttu-id="d8119-144">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="d8119-144">Exclude glob</span></span>                                                  | <span data-ttu-id="d8119-145">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="d8119-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="d8119-146">Compiler</span><span class="sxs-lookup"><span data-stu-id="d8119-146">Compile</span></span>           | <span data-ttu-id="d8119-147">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="d8119-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="d8119-148">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d8119-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="d8119-149">N/A</span><span class="sxs-lookup"><span data-stu-id="d8119-149">N/A</span></span>                      |
| <span data-ttu-id="d8119-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="d8119-150">EmbeddedResource</span></span>  | <span data-ttu-id="d8119-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="d8119-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="d8119-152">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d8119-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d8119-153">N/A</span><span class="sxs-lookup"><span data-stu-id="d8119-153">N/A</span></span>                      |
| <span data-ttu-id="d8119-154">Aucun</span><span class="sxs-lookup"><span data-stu-id="d8119-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="d8119-155">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="d8119-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="d8119-156">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="d8119-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="d8119-157">Les `./bin` `./obj` dossiers et, représentés par les `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Propriétés et MSBuild, sont exclus par défaut de modèles glob.</span><span class="sxs-lookup"><span data-stu-id="d8119-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="d8119-158">Les exclusions sont représentées par la propriété `$(DefaultItemExcludes)` .</span><span class="sxs-lookup"><span data-stu-id="d8119-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="d8119-159">Erreurs de build</span><span class="sxs-lookup"><span data-stu-id="d8119-159">Build errors</span></span>

<span data-ttu-id="d8119-160">Si vous définissez explicitement l’un de ces éléments dans votre fichier projet, vous risquez d’obtenir une erreur de build « NETSDK1022 » similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d8119-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="d8119-161">Les éléments « compile » dupliqués ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="d8119-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="d8119-162">Le kit de développement logiciel (SDK) .NET comprend les éléments de « compilation » de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="d8119-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="d8119-163">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d8119-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="d8119-164">Les éléments’EmbeddedResource’dupliqués ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="d8119-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="d8119-165">Le kit de développement logiciel (SDK) .NET comprend les éléments’EmbeddedResource’de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="d8119-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="d8119-166">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété’EnableDefaultEmbeddedResourceItems’sur’false’si vous souhaitez les inclure explicitement dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d8119-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="d8119-167">Pour résoudre les erreurs, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8119-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="d8119-168">Supprimez les `Compile` éléments explicites, `EmbeddedResource` ou `None` qui correspondent aux éléments implicites listés dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="d8119-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="d8119-169">Affectez à la propriété la valeur `EnableDefaultItems` `false` pour désactiver toute inclusion de fichier implicite :</span><span class="sxs-lookup"><span data-stu-id="d8119-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="d8119-170">Si vous souhaitez spécifier des fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l' `Content` élément.</span><span class="sxs-lookup"><span data-stu-id="d8119-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="d8119-171">Désactivez de manière sélective uniquement `Compile` , `EmbeddedResource` ou `None` modèles glob en affectant `EnableDefaultCompileItems` à la propriété, ou la valeur `EnableDefaultEmbeddedResourceItems` `EnableDefaultNoneItems` `false` :</span><span class="sxs-lookup"><span data-stu-id="d8119-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="d8119-172">Si vous désactivez uniquement `Compile` modèles glob, Explorateur de solutions dans Visual Studio affiche toujours \* les éléments. cs dans le cadre du projet, inclus en tant qu' `None` éléments.</span><span class="sxs-lookup"><span data-stu-id="d8119-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="d8119-173">Pour désactiver la glob implicite `None` , affectez la valeur `EnableDefaultNoneItems` à `false` .</span><span class="sxs-lookup"><span data-stu-id="d8119-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="d8119-174">Personnaliser la Build</span><span class="sxs-lookup"><span data-stu-id="d8119-174">Customize the build</span></span>

<span data-ttu-id="d8119-175">Il existe plusieurs façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="d8119-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="d8119-176">Vous souhaiterez peut-être substituer une propriété en la passant comme argument à une commande [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="d8119-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="d8119-177">Vous pouvez également ajouter la propriété au fichier projet ou à un fichier *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="d8119-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="d8119-178">Pour obtenir la liste des propriétés utiles pour les projets .NET Core, consultez [référence MSBuild pour les projets kit SDK .net Core](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="d8119-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="d8119-179">Cibles personnalisées</span><span class="sxs-lookup"><span data-stu-id="d8119-179">Custom targets</span></span>

<span data-ttu-id="d8119-180">Les projets .NET Core peuvent empaqueter des cibles et des propriétés MSBuild personnalisées pour une utilisation par des projets qui utilisent le package.</span><span class="sxs-lookup"><span data-stu-id="d8119-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="d8119-181">Utilisez ce type d’extensibilité lorsque vous souhaitez :</span><span class="sxs-lookup"><span data-stu-id="d8119-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="d8119-182">Étendez le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="d8119-182">Extend the build process.</span></span>
- <span data-ttu-id="d8119-183">Accédez aux artefacts du processus de génération, tels que les fichiers générés.</span><span class="sxs-lookup"><span data-stu-id="d8119-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="d8119-184">Inspectez la configuration sous laquelle la build est appelée.</span><span class="sxs-lookup"><span data-stu-id="d8119-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="d8119-185">Vous ajoutez des cibles de génération personnalisées ou des propriétés en plaçant des fichiers dans le formulaire `<package_id>.targets` ou `<package_id>.props` (par exemple, `Contoso.Utility.UsefulStuff.targets` ) dans le dossier *Build* du projet.</span><span class="sxs-lookup"><span data-stu-id="d8119-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="d8119-186">Le code XML suivant est un extrait d’un fichier *. csproj* qui indique [`dotnet pack`](../tools/dotnet-pack.md) à la commande ce qu’il faut empaqueter.</span><span class="sxs-lookup"><span data-stu-id="d8119-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="d8119-187">L' `<ItemGroup Label="dotnet pack instructions">` élément place les fichiers cibles dans le dossier de *Build* à l’intérieur du package.</span><span class="sxs-lookup"><span data-stu-id="d8119-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="d8119-188">L' `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` élément place les assemblys et les fichiers *. JSON* dans le dossier de *Build* .</span><span class="sxs-lookup"><span data-stu-id="d8119-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="d8119-189">Pour utiliser une cible personnalisée dans votre projet, ajoutez un `PackageReference` élément qui pointe vers le package et sa version.</span><span class="sxs-lookup"><span data-stu-id="d8119-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="d8119-190">Contrairement aux outils, le package de cibles personnalisées est inclus dans la fermeture des dépendances du projet consommatrice.</span><span class="sxs-lookup"><span data-stu-id="d8119-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="d8119-191">Vous pouvez configurer l’utilisation de la cible personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d8119-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="d8119-192">Étant donné qu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible donnée, exécutée après une autre cible, ou être appelée manuellement à l’aide de la `dotnet msbuild -t:<target-name>` commande.</span><span class="sxs-lookup"><span data-stu-id="d8119-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="d8119-193">Toutefois, pour offrir une meilleure expérience utilisateur, vous pouvez combiner des outils par projet et des cibles personnalisées.</span><span class="sxs-lookup"><span data-stu-id="d8119-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="d8119-194">Dans ce scénario, l’outil par projet accepte tous les paramètres nécessaires et les convertit en l’appel requis [`dotnet msbuild`](../tools/dotnet-msbuild.md) qui exécute la cible.</span><span class="sxs-lookup"><span data-stu-id="d8119-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="d8119-195">Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="d8119-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8119-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8119-196">See also</span></span>

- [<span data-ttu-id="d8119-197">Installez .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8119-197">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="d8119-198">Comment utiliser les kits de développement logiciel (SDK) de projet MSBuild</span><span class="sxs-lookup"><span data-stu-id="d8119-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="d8119-199">Packages et cibles MSBuild personnalisés avec NuGet</span><span class="sxs-lookup"><span data-stu-id="d8119-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
