---
title: Porter une application WPF sur .NET Core 3.0
description: Explique comment porter une application .NET Framework Windows Presentation Foundation sur .NET Core 3.0 pour Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 9885f666e68b795b9b6aba9cf31f9750e30fd170
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512282"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="e2b5f-103">Procédure : Porter une application de bureau WPF sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="e2b5f-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="e2b5f-104">Cet article explique comment porter votre application de bureau Windows Presentation Foundation (WPF) du .NET Framework vers .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="e2b5f-105">Le SDK .NET Core 3.0 prend en charge les applications WPF.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="e2b5f-106">WPF reste un framework Windows qui s’exécute exclusivement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="e2b5f-107">Cet exemple utilise l’interface CLI du kit SDK .NET Core pour créer et gérer un projet.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="e2b5f-108">Dans cet article, différents noms sont utilisés pour identifier les types de fichiers servant à la migration.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="e2b5f-109">Les fichiers de votre projet porteront d’autres noms ; faites-les correspondre mentalement à la liste ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="e2b5f-110">Fichier</span><span class="sxs-lookup"><span data-stu-id="e2b5f-110">File</span></span> | <span data-ttu-id="e2b5f-111">Description</span><span class="sxs-lookup"><span data-stu-id="e2b5f-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="e2b5f-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-112">**MyApps.sln**</span></span> | <span data-ttu-id="e2b5f-113">Nom du fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-113">The name of the solution file.</span></span> |
| <span data-ttu-id="e2b5f-114">**MyWPF.csproj**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="e2b5f-115">Nom du projet WPF .NET Framework à porter.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="e2b5f-116">**MyWPFCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="e2b5f-117">Nom du nouveau projet .NET Core en création.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="e2b5f-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="e2b5f-119">Exécutable de l’application WPF .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-119">The .NET Core WPF app executable.</span></span> |

>[!IMPORTANT]
><span data-ttu-id="e2b5f-120">Bien que cet article utilise C# comme langage cible, les étapes sont les mêmes pour VB.NET, à ceci près que VB.NET utilise des fichiers *.vbproj* et *.vb* au lieu de fichiers *.csproj* et *.cs*, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-120">Even though this article uses C# as the target language, the steps are the same for VB.NET, except that VB.NET uses *.vbproj* and *.vb* files instead of *.csproj* and *.cs* files, respectively.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2b5f-121">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e2b5f-121">Prerequisites</span></span>

- <span data-ttu-id="e2b5f-122">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour tout le travail de conception.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-122">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="e2b5f-123">Installez les charges de travail Visual Studio suivantes :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="e2b5f-124">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="e2b5f-124">.NET desktop development</span></span>
  - <span data-ttu-id="e2b5f-125">Développement multiplateforme .NET</span><span class="sxs-lookup"><span data-stu-id="e2b5f-125">.NET cross-platform development</span></span>

- <span data-ttu-id="e2b5f-126">Un projet WPF de travail dans une solution qui se génère et s’exécute sans problème.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-126">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="e2b5f-127">Installez la dernière préversion de [.NET Core 3.0](https://aka.ms/netcore3download).</span><span class="sxs-lookup"><span data-stu-id="e2b5f-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="e2b5f-128">**Visual Studio 2017** ne prend pas en charge les projets .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="e2b5f-129">**Visual Studio 2019** prend en charge les projet .NET Core 3.0, mais offre une prise en charge limitée du concepteur visuel WPF .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-129">**Visual Studio 2019** supports .NET Core 3.0 projects but has limited support for the .NET Core WPF visual designer.</span></span> <span data-ttu-id="e2b5f-130">Pour utiliser un concepteur visuel entièrement pris en charge, votre solution doit comporter un projet WPF .NET Framework qui partage ses fichiers avec le projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-130">To use a fully-supported visual designer, you must have a .NET Framework WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="e2b5f-131">Consider</span><span class="sxs-lookup"><span data-stu-id="e2b5f-131">Consider</span></span>

<span data-ttu-id="e2b5f-132">Voici les points à prendre en compte pour porter une application WPF .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="e2b5f-133">Vérifiez que votre application est une bonne candidate à la migration.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="e2b5f-134">Utilisez [l’Analyseur de portabilité .NET](../../standard/analyzers/portability-analyzer.md) pour déterminer si votre projet sera migré vers .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="e2b5f-135">S’il présente des problèmes avec .NET Core 3.0, l’analyseur permettra de les identifier.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="e2b5f-136">Vous utilisez une autre version de WPF.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="e2b5f-137">Lors de la sortie de .NET Core 3.0 Preview 1, WPF est devenu open source sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="e2b5f-138">Le code de WPF .NET Core est une duplication du codebase WPF .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="e2b5f-139">Il peut y avoir des différences qui empêchent le portage de l’application.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="e2b5f-140">Le [Pack de compatibilité Windows][compat-pack] peut faciliter la migration.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="e2b5f-141">Certaines API disponibles dans .NET Framework ne le sont pas dans .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="e2b5f-142">Le [Pack de compatibilité Windows][compat-pack] ajoute la plupart d’entre elles, ce qui peut faciliter la compatibilité de l’application WPF avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="e2b5f-143">Mettez à jour les packages NuGet utilisés par votre projet.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="e2b5f-144">Il est toujours préférable d’utiliser les dernières versions des packages NuGet avant toute migration.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="e2b5f-145">Si votre application fait référence à des packages NuGet, passez à la dernière version.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="e2b5f-146">Vérifiez que votre application se génère correctement.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="e2b5f-147">En cas d’erreurs de package après la mise à niveau, passez à la dernière version du package qui ne casse pas votre code.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="e2b5f-148">Visual Studio 2019 ne gère pas encore le Concepteur WPF pour .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-148">Visual Studio 2019 doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="e2b5f-149">Pour le moment, vous devez conserver le fichier projet WPF actuel du .NET Framework pour pouvoir utiliser le Concepteur WPF dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="e2b5f-150">Créer un projet de kit SDK</span><span class="sxs-lookup"><span data-stu-id="e2b5f-150">Create a new SDK project</span></span>

<span data-ttu-id="e2b5f-151">Le nouveau projet .NET Core 3.0 doit se trouver dans un répertoire différent de celui du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="e2b5f-152">S’ils sont dans le même répertoire, des conflits risquent de se produire avec les fichiers générés dans le répertoire **obj**.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="e2b5f-153">Dans cet exemple, vous allez créer un répertoire nommé **MyWPFAppCore** dans le répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="e2b5f-154">Ensuite, vous avez besoin de créer le projet **MyWPFCore.csproj** dans le répertoire **MyWPFAppCore**.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="e2b5f-155">Vous pouvez créer ce fichier manuellement avec l’éditeur de texte de votre choix.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="e2b5f-156">Collez-y le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e2b5f-157">Si vous ne souhaitez pas créer manuellement le fichier projet, vous pouvez utiliser Visual Studio ou le kit SDK .NET Core pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="e2b5f-158">Il faut toutefois supprimer tous les fichiers générés par le modèle de projet à l’exception du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="e2b5f-159">Pour utiliser le kit SDK, exécutez la commande suivante à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="e2b5f-160">Une fois **MyWPFCore.csproj** créé, la structure de répertoires doit se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="e2b5f-161">Ajoutez le projet **MyWPFCore.csproj** à **MyApps.sln** avec Visual Studio ou l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="e2b5f-162">Corriger la génération d’informations sur l’assembly</span><span class="sxs-lookup"><span data-stu-id="e2b5f-162">Fix assembly info generation</span></span>

<span data-ttu-id="e2b5f-163">Les projets Windows Presentation Foundation créés avec le .NET Framework comportent un fichier `AssemblyInfo.cs` qui contient des attributs d’assembly, comme la version de l’assembly à générer.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="e2b5f-164">Les projets de style kit SDK génèrent automatiquement ces informations selon le fichier projet du kit SDK.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="e2b5f-165">Ces deux types « d’informations sur l’assembly » entrent un conflit.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="e2b5f-166">Pour résoudre ce problème, désactivez la génération automatique, ce qui force le projet à utiliser votre fichier `AssemblyInfo.cs`.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="e2b5f-167">Il y a trois paramètres à ajouter au nœud `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="e2b5f-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="e2b5f-169">Si cette propriété est définie sur `false`, il ne génère pas les attributs d’assembly,</span><span class="sxs-lookup"><span data-stu-id="e2b5f-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="e2b5f-170">ce qui permet d’éviter le conflit avec le fichier `AssemblyInfo.cs` du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="e2b5f-171">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-171">**AssemblyName**</span></span>\
<span data-ttu-id="e2b5f-172">La valeur de cette propriété est le binaire de sortie créé lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="e2b5f-173">Il n’est pas nécessaire d’ajouter une extension au nom.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="e2b5f-174">Par exemple, `MyCoreApp` produit `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="e2b5f-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="e2b5f-175">**RootNamespace**</span></span>\
<span data-ttu-id="e2b5f-176">Il s’agit de l’espace de noms utilisé par défaut par le projet,</span><span class="sxs-lookup"><span data-stu-id="e2b5f-176">The default namespace used by your project.</span></span> <span data-ttu-id="e2b5f-177">qui doit correspondre à celui du projet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="e2b5f-178">Ajoutez ces trois éléments au nœud `<PropertyGroup>` dans le fichier `MyWPFCore.csproj` :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="e2b5f-179">Ajouter le code source</span><span class="sxs-lookup"><span data-stu-id="e2b5f-179">Add source code</span></span>
<span data-ttu-id="e2b5f-180">Actuellement, le projet **MyWPFCore.csproj** ne compile pas de code du tout.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="e2b5f-181">Par défaut, les projets .NET Core intègrent automatiquement tout le code source du répertoire actif et des répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="e2b5f-182">Il faut configurer le projet pour inclure le code du projet du .NET Framework avec un chemin d’accès relatif.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="e2b5f-183">Si votre projet .NET Framework utilisait des fichiers **.resx** pour les icônes et les ressources des fenêtres et contrôles, ajoutez-les également.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="e2b5f-184">Le premier nœud `<ItemGroup>` que vous devez ajouter à votre projet contient le fichier **App.xaml** qui représente la configuration de démarrage et les ressources que votre application utilise.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="e2b5f-185">Le fichier **App.xaml** est également assorti d’un fichier **App.xaml.cs**, mais il sera automatiquement inclus dans un autre `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="e2b5f-186">Ajoutez ensuite le nœud `<ItemGroup>` suivant à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="e2b5f-187">Chaque instruction inclut un modèle Glob de fichier qui comporte les répertoires enfants.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="e2b5f-188">Ce modèle inclut le code source de votre projet, tous les fichiers de paramètres et toutes les ressources.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="e2b5f-189">Le répertoire **obj** est explicitement exclu.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="e2b5f-190">Ensuite, incluez un autre nœud `<ItemGroup>` qui contient une entrée `<Page>` pour chaque fichier **xaml** contenu dans votre projet, mis à part le fichier **App.xaml**.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="e2b5f-191">Ces fichiers contiennent toutes les fenêtres, pages et ressources qui sont au format **xaml**.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="e2b5f-192">Vous ne pouvez pas utiliser un modèle Glob ici et vous devez ajouter une entrée pour chaque fichier et indiquer le `<Generator>` utilisé.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="e2b5f-193">Ajouter des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="e2b5f-193">Add NuGet packages</span></span>

<span data-ttu-id="e2b5f-194">Ajoutez au projet .NET Core chacun des packages NuGet auxquels le projet .NET Framework fait référence.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="e2b5f-195">Votre application WPF .NET Framework comporte très probablement un fichier **packages.config** contenant la liste de tous les packages NuGet auxquels votre projet fait référence.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="e2b5f-196">Vous pouvez consulter cette liste pour déterminer quels packages NuGet ajouter au projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="e2b5f-197">Par exemple, si le projet .NET Framework fait référence au package NuGet `MahApps.Metro`, ajoutez-le au projet avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="e2b5f-198">Vous pouvez aussi ajouter la référence au package avec l’interface CLI .NET Core à partir du répertoire **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="e2b5f-199">La commande précédente ajoute la référence NuGet suivante au projet **MyWPFCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="e2b5f-200">Problèmes de compilation</span><span class="sxs-lookup"><span data-stu-id="e2b5f-200">Problems compiling</span></span>

<span data-ttu-id="e2b5f-201">Si avez des difficultés à compiler vos projets, c’est peut-être le signe que vous utilisez des API Windows disponibles dans .NET Framework et non dans .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="e2b5f-202">Vous pouvez essayer d’ajouter le package NuGet [Pack de compatibilité Windows][compat-pack] à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="e2b5f-203">Ce package, qui s’exécute seulement sur Windows, ajoute environ 20 000 API Windows aux projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="e2b5f-204">La commande précédente ajoute le code suivant au projet **MyWPFCore.csproj** :</span><span class="sxs-lookup"><span data-stu-id="e2b5f-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="e2b5f-205">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="e2b5f-205">WPF Designer</span></span>

<span data-ttu-id="e2b5f-206">Comme nous l’avons indiqué dans cet article, Visual Studio 2019 ne prend en charge le Concepteur WPF que dans les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-206">As detailed in this article, Visual Studio 2019 only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="e2b5f-207">En créant un projet .NET Core côte à côte, vous pouvez tester votre projet avec .NET Core tout en utilisant le projet .NET Framework pour concevoir des formulaires.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="e2b5f-208">Le fichier de solution comporte à la fois les projets .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="e2b5f-209">Ajoutez et concevez vos formulaires et vos contrôles dans le projet .NET Framework ; à partir des modèles Glob de fichier que nous avons ajoutés aux projets .NET Core, les nouveaux fichiers et les fichiers modifiés sont automatiquement intégrés au projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="e2b5f-210">Dès que Visual Studio 2019 prendra en charge le Concepteur WPF, vous pourrez copier/coller le contenu de votre fichier projet .NET Core dans le fichier projet .NET Framework,</span><span class="sxs-lookup"><span data-stu-id="e2b5f-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="e2b5f-211">puis supprimer les modèles Glob de fichier ajoutés avec les éléments `<Source>` et `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="e2b5f-212">Résolvez le chemin d’accès des références de projet utilisées par votre application.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="e2b5f-213">Le projet .NET Framework est ainsi mis à niveau en un projet .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e2b5f-214">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e2b5f-214">Next steps</span></span>

- <span data-ttu-id="e2b5f-215">Découvrez-en plus sur le [Pack de compatibilité Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="e2b5f-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="e2b5f-216">Regardez une [vidéo sur le portage](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) de projets WPF .NET Framework vers .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b5f-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
