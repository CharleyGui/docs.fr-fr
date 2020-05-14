---
title: Créer une application Hello World avec .NET Core dans Visual Studio
description: Découvrez comment créer votre première application de console .NET Core avec C# ou Visual Basic à l’aide de Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394828"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="ecec1-103">Didacticiel : créer votre première application de console .NET Core dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="ecec1-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="ecec1-104">Cet article fournit une présentation pas à pas de la création et de l’exécution d’une application console Hello World .NET Core dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ecec1-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="ecec1-105">Une application Hello World est traditionnellement utilisée pour introduire des débutants dans un nouveau langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="ecec1-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="ecec1-106">Ce programme affiche simplement l’expression « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="ecec1-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="ecec1-107">à l’écran.</span><span class="sxs-lookup"><span data-stu-id="ecec1-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ecec1-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ecec1-108">Prerequisites</span></span>

- <span data-ttu-id="ecec1-109">[Visual Studio 2019 version 16,4 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="ecec1-110">Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="ecec1-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="ecec1-111">Pour plus d’informations, consultez la section [install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) de l’article [install the kit SDK .net Core](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="ecec1-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="ecec1-112">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="ecec1-112">Create the app</span></span>

<span data-ttu-id="ecec1-113">Les instructions suivantes créent une application console Hello World simple :</span><span class="sxs-lookup"><span data-stu-id="ecec1-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="ecec1-114">C#</span><span class="sxs-lookup"><span data-stu-id="ecec1-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="ecec1-115">Ouvrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ecec1-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="ecec1-116">Créez un nouveau projet d’application console C# .NET Core nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="ecec1-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="ecec1-117">Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-117">On the start window, choose **Create a new project**.</span></span>

      ![Bouton créer un projet sélectionné dans la fenêtre de démarrage de Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="ecec1-119">Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="ecec1-120">Ensuite, choisissez **C#** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="ecec1-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="ecec1-121">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Créer une fenêtre de projet avec les filtres sélectionnés](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="ecec1-123">Si vous ne voyez pas les modèles .NET Core, vous ne disposez probablement pas de la charge de travail requise installée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="ecec1-124">Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="ecec1-125">Le Visual Studio Installer s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="ecec1-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="ecec1-126">Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="ecec1-127">Dans la page **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="ecec1-128">Ensuite, choisissez **créer**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-128">Then, choose **Create**.</span></span>

      ![Configurer votre nouvelle fenêtre de projet avec les champs nom du projet, emplacement et nom de la solution](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="ecec1-130">Le modèle d’application console C# pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de <xref:System.String> comme argument.</span><span class="sxs-lookup"><span data-stu-id="ecec1-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="ecec1-131">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="ecec1-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="ecec1-132">Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.</span><span class="sxs-lookup"><span data-stu-id="ecec1-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="ecec1-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecec1-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="ecec1-135">Ouvrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ecec1-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="ecec1-136">Créez un projet d’application console .NET Core Visual Basic nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="ecec1-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="ecec1-137">Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-137">On the start window, choose **Create a new project**.</span></span>

      ![Bouton créer un projet sélectionné dans la fenêtre de démarrage de Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="ecec1-139">Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="ecec1-140">Ensuite, choisissez **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="ecec1-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="ecec1-141">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Choisir le modèle Visual Basic pour l’application console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="ecec1-143">Si vous ne voyez pas les modèles .NET Core, vous ne disposez probablement pas de la charge de travail requise installée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="ecec1-144">Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="ecec1-145">Le Visual Studio Installer s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="ecec1-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="ecec1-146">Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="ecec1-147">Dans la page **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="ecec1-148">Ensuite, choisissez **créer**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="ecec1-149">Le modèle d’application console pour .NET Core définit automatiquement une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument.</span><span class="sxs-lookup"><span data-stu-id="ecec1-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="ecec1-150">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="ecec1-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="ecec1-151">Les arguments de ligne de commande fournis lorsque l’application est lancée sont disponibles dans le `args` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ecec1-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="ecec1-153">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="ecec1-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="ecec1-154">Il appelle la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="ecec1-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="ecec1-155">dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ecec1-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="ecec1-156">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="ecec1-156">Run the app</span></span>

1. <span data-ttu-id="ecec1-157">Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Barre d’outils Visual Studio avec le bouton Exécuter HelloWorld sélectionné](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="ecec1-159">Une fenêtre de console s’ouvre avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="ecec1-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="ecec1-160">imprimé à l’écran et certaines informations de débogage de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ecec1-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="ecec1-162">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ecec1-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="ecec1-163">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="ecec1-163">Enhance the app</span></span>

<span data-ttu-id="ecec1-164">Améliorez votre application pour inviter l’utilisateur à entrer son nom, et pour l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="ecec1-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="ecec1-165">Les instructions suivantes modifient et réexécutent l’application :</span><span class="sxs-lookup"><span data-stu-id="ecec1-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="ecec1-166">C#</span><span class="sxs-lookup"><span data-stu-id="ecec1-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="ecec1-167">Remplacez le contenu de la `Main` méthode, qui est actuellement simplement la ligne qui appelle `Console.WriteLine` , par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ecec1-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   <span data-ttu-id="ecec1-168">Ce code affiche « What is your name? ».</span><span class="sxs-lookup"><span data-stu-id="ecec1-168">This code displays "What is your name?"</span></span> <span data-ttu-id="ecec1-169">dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="ecec1-170">Il stocke cette chaîne dans une variable nommée `name`.</span><span class="sxs-lookup"><span data-stu-id="ecec1-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="ecec1-171">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="ecec1-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="ecec1-172">Enfin, elle utilise une [chaîne interpolée](../../csharp/language-reference/tokens/interpolated.md) pour afficher ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ecec1-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="ecec1-173">Compilez le programme en choisissant **générer**  >  **générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="ecec1-174">Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="ecec1-175">Répondez à l’invite en entrant un nom et en appuyant sur la touche **entrée** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="ecec1-177">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ecec1-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="ecec1-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecec1-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="ecec1-179">Remplacez le contenu de la `Main` méthode, qui est actuellement simplement la ligne qui appelle `Console.WriteLine` , par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ecec1-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   <span data-ttu-id="ecec1-180">Ce code affiche « What is your name? ».</span><span class="sxs-lookup"><span data-stu-id="ecec1-180">This code displays "What is your name?"</span></span> <span data-ttu-id="ecec1-181">dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée.</span><span class="sxs-lookup"><span data-stu-id="ecec1-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="ecec1-182">Il stocke cette chaîne dans une variable nommée `name`.</span><span class="sxs-lookup"><span data-stu-id="ecec1-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="ecec1-183">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="ecec1-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="ecec1-184">Enfin, elle utilise une [chaîne interpolée](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) pour afficher ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ecec1-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="ecec1-185">Compilez le programme en choisissant **générer**  >  **générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="ecec1-186">Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="ecec1-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="ecec1-187">Répondez à l’invite en entrant un nom et en appuyant sur la touche **entrée** .</span><span class="sxs-lookup"><span data-stu-id="ecec1-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="ecec1-189">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="ecec1-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="ecec1-190">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ecec1-190">Next steps</span></span>

<span data-ttu-id="ecec1-191">Dans cet article, vous avez créé et exécuté votre première application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ecec1-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="ecec1-192">À l’étape suivante, vous allez déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="ecec1-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ecec1-193">Déboguer une application Hello World .NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ecec1-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
