---
title: Présentation de C# -vous familiariser avec les outils de développement
description: Cet article constitue une introduction aux outils que vous utiliserez pour développer des applications C# et .NET sur votre ordinateur.
ms.date: 10/23/2018
ms.openlocfilehash: fe39bd5e89bb168316b19c62d6e022e36c58fc2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850755"
---
# <a name="become-familiar-with-the-net-development-tools"></a><span data-ttu-id="8511c-103">Vous familiariser avec les outils de développement .NET</span><span class="sxs-lookup"><span data-stu-id="8511c-103">Become familiar with the .NET development tools</span></span>

<span data-ttu-id="8511c-104">La première étape pour exécuter un tutoriel sur votre ordinateur consiste à configurer un environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="8511c-104">The first step in running a tutorial on your machine is to set up a development environment.</span></span>
<span data-ttu-id="8511c-105">Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="8511c-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

<span data-ttu-id="8511c-106">Vous pouvez aussi installer le [Kit SDK .NET Core](https://dotnet.microsoft.com/download) et [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="8511c-106">Alternatively, you can install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="8511c-107">Flux de développement d’une application de base</span><span class="sxs-lookup"><span data-stu-id="8511c-107">Basic application development flow</span></span>

<span data-ttu-id="8511c-108">Vous créez des applications à l’aide de la commande [`dotnet new`](../../../core/tools/dotnet-new.md).</span><span class="sxs-lookup"><span data-stu-id="8511c-108">You'll create applications using the [`dotnet new`](../../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="8511c-109">Cette commande génère les fichiers et ressources nécessaires pour votre application.</span><span class="sxs-lookup"><span data-stu-id="8511c-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="8511c-110">Les tutoriels de présentation de C# utilisent tous le type d’application `console`.</span><span class="sxs-lookup"><span data-stu-id="8511c-110">The introduction to C# tutorials all use the `console` application type.</span></span> <span data-ttu-id="8511c-111">Une fois que vous avez les bases, vous pouvez développer d’autres types d’applications.</span><span class="sxs-lookup"><span data-stu-id="8511c-111">Once you've got the basics, you can expand to other application types.</span></span>

<span data-ttu-id="8511c-112">Les autres commandes que vous utiliserez sont [`dotnet build`](../../../core/tools/dotnet-build.md) pour générer le fichier exécutable et [`dotnet run`](../../../core/tools/dotnet-run.md) pour exécuter le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="8511c-112">The other commands you'll use are [`dotnet build`](../../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-tutorial"></a><span data-ttu-id="8511c-113">Choisir un tutoriel</span><span class="sxs-lookup"><span data-stu-id="8511c-113">Pick your tutorial</span></span>

<span data-ttu-id="8511c-114">Vous pouvez commencer par l’un des tutoriels suivants :</span><span class="sxs-lookup"><span data-stu-id="8511c-114">You can start with any of the following tutorials:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="8511c-115">Nombres en C#</span><span class="sxs-lookup"><span data-stu-id="8511c-115">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="8511c-116">Dans le tutoriel [Nombres en C#](numbers-in-csharp-local.md), vous allez apprendre comment les ordinateurs stockent les nombres et comment effectuer des calculs avec différents types numériques.</span><span class="sxs-lookup"><span data-stu-id="8511c-116">In the [Numbers in C#](numbers-in-csharp-local.md) tutorial, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="8511c-117">Vous apprendrez les bases de l’arrondi et comment effectuer des calculs mathématiques à l’aide de C#.</span><span class="sxs-lookup"><span data-stu-id="8511c-117">You'll learn the basics of rounding and how to perform mathematical calculations using C#.</span></span>

<span data-ttu-id="8511c-118">Ce tutoriel part du principe que vous avez terminé la leçon [Hello world](hello-world.yml).</span><span class="sxs-lookup"><span data-stu-id="8511c-118">This tutorial assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="8511c-119">Branches et boucles</span><span class="sxs-lookup"><span data-stu-id="8511c-119">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="8511c-120">Le tutoriel [Branches et boucles](branches-and-loops-local.md) explique les bases de la sélection de différents chemins d’exécution de code en fonction des valeurs stockées dans des variables.</span><span class="sxs-lookup"><span data-stu-id="8511c-120">The [Branches and loops](branches-and-loops-local.md) tutorial teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="8511c-121">Vous allez apprendre les principes fondamentaux du flux de contrôle, sur la base duquel les programmes prennent des décisions et choisissent différentes actions.</span><span class="sxs-lookup"><span data-stu-id="8511c-121">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span>

<span data-ttu-id="8511c-122">Ce tutoriel part du principe que vous avez fini les leçons [Hello world](hello-world.yml) et [Nombres en C#](numbers-in-csharp-local.md).</span><span class="sxs-lookup"><span data-stu-id="8511c-122">This tutorial assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="8511c-123">Collection de listes</span><span class="sxs-lookup"><span data-stu-id="8511c-123">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="8511c-124">La leçon [Collection de listes](arrays-and-collections.md) vous présente le type Collection de listes qui stocke les séquences de données.</span><span class="sxs-lookup"><span data-stu-id="8511c-124">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="8511c-125">Vous apprendrez à ajouter et à supprimer des éléments, à rechercher des éléments et à trier des listes.</span><span class="sxs-lookup"><span data-stu-id="8511c-125">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="8511c-126">Vous découvrirez différents types de listes.</span><span class="sxs-lookup"><span data-stu-id="8511c-126">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="8511c-127">Ce tutoriel part du principe que vous avez fini les leçons listées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="8511c-127">This tutorial assumes that you have finished the lessons listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="8511c-128">Présentation des classes</span><span class="sxs-lookup"><span data-stu-id="8511c-128">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="8511c-129">Ce dernier tutoriel de présentation de C#, qui s’exécute sur votre ordinateur, fait appel à votre propre environnement de développement local et à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8511c-129">This final introduction to C# tutorial is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="8511c-130">Vous allez créer une application console et voir les fonctionnalités orientées objet de base qui font partie du langage C#.</span><span class="sxs-lookup"><span data-stu-id="8511c-130">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
