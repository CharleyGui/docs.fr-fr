---
title: Port a Windows Forms app to .NET Core
description: Vous apprend à porter une application .NET Framework Windows Forms à .NET Core for Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.openlocfilehash: dbd522851faa0a4fe435199914a034ee230d3455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116025"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="be328-103">Comment porter une application de bureau Windows Forms à .NET Core</span><span class="sxs-lookup"><span data-stu-id="be328-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="be328-104">Cet article décrit comment porter votre application de bureau windows Forms à partir de .NET Framework à .NET Core 3.0 ou plus tard.</span><span class="sxs-lookup"><span data-stu-id="be328-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="be328-105">Le kit de développement logiciel (SDK) .NET Core 3.0 prend en charge les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be328-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="be328-106">Windows Forms reste une infrastructure Windows qui s’exécute exclusivement sous Windows.</span><span class="sxs-lookup"><span data-stu-id="be328-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="be328-107">Cet exemple utilise l’interface CLI du kit SDK .NET Core pour créer et gérer un projet.</span><span class="sxs-lookup"><span data-stu-id="be328-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="be328-108">Dans cet article, différents noms sont utilisés pour identifier les types de fichiers servant à la migration.</span><span class="sxs-lookup"><span data-stu-id="be328-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="be328-109">Les fichiers de votre projet porteront d’autres noms ; faites-les correspondre mentalement à la liste ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="be328-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="be328-110">Fichier</span><span class="sxs-lookup"><span data-stu-id="be328-110">File</span></span> | <span data-ttu-id="be328-111">Description</span><span class="sxs-lookup"><span data-stu-id="be328-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="be328-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="be328-112">**MyApps.sln**</span></span> | <span data-ttu-id="be328-113">Nom du fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="be328-113">The name of the solution file.</span></span> |
| <span data-ttu-id="be328-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="be328-114">**MyForms.csproj**</span></span> | <span data-ttu-id="be328-115">Nom du projet Windows Forms .NET Framework à porter.</span><span class="sxs-lookup"><span data-stu-id="be328-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="be328-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="be328-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="be328-117">Nom du nouveau projet .NET Core en création.</span><span class="sxs-lookup"><span data-stu-id="be328-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="be328-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="be328-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="be328-119">Exécutable de l’application Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="be328-120">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="be328-120">Prerequisites</span></span>

- <span data-ttu-id="be328-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour tout le travail de conception.</span><span class="sxs-lookup"><span data-stu-id="be328-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="be328-122">Installez les charges de travail Visual Studio suivantes :</span><span class="sxs-lookup"><span data-stu-id="be328-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="be328-123">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="be328-123">.NET desktop development</span></span>
  - <span data-ttu-id="be328-124">Développement multiplateforme .NET Core</span><span class="sxs-lookup"><span data-stu-id="be328-124">.NET Core cross-platform development</span></span>

- <span data-ttu-id="be328-125">Un projet Windows Forms de travail dans une solution qui se génère et s’exécute sans problème.</span><span class="sxs-lookup"><span data-stu-id="be328-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="be328-126">Un projet codé en C.</span><span class="sxs-lookup"><span data-stu-id="be328-126">A project coded in C#.</span></span>
- <span data-ttu-id="be328-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 ou plus tard.</span><span class="sxs-lookup"><span data-stu-id="be328-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="be328-128">**Visual Studio 2017** ne prend pas en charge les projets .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="be328-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="be328-129">**Visual Studio 2019** est compatible avec les projets .NET Core 3.0, mais ne gère pas encore le Concepteur visuel pour les projets Windows Forms .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="be328-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="be328-130">Pour utiliser le concepteur visuel, vous devez avoir un projet .NET Windows Forms dans une solution qui partage les fichiers de formulaires avec le projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-130">To use the visual designer, you must have a .NET Windows Forms project in a solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="be328-131">Consider</span><span class="sxs-lookup"><span data-stu-id="be328-131">Consider</span></span>

<span data-ttu-id="be328-132">Voici les points à prendre en compte pour porter une application Windows Forms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be328-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="be328-133">Vérifiez que votre application est une bonne candidate à la migration.</span><span class="sxs-lookup"><span data-stu-id="be328-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="be328-134">Utilisez [l’Analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour déterminer si votre projet sera migré vers .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="be328-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="be328-135">S’il présente des problèmes avec .NET Core 3.0, l’analyseur permettra de les identifier.</span><span class="sxs-lookup"><span data-stu-id="be328-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="be328-136">Vous utilisez une autre version de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be328-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="be328-137">Lorsque .NET Core 3.0 Preview 1 a été publié, Windows Forms est allé open source sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="be328-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="be328-138">Le code pour .NET Core Windows Forms est une fourchette de la base de code .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="be328-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="be328-139">Il peut y avoir des différences qui empêchent le portage de l’application.</span><span class="sxs-lookup"><span data-stu-id="be328-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="be328-140">Le [Pack de compatibilité Windows][compat-pack] peut faciliter la migration.</span><span class="sxs-lookup"><span data-stu-id="be328-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="be328-141">Certaines API disponibles dans .NET Framework ne le sont pas dans .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="be328-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="be328-142">Le [Pack de compatibilité Windows][compat-pack] ajoute la plupart d’entre elles, ce qui peut faciliter la compatibilité de l’application Windows Forms avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="be328-143">Mettez à jour les packages NuGet utilisés par votre projet.</span><span class="sxs-lookup"><span data-stu-id="be328-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="be328-144">Il est toujours préférable d’utiliser les dernières versions des packages NuGet avant toute migration.</span><span class="sxs-lookup"><span data-stu-id="be328-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="be328-145">Si votre application fait référence à des packages NuGet, passez à la dernière version.</span><span class="sxs-lookup"><span data-stu-id="be328-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="be328-146">Vérifiez que votre application se génère correctement.</span><span class="sxs-lookup"><span data-stu-id="be328-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="be328-147">En cas d’erreurs de package après la mise à niveau, passez à la dernière version du package qui ne casse pas votre code.</span><span class="sxs-lookup"><span data-stu-id="be328-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="be328-148">Visual Studio 2019 ne gère pas encore le Concepteur Windows Forms pour .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="be328-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="be328-149">Il faut actuellement conserver le fichier projet Windows Forms .NET Framework actuel pour pouvoir utiliser le Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be328-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="be328-150">Créer un projet de kit SDK</span><span class="sxs-lookup"><span data-stu-id="be328-150">Create a new SDK project</span></span>

<span data-ttu-id="be328-151">Le nouveau projet .NET Core 3.0 doit se trouver dans un répertoire différent de celui du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be328-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="be328-152">S’ils sont dans le même répertoire, des conflits risquent de se produire avec les fichiers générés dans le répertoire **obj**.</span><span class="sxs-lookup"><span data-stu-id="be328-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="be328-153">Dans cet exemple, créons un répertoire nommé **MyFormsAppCore** dans le répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="be328-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="be328-154">Créons maintenant le projet **MyFormsCore.csproj** dans le répertoire **MyFormsAppCore**.</span><span class="sxs-lookup"><span data-stu-id="be328-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="be328-155">Vous pouvez créer ce fichier manuellement avec l’éditeur de texte de votre choix.</span><span class="sxs-lookup"><span data-stu-id="be328-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="be328-156">Collez-y le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="be328-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="be328-157">Si vous ne souhaitez pas créer manuellement le fichier projet, vous pouvez utiliser Visual Studio ou le kit SDK .NET Core pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="be328-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="be328-158">Il faut toutefois supprimer tous les fichiers générés par le modèle de projet à l’exception du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="be328-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="be328-159">Pour utiliser le kit SDK, exécutez la commande suivante à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="be328-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="be328-160">Après la création de **MyFormsCore.csproj**, la structure de répertoires devrait se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="be328-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="be328-161">Ajoutez le projet **MyFormsCore.csproj** à **MyApps.sln** avec Visual Studio ou le CLI .NET Core de l’annuaire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="be328-161">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="be328-162">Corriger la génération d’informations sur l’assembly</span><span class="sxs-lookup"><span data-stu-id="be328-162">Fix assembly info generation</span></span>

<span data-ttu-id="be328-163">Les projets Windows Forms créés avec .NET Framework comportent un fichier `AssemblyInfo.cs` qui contient des attributs d’assembly, comme la version de l’assembly à générer.</span><span class="sxs-lookup"><span data-stu-id="be328-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="be328-164">Les projets de style kit SDK génèrent automatiquement ces informations selon le fichier projet du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="be328-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="be328-165">Ces deux types « d’informations sur l’assembly » entrent un conflit.</span><span class="sxs-lookup"><span data-stu-id="be328-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="be328-166">Pour résoudre ce problème, désactivez la génération automatique, ce qui force le projet à utiliser votre fichier `AssemblyInfo.cs`.</span><span class="sxs-lookup"><span data-stu-id="be328-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="be328-167">Il y a trois paramètres à ajouter au nœud `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="be328-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="be328-168">**GénérerAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="be328-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="be328-169">Si cette propriété est définie sur `false`, il ne génère pas les attributs d’assembly,</span><span class="sxs-lookup"><span data-stu-id="be328-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="be328-170">ce qui permet d’éviter le conflit avec le fichier `AssemblyInfo.cs` du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be328-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="be328-171">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="be328-171">**AssemblyName**</span></span>\
<span data-ttu-id="be328-172">La valeur de cette propriété est le binaire de sortie créé lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="be328-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="be328-173">Il n’est pas nécessaire d’ajouter une extension au nom.</span><span class="sxs-lookup"><span data-stu-id="be328-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="be328-174">Par exemple, `MyCoreApp` produit `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="be328-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="be328-175">**RootNamespace (RootNamespace)**</span><span class="sxs-lookup"><span data-stu-id="be328-175">**RootNamespace**</span></span>\
<span data-ttu-id="be328-176">Il s’agit de l’espace de noms utilisé par défaut par le projet,</span><span class="sxs-lookup"><span data-stu-id="be328-176">The default namespace used by your project.</span></span> <span data-ttu-id="be328-177">qui doit correspondre à celui du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be328-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="be328-178">Ajoutez ces trois éléments au nœud `<PropertyGroup>` dans le fichier `MyFormsCore.csproj` :</span><span class="sxs-lookup"><span data-stu-id="be328-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="be328-179">Ajouter le code source</span><span class="sxs-lookup"><span data-stu-id="be328-179">Add source code</span></span>

<span data-ttu-id="be328-180">Actuellement, le projet **MyFormsCore.csproj** ne compile pas de code du tout.</span><span class="sxs-lookup"><span data-stu-id="be328-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="be328-181">Par défaut, les projets .NET Core intègrent automatiquement tout le code source du répertoire actif et des répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="be328-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="be328-182">Il faut configurer le projet pour inclure le code du projet du .NET Framework avec un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="be328-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="be328-183">Si votre projet .NET Framework utilisait des fichiers **.resx** pour les icônes et les ressources des formulaires, ajoutez-les également.</span><span class="sxs-lookup"><span data-stu-id="be328-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="be328-184">Ajoutez le nœud `<ItemGroup>` suivant à votre projet.</span><span class="sxs-lookup"><span data-stu-id="be328-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="be328-185">Chaque instruction inclut un modèle Glob de fichier qui comporte les répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="be328-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="be328-186">Vous pouvez également créer une entrée `<Compile>` ou `<EmbeddedResource>` pour chaque fichier de votre projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be328-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="be328-187">Ajout de packages NuGet</span><span class="sxs-lookup"><span data-stu-id="be328-187">Add NuGet packages</span></span>

<span data-ttu-id="be328-188">Ajoutez au projet .NET Core chacun des packages NuGet auxquels le projet .NET Framework fait référence.</span><span class="sxs-lookup"><span data-stu-id="be328-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="be328-189">Votre application Windows Forms .NET Framework comporte très probablement un fichier **packages.config** contenant la liste de tous les packages NuGet auxquels votre projet fait référence.</span><span class="sxs-lookup"><span data-stu-id="be328-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="be328-190">Vous pouvez consulter cette liste pour déterminer quels packages NuGet ajouter au projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="be328-191">Par exemple, si le projet .NET Framework faisait référence aux packages NuGet `MetroFramework`, `MetroFramework.Design` et `MetroFramework.Fonts`, ajoutez-les au projet avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="be328-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="be328-192">Les commandes précédentes ajoutent les références NuGet suivantes au projet **MyFormsCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="be328-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="be328-193">Porter des bibliothèques de contrôles</span><span class="sxs-lookup"><span data-stu-id="be328-193">Port control libraries</span></span>

<span data-ttu-id="be328-194">Les instructions à suivre pour porter un projet de bibliothèque de contrôles Windows Forms sont les mêmes que pour un projet d’application Windows Forms .NET Framework, à l’exception de quelques paramètres.</span><span class="sxs-lookup"><span data-stu-id="be328-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="be328-195">Par ailleurs, la compilation s’effectue dans une bibliothèque plutôt qu’un exécutable.</span><span class="sxs-lookup"><span data-stu-id="be328-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="be328-196">La différence entre le projet d’exécutable et le projet de bibliothèque, au-delà des chemins d’accès des modèles Glob de fichiers comportant le code source, est minime.</span><span class="sxs-lookup"><span data-stu-id="be328-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="be328-197">Reprenons l’exemple de l’étape précédente pour développer les projets et les fichiers de travail.</span><span class="sxs-lookup"><span data-stu-id="be328-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="be328-198">Fichier</span><span class="sxs-lookup"><span data-stu-id="be328-198">File</span></span> | <span data-ttu-id="be328-199">Description</span><span class="sxs-lookup"><span data-stu-id="be328-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="be328-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="be328-200">**MyApps.sln**</span></span> | <span data-ttu-id="be328-201">Nom du fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="be328-201">The name of the solution file.</span></span> |
| <span data-ttu-id="be328-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="be328-202">**MyControls.csproj**</span></span> | <span data-ttu-id="be328-203">Nom du projet de contrôles Windows Forms .NET Framework à porter.</span><span class="sxs-lookup"><span data-stu-id="be328-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="be328-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="be328-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="be328-205">Nom du nouveau projet de bibliothèque .NET Core en création.</span><span class="sxs-lookup"><span data-stu-id="be328-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="be328-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="be328-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="be328-207">Bibliothèque de contrôles Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="be328-208">Examinez les différences entre le projet `MyControlsCore.csproj` et le projet `MyFormsCore.csproj` créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="be328-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="be328-209">Voici un exemple de fichier de projet de bibliothèque de contrôles Windows Forms .NET Core :</span><span class="sxs-lookup"><span data-stu-id="be328-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="be328-210">Comme on peut le voir, le nœud `<OutputType>` a été supprimé, ce qui conduit le compilateur à générer par défaut une bibliothèque au lieu d’un exécutable.</span><span class="sxs-lookup"><span data-stu-id="be328-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="be328-211">`<AssemblyName>` et `<RootNamespace>` ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="be328-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="be328-212">En particulier, `<RootNamespace>` doit correspondre à l’espace de noms de la bibliothèque de contrôles Windows Forms portée.</span><span class="sxs-lookup"><span data-stu-id="be328-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="be328-213">Enfin, les nœuds `<Compile>` et `<EmbeddedResource>` ont été ajustés pour pointer vers le dossier de la bibliothèque en question.</span><span class="sxs-lookup"><span data-stu-id="be328-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="be328-214">Ensuite, dans le principal projet .NET Core **MyFormsCore.csproj,** ajoutez une référence à la nouvelle bibliothèque .NET Core Windows Forms Control.</span><span class="sxs-lookup"><span data-stu-id="be328-214">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="be328-215">avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="be328-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="be328-216">La commande précédente ajoute le code suivant au projet **MyFormsCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="be328-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="be328-217">Problèmes de compilation</span><span class="sxs-lookup"><span data-stu-id="be328-217">Compilation problems</span></span>

<span data-ttu-id="be328-218">Si avez des difficultés à compiler vos projets, c’est peut-être le signe que vous utilisez des API Windows disponibles dans .NET Framework et non dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="be328-219">Vous pouvez essayer d’ajouter le package NuGet [Pack de compatibilité Windows][compat-pack] à votre projet.</span><span class="sxs-lookup"><span data-stu-id="be328-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="be328-220">Ce package, qui s’exécute seulement sur Windows, ajoute environ 20 000 API Windows aux projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="be328-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="be328-221">La commande précédente ajoute le code suivant au projet **MyFormsCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="be328-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="be328-222">Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be328-222">Windows Forms Designer</span></span>

<span data-ttu-id="be328-223">Comme nous l’avons indiqué dans cet article, Visual Studio 2019 ne prend en charge le Concepteur Windows Forms que dans les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="be328-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="be328-224">En créant un projet .NET Core côte à côte, vous pouvez tester votre projet avec .NET Core tout en utilisant le projet .NET Framework pour concevoir des formulaires.</span><span class="sxs-lookup"><span data-stu-id="be328-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="be328-225">Le fichier de solution comporte à la fois les projets .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="be328-226">Ajoutez et concevez vos formulaires et vos contrôles dans le projet .NET Framework ; à partir des modèles Glob de fichier que nous avons ajoutés aux projets .NET Core, les nouveaux fichiers et les fichiers modifiés sont automatiquement intégrés au projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="be328-227">Dès que Visual Studio 2019 prendra en charge le Concepteur Windows Forms, vous pourrez copier/coller le contenu de votre fichier projet .NET Core dans le fichier projet .NET Framework,</span><span class="sxs-lookup"><span data-stu-id="be328-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="be328-228">puis supprimer les modèles Glob de fichier ajoutés avec les éléments `<Source>` et `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="be328-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="be328-229">Résolvez le chemin d’accès des références de projet utilisées par votre application.</span><span class="sxs-lookup"><span data-stu-id="be328-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="be328-230">Le projet .NET Framework est ainsi mis à niveau en un projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="be328-231">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="be328-231">Next steps</span></span>

- <span data-ttu-id="be328-232">En savoir plus sur [les changements de rupture de .NET Framework à .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="be328-232">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="be328-233">En savoir plus sur le [Pack de compatibilité Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="be328-233">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="be328-234">Regardez une [vidéo sur le portage](https://www.youtube.com/watch?v=upVQEUc_KwU) de projets Windows Forms .NET Framework vers .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be328-234">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
