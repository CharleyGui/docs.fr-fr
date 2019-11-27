---
title: Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac
description: Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: feaed88e902080c5c3b07578b78f8437489a690c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428586"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="a7aa7-103">Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="a7aa7-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="a7aa7-104">Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="a7aa7-105">Cette rubrique vous guide lors de la création d’une application console simple à l’aide de Visual Studio pour Mac et de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="a7aa7-106">Vos commentaires sont extrêmement précieux.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-106">Your feedback is highly valued.</span></span> <span data-ttu-id="a7aa7-107">Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="a7aa7-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="a7aa7-108">Dans Visual Studio pour Mac, sélectionnez **Aide** > **Signaler un problème** dans le menu ou **Signaler un problème** sur l’écran d’accueil, ce qui ouvre une fenêtre permettant de soumettre un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="a7aa7-109">Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="a7aa7-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="a7aa7-110">Pour soumettre une suggestion, sélectionnez **Aide** > **Faire une suggestion** dans le menu ou **Faire une suggestion** sur l’écran d’accueil, ce qui vous amène à la [page web de la communauté des développeurs Visual Studio pour Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="a7aa7-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a7aa7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a7aa7-111">Prerequisites</span></span>

<span data-ttu-id="a7aa7-112">Consultez la rubrique [dépendances et exigences de .net Core](../install/dependencies.md?tabs=netcore30&pivots=os-macos) .</span><span class="sxs-lookup"><span data-stu-id="a7aa7-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-macos) topic.</span></span>

<span data-ttu-id="a7aa7-113">Consultez l’article sur la [prise en charge de .net Core](/visualstudio/mac/net-core-support) pour vous assurer que vous utilisez une version prise en charge de .net core.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="a7aa7-114">Prise en main</span><span class="sxs-lookup"><span data-stu-id="a7aa7-114">Get started</span></span>

<span data-ttu-id="a7aa7-115">Si vous avez déjà installé les composants requis et Visual Studio pour Mac, ignorez cette section et passez à la [création d’un projet](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="a7aa7-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="a7aa7-116">Suivez ces étapes pour installer les composants requis et Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="a7aa7-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="a7aa7-117">Téléchargez le [programme d’installation de Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="a7aa7-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="a7aa7-118">Exécutez le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-118">Run the installer.</span></span> <span data-ttu-id="a7aa7-119">Lisez et acceptez le contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-119">Read and accept the license agreement.</span></span> <span data-ttu-id="a7aa7-120">Pendant l’installation, sélectionnez l’option d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="a7aa7-121">Vous avez la possibilité d’installer Xamarin, une technologie de développement d’application mobile multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="a7aa7-122">L’installation de Xamarin et de ses composants associés est facultative pour le développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="a7aa7-123">Pour obtenir une vue d’ensemble du processus d’installation de Visual Studio pour Mac, consultez la [documentation de Visual Studio pour Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="a7aa7-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="a7aa7-124">Une fois l’installation terminée, démarrez l’IDE Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="a7aa7-125">Création d'un projet</span><span class="sxs-lookup"><span data-stu-id="a7aa7-125">Creating a project</span></span>

1. <span data-ttu-id="a7aa7-126">Sélectionnez **Nouveau** dans la fenêtre Démarrer.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-126">Select **New** on the Start Window.</span></span>

   ![Bouton Nouveau sur l’écran Démarrer de Visual Studio pour Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="a7aa7-128">Dans la boîte de dialogue **Nouveau projet**, sélectionnez **App** dans le nœud **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="a7aa7-129">Sélectionnez le modèle **Application console** puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Liste des modèles Nouveau projet](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="a7aa7-131">Si plusieurs versions de .NET Core sont installées, sélectionnez le framework cible pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="a7aa7-132">Tapez « HelloWorld » comme **nom de projet**.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="a7aa7-133">Sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-133">Select **Create**.</span></span>

   ![Boîte de dialogue de configuration de votre nouvelle application console](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="a7aa7-135">Attendez la restauration des dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="a7aa7-136">Le projet comporte un seul fichier C#, *Program.cs*, contenant une classe `Program` avec une méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="a7aa7-137">L’instruction `Console.WriteLine` affichera « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="a7aa7-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="a7aa7-138">dans la console lorsque l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-138">to the console when the app is run.</span></span>

   ![Fenêtre principale avec le fichier Program.cs ouvert](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="a7aa7-140">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="a7aa7-140">Run the application</span></span>

<span data-ttu-id="a7aa7-141">Exécutez l’application en mode débogage à l’aide de ⌘ ↵ (commande + entrée) ou en mode mise en production en utilisant ⌥ ⌘ ↵ (option + commande + entrée).</span><span class="sxs-lookup"><span data-stu-id="a7aa7-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Le volet de sortie de l’application affiche Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="a7aa7-143">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="a7aa7-143">Next step</span></span>

<span data-ttu-id="a7aa7-144">La rubrique [Génération d’une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](using-on-mac-vs-full-solution.md) vous montre comment créer une solution complète .NET Core qui inclut une bibliothèque réutilisable et un test unitaire.</span><span class="sxs-lookup"><span data-stu-id="a7aa7-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
