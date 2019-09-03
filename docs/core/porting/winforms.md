---
title: Porter une application Windows Forms sur .NET Core 3.0
description: Explique comment porter une application Windows Forms .NET Framework sur .NET Core 3.0 pour Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 7ef36be47648ae338b5fe70b75431006c99be31f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105212"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="d3974-103">Procédure : Porter une application de bureau Windows Forms sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3974-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="d3974-104">Cet article explique comment porter une application de bureau Windows Forms de .NET Framework vers .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3974-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="d3974-105">Le kit de développement logiciel (SDK) .NET Core 3.0 prend en charge les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3974-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="d3974-106">Windows Forms reste une infrastructure Windows qui s’exécute exclusivement sous Windows.</span><span class="sxs-lookup"><span data-stu-id="d3974-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="d3974-107">Cet exemple utilise l’interface CLI du kit SDK .NET Core pour créer et gérer un projet.</span><span class="sxs-lookup"><span data-stu-id="d3974-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="d3974-108">Dans cet article, différents noms sont utilisés pour identifier les types de fichiers servant à la migration.</span><span class="sxs-lookup"><span data-stu-id="d3974-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="d3974-109">Les fichiers de votre projet porteront d’autres noms ; faites-les correspondre mentalement à la liste ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d3974-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="d3974-110">Fichier</span><span class="sxs-lookup"><span data-stu-id="d3974-110">File</span></span> | <span data-ttu-id="d3974-111">Description</span><span class="sxs-lookup"><span data-stu-id="d3974-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="d3974-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="d3974-112">**MyApps.sln**</span></span> | <span data-ttu-id="d3974-113">Nom du fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="d3974-113">The name of the solution file.</span></span> |
| <span data-ttu-id="d3974-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3974-114">**MyForms.csproj**</span></span> | <span data-ttu-id="d3974-115">Nom du projet Windows Forms .NET Framework à porter.</span><span class="sxs-lookup"><span data-stu-id="d3974-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="d3974-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3974-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="d3974-117">Nom du nouveau projet .NET Core en création.</span><span class="sxs-lookup"><span data-stu-id="d3974-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="d3974-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="d3974-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="d3974-119">Exécutable de l’application Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="d3974-120">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d3974-120">Prerequisites</span></span>

- <span data-ttu-id="d3974-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour tout le travail de conception.</span><span class="sxs-lookup"><span data-stu-id="d3974-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="d3974-122">Installez les charges de travail Visual Studio suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3974-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="d3974-123">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="d3974-123">.NET desktop development</span></span>
  - <span data-ttu-id="d3974-124">Développement multiplateforme .NET</span><span class="sxs-lookup"><span data-stu-id="d3974-124">.NET cross-platform development</span></span>

- <span data-ttu-id="d3974-125">Un projet Windows Forms de travail dans une solution qui se génère et s’exécute sans problème.</span><span class="sxs-lookup"><span data-stu-id="d3974-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="d3974-126">Le projet doit être codé en C#.</span><span class="sxs-lookup"><span data-stu-id="d3974-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="d3974-127">Installez la dernière préversion de [.NET Core 3.0](https://aka.ms/netcore3download).</span><span class="sxs-lookup"><span data-stu-id="d3974-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="d3974-128">**Visual Studio 2017** ne prend pas en charge les projets .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3974-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="d3974-129">**Visual Studio 2019** est compatible avec les projets .NET Core 3.0, mais ne gère pas encore le Concepteur visuel pour les projets Windows Forms .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3974-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="d3974-130">Pour pouvoir utiliser le Concepteur visuel, il faut que la solution comporte un projet Windows Forms .NET qui partage les fichiers de formulaires avec le projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="d3974-131">Consider</span><span class="sxs-lookup"><span data-stu-id="d3974-131">Consider</span></span>

<span data-ttu-id="d3974-132">Voici les points à prendre en compte pour porter une application Windows Forms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="d3974-133">Vérifiez que votre application est une bonne candidate à la migration.</span><span class="sxs-lookup"><span data-stu-id="d3974-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="d3974-134">Utilisez [l’Analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour déterminer si votre projet sera migré vers .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3974-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="d3974-135">S’il présente des problèmes avec .NET Core 3.0, l’analyseur permettra de les identifier.</span><span class="sxs-lookup"><span data-stu-id="d3974-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="d3974-136">Vous utilisez une autre version de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3974-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="d3974-137">Lors de la sortie de .NET Core 3.0 Preview 1, Windows Forms est devenu open source sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="d3974-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="d3974-138">Le code de Windows Forms .NET Core est une duplication du codebase Windows Forms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="d3974-139">Il peut y avoir des différences qui empêchent le portage de l’application.</span><span class="sxs-lookup"><span data-stu-id="d3974-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="d3974-140">Le [Pack de compatibilité Windows][compat-pack] peut faciliter la migration.</span><span class="sxs-lookup"><span data-stu-id="d3974-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="d3974-141">Certaines API disponibles dans .NET Framework ne le sont pas dans .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3974-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="d3974-142">Le [Pack de compatibilité Windows][compat-pack] ajoute la plupart d’entre elles, ce qui peut faciliter la compatibilité de l’application Windows Forms avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="d3974-143">Mettez à jour les packages NuGet utilisés par votre projet.</span><span class="sxs-lookup"><span data-stu-id="d3974-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="d3974-144">Il est toujours préférable d’utiliser les dernières versions des packages NuGet avant toute migration.</span><span class="sxs-lookup"><span data-stu-id="d3974-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="d3974-145">Si votre application fait référence à des packages NuGet, passez à la dernière version.</span><span class="sxs-lookup"><span data-stu-id="d3974-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="d3974-146">Vérifiez que votre application se génère correctement.</span><span class="sxs-lookup"><span data-stu-id="d3974-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="d3974-147">En cas d’erreurs de package après la mise à niveau, passez à la dernière version du package qui ne casse pas votre code.</span><span class="sxs-lookup"><span data-stu-id="d3974-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="d3974-148">Visual Studio 2019 ne gère pas encore le Concepteur Windows Forms pour .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d3974-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="d3974-149">Il faut actuellement conserver le fichier projet Windows Forms .NET Framework actuel pour pouvoir utiliser le Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3974-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="d3974-150">Créer un projet de kit SDK</span><span class="sxs-lookup"><span data-stu-id="d3974-150">Create a new SDK project</span></span>

<span data-ttu-id="d3974-151">Le nouveau projet .NET Core 3.0 doit se trouver dans un répertoire différent de celui du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="d3974-152">S’ils sont dans le même répertoire, des conflits risquent de se produire avec les fichiers générés dans le répertoire **obj**.</span><span class="sxs-lookup"><span data-stu-id="d3974-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="d3974-153">Dans cet exemple, créons un répertoire nommé **MyFormsAppCore** dans le répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="d3974-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="d3974-154">Créons maintenant le projet **MyFormsCore.csproj** dans le répertoire **MyFormsAppCore**.</span><span class="sxs-lookup"><span data-stu-id="d3974-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="d3974-155">Vous pouvez créer ce fichier manuellement avec l’éditeur de texte de votre choix.</span><span class="sxs-lookup"><span data-stu-id="d3974-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="d3974-156">Collez-y le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="d3974-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="d3974-157">Si vous ne souhaitez pas créer manuellement le fichier projet, vous pouvez utiliser Visual Studio ou le kit SDK .NET Core pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="d3974-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="d3974-158">Il faut toutefois supprimer tous les fichiers générés par le modèle de projet à l’exception du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="d3974-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="d3974-159">Pour utiliser le kit SDK, exécutez la commande suivante à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="d3974-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="d3974-160">Après la création de **MyFormsCore.csproj**, la structure de répertoires devrait se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="d3974-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="d3974-161">Ajoutez le projet **MyFormsCore.csproj** à **MyApps.sln** avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="d3974-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="d3974-162">Corriger la génération d’informations sur l’assembly</span><span class="sxs-lookup"><span data-stu-id="d3974-162">Fix assembly info generation</span></span>

<span data-ttu-id="d3974-163">Les projets Windows Forms créés avec .NET Framework comportent un fichier `AssemblyInfo.cs` qui contient des attributs d’assembly, comme la version de l’assembly à générer.</span><span class="sxs-lookup"><span data-stu-id="d3974-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="d3974-164">Les projets de style kit SDK génèrent automatiquement ces informations selon le fichier projet du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="d3974-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="d3974-165">Ces deux types « d’informations sur l’assembly » entrent un conflit.</span><span class="sxs-lookup"><span data-stu-id="d3974-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="d3974-166">Pour résoudre ce problème, désactivez la génération automatique, ce qui force le projet à utiliser votre fichier `AssemblyInfo.cs`.</span><span class="sxs-lookup"><span data-stu-id="d3974-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="d3974-167">Il y a trois paramètres à ajouter au nœud `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="d3974-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="d3974-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="d3974-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="d3974-169">Si cette propriété est définie sur `false`, il ne génère pas les attributs d’assembly,</span><span class="sxs-lookup"><span data-stu-id="d3974-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="d3974-170">ce qui permet d’éviter le conflit avec le fichier `AssemblyInfo.cs` du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="d3974-171">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="d3974-171">**AssemblyName**</span></span>\
<span data-ttu-id="d3974-172">La valeur de cette propriété est le binaire de sortie créé lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d3974-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="d3974-173">Il n’est pas nécessaire d’ajouter une extension au nom.</span><span class="sxs-lookup"><span data-stu-id="d3974-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="d3974-174">Par exemple, `MyCoreApp` produit `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="d3974-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="d3974-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="d3974-175">**RootNamespace**</span></span>\
<span data-ttu-id="d3974-176">Il s’agit de l’espace de noms utilisé par défaut par le projet,</span><span class="sxs-lookup"><span data-stu-id="d3974-176">The default namespace used by your project.</span></span> <span data-ttu-id="d3974-177">qui doit correspondre à celui du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="d3974-178">Ajoutez ces trois éléments au nœud `<PropertyGroup>` dans le fichier `MyFormsCore.csproj` :</span><span class="sxs-lookup"><span data-stu-id="d3974-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="d3974-179">Ajouter le code source</span><span class="sxs-lookup"><span data-stu-id="d3974-179">Add source code</span></span>

<span data-ttu-id="d3974-180">Actuellement, le projet **MyFormsCore.csproj** ne compile pas de code du tout.</span><span class="sxs-lookup"><span data-stu-id="d3974-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="d3974-181">Par défaut, les projets .NET Core intègrent automatiquement tout le code source du répertoire actif et des répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="d3974-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="d3974-182">Il faut configurer le projet pour inclure le code du projet du .NET Framework avec un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="d3974-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="d3974-183">Si votre projet .NET Framework utilisait des fichiers **.resx** pour les icônes et les ressources des formulaires, ajoutez-les également.</span><span class="sxs-lookup"><span data-stu-id="d3974-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="d3974-184">Ajoutez le nœud `<ItemGroup>` suivant à votre projet.</span><span class="sxs-lookup"><span data-stu-id="d3974-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="d3974-185">Chaque instruction inclut un modèle Glob de fichier qui comporte les répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="d3974-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="d3974-186">Vous pouvez également créer une entrée `<Compile>` ou `<EmbeddedResource>` pour chaque fichier de votre projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="d3974-187">Ajouter des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="d3974-187">Add NuGet packages</span></span>

<span data-ttu-id="d3974-188">Ajoutez au projet .NET Core chacun des packages NuGet auxquels le projet .NET Framework fait référence.</span><span class="sxs-lookup"><span data-stu-id="d3974-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="d3974-189">Votre application Windows Forms .NET Framework comporte très probablement un fichier **packages.config** contenant la liste de tous les packages NuGet auxquels votre projet fait référence.</span><span class="sxs-lookup"><span data-stu-id="d3974-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="d3974-190">Vous pouvez consulter cette liste pour déterminer quels packages NuGet ajouter au projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="d3974-191">Par exemple, si le projet .NET Framework faisait référence aux packages NuGet `MetroFramework`, `MetroFramework.Design` et `MetroFramework.Fonts`, ajoutez-les au projet avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="d3974-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="d3974-192">Les commandes précédentes ajoutent les références NuGet suivantes au projet **MyFormsCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="d3974-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="d3974-193">Porter des bibliothèques de contrôles</span><span class="sxs-lookup"><span data-stu-id="d3974-193">Port control libraries</span></span>

<span data-ttu-id="d3974-194">Les instructions à suivre pour porter un projet de bibliothèque de contrôles Windows Forms sont les mêmes que pour un projet d’application Windows Forms .NET Framework, à l’exception de quelques paramètres.</span><span class="sxs-lookup"><span data-stu-id="d3974-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="d3974-195">Par ailleurs, la compilation s’effectue dans une bibliothèque plutôt qu’un exécutable.</span><span class="sxs-lookup"><span data-stu-id="d3974-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="d3974-196">La différence entre le projet d’exécutable et le projet de bibliothèque, au-delà des chemins d’accès des modèles Glob de fichiers comportant le code source, est minime.</span><span class="sxs-lookup"><span data-stu-id="d3974-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="d3974-197">Reprenons l’exemple de l’étape précédente pour développer les projets et les fichiers de travail.</span><span class="sxs-lookup"><span data-stu-id="d3974-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="d3974-198">Fichier</span><span class="sxs-lookup"><span data-stu-id="d3974-198">File</span></span> | <span data-ttu-id="d3974-199">Description</span><span class="sxs-lookup"><span data-stu-id="d3974-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="d3974-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="d3974-200">**MyApps.sln**</span></span> | <span data-ttu-id="d3974-201">Nom du fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="d3974-201">The name of the solution file.</span></span> |
| <span data-ttu-id="d3974-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3974-202">**MyControls.csproj**</span></span> | <span data-ttu-id="d3974-203">Nom du projet de contrôles Windows Forms .NET Framework à porter.</span><span class="sxs-lookup"><span data-stu-id="d3974-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="d3974-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="d3974-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="d3974-205">Nom du nouveau projet de bibliothèque .NET Core en création.</span><span class="sxs-lookup"><span data-stu-id="d3974-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="d3974-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="d3974-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="d3974-207">Bibliothèque de contrôles Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-207">The .NET Core Windows Forms Controls library.</span></span> |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

<span data-ttu-id="d3974-208">Examinez les différences entre le projet `MyControlsCore.csproj` et le projet `MyFormsCore.csproj` créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="d3974-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

<span data-ttu-id="d3974-209">Voici un exemple de fichier de projet de bibliothèque de contrôles Windows Forms .NET Core :</span><span class="sxs-lookup"><span data-stu-id="d3974-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>
  
  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>
  
</Project>
```

<span data-ttu-id="d3974-210">Comme on peut le voir, le nœud `<OutputType>` a été supprimé, ce qui conduit le compilateur à générer par défaut une bibliothèque au lieu d’un exécutable.</span><span class="sxs-lookup"><span data-stu-id="d3974-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="d3974-211">`<AssemblyName>` et `<RootNamespace>` ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="d3974-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="d3974-212">En particulier, `<RootNamespace>` doit correspondre à l’espace de noms de la bibliothèque de contrôles Windows Forms portée.</span><span class="sxs-lookup"><span data-stu-id="d3974-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="d3974-213">Enfin, les nœuds `<Compile>` et `<EmbeddedResource>` ont été ajustés pour pointer vers le dossier de la bibliothèque en question.</span><span class="sxs-lookup"><span data-stu-id="d3974-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="d3974-214">Maintenant, dans le projet **MyFormsCore.csproj** .NET Core principal, ajoutez une référence à la nouvelle bibliothèque de contrôles Windows Forms .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3974-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="d3974-215">avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="d3974-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="d3974-216">La commande précédente ajoute le code suivant au projet **MyFormsCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="d3974-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="d3974-217">Problèmes de compilation</span><span class="sxs-lookup"><span data-stu-id="d3974-217">Problems compiling</span></span>

<span data-ttu-id="d3974-218">Si avez des difficultés à compiler vos projets, c’est peut-être le signe que vous utilisez des API Windows disponibles dans .NET Framework et non dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="d3974-219">Vous pouvez essayer d’ajouter le package NuGet [Pack de compatibilité Windows][compat-pack] à votre projet.</span><span class="sxs-lookup"><span data-stu-id="d3974-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="d3974-220">Ce package, qui s’exécute seulement sur Windows, ajoute environ 20 000 API Windows aux projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d3974-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="d3974-221">La commande précédente ajoute le code suivant au projet **MyFormsCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="d3974-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="d3974-222">Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3974-222">Windows Forms Designer</span></span>

<span data-ttu-id="d3974-223">Comme nous l’avons indiqué dans cet article, Visual Studio 2019 ne prend en charge le Concepteur Windows Forms que dans les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3974-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="d3974-224">En créant un projet .NET Core côte à côte, vous pouvez tester votre projet avec .NET Core tout en utilisant le projet .NET Framework pour concevoir des formulaires.</span><span class="sxs-lookup"><span data-stu-id="d3974-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="d3974-225">Le fichier de solution comporte à la fois les projets .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="d3974-226">Ajoutez et concevez vos formulaires et vos contrôles dans le projet .NET Framework ; à partir des modèles Glob de fichier que nous avons ajoutés aux projets .NET Core, les nouveaux fichiers et les fichiers modifiés sont automatiquement intégrés au projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="d3974-227">Dès que Visual Studio 2019 prendra en charge le Concepteur Windows Forms, vous pourrez copier/coller le contenu de votre fichier projet .NET Core dans le fichier projet .NET Framework,</span><span class="sxs-lookup"><span data-stu-id="d3974-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="d3974-228">puis supprimer les modèles Glob de fichier ajoutés avec les éléments `<Source>` et `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="d3974-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="d3974-229">Résolvez le chemin d’accès des références de projet utilisées par votre application.</span><span class="sxs-lookup"><span data-stu-id="d3974-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="d3974-230">Le projet .NET Framework est ainsi mis à niveau en un projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="d3974-231">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d3974-231">Next steps</span></span>

- <span data-ttu-id="d3974-232">Découvrez-en plus sur le [Pack de compatibilité Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="d3974-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="d3974-233">Regardez une [vidéo sur le portage](https://www.youtube.com/watch?v=upVQEUc_KwU) de projets Windows Forms .NET Framework vers .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3974-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
