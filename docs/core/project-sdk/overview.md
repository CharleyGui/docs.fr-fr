---
title: Vue d’ensemble du SDK de projet .NET
titleSuffix: ''
description: Découvrez les kits de développement logiciel (SDK) de projet .NET.
ms.date: 09/17/2020
ms.topic: conceptual
ms.openlocfilehash: d0eb4291f4def9263f37d2d09f09ef43d40dfbac
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506394"
---
# <a name="net-project-sdks"></a><span data-ttu-id="52ab4-103">SDK de projet .NET</span><span class="sxs-lookup"><span data-stu-id="52ab4-103">.NET project SDKs</span></span>

<span data-ttu-id="52ab4-104">Les projets .NET Core et .NET 5,0 et versions ultérieures sont associés à un kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="52ab4-104">.NET Core and .NET 5.0 and later projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="52ab4-105">Chaque *Kit de développement logiciel (SDK) de projet* est un ensemble de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild et de [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication de code.</span><span class="sxs-lookup"><span data-stu-id="52ab4-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="52ab4-106">Un projet qui fait référence à un kit de développement logiciel (SDK) de projet est parfois appelé *projet de style SDK*.</span><span class="sxs-lookup"><span data-stu-id="52ab4-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="52ab4-107">Kits de développement logiciel disponibles</span><span class="sxs-lookup"><span data-stu-id="52ab4-107">Available SDKs</span></span>

<span data-ttu-id="52ab4-108">Les kits de développement logiciel (SDK) suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="52ab4-108">The following SDKs are available:</span></span>

| <span data-ttu-id="52ab4-109">id</span><span class="sxs-lookup"><span data-stu-id="52ab4-109">ID</span></span> | <span data-ttu-id="52ab4-110">Description</span><span class="sxs-lookup"><span data-stu-id="52ab4-110">Description</span></span> | <span data-ttu-id="52ab4-111">Dépôt</span><span class="sxs-lookup"><span data-stu-id="52ab4-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="52ab4-112">Le kit de développement logiciel (SDK) .NET</span><span class="sxs-lookup"><span data-stu-id="52ab4-112">The .NET SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="52ab4-113">[SDK Web](/aspnet/core/razor-pages/web-sdk) .net</span><span class="sxs-lookup"><span data-stu-id="52ab4-113">The .NET [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="52ab4-114">Le [Kit de développement logiciel (SDK) .net Razor](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="52ab4-114">The .NET [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="52ab4-115">Le kit de développement logiciel (SDK) .NET Worker service</span><span class="sxs-lookup"><span data-stu-id="52ab4-115">The .NET Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="52ab4-116">Le kit de développement logiciel (SDK) WinForms et WPF\*</span><span class="sxs-lookup"><span data-stu-id="52ab4-116">The WinForms and WPF SDK\*</span></span> | <span data-ttu-id="52ab4-117"><https://github.com/dotnet/winforms> et <https://github.com/dotnet/wpf></span><span class="sxs-lookup"><span data-stu-id="52ab4-117"><https://github.com/dotnet/winforms> and <https://github.com/dotnet/wpf></span></span> |

<span data-ttu-id="52ab4-118">Le kit de développement logiciel (SDK) .NET est le kit de développement logiciel de base pour .NET.</span><span class="sxs-lookup"><span data-stu-id="52ab4-118">The .NET SDK is the base SDK for .NET.</span></span> <span data-ttu-id="52ab4-119">Les autres SDK référencent le kit de développement logiciel (SDK) .NET, et les projets associés aux autres SDK disposent de toutes les propriétés du SDK .NET.</span><span class="sxs-lookup"><span data-stu-id="52ab4-119">The other SDKs reference the .NET SDK, and projects that are associated with the other SDKs have all the .NET SDK properties available to them.</span></span> <span data-ttu-id="52ab4-120">Le SDK Web, par exemple, dépend à la fois du kit de développement logiciel (SDK) .NET et du kit de développement logiciel (SDK) Razor.</span><span class="sxs-lookup"><span data-stu-id="52ab4-120">The Web SDK, for example, depends on both the .NET SDK and the Razor SDK.</span></span>

<span data-ttu-id="52ab4-121">Vous pouvez également créer votre propre kit de développement logiciel (SDK) qui peut être distribué via NuGet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-121">You can also author your own SDK that can be distributed via NuGet.</span></span>

<span data-ttu-id="52ab4-122">\* À compter de .NET 5,0, les projets Windows Forms et Windows Presentation Foundation (WPF) doivent spécifier le kit de développement logiciel (SDK) .NET ( `Microsoft.NET.Sdk` ) au lieu de `Microsoft.NET.Sdk.WindowsDesktop` .</span><span class="sxs-lookup"><span data-stu-id="52ab4-122">\* Starting in .NET 5.0, Windows Forms and Windows Presentation Foundation (WPF) projects should specify the .NET SDK (`Microsoft.NET.Sdk`) instead of `Microsoft.NET.Sdk.WindowsDesktop`.</span></span> <span data-ttu-id="52ab4-123">Pour ces projets, `TargetFramework` l’affectation de la valeur à `net5.0-windows` et `UseWPF` ou `UseWindowsForms` à `true` entraîne l’importation automatique du kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="52ab4-123">For these projects, setting `TargetFramework` to `net5.0-windows` and `UseWPF` or `UseWindowsForms` to `true` will automatically import the Windows desktop SDK.</span></span> <span data-ttu-id="52ab4-124">Si votre projet cible .NET 5,0 ou une version ultérieure et spécifie le `Microsoft.NET.Sdk.WindowsDesktop` Kit de développement logiciel (SDK), vous obtiendrez un avertissement de génération NETSDK1137.</span><span class="sxs-lookup"><span data-stu-id="52ab4-124">If your project targets .NET 5.0 or later and specifies the `Microsoft.NET.Sdk.WindowsDesktop` SDK, you'll get build warning NETSDK1137.</span></span>

## <a name="project-files"></a><span data-ttu-id="52ab4-125">Fichiers projet</span><span class="sxs-lookup"><span data-stu-id="52ab4-125">Project files</span></span>

<span data-ttu-id="52ab4-126">Les projets .NET sont basés sur le format [MSBuild](/visualstudio/msbuild/msbuild) .</span><span class="sxs-lookup"><span data-stu-id="52ab4-126">.NET projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="52ab4-127">Les fichiers projet, qui ont des extensions telles que *. csproj* pour les projets C# et *. fsproj* pour les projets F #, sont au format XML.</span><span class="sxs-lookup"><span data-stu-id="52ab4-127">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="52ab4-128">L’élément racine d’un fichier projet MSBuild est l’élément de [projet](/visualstudio/msbuild/project-element-msbuild) .</span><span class="sxs-lookup"><span data-stu-id="52ab4-128">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="52ab4-129">L' `Project` élément possède un `Sdk` attribut facultatif qui spécifie le kit de développement logiciel (SDK) (et la version) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="52ab4-129">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="52ab4-130">Pour utiliser les outils .NET et générer votre code, affectez `Sdk` à l’attribut l’un des ID dans le tableau [Kits de développement](#available-sdks) logiciel (SDK) disponibles.</span><span class="sxs-lookup"><span data-stu-id="52ab4-130">To use the .NET tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="52ab4-131">Pour spécifier un kit de développement logiciel (SDK) qui provient de NuGet, incluez la version à la fin du nom, ou spécifiez le nom et la version dans le fichier *global.js* .</span><span class="sxs-lookup"><span data-stu-id="52ab4-131">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="52ab4-132">Vous pouvez également spécifier le kit de développement logiciel (SDK) à l’aide de l’élément [SDK](/visualstudio/msbuild/sdk-element-msbuild) de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="52ab4-132">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="52ab4-133">Le référencement d’un kit de développement logiciel (SDK) de l’une de ces manières simplifie grandement les fichiers projet pour .NET.</span><span class="sxs-lookup"><span data-stu-id="52ab4-133">Referencing an SDK in one of these ways greatly simplifies project files for .NET.</span></span> <span data-ttu-id="52ab4-134">Lors de l’évaluation du projet, MSBuild ajoute des importations implicites pour `Sdk.props` en haut du fichier projet et `Sdk.targets` en bas.</span><span class="sxs-lookup"><span data-stu-id="52ab4-134">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

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
> <span data-ttu-id="52ab4-135">Sur un ordinateur Windows, les fichiers *SDK. props* et *SDK. targets* se trouvent dans le dossier *%ProgramFiles%\dotnet\sdk \\ [version] \Sdks\Microsoft.net.Sdk\Sdk*</span><span class="sxs-lookup"><span data-stu-id="52ab4-135">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="52ab4-136">Prétraiter le fichier projet</span><span class="sxs-lookup"><span data-stu-id="52ab4-136">Preprocess the project file</span></span>

<span data-ttu-id="52ab4-137">Vous pouvez voir le projet entièrement développé, car MSBuild le voit après l’inclusion du kit de développement logiciel (SDK) et de ses cibles à l’aide de la `dotnet msbuild -preprocess` commande.</span><span class="sxs-lookup"><span data-stu-id="52ab4-137">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="52ab4-138">Le commutateur de [prétraitement](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la [`dotnet msbuild`](../tools/dotnet-msbuild.md) commande indique quels fichiers sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-138">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="52ab4-139">Si le projet comporte plusieurs frameworks cibles, vous ne concentrez les résultats de la commande que sur un Framework en le spécifiant en tant que propriété MSBuild.</span><span class="sxs-lookup"><span data-stu-id="52ab4-139">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="52ab4-140">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="52ab4-140">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

## <a name="default-includes-and-excludes"></a><span data-ttu-id="52ab4-141">Inclusions et exclusions par défaut</span><span class="sxs-lookup"><span data-stu-id="52ab4-141">Default includes and excludes</span></span>

<span data-ttu-id="52ab4-142">La valeur par défaut inclut et exclut [ `Compile` les éléments, les](/visualstudio/msbuild/common-msbuild-project-items#compile) [ressources incorporées](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)et les [ `None` éléments](/visualstudio/msbuild/common-msbuild-project-items#none) sont définis dans le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="52ab4-142">The default includes and excludes for [`Compile` items](/visualstudio/msbuild/common-msbuild-project-items#compile), [embedded resources](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource), and [`None` items](/visualstudio/msbuild/common-msbuild-project-items#none) are defined in the SDK.</span></span> <span data-ttu-id="52ab4-143">Contrairement aux projets de .NET Framework non SDK, vous n’avez pas besoin de spécifier ces éléments dans votre fichier projet, car les valeurs par défaut couvrent les cas d’utilisation les plus courants.</span><span class="sxs-lookup"><span data-stu-id="52ab4-143">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="52ab4-144">Ce comportement rend le fichier projet plus petit et plus facile à comprendre et à modifier manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="52ab4-144">This behavior makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="52ab4-145">Le tableau suivant répertorie les éléments et les [modèles glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le kit de développement logiciel (SDK) .net :</span><span class="sxs-lookup"><span data-stu-id="52ab4-145">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET SDK:</span></span>

| <span data-ttu-id="52ab4-146">Élément</span><span class="sxs-lookup"><span data-stu-id="52ab4-146">Element</span></span>           | <span data-ttu-id="52ab4-147">Inclure Glob</span><span class="sxs-lookup"><span data-stu-id="52ab4-147">Include glob</span></span>                              | <span data-ttu-id="52ab4-148">Exclure Glob</span><span class="sxs-lookup"><span data-stu-id="52ab4-148">Exclude glob</span></span>                                                  | <span data-ttu-id="52ab4-149">Supprimer Glob</span><span class="sxs-lookup"><span data-stu-id="52ab4-149">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="52ab4-150">Compiler</span><span class="sxs-lookup"><span data-stu-id="52ab4-150">Compile</span></span>           | <span data-ttu-id="52ab4-151">\*\*/\*.cs (ou autres extensions de langage)</span><span class="sxs-lookup"><span data-stu-id="52ab4-151">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="52ab4-152">\*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="52ab4-152">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="52ab4-153">N/A</span><span class="sxs-lookup"><span data-stu-id="52ab4-153">N/A</span></span>                      |
| <span data-ttu-id="52ab4-154">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="52ab4-154">EmbeddedResource</span></span>  | <span data-ttu-id="52ab4-155">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="52ab4-155">\*\*/\*.resx</span></span>                              | <span data-ttu-id="52ab4-156">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="52ab4-156">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="52ab4-157">N/A</span><span class="sxs-lookup"><span data-stu-id="52ab4-157">N/A</span></span>                      |
| <span data-ttu-id="52ab4-158">None</span><span class="sxs-lookup"><span data-stu-id="52ab4-158">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="52ab4-159">\*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="52ab4-159">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="52ab4-160">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="52ab4-160">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="52ab4-161">Les `./bin` `./obj` dossiers et, représentés par les `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Propriétés et MSBuild, sont exclus par défaut de modèles glob.</span><span class="sxs-lookup"><span data-stu-id="52ab4-161">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="52ab4-162">Les exclusions sont représentées par la [propriété DefaultItemExcludes](msbuild-props.md#defaultitemexcludes).</span><span class="sxs-lookup"><span data-stu-id="52ab4-162">Excludes are represented by the [DefaultItemExcludes property](msbuild-props.md#defaultitemexcludes).</span></span>

### <a name="build-errors"></a><span data-ttu-id="52ab4-163">Erreurs de build</span><span class="sxs-lookup"><span data-stu-id="52ab4-163">Build errors</span></span>

<span data-ttu-id="52ab4-164">Si vous définissez explicitement l’un de ces éléments dans votre fichier projet, vous risquez d’obtenir une erreur de build « NETSDK1022 » similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="52ab4-164">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="52ab4-165">Les éléments « compile » dupliqués ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="52ab4-165">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="52ab4-166">Le kit de développement logiciel (SDK) .NET comprend les éléments de « compilation » de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="52ab4-166">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="52ab4-167">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="52ab4-168">Les éléments’EmbeddedResource’dupliqués ont été inclus.</span><span class="sxs-lookup"><span data-stu-id="52ab4-168">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="52ab4-169">Le kit de développement logiciel (SDK) .NET comprend les éléments’EmbeddedResource’de votre répertoire de projet par défaut.</span><span class="sxs-lookup"><span data-stu-id="52ab4-169">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="52ab4-170">Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété’EnableDefaultEmbeddedResourceItems’sur’false’si vous souhaitez les inclure explicitement dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-170">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="52ab4-171">Pour résoudre les erreurs, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="52ab4-171">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="52ab4-172">Supprimez les `Compile` éléments explicites, `EmbeddedResource` ou `None` qui correspondent aux éléments implicites listés dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="52ab4-172">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="52ab4-173">Affectez à la [propriété EnableDefaultItems](msbuild-props.md#enabledefaultitems) la valeur `false` pour désactiver toute inclusion de fichier implicite :</span><span class="sxs-lookup"><span data-stu-id="52ab4-173">Set the [EnableDefaultItems property](msbuild-props.md#enabledefaultitems) to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="52ab4-174">Si vous souhaitez spécifier des fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes MSBuild connus pour cela, par exemple, l' `Content` élément.</span><span class="sxs-lookup"><span data-stu-id="52ab4-174">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="52ab4-175">Désactivez de manière sélective uniquement `Compile` , `EmbeddedResource` ou `None` modèles glob en affectant à la propriété [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems)ou [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) la valeur `false` :</span><span class="sxs-lookup"><span data-stu-id="52ab4-175">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the [EnableDefaultCompileItems](msbuild-props.md#enabledefaultcompileitems), [EnableDefaultEmbeddedResourceItems](msbuild-props.md#enabledefaultembeddedresourceitems), or [EnableDefaultNoneItems](msbuild-props.md#enabledefaultnoneitems) property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="52ab4-176">Si vous désactivez uniquement `Compile` modèles glob, Explorateur de solutions dans Visual Studio affiche toujours \* les éléments. cs dans le cadre du projet, inclus en tant qu' `None` éléments.</span><span class="sxs-lookup"><span data-stu-id="52ab4-176">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="52ab4-177">Pour désactiver la glob implicite `None` , affectez la valeur `EnableDefaultNoneItems` à `false` .</span><span class="sxs-lookup"><span data-stu-id="52ab4-177">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="52ab4-178">Références de package implicites</span><span class="sxs-lookup"><span data-stu-id="52ab4-178">Implicit package references</span></span>

<span data-ttu-id="52ab4-179">Quand vous ciblez .NET Core 1,0-2,2 ou .NET Standard 1,0-2,0, le kit de développement logiciel (SDK) .NET ajoute des références implicites à certains sous- *packages*.</span><span class="sxs-lookup"><span data-stu-id="52ab4-179">When targeting .NET Core 1.0 - 2.2 or .NET Standard 1.0 - 2.0, the .NET SDK adds implicit references to certain *metapackages*.</span></span> <span data-ttu-id="52ab4-180">Un reconditionnement est un package basé sur une infrastructure qui se compose uniquement de dépendances sur d’autres packages.</span><span class="sxs-lookup"><span data-stu-id="52ab4-180">A metapackage is a framework-based package that consists only of dependencies on other packages.</span></span> <span data-ttu-id="52ab4-181">Les reconditionnements sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété [targetFramework](msbuild-props.md#targetframework) ou [TargetFrameworks](msbuild-props.md#targetframeworks) de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-181">Metapackages are implicitly referenced based on the target framework(s) specified in the [TargetFramework](msbuild-props.md#targetframework) or [TargetFrameworks](msbuild-props.md#targetframeworks) property of your project file.</span></span>

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

<span data-ttu-id="52ab4-182">Si nécessaire, vous pouvez désactiver les références de package implicites à l’aide de la propriété [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) et ajouter des références explicites uniquement aux frameworks ou aux packages dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="52ab4-182">If needed, you can disable implicit package references using the [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) property, and add explicit references to just the frameworks or packages you need.</span></span>

<span data-ttu-id="52ab4-183">Recommandations :</span><span class="sxs-lookup"><span data-stu-id="52ab4-183">Recommendations:</span></span>

- <span data-ttu-id="52ab4-184">Quand vous ciblez .NET Framework, .NET Core 1,0-2,2 ou .NET Standard 1,0-2,0, n’ajoutez pas de référence explicite aux `Microsoft.NETCore.App` packages ou à l' `NETStandard.Library` aide d’un `<PackageReference>` élément de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-184">When targeting .NET Framework, .NET Core 1.0 - 2.2, or .NET Standard 1.0 - 2.0, don't add an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span> <span data-ttu-id="52ab4-185">Pour les projets .NET Core 1,0-2,2 et .NET Standard 1,0-2,0, ces packages sont référencés implicitement.</span><span class="sxs-lookup"><span data-stu-id="52ab4-185">For .NET Core 1.0 - 2.2 and .NET Standard 1.0 - 2.0 projects, these metapackages are implicitly referenced.</span></span> <span data-ttu-id="52ab4-186">Pour les projets .NET Framework, si une version de `NETStandard.Library` est nécessaire lors de l’utilisation d’un package NuGet basé sur .NET standard, NuGet installe automatiquement cette version.</span><span class="sxs-lookup"><span data-stu-id="52ab4-186">For .NET Framework projects, if any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>
- <span data-ttu-id="52ab4-187">Si vous avez besoin d’une version spécifique du runtime lorsque vous ciblez .NET Core 1,0-2,2, utilisez la `<RuntimeFrameworkVersion>` propriété dans votre projet (par exemple, `1.0.4` ) au lieu de référencer le repackage.</span><span class="sxs-lookup"><span data-stu-id="52ab4-187">If you need a specific version of the runtime when targeting .NET Core 1.0 - 2.2, use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span> <span data-ttu-id="52ab4-188">Par exemple, vous pouvez avoir besoin d’une version de correctif spécifique de 1.0.0 LTS Runtime si vous utilisez des [déploiements autonomes](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="52ab4-188">For example, you might need a specific patch version of 1.0.0 LTS runtime if you're using [self-contained deployments](../deploying/index.md#publish-self-contained).</span></span>
- <span data-ttu-id="52ab4-189">Si vous avez besoin d’une version spécifique du `NETStandard.Library` repackage lorsque vous ciblez .NET Standard 1,0-2,0, vous pouvez utiliser la `<NetStandardImplicitPackageVersion>` propriété et définir la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="52ab4-189">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard 1.0 - 2.0, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>

## <a name="build-events"></a><span data-ttu-id="52ab4-190">Événements de build</span><span class="sxs-lookup"><span data-stu-id="52ab4-190">Build events</span></span>

<span data-ttu-id="52ab4-191">Dans les projets de type SDK, utilisez une cible MSBuild nommée `PreBuild` ou `PostBuild` et définissez la `BeforeTargets` propriété pour `PreBuild` ou `AfterTargets` pour la propriété de `PostBuild` .</span><span class="sxs-lookup"><span data-stu-id="52ab4-191">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - <span data-ttu-id="52ab4-192">Vous pouvez utiliser n’importe quel nom pour les cibles MSBuild.</span><span class="sxs-lookup"><span data-stu-id="52ab4-192">You can use any name for the MSBuild targets.</span></span> <span data-ttu-id="52ab4-193">Toutefois, l’IDE de Visual Studio reconnaît `PreBuild` et `PostBuild` cible, donc en utilisant ces noms, vous pouvez modifier les commandes dans l’IDE.</span><span class="sxs-lookup"><span data-stu-id="52ab4-193">However, the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so by using those names, you can edit the commands in the IDE.</span></span>
> - <span data-ttu-id="52ab4-194">Les propriétés `PreBuildEvent` et ne `PostBuildEvent` sont pas recommandées dans les projets de style SDK, car les macros telles que ne sont pas `$(ProjectDir)` résolues.</span><span class="sxs-lookup"><span data-stu-id="52ab4-194">The properties `PreBuildEvent` and `PostBuildEvent` are not recommended in SDK-style projects, because macros such as `$(ProjectDir)` aren't resolved.</span></span> <span data-ttu-id="52ab4-195">Par exemple, le code suivant n’est pas pris en charge :</span><span class="sxs-lookup"><span data-stu-id="52ab4-195">For example, the following code is not supported:</span></span>
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a><span data-ttu-id="52ab4-196">Personnaliser la Build</span><span class="sxs-lookup"><span data-stu-id="52ab4-196">Customize the build</span></span>

<span data-ttu-id="52ab4-197">Il existe plusieurs façons de [personnaliser une build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="52ab4-197">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="52ab4-198">Vous souhaiterez peut-être substituer une propriété en la passant comme argument à une commande [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) ou [dotnet](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="52ab4-198">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="52ab4-199">Vous pouvez également ajouter la propriété au fichier projet ou à un fichier *Directory. Build. props* .</span><span class="sxs-lookup"><span data-stu-id="52ab4-199">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="52ab4-200">Pour obtenir la liste des propriétés utiles pour les projets .NET, consultez informations de [référence sur MSBuild pour les projets SDK .net](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="52ab4-200">For a list of useful properties for .NET projects, see [MSBuild reference for .NET SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="52ab4-201">Cibles personnalisées</span><span class="sxs-lookup"><span data-stu-id="52ab4-201">Custom targets</span></span>

<span data-ttu-id="52ab4-202">Les projets .NET peuvent empaqueter des cibles et des propriétés MSBuild personnalisées pour une utilisation par les projets qui utilisent le package.</span><span class="sxs-lookup"><span data-stu-id="52ab4-202">.NET projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="52ab4-203">Utilisez ce type d’extensibilité lorsque vous souhaitez :</span><span class="sxs-lookup"><span data-stu-id="52ab4-203">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="52ab4-204">Étendez le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="52ab4-204">Extend the build process.</span></span>
- <span data-ttu-id="52ab4-205">Accédez aux artefacts du processus de génération, tels que les fichiers générés.</span><span class="sxs-lookup"><span data-stu-id="52ab4-205">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="52ab4-206">Inspectez la configuration sous laquelle la build est appelée.</span><span class="sxs-lookup"><span data-stu-id="52ab4-206">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="52ab4-207">Vous ajoutez des cibles de génération personnalisées ou des propriétés en plaçant des fichiers dans le formulaire `<package_id>.targets` ou `<package_id>.props` (par exemple, `Contoso.Utility.UsefulStuff.targets` ) dans le dossier *Build* du projet.</span><span class="sxs-lookup"><span data-stu-id="52ab4-207">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="52ab4-208">Le code XML suivant est un extrait d’un fichier *. csproj* qui indique [`dotnet pack`](../tools/dotnet-pack.md) à la commande ce qu’il faut empaqueter.</span><span class="sxs-lookup"><span data-stu-id="52ab4-208">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="52ab4-209">L' `<ItemGroup Label="dotnet pack instructions">` élément place les fichiers cibles dans le dossier de *Build* à l’intérieur du package.</span><span class="sxs-lookup"><span data-stu-id="52ab4-209">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="52ab4-210">L' `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` élément place les assemblys et les fichiers *. JSON* dans le dossier de *Build* .</span><span class="sxs-lookup"><span data-stu-id="52ab4-210">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

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

<span data-ttu-id="52ab4-211">Pour utiliser une cible personnalisée dans votre projet, ajoutez un `PackageReference` élément qui pointe vers le package et sa version.</span><span class="sxs-lookup"><span data-stu-id="52ab4-211">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="52ab4-212">Contrairement aux outils, le package de cibles personnalisées est inclus dans la fermeture des dépendances du projet consommatrice.</span><span class="sxs-lookup"><span data-stu-id="52ab4-212">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="52ab4-213">Vous pouvez configurer l’utilisation de la cible personnalisée.</span><span class="sxs-lookup"><span data-stu-id="52ab4-213">You can configure how to use the custom target.</span></span> <span data-ttu-id="52ab4-214">Étant donné qu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible donnée, exécutée après une autre cible, ou être appelée manuellement à l’aide de la `dotnet msbuild -t:<target-name>` commande.</span><span class="sxs-lookup"><span data-stu-id="52ab4-214">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="52ab4-215">Toutefois, pour offrir une meilleure expérience utilisateur, vous pouvez combiner des outils par projet et des cibles personnalisées.</span><span class="sxs-lookup"><span data-stu-id="52ab4-215">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="52ab4-216">Dans ce scénario, l’outil par projet accepte tous les paramètres nécessaires et les convertit en l’appel requis [`dotnet msbuild`](../tools/dotnet-msbuild.md) qui exécute la cible.</span><span class="sxs-lookup"><span data-stu-id="52ab4-216">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="52ab4-217">Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="52ab4-217">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="52ab4-218">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52ab4-218">See also</span></span>

- [<span data-ttu-id="52ab4-219">Installez .NET Core</span><span class="sxs-lookup"><span data-stu-id="52ab4-219">Install .NET Core</span></span>](../install/index.yml)
- [<span data-ttu-id="52ab4-220">Comment utiliser les kits de développement logiciel (SDK) de projet MSBuild</span><span class="sxs-lookup"><span data-stu-id="52ab4-220">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="52ab4-221">Packages et cibles MSBuild personnalisés avec NuGet</span><span class="sxs-lookup"><span data-stu-id="52ab4-221">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
