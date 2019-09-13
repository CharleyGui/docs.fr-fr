---
title: Chargement des dépendances-.NET Core
description: Vue d’ensemble du chargement des dépendances managées et non managées dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 0388bd1fa29ce1caad93c917503dac9eed8974e1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926396"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="bca2c-103">Chargement des dépendances dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="bca2c-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="bca2c-104">Chaque application .NET Core a des dépendances.</span><span class="sxs-lookup"><span data-stu-id="bca2c-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="bca2c-105">Même l’application `hello world` simple a des dépendances sur des parties des bibliothèques de classes .net core.</span><span class="sxs-lookup"><span data-stu-id="bca2c-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="bca2c-106">La compréhension de la logique de chargement d’assembly .NET Core par défaut peut aider à comprendre et à déboguer les problèmes de déploiement classiques.</span><span class="sxs-lookup"><span data-stu-id="bca2c-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="bca2c-107">Dans certaines applications, les dépendances sont déterminées dynamiquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bca2c-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="bca2c-108">Dans ces situations, il est essentiel de comprendre comment les assemblys managés et les dépendances non managées sont chargés.</span><span class="sxs-lookup"><span data-stu-id="bca2c-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="bca2c-109">Présentation d’AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="bca2c-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="bca2c-110">L' <xref:System.Runtime.Loader.AssemblyLoadContext> API est essentielle à la conception du chargement .net core.</span><span class="sxs-lookup"><span data-stu-id="bca2c-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="bca2c-111">L’article [Présentation de AssemblyLoadContext](understanding-assemblyloadcontext.md) fournit une vue d’ensemble conceptuelle de la conception.</span><span class="sxs-lookup"><span data-stu-id="bca2c-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="bca2c-112">Chargement des détails</span><span class="sxs-lookup"><span data-stu-id="bca2c-112">Loading details</span></span>

<span data-ttu-id="bca2c-113">Les détails de l’algorithme de chargement sont présentés brièvement dans plusieurs articles :</span><span class="sxs-lookup"><span data-stu-id="bca2c-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="bca2c-114">Algorithme de chargement d’assembly managé</span><span class="sxs-lookup"><span data-stu-id="bca2c-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="bca2c-115">Algorithme de chargement d’assembly satellite</span><span class="sxs-lookup"><span data-stu-id="bca2c-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="bca2c-116">Algorithme de chargement de bibliothèque non managée (natif)</span><span class="sxs-lookup"><span data-stu-id="bca2c-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="bca2c-117">Détection par défaut</span><span class="sxs-lookup"><span data-stu-id="bca2c-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="bca2c-118">Créer une application .NET Core avec des plug-ins</span><span class="sxs-lookup"><span data-stu-id="bca2c-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="bca2c-119">Le didacticiel [créer une application .net core avec des plug-ins](../tutorials/creating-app-with-plugin-support.md) décrit comment créer un AssemblyLoadContext personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bca2c-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="bca2c-120">Il utilise un <xref:System.Runtime.Loader.AssemblyDependencyResolver> pour résoudre les dépendances du plug-in.</span><span class="sxs-lookup"><span data-stu-id="bca2c-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="bca2c-121">Le didacticiel isole correctement les dépendances du plug-in à partir de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="bca2c-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="bca2c-122">Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="bca2c-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="bca2c-123">L’article [comment utiliser et déboguer l’assembly dans .net Core](../../standard/assembly/unloadability-howto.md) est un didacticiel pas à pas.</span><span class="sxs-lookup"><span data-stu-id="bca2c-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability-howto.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="bca2c-124">Il montre comment charger une application .NET Core, l’exécuter, puis la décharger.</span><span class="sxs-lookup"><span data-stu-id="bca2c-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="bca2c-125">L’article fournit également des conseils de débogage.</span><span class="sxs-lookup"><span data-stu-id="bca2c-125">The article also provides debugging tips.</span></span>
