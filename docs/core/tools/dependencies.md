---
title: Gérer les dépendances dans les outils .NET Core
description: Explique comment gérer les dépendances avec les outils .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 28280dc05e746cdef4e90870cd4cb528382c45bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787863"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a><span data-ttu-id="15875-103">Gérer les dépendances avec kit SDK .NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="15875-103">Manage dependencies with .NET Core SDK 1.0</span></span>

<span data-ttu-id="15875-104">Le passage des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier projet et des ressources permettant le suivi des dépendances.</span><span class="sxs-lookup"><span data-stu-id="15875-104">With the move of .NET Core projects from project.json to csproj and MSBuild, a significant investment also happened that resulted in unification of the project file and assets that allow tracking of dependencies.</span></span> <span data-ttu-id="15875-105">Pour les projets .NET Core, cela est similaire à ce que fait Project. JSON.</span><span class="sxs-lookup"><span data-stu-id="15875-105">For .NET Core projects, this is similar to what project.json did.</span></span> <span data-ttu-id="15875-106">Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet.</span><span class="sxs-lookup"><span data-stu-id="15875-106">There is no separate JSON or XML file that tracks NuGet dependencies.</span></span> <span data-ttu-id="15875-107">Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="15875-107">With this change, we've also introduced another type of *reference* into the csproj syntax called the `<PackageReference>`.</span></span>

<span data-ttu-id="15875-108">Ce document décrit le nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="15875-108">This document describes the new reference type.</span></span> <span data-ttu-id="15875-109">Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence.</span><span class="sxs-lookup"><span data-stu-id="15875-109">It also shows how to add a package dependency using this new reference type to your project.</span></span>

## <a name="the-new-packagereference-element"></a><span data-ttu-id="15875-110">Nouvel élément \<PackageReference></span><span class="sxs-lookup"><span data-stu-id="15875-110">The new \<PackageReference> element</span></span>

<span data-ttu-id="15875-111">`<PackageReference>` présente la structure de base suivante :</span><span class="sxs-lookup"><span data-stu-id="15875-111">The `<PackageReference>` has the following basic structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="15875-112">Si vous êtes familiarisé avec MSBuild, il est similaire aux autres types de référence existants.</span><span class="sxs-lookup"><span data-stu-id="15875-112">If you are familiar with MSBuild, it will look familiar to the other reference types that already exist.</span></span> <span data-ttu-id="15875-113">La clé est l’instruction `Include`, qui spécifie l’ID de package que vous souhaitez ajouter au projet.</span><span class="sxs-lookup"><span data-stu-id="15875-113">The key is the `Include` statement, which specifies the package id that you wish to add to the project.</span></span> <span data-ttu-id="15875-114">L’élément enfant `<Version>` spécifie la version à obtenir.</span><span class="sxs-lookup"><span data-stu-id="15875-114">The `<Version>` child element specifies the version to get.</span></span> <span data-ttu-id="15875-115">Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="15875-115">The versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="15875-116">Si vous n’êtes pas familiarisé avec la syntaxe `csproj` générale, consultez la documentation de [référence sur les projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="15875-116">If you are not familiar with the overall `csproj` syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="15875-117">L’ajout d’une dépendance qui n’est disponible que dans une cible spécifique s’effectue à l’aide de conditions décrites dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="15875-117">Adding a dependency that is available only in a specific target is done using conditions like in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="15875-118">D’après le code ci-dessus, la dépendance n’est valide que si la génération se produit pour la cible donnée.</span><span class="sxs-lookup"><span data-stu-id="15875-118">The above means that the dependency will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="15875-119">La `$(TargetFramework)` dans la condition est une propriété MSBuild qui est définie dans le projet.</span><span class="sxs-lookup"><span data-stu-id="15875-119">The `$(TargetFramework)` in the condition is an MSBuild property that is being set in the project.</span></span> <span data-ttu-id="15875-120">Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="15875-120">For most common .NET Core applications, you will not need to do this.</span></span>

## <a name="add-a-dependency-to-the-project"></a><span data-ttu-id="15875-121">Ajouter une dépendance au projet</span><span class="sxs-lookup"><span data-stu-id="15875-121">Add a dependency to the project</span></span>

<span data-ttu-id="15875-122">Ajouter une dépendance à votre projet est une opération simple.</span><span class="sxs-lookup"><span data-stu-id="15875-122">Adding a dependency to your project is straightforward.</span></span> <span data-ttu-id="15875-123">Voici un exemple montrant comment ajouter la version `9.0.1` de Json.NET à votre projet.</span><span class="sxs-lookup"><span data-stu-id="15875-123">Here is an example of how to add Json.NET version `9.0.1` to your project.</span></span> <span data-ttu-id="15875-124">Bien entendu, cela vaut également pour toute autre dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="15875-124">Of course, it is applicable to any other NuGet dependency.</span></span>

<span data-ttu-id="15875-125">Quand vous ouvrez votre fichier projet, vous voyez au moins deux nœuds `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="15875-125">When you open your project file, you will see two or more `<ItemGroup>` nodes.</span></span> <span data-ttu-id="15875-126">L’un de ces nœuds contient déjà des éléments `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="15875-126">You will notice that one of the nodes already has `<PackageReference>` elements in it.</span></span> <span data-ttu-id="15875-127">Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un nouveau. C’est à vous, car le résultat sera le même.</span><span class="sxs-lookup"><span data-stu-id="15875-127">You can add your new dependency to this node, or create a new one; it is up to you, as the result will be the same.</span></span>

<span data-ttu-id="15875-128">L’exemple suivant utilise le modèle par défaut qui est supprimé par `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="15875-128">The following example uses the default template that's dropped by `dotnet new console`.</span></span> <span data-ttu-id="15875-129">Il s’agit d’une application console simple.</span><span class="sxs-lookup"><span data-stu-id="15875-129">This is a simple console application.</span></span> <span data-ttu-id="15875-130">Lorsque vous ouvrez le projet, vous trouverez le `<ItemGroup>` avec des `<PackageReference>` déjà existants.</span><span class="sxs-lookup"><span data-stu-id="15875-130">When you open up the project, you'll find the `<ItemGroup>` with already existing `<PackageReference>` in it.</span></span> <span data-ttu-id="15875-131">Ajoutez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="15875-131">Add the following to it:</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

<span data-ttu-id="15875-132">Après cela, enregistrez le projet et exécutez la commande `dotnet restore` pour installer la dépendance.</span><span class="sxs-lookup"><span data-stu-id="15875-132">After this, save the project and run the `dotnet restore` command to install the dependency.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="15875-133">Le projet complet ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="15875-133">The full project looks like this:</span></span>

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

## <a name="remove-a-dependency-from-the-project"></a><span data-ttu-id="15875-134">Supprimer une dépendance du projet</span><span class="sxs-lookup"><span data-stu-id="15875-134">Remove a dependency from the project</span></span>

<span data-ttu-id="15875-135">Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="15875-135">Removing a dependency from the project file involves simply removing the `<PackageReference>` from the project file.</span></span>
