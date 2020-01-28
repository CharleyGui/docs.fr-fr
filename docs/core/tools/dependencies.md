---
title: Gérer les dépendances dans les outils .NET Core
description: Explique comment gérer les dépendances avec les outils .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: e14fa42534d807e2a0fcce1dabe747c18c5166b7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733377"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="7b85a-103">Gestion des dépendances avec le SDK .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="7b85a-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="7b85a-104">Le passage des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier projet et des ressources permettant le suivi des dépendances.</span><span class="sxs-lookup"><span data-stu-id="7b85a-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="7b85a-105">Pour les projets .NET Core, cela est similaire à ce que project.json faisait.</span><span class="sxs-lookup"><span data-stu-id="7b85a-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="7b85a-106">Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet.</span><span class="sxs-lookup"><span data-stu-id="7b85a-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="7b85a-107">Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="7b85a-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="7b85a-108">Ce document décrit le nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="7b85a-108">This document describes the new reference type.</span></span> <span data-ttu-id="7b85a-109">Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="7b85a-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="7b85a-110">Nouvel élément \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="7b85a-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="7b85a-111">`<PackageReference>` présente la structure de base suivante :</span><span class="sxs-lookup"><span data-stu-id="7b85a-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="7b85a-112">Si vous êtes familiarisé avec MSBuild, il est similaire aux autres types de référence existants.</span><span class="sxs-lookup"><span data-stu-id="7b85a-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="7b85a-113">La partie essentielle est l’instruction `Include` qui spécifie l’ID de package que vous souhaitez ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="7b85a-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="7b85a-114">L’élément enfant `<Version>` spécifie la version à obtenir.</span><span class="sxs-lookup"><span data-stu-id="7b85a-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="7b85a-115">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="7b85a-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="7b85a-116">Si vous n’êtes pas familiarisé avec la syntaxe `csproj` générale, consultez la documentation de [référence sur les projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="7b85a-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="7b85a-117">L’ajout d’une dépendance qui n’est disponible que dans une cible spécifique s’effectue à l’aide de conditions décrites dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7b85a-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="7b85a-118">D’après le code ci-dessus, la dépendance n’est valide que si la génération se produit pour la cible donnée.</span><span class="sxs-lookup"><span data-stu-id="7b85a-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="7b85a-119">La `$(TargetFramework)` dans la condition est une propriété MSBuild qui est définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="7b85a-119">The `$(TargetFramework)` in the condition is an MSBuild property that is being set in the project.</span></span> <span data-ttu-id="7b85a-120">Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7b85a-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="7b85a-121">Ajout d’une dépendance à votre projet</span><span class="sxs-lookup"><span data-stu-id="7b85a-121">Adding a dependency to your project</span></span>
<span data-ttu-id="7b85a-122">Ajouter une dépendance à votre projet est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="7b85a-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="7b85a-123">Voici un exemple montrant comment ajouter la version `9.0.1` de Json.NET à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7b85a-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="7b85a-124">Bien entendu, cela vaut également pour toute autre dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="7b85a-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="7b85a-125">Quand vous ouvrez votre fichier projet, vous voyez au moins deux nœuds `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="7b85a-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="7b85a-126">L’un de ces nœuds contient déjà des éléments `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="7b85a-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="7b85a-127">Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un ; quel que soit votre choix, le résultat est le même.</span><span class="sxs-lookup"><span data-stu-id="7b85a-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="7b85a-128">Dans cet exemple, nous allons utiliser le modèle par défaut qui est déposé par `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="7b85a-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="7b85a-129">Il s’agit d’une application console simple.</span><span class="sxs-lookup"><span data-stu-id="7b85a-129">This is a simple console application.</span></span> <span data-ttu-id="7b85a-130">Quand nous ouvrons le projet, nous trouvons `<ItemGroup>`, qui contient déjà `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="7b85a-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="7b85a-131">Nous y ajoutons le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7b85a-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="7b85a-132">Ensuite, nous enregistrons le projet et exécutons la commande `dotnet restore` pour installer la dépendance.</span><span class="sxs-lookup"><span data-stu-id="7b85a-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="7b85a-133">Le projet complet ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="7b85a-133">The full project looks like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="7b85a-134">Suppression d’une dépendance du projet</span><span class="sxs-lookup"><span data-stu-id="7b85a-134">Removing a dependency from the project</span></span>
<span data-ttu-id="7b85a-135">Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="7b85a-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
