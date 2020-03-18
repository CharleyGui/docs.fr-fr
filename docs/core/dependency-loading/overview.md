---
title: Chargement de dépendance - .NET Core
description: Aperçu du chargement de dépendance géré et non géré dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416663"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="63845-103">Chargement de dépendance dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="63845-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="63845-104">Chaque application .NET Core a des dépendances.</span><span class="sxs-lookup"><span data-stu-id="63845-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="63845-105">Même l’application simple `hello world` a des dépendances sur des parties des bibliothèques de classe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63845-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="63845-106">Comprendre la logique de chargement par défaut .NET Core peut aider à comprendre et à déboguer les problèmes de déploiement typiques.</span><span class="sxs-lookup"><span data-stu-id="63845-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="63845-107">Dans certaines applications, les dépendances sont déterminées dynamiquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="63845-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="63845-108">Dans ces situations, il est essentiel de comprendre comment les assemblages gérés et les dépendances non gérées sont chargés.</span><span class="sxs-lookup"><span data-stu-id="63845-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="63845-109">Présentation d’AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="63845-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="63845-110">L’API <xref:System.Runtime.Loader.AssemblyLoadContext> est au cœur de la conception de chargement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63845-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="63845-111">[L’article Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) fournit un aperçu conceptuel de la conception.</span><span class="sxs-lookup"><span data-stu-id="63845-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="63845-112">Chargement des détails</span><span class="sxs-lookup"><span data-stu-id="63845-112">Loading details</span></span>

<span data-ttu-id="63845-113">Les détails de l’algorithme de chargement sont brièvement couverts dans plusieurs articles :</span><span class="sxs-lookup"><span data-stu-id="63845-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="63845-114">Algorithme de chargement d’assemblage géré</span><span class="sxs-lookup"><span data-stu-id="63845-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="63845-115">Algorithme de chargement d’assemblage par satellite</span><span class="sxs-lookup"><span data-stu-id="63845-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="63845-116">Algorithme de chargement de bibliothèque non gestion (indigène)</span><span class="sxs-lookup"><span data-stu-id="63845-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="63845-117">Sondage par défaut</span><span class="sxs-lookup"><span data-stu-id="63845-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="63845-118">Créer une application .NET Core avec des plug-ins</span><span class="sxs-lookup"><span data-stu-id="63845-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="63845-119">Le tutoriel [Créer une application .NET Core avec des plugins](../tutorials/creating-app-with-plugin-support.md) décrit comment créer un assemblyLoadContext personnalisé.</span><span class="sxs-lookup"><span data-stu-id="63845-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="63845-120">Il utilise <xref:System.Runtime.Loader.AssemblyDependencyResolver> un pour résoudre les dépendances du plugin.</span><span class="sxs-lookup"><span data-stu-id="63845-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="63845-121">Le tutoriel isole correctement les dépendances du plugin de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="63845-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="63845-122">Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="63845-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="63845-123">Le [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article est un tutoriel étape par étape.</span><span class="sxs-lookup"><span data-stu-id="63845-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="63845-124">Il montre comment charger une application .NET Core, exécuter, puis le décharger.</span><span class="sxs-lookup"><span data-stu-id="63845-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="63845-125">L’article fournit également des conseils de débogage.</span><span class="sxs-lookup"><span data-stu-id="63845-125">The article also provides debugging tips.</span></span>
