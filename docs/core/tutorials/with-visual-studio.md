---
title: Créez une application Hello World avec .NET Core dans Visual Studio
description: Apprenez à créer votre première application de console .NET Core avec C ou Visual Basic à l’aide de Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713997"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="e927c-103">Tutorial: Créer votre première application de console .NET Core dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e927c-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="e927c-104">Cet article fournit une introduction étape par étape pour créer et exécuter une application de console Hello World .NET Core dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e927c-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="e927c-105">Une application Hello World est traditionnellement utilisée pour initier les débutants à un nouveau langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="e927c-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="e927c-106">Ce programme affiche simplement l’expression "Bonjour monde!"</span><span class="sxs-lookup"><span data-stu-id="e927c-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="e927c-107">à l’écran.</span><span class="sxs-lookup"><span data-stu-id="e927c-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e927c-108">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="e927c-108">Prerequisites</span></span>

- <span data-ttu-id="e927c-109">[Visual Studio 2019 version 16.4 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail de développement **multiplateforme .NET Core** installé.</span><span class="sxs-lookup"><span data-stu-id="e927c-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="e927c-110">.NET Core 3.1 SDK est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="e927c-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="e927c-111">Pour plus d’informations, voir la section [Installer avec Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) sur [l’installation de l’article .NET Core SDK.](../install/sdk.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="e927c-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="e927c-112">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="e927c-112">Create the app</span></span>

<span data-ttu-id="e927c-113">Les instructions suivantes créent une simple application de console Hello World :</span><span class="sxs-lookup"><span data-stu-id="e927c-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="e927c-114">C #</span><span class="sxs-lookup"><span data-stu-id="e927c-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e927c-115">Ouvrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e927c-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="e927c-116">Créez un nouveau projet d’application de console c.NET Core nommé "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="e927c-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="e927c-117">Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="e927c-117">On the start window, choose **Create a new project**.</span></span>

      ![Créez un nouveau bouton de projet sélectionné sur la fenêtre de démarrage visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="e927c-119">Sur la **page Créer un nouveau projet,** entrez la **console** dans la boîte de recherche.</span><span class="sxs-lookup"><span data-stu-id="e927c-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e927c-120">Ensuite, choisissez **C dans** la liste linguistique, puis choisissez toutes **les plates-formes** de la liste de la plate-forme.</span><span class="sxs-lookup"><span data-stu-id="e927c-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e927c-121">Choisissez le modèle **Console App (.NET Core),** puis choisissez **Next**.</span><span class="sxs-lookup"><span data-stu-id="e927c-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Créer une nouvelle fenêtre de projet avec des filtres sélectionnés](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="e927c-123">Si vous ne voyez pas les modèles .NET Core, vous manquez probablement la charge de travail requise installée.</span><span class="sxs-lookup"><span data-stu-id="e927c-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="e927c-124">Sous le **message Ne pas trouver ce que vous recherchez?** message, choisissez l’installation plus **d’outils et de fonctionnalités** lien.</span><span class="sxs-lookup"><span data-stu-id="e927c-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e927c-125">L’installateur Visual Studio ouvre ses portes.</span><span class="sxs-lookup"><span data-stu-id="e927c-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e927c-126">Assurez-vous d’avoir installé la charge de travail **de développement multiplateforme .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="e927c-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="e927c-127">Sur la configuration de votre nouvelle page **de projet,** entrez **HelloWorld** dans la boîte **de nom du projet.**</span><span class="sxs-lookup"><span data-stu-id="e927c-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e927c-128">Ensuite, choisissez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="e927c-128">Then, choose **Create**.</span></span>

      ![Configurez votre nouvelle fenêtre de projet avec le nom, l’emplacement et les champs de noms de solution du projet](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="e927c-130">Le modèle d’application console C# pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de <xref:System.String> comme argument.</span><span class="sxs-lookup"><span data-stu-id="e927c-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="e927c-131">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="e927c-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e927c-132">Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.</span><span class="sxs-lookup"><span data-stu-id="e927c-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="e927c-134">Base visuelle</span><span class="sxs-lookup"><span data-stu-id="e927c-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e927c-135">Ouvrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e927c-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="e927c-136">Créez un nouveau projet d’application de console Visual Basic .NET Core nommé "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="e927c-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="e927c-137">Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="e927c-137">On the start window, choose **Create a new project**.</span></span>

      ![Créez un nouveau bouton de projet sélectionné sur la fenêtre de démarrage visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="e927c-139">Sur la **page Créer un nouveau projet,** entrez la **console** dans la boîte de recherche.</span><span class="sxs-lookup"><span data-stu-id="e927c-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e927c-140">Ensuite, choisissez **Visual Basic** dans la liste de langue, puis choisissez toutes **les plates-formes** de la liste de la plate-forme.</span><span class="sxs-lookup"><span data-stu-id="e927c-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e927c-141">Choisissez le modèle **Console App (.NET Core),** puis choisissez **Next**.</span><span class="sxs-lookup"><span data-stu-id="e927c-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Choisir le modèle Visual Basic pour l’application console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="e927c-143">Si vous ne voyez pas les modèles .NET Core, vous manquez probablement la charge de travail requise installée.</span><span class="sxs-lookup"><span data-stu-id="e927c-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="e927c-144">Sous le **message Ne pas trouver ce que vous recherchez?** message, choisissez l’installation plus **d’outils et de fonctionnalités** lien.</span><span class="sxs-lookup"><span data-stu-id="e927c-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="e927c-145">L’installateur Visual Studio ouvre ses portes.</span><span class="sxs-lookup"><span data-stu-id="e927c-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="e927c-146">Assurez-vous d’avoir installé la charge de travail **de développement multiplateforme .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="e927c-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="e927c-147">Sur la configuration de votre nouvelle page **de projet,** entrez **HelloWorld** dans la boîte **de nom du projet.**</span><span class="sxs-lookup"><span data-stu-id="e927c-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="e927c-148">Ensuite, choisissez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="e927c-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="e927c-149">Le modèle d’application console pour .NET `Program`Core définit automatiquement `Main`une classe, , avec une seule méthode, , qui prend un <xref:System.String> tableau comme un argument.</span><span class="sxs-lookup"><span data-stu-id="e927c-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="e927c-150">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="e927c-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="e927c-151">Tous les arguments de ligne de commande fournis `args` lors du lancement de l’application sont disponibles dans le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e927c-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="e927c-153">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="e927c-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="e927c-154">Il appelle la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="e927c-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="e927c-155">dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="e927c-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="e927c-156">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="e927c-156">Run the app</span></span>

1. <span data-ttu-id="e927c-157">Pour exécuter le programme, choisissez **HelloWorld** sur la barre d’outils, ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="e927c-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Barre d’outils Visual Studio avec le bouton HelloWorld run sélectionné](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="e927c-159">Une fenêtre console s’ouvre sur le texte "Bonjour monde!"</span><span class="sxs-lookup"><span data-stu-id="e927c-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="e927c-160">imprimés à l’écran et quelques informations de débbug Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e927c-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="e927c-162">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="e927c-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="e927c-163">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="e927c-163">Enhance the app</span></span>

<span data-ttu-id="e927c-164">Améliorez votre application pour inviter l’utilisateur à entrer son nom, et pour l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="e927c-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="e927c-165">Les instructions suivantes modifient et exécutent à nouveau l’application :</span><span class="sxs-lookup"><span data-stu-id="e927c-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="e927c-166">C #</span><span class="sxs-lookup"><span data-stu-id="e927c-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e927c-167">Remplacer le contenu `Main` de la méthode, qui `Console.WriteLine`est actuellement juste la ligne qui appelle , avec le code suivant:</span><span class="sxs-lookup"><span data-stu-id="e927c-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="e927c-168">Ce code affiche « What is your name? ».</span><span class="sxs-lookup"><span data-stu-id="e927c-168">This code displays "What is your name?"</span></span> <span data-ttu-id="e927c-169">dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée.</span><span class="sxs-lookup"><span data-stu-id="e927c-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="e927c-170">Il stocke cette chaîne dans une variable nommée `name`.</span><span class="sxs-lookup"><span data-stu-id="e927c-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="e927c-171">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="e927c-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e927c-172">Enfin, elle utilise une [chaîne interpolée](../../csharp/language-reference/tokens/interpolated.md) pour afficher ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="e927c-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="e927c-173">Compilez le programme en choisissant **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="e927c-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="e927c-174">Pour exécuter le programme, choisissez **HelloWorld** sur la barre d’outils, ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="e927c-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="e927c-175">Répondez à l’invite en entrant un nom et en appuyant sur la clé **Enter.**</span><span class="sxs-lookup"><span data-stu-id="e927c-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="e927c-177">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="e927c-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="e927c-178">Base visuelle</span><span class="sxs-lookup"><span data-stu-id="e927c-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e927c-179">Remplacer le contenu `Main` de la méthode, qui `Console.WriteLine`est actuellement juste la ligne qui appelle , avec le code suivant:</span><span class="sxs-lookup"><span data-stu-id="e927c-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="e927c-180">Ce code affiche « What is your name? ».</span><span class="sxs-lookup"><span data-stu-id="e927c-180">This code displays "What is your name?"</span></span> <span data-ttu-id="e927c-181">dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée.</span><span class="sxs-lookup"><span data-stu-id="e927c-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="e927c-182">Il stocke cette chaîne dans une variable nommée `name`.</span><span class="sxs-lookup"><span data-stu-id="e927c-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="e927c-183">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="e927c-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="e927c-184">Enfin, elle utilise une [chaîne interpolée](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) pour afficher ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="e927c-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="e927c-185">Compilez le programme en choisissant **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="e927c-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="e927c-186">Pour exécuter le programme, choisissez **HelloWorld** sur la barre d’outils, ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="e927c-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="e927c-187">Répondez à l’invite en entrant un nom et en appuyant sur la clé **Enter.**</span><span class="sxs-lookup"><span data-stu-id="e927c-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="e927c-189">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="e927c-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="e927c-190">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e927c-190">Next steps</span></span>

<span data-ttu-id="e927c-191">Dans cet article, vous avez créé et exécuté votre première application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e927c-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="e927c-192">Dans l’étape suivante, vous déboiffez votre application.</span><span class="sxs-lookup"><span data-stu-id="e927c-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e927c-193">Debug a .NET Core Hello World application dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e927c-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
