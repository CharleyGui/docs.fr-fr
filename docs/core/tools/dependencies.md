---
title: Gérer les dépendances dans les outils .NET Core
description: Explique comment gérer les dépendances avec les outils .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 9c088829ce3d5197198b7ff22a1331b8baba41d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714209"
---
# <a name="managing-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="fb3c9-103">Gestion des dépendances avec le SDK .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="fb3c9-103">Managing dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="fb3c9-104">Le passage des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier projet et des ressources permettant le suivi des dépendances.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="fb3c9-105">Pour les projets .NET Core, cela est similaire à ce que project.json faisait.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-105">For .NET Core projects this is similar to what project.json did.</span></span> <span data-ttu-id="fb3c9-106">Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="fb3c9-107">Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span> 

<span data-ttu-id="fb3c9-108">Ce document décrit le nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-108">This document describes the new reference type.</span></span> <span data-ttu-id="fb3c9-109">Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-109">It also shows how to add a package dependency using this new reference type to your project.</span></span> 

## <a name="the-new-packagereference-element"></a><span data-ttu-id="fb3c9-110">Nouvel élément \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="fb3c9-110">The new \<PackageReference> element</span></span>
<span data-ttu-id="fb3c9-111">`<PackageReference>` présente la structure de base suivante :</span><span class="sxs-lookup"><span data-stu-id="fb3c9-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="fb3c9-112">Si vous êtes familiarisé avec MSBuild, il est similaire aux autres types de référence existants.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="fb3c9-113">La partie essentielle est l’instruction `Include` qui spécifie l’ID de package que vous souhaitez ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-113">The key is the `Include` statement which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="fb3c9-114">L’élément enfant `<Version>` spécifie la version à obtenir.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="fb3c9-115">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="fb3c9-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="fb3c9-116">Si vous n’êtes pas familiarisé avec la syntaxe `csproj` générale, consultez la documentation de [référence sur les projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>  

<span data-ttu-id="fb3c9-117">L’ajout d’une dépendance qui n’est disponible que dans une cible spécifique s’effectue à l’aide de conditions décrites dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="fb3c9-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="fb3c9-118">D’après le code ci-dessus, la dépendance n’est valide que si la génération se produit pour la cible donnée.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="fb3c9-119">Dans la condition, `$(TargetFramework)` est une propriété MSBuild définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-119">The `$(TargetFramework)` in the condition is a MSBuild property that is being set in the project.</span></span> <span data-ttu-id="fb3c9-120">Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-120">For most common .NET Core applications, you will not need to do this.</span></span> 

## <a name="adding-a-dependency-to-your-project"></a><span data-ttu-id="fb3c9-121">Ajout d’une dépendance à votre projet</span><span class="sxs-lookup"><span data-stu-id="fb3c9-121">Adding a dependency to your project</span></span>
<span data-ttu-id="fb3c9-122">Ajouter une dépendance à votre projet est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="fb3c9-123">Voici un exemple montrant comment ajouter la version `9.0.1` de Json.NET à votre projet.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="fb3c9-124">Bien entendu, cela vaut également pour toute autre dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-124">Of course, it is applicable to any other NuGet dependency.</span></span> 

<span data-ttu-id="fb3c9-125">Quand vous ouvrez votre fichier projet, vous voyez au moins deux nœuds `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="fb3c9-126">L’un de ces nœuds contient déjà des éléments `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="fb3c9-127">Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un ; quel que soit votre choix, le résultat est le même.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-127">You can add your new dependency to this node, or create a new one; it is completely up to you as the result will be the same.</span></span> 

<span data-ttu-id="fb3c9-128">Dans cet exemple, nous allons utiliser le modèle par défaut qui est déposé par `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-128">In this example we will use the default template that is dropped by `dotnet new console`.</span></span> <span data-ttu-id="fb3c9-129">Il s’agit d’une application console simple.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-129">This is a simple console application.</span></span> <span data-ttu-id="fb3c9-130">Quand nous ouvrons le projet, nous trouvons `<ItemGroup>`, qui contient déjà `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-130">When we open up the project, we first find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="fb3c9-131">Nous y ajoutons le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fb3c9-131">We then add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="fb3c9-132">Ensuite, nous enregistrons le projet et exécutons la commande `dotnet restore` pour installer la dépendance.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-132">After this, we save the project and run the `dotnet restore` command to install the dependency.</span></span> 

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="fb3c9-133">Le projet complet ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="fb3c9-133">The full project looks like this:</span></span>

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

## <a name="removing-a-dependency-from-the-project"></a><span data-ttu-id="fb3c9-134">Suppression d’une dépendance du projet</span><span class="sxs-lookup"><span data-stu-id="fb3c9-134">Removing a dependency from the project</span></span>
<span data-ttu-id="fb3c9-135">Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="fb3c9-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
