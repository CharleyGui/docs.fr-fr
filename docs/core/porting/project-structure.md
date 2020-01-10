---
title: Organiser des projets pour .NET Framework et .NET Core
description: Aide destinée aux propriétaires de projet qui souhaitent compiler leur solution côte à côte pour le .NET Framework et .NET Core.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777332"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="58d0e-103">Organiser votre projet pour prendre en charge à la fois le .NET Framework et .NET Core</span><span class="sxs-lookup"><span data-stu-id="58d0e-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="58d0e-104">Vous pouvez créer une solution compilée pour .NET Framework et .NET Core côte à côte.</span><span class="sxs-lookup"><span data-stu-id="58d0e-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="58d0e-105">Cet article aborde plusieurs options d’organisation de projets pour vous aider à atteindre cet objectif.</span><span class="sxs-lookup"><span data-stu-id="58d0e-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="58d0e-106">Voici quelques scénarios classiques à prendre en compte lorsque vous décidez comment configurer la disposition de votre projet avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="58d0e-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="58d0e-107">La liste peut ne pas couvrir tout ce que vous souhaitez : établissez vos priorités en fonction des besoins de votre projet.</span><span class="sxs-lookup"><span data-stu-id="58d0e-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="58d0e-108">**Combiner des projets existants et des projets .NET Core pour en faire des projets uniques**</span><span class="sxs-lookup"><span data-stu-id="58d0e-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="58d0e-109">*En voici les avantages :*</span><span class="sxs-lookup"><span data-stu-id="58d0e-109">*What this is good for:*</span></span>
  - <span data-ttu-id="58d0e-110">Simplifie votre processus de génération en compilant un projet unique plutôt que plusieurs projets qui ciblent chacun une version ou une plateforme .NET Framework différente.</span><span class="sxs-lookup"><span data-stu-id="58d0e-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="58d0e-111">Simplifie la gestion des fichiers sources pour les projets multi-ciblés, car vous devez gérer un seul fichier projet.</span><span class="sxs-lookup"><span data-stu-id="58d0e-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="58d0e-112">Lors de l’ajout ou de la suppression de fichiers sources, les alternatives vous obligent à les synchroniser manuellement avec d’autres projets.</span><span class="sxs-lookup"><span data-stu-id="58d0e-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="58d0e-113">Générez facilement un package NuGet à des fins de consommation.</span><span class="sxs-lookup"><span data-stu-id="58d0e-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="58d0e-114">Vous permet d’écrire du code pour une version spécifique du .NET Framework dans vos bibliothèques via l’utilisation de directives de compilation.</span><span class="sxs-lookup"><span data-stu-id="58d0e-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="58d0e-115">*Scénarios non pris en charge :*</span><span class="sxs-lookup"><span data-stu-id="58d0e-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="58d0e-116">Requiert que les développeurs utilisent Visual Studio 2017 ou une version ultérieure pour ouvrir des projets existants.</span><span class="sxs-lookup"><span data-stu-id="58d0e-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="58d0e-117">Pour prendre en charge les versions antérieures de Visual Studio, [conserver vos fichiers projet dans des dossiers différents](#support-vs) est une meilleure option.</span><span class="sxs-lookup"><span data-stu-id="58d0e-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="58d0e-118">[**Séparer les projets existants des nouveaux projets .NET Core**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="58d0e-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="58d0e-119">*En voici les avantages :*</span><span class="sxs-lookup"><span data-stu-id="58d0e-119">*What this is good for:*</span></span>
  - <span data-ttu-id="58d0e-120">Prend en charge le développement sur des projets existants pour les développeurs et les contributeurs qui ne disposent pas de Visual Studio 2017 ou d’une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="58d0e-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="58d0e-121">Réduit la possibilité de créer des bogues dans des projets existants car aucune évolution du code n’est requise dans ces projets.</span><span class="sxs-lookup"><span data-stu-id="58d0e-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="58d0e-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="58d0e-122">Example</span></span>

<span data-ttu-id="58d0e-123">Considérez le dépôt ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="58d0e-123">Consider the repository below:</span></span>

![Projet existant](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="58d0e-125">**Code source**</span><span class="sxs-lookup"><span data-stu-id="58d0e-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="58d0e-126">La section suivante décrit plusieurs méthodes pour ajouter la prise en charge de .NET Core pour ce dépôt en fonction des contraintes et de la complexité des projets existants.</span><span class="sxs-lookup"><span data-stu-id="58d0e-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="58d0e-127">Remplacer les projets existants par un projet .NET Core multiciblé</span><span class="sxs-lookup"><span data-stu-id="58d0e-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="58d0e-128">Réorganisez le dépôt de sorte que tous les fichiers *\*.csproj* existants soient supprimés et qu’un seul fichier *\*.csproj* ciblant plusieurs frameworks soit créé.</span><span class="sxs-lookup"><span data-stu-id="58d0e-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="58d0e-129">Il s’agit d’une option intéressante, car un seul projet peut être compilé pour différents frameworks.</span><span class="sxs-lookup"><span data-stu-id="58d0e-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="58d0e-130">Elle permet également de gérer différentes options de compilation et dépendances par framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="58d0e-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Créer un csproj ciblant plusieurs frameworks](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="58d0e-132">**Code source**</span><span class="sxs-lookup"><span data-stu-id="58d0e-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="58d0e-133">Les modifications à noter sont :</span><span class="sxs-lookup"><span data-stu-id="58d0e-133">Changes to note are:</span></span>

- <span data-ttu-id="58d0e-134">Remplacement de *packages.config* et de *\*.csproj* par un nouveau [.csproj *\*.NET Core*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="58d0e-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="58d0e-135">Les packages NuGet sont spécifiés avec `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="58d0e-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="58d0e-136">Conserver les projets existants et créer un projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="58d0e-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="58d0e-137">Si des projets existants ciblent des frameworks plus anciens, vous pouvez laisser ces projets inchangés et utiliser un projet .NET Core pour cibler les futurs frameworks.</span><span class="sxs-lookup"><span data-stu-id="58d0e-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Projet .NET Core avec un projet existant dans un dossier différent](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="58d0e-139">**Code source**</span><span class="sxs-lookup"><span data-stu-id="58d0e-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="58d0e-140">Le projet .NET Core et les projets existants sont conservés dans des dossiers distincts.</span><span class="sxs-lookup"><span data-stu-id="58d0e-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="58d0e-141">Si vous conservez des projets dans des dossiers distincts, vous n’avez pas besoin de disposer de Visual Studio 2017 ou d’une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="58d0e-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="58d0e-142">Vous pouvez créer une solution distincte qui ouvre seulement les anciens projets.</span><span class="sxs-lookup"><span data-stu-id="58d0e-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="58d0e-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58d0e-143">See also</span></span>

- [<span data-ttu-id="58d0e-144">Documentation sur le portage .NET Core</span><span class="sxs-lookup"><span data-stu-id="58d0e-144">.NET Core porting documentation</span></span>](index.md)
