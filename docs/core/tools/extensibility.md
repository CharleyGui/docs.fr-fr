---
title: Modèle d’extensibilité des outils CLI .NET Core
description: Découvrez comment vous pouvez étendre le CLI .NET Core.
ms.date: 04/12/2017
ms.openlocfilehash: 56a9cedc090ddca446c0ee1a60f2ca49590e7635
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451153"
---
# <a name="net-core-cli-extensibility-model"></a><span data-ttu-id="a19fd-103">Modèle d’extensibilité des outils CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="a19fd-103">.NET Core CLI extensibility model</span></span>

<span data-ttu-id="a19fd-104">Cet article décrit les différentes façons dont vous pouvez étendre les CLI .NET Core et explique les scénarios qui les pilotent.</span><span class="sxs-lookup"><span data-stu-id="a19fd-104">This article covers the different ways you can extend the .NET Core CLI and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="a19fd-105">Vous verrez comment utiliser les outils et comment créer les différents types d’outils.</span><span class="sxs-lookup"><span data-stu-id="a19fd-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-the-cli"></a><span data-ttu-id="a19fd-106">Comment étendre l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="a19fd-106">How to extend the CLI</span></span>
<span data-ttu-id="a19fd-107">L’interface CLI peut être étendue de trois manières principales :</span><span class="sxs-lookup"><span data-stu-id="a19fd-107">The CLI can be extended in three main ways:</span></span>

1. [<span data-ttu-id="a19fd-108">Par le biais des packages NuGet, par projet</span><span class="sxs-lookup"><span data-stu-id="a19fd-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="a19fd-109">Les outils par projet sont contenus dans le contexte du projet, mais ils permettent une installation rapide grâce à une restauration.</span><span class="sxs-lookup"><span data-stu-id="a19fd-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="a19fd-110">Par le biais des packages NuGet avec des cibles personnalisées</span><span class="sxs-lookup"><span data-stu-id="a19fd-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="a19fd-111">Les cibles personnalisées vous permettent d’étendre facilement le processus de génération avec des tâches personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a19fd-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="a19fd-112">Par le biais du chemin (PATH) du système</span><span class="sxs-lookup"><span data-stu-id="a19fd-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="a19fd-113">Les outils basés sur le chemin sont efficaces pour les outils généraux multiprojets qui sont utilisables sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a19fd-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="a19fd-114">Les trois mécanismes d’extensibilité présentés ci-dessus ne sont pas exclusifs.</span><span class="sxs-lookup"><span data-stu-id="a19fd-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="a19fd-115">Vous pouvez utiliser un seul, une partie ou la totalité d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="a19fd-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="a19fd-116">Le choix de la méthode dépend en grande partie de l’objectif de votre extension.</span><span class="sxs-lookup"><span data-stu-id="a19fd-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="a19fd-117">Extensibilité par projet</span><span class="sxs-lookup"><span data-stu-id="a19fd-117">Per-project based extensibility</span></span>
<span data-ttu-id="a19fd-118">Les outils par projet sont des [déploiements dépendants du framework](../deploying/index.md#publish-runtime-dependent) qui sont distribués dans les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="a19fd-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) that are distributed as NuGet packages.</span></span> <span data-ttu-id="a19fd-119">Les outils sont uniquement disponibles dans le contexte du projet qui les référence et pour lequel ils sont restaurés.</span><span class="sxs-lookup"><span data-stu-id="a19fd-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="a19fd-120">Les appels en dehors du contexte du projet (par exemple, en dehors du répertoire qui contient le projet) échouent parce que la commande est introuvable.</span><span class="sxs-lookup"><span data-stu-id="a19fd-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="a19fd-121">Ces outils sont parfaits pour les serveurs de build, puisque rien en dehors du fichier projet n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a19fd-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="a19fd-122">Le processus de génération exécute la restauration pour le projet qu’il génère, et des outils seront disponibles.</span><span class="sxs-lookup"><span data-stu-id="a19fd-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="a19fd-123">Les projets de langage, tels que F#, figurent également dans cette catégorie puisque chaque projet ne peut être écrit que dans un langage.</span><span class="sxs-lookup"><span data-stu-id="a19fd-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="a19fd-124">Enfin, ce modèle d’extensibilité prend en charge la création d’outils qui ont besoin d’accéder à la sortie générée du projet.</span><span class="sxs-lookup"><span data-stu-id="a19fd-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="a19fd-125">Par exemple, les outils d’affichage Razor des applications MVC [ASP.NET](https://www.asp.net/) appartiennent à cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="a19fd-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="a19fd-126">Utilisation des outils par projet</span><span class="sxs-lookup"><span data-stu-id="a19fd-126">Consuming per-project tools</span></span>
<span data-ttu-id="a19fd-127">Vous devez ajouter un élément `<DotNetCliToolReference>` à votre fichier projet pour chaque outil que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="a19fd-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="a19fd-128">À l’intérieur de l’élément `<DotNetCliToolReference>`, vous référencez le package dans lequel réside l’outil et spécifiez la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="a19fd-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="a19fd-129">Après l’exécution de [`dotnet restore`](dotnet-restore.md), l’outil et ses dépendances sont restaurés.</span><span class="sxs-lookup"><span data-stu-id="a19fd-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a19fd-130">Pour les outils qui doivent charger la sortie de génération du projet pour l’exécution, il existe généralement une autre dépendance qui est répertoriée sous les dépendances régulières du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a19fd-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="a19fd-131">Étant donné que l’interface CLI utilise MSBuild comme moteur de génération, nous vous recommandons d’écrire ces parties de l’outil sous forme de [cibles](/visualstudio/msbuild/msbuild-targets) et [tâches](/visualstudio/msbuild/msbuild-tasks) MSBuild personnalisées puisqu’elles peuvent ensuite prendre part à l’ensemble du processus de génération.</span><span class="sxs-lookup"><span data-stu-id="a19fd-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="a19fd-132">Elles peuvent aussi facilement récupérer tout ou partie des données produites par la génération, notamment l’emplacement des fichiers de sortie ou la configuration en cours de génération, etc.</span><span class="sxs-lookup"><span data-stu-id="a19fd-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, and so on.</span></span> <span data-ttu-id="a19fd-133">Toutes ces informations deviennent un jeu de propriétés MSBuild qui peut être lu à partir de toutes les cibles.</span><span class="sxs-lookup"><span data-stu-id="a19fd-133">All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="a19fd-134">Vous verrez comment ajouter une cible personnalisée à l’aide de NuGet plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="a19fd-134">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="a19fd-135">Voyons un exemple d’ajout d’un outil simple de type « tools-only » à un projet simple.</span><span class="sxs-lookup"><span data-stu-id="a19fd-135">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="a19fd-136">Prenons un exemple de commande appelé `dotnet-api-search` qui vous permette de parcourir les packages NuGet à la recherche de l’API spécifiée. Voici le fichier projet de l’application console qui utilise cet outil :</span><span class="sxs-lookup"><span data-stu-id="a19fd-136">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="a19fd-137">L’élément `<DotNetCliToolReference>` est structuré de la même façon que l’élément `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-137">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="a19fd-138">Pour procéder à la restauration, il a besoin de l’ID de package du package qui contient l’outil et sa version.</span><span class="sxs-lookup"><span data-stu-id="a19fd-138">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="a19fd-139">Outils de création</span><span class="sxs-lookup"><span data-stu-id="a19fd-139">Building tools</span></span>
<span data-ttu-id="a19fd-140">Comme nous l’avons mentionné précédemment, les outils sont des applications console portables.</span><span class="sxs-lookup"><span data-stu-id="a19fd-140">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="a19fd-141">Vous les créez comme toute autre application console.</span><span class="sxs-lookup"><span data-stu-id="a19fd-141">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="a19fd-142">Une fois l’outil créé, utilisez la commande [`dotnet pack`](dotnet-pack.md) pour créer un package NuGet (fichier .nupkg) devant contenir votre code, les informations sur ses dépendances, etc.</span><span class="sxs-lookup"><span data-stu-id="a19fd-142">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="a19fd-143">Vous pouvez donner n’importe quel nom au package. Toutefois, l’application qui s’y trouve, le fichier binaire de l’outil, doit respecter la convention de `dotnet-<command>` pour pouvoir être appelée par `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-143">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="a19fd-144">Dans les versions antérieures à RC3 des outils en ligne de commande .NET Core, la commande `dotnet pack` présentait un bogue qui empêchait la compression de *.runtimeconfig.json* avec l’outil.</span><span class="sxs-lookup"><span data-stu-id="a19fd-144">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the *.runtimeconfig.json* to not be packed with the tool.</span></span> <span data-ttu-id="a19fd-145">L’absence de ce fichier aboutit à des erreurs lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a19fd-145">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="a19fd-146">Si vous rencontrez ce comportement, veillez à utiliser les outils les plus récents et essayez `dotnet pack` une nouvelle fois.</span><span class="sxs-lookup"><span data-stu-id="a19fd-146">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="a19fd-147">Étant donné que les outils sont des applications portables, l’utilisateur qui utilise un outil doit disposer de la version des bibliothèques .NET Core à l’aide desquelles l’outil a été développé, afin de pouvoir l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="a19fd-147">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="a19fd-148">Toute autre dépendance que l’outil utilise et qui ne figure pas dans les bibliothèques .NET Core est restaurée et placée dans le cache de NuGet.</span><span class="sxs-lookup"><span data-stu-id="a19fd-148">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="a19fd-149">L’outil entier est, par conséquent, exécuté à l’aide des assemblys des bibliothèques .NET Core et du cache de NuGet.</span><span class="sxs-lookup"><span data-stu-id="a19fd-149">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="a19fd-150">Ces types d’outils ont un graphique de dépendance qui est complètement distinct du graphique de dépendance du projet qui les utilise.</span><span class="sxs-lookup"><span data-stu-id="a19fd-150">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="a19fd-151">Le processus de restauration restaure d’abord les dépendances du projet, puis restaure chacun des outils et leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="a19fd-151">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="a19fd-152">Vous trouverez des exemples plus complets dans le [dépôt sur les outils CLI .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span><span class="sxs-lookup"><span data-stu-id="a19fd-152">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="a19fd-153">Vous pouvez également voir l’[implémentation des outils utilisés](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) dans le même dépôt.</span><span class="sxs-lookup"><span data-stu-id="a19fd-153">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

## <a name="custom-targets"></a><span data-ttu-id="a19fd-154">Cibles personnalisées</span><span class="sxs-lookup"><span data-stu-id="a19fd-154">Custom targets</span></span>

<span data-ttu-id="a19fd-155">NuGet peut [empaqueter des fichiers de cibles et de propriétés MSBuild personnalisées](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="a19fd-155">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="a19fd-156">Avec le déplacement de .NET Core pour utiliser MSBuild, le même mécanisme d’extensibilité s’applique désormais aux projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a19fd-156">With the move of the .NET Core to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="a19fd-157">Vous utilisez ce type d’extensibilité quand vous souhaitez étendre le processus de génération, accéder à tous les artefacts dans le processus de génération, tels que les fichiers générés, inspecter la configuration sous laquelle la build est appelée, etc.</span><span class="sxs-lookup"><span data-stu-id="a19fd-157">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, and so on.</span></span>

<span data-ttu-id="a19fd-158">Dans l’exemple suivant, vous pouvez voir le fichier projet de la cible à l’aide de la syntaxe `csproj`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-158">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="a19fd-159">Celle-ci indique à la commande [`dotnet pack`](dotnet-pack.md) les éléments à empaqueter. Les fichiers de cibles et les assemblys sont placés dans le dossier *build* à l’intérieur du package.</span><span class="sxs-lookup"><span data-stu-id="a19fd-159">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="a19fd-160">Notez l’élément `<ItemGroup>` dont la propriété `Label` a la valeur `dotnet pack instructions`, et la cible définie en dessous.</span><span class="sxs-lookup"><span data-stu-id="a19fd-160">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
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
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="a19fd-161">L’utilisation de cibles personnalisées s’effectue en fournissant un `<PackageReference>` qui pointe vers le package et sa version dans le projet en cours d’extension.</span><span class="sxs-lookup"><span data-stu-id="a19fd-161">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="a19fd-162">Contrairement aux outils, le package des cibles personnalisées n’est pas inclus dans la fermeture de dépendance du projet de consommation.</span><span class="sxs-lookup"><span data-stu-id="a19fd-162">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="a19fd-163">L’utilisation de la cible personnalisée dépend uniquement de la façon dont vous la configurez.</span><span class="sxs-lookup"><span data-stu-id="a19fd-163">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="a19fd-164">Puisqu’il s’agit d’une cible MSBuild, elle peut dépendre d’une cible donnée, exécutée après une autre cible, et peut également être appelée manuellement à l’aide de la commande `dotnet msbuild -t:<target-name>`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-164">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild -t:<target-name>` command.</span></span>

<span data-ttu-id="a19fd-165">Toutefois, si vous souhaitez procurer une meilleure expérience à vos utilisateurs, vous pouvez combiner des outils par projet et des cibles personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a19fd-165">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="a19fd-166">Dans ce scénario, l’outil par projet se contenterait essentiellement d’accepter tous les paramètres nécessaires à partir desquels il générerait l’invocation [`dotnet msbuild`](dotnet-msbuild.md) nécessaire pour exécuter la cible.</span><span class="sxs-lookup"><span data-stu-id="a19fd-166">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="a19fd-167">Vous pouvez voir un exemple de ce type de synergie sur le dépôt des [exemples du MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) du projet [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="a19fd-167">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="path-based-extensibility"></a><span data-ttu-id="a19fd-168">Extensibilité basée sur le chemin (PATH)</span><span class="sxs-lookup"><span data-stu-id="a19fd-168">PATH-based extensibility</span></span>
<span data-ttu-id="a19fd-169">L’extensibilité basée sur le chemin est généralement utilisée pour les ordinateurs de développement qui nécessitent un outil qui traite conceptuellement plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="a19fd-169">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="a19fd-170">Le principal inconvénient de ce mécanisme d’extension est qu’il est limité à l’ordinateur sur lequel est installé l’outil.</span><span class="sxs-lookup"><span data-stu-id="a19fd-170">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="a19fd-171">Si vous avez besoin de l’installer sur un autre ordinateur, vous devrez le déployer.</span><span class="sxs-lookup"><span data-stu-id="a19fd-171">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="a19fd-172">Ce modèle d’extensibilité des outils CLI est très simple.</span><span class="sxs-lookup"><span data-stu-id="a19fd-172">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="a19fd-173">Comme indiqué dans la [présentation des outils CLI .NET Core](index.md), le pilote `dotnet` peut exécuter toutes les commandes dont le nom respecte la convention `dotnet-<command>`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-173">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="a19fd-174">La logique de résolution par défaut sonde d’abord plusieurs emplacements avant de revenir au chemin (PATH) système.</span><span class="sxs-lookup"><span data-stu-id="a19fd-174">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="a19fd-175">Si la commande demandée existe dans le chemin système et s’il s’agit d’un fichier binaire qui peut être appelé, le pilote `dotnet` l’appellera.</span><span class="sxs-lookup"><span data-stu-id="a19fd-175">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="a19fd-176">Le fichier doit être exécutable.</span><span class="sxs-lookup"><span data-stu-id="a19fd-176">The file must be executable.</span></span> <span data-ttu-id="a19fd-177">Sur les systèmes Unix, il peut s’agir de tous les fichiers dont le bit d’exécution est défini via `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-177">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="a19fd-178">Sur Windows, vous pouvez utiliser des fichiers *cmd*.</span><span class="sxs-lookup"><span data-stu-id="a19fd-178">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="a19fd-179">Examinons l’implémentation simple d’un outil « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="a19fd-179">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="a19fd-180">Nous allons utiliser `bash` et `cmd` sur Windows.</span><span class="sxs-lookup"><span data-stu-id="a19fd-180">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="a19fd-181">La commande suivante répète simplement « Hello World » dans la console.</span><span class="sxs-lookup"><span data-stu-id="a19fd-181">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="a19fd-182">Sur Mac OS, nous pouvons enregistrer ce script en tant que `dotnet-hello` et définir son bit exécutable avec `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-182">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="a19fd-183">Nous pouvons ensuite créer un lien symbolique vers le script dans `/usr/local/bin` à l’aide de la commande `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-183">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="a19fd-184">Cela permet d’appeler la commande à l’aide de la syntaxe `dotnet hello`.</span><span class="sxs-lookup"><span data-stu-id="a19fd-184">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="a19fd-185">Sur Windows, nous pouvons enregistrer ce script en tant que `dotnet-hello.cmd` et le placer dans un emplacement figurant dans un chemin système (ou vous pouvez l’ajouter à un dossier qui existe déjà dans le chemin).</span><span class="sxs-lookup"><span data-stu-id="a19fd-185">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="a19fd-186">Après cela, vous pouvez simplement utiliser `dotnet hello` pour exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="a19fd-186">After this, you can just use `dotnet hello` to run this example.</span></span>
