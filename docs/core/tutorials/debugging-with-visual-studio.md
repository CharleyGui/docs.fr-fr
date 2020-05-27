---
title: Déboguer une application console .NET Core avec Visual Studio
description: Découvrez comment déboguer une application console .NET Core avec Visual Studio.
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005412"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="0a28d-103">Didacticiel : déboguer une application console .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0a28d-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="0a28d-104">Ce didacticiel présente les outils de débogage disponibles dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a28d-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a28d-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0a28d-105">Prerequisites</span></span>

- <span data-ttu-id="0a28d-106">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0a28d-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="0a28d-107">Configuration de build Debug</span><span class="sxs-lookup"><span data-stu-id="0a28d-107">Debug build configuration</span></span>

<span data-ttu-id="0a28d-108">*Débogage* et *Mise en production* sont deux des configurations de build par défaut de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a28d-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="0a28d-109">La configuration de build actuelle s’affiche sur la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="0a28d-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="0a28d-110">L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :</span><span class="sxs-lookup"><span data-stu-id="0a28d-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![Barre d’outils Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="0a28d-112">Commencez par exécuter la version de débogage de l’application.</span><span class="sxs-lookup"><span data-stu-id="0a28d-112">Begin by running the Debug version of the app.</span></span> <span data-ttu-id="0a28d-113">La configuration de la build Debug désactive la plupart des optimisations du compilateur et fournit des informations plus détaillées pendant le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="0a28d-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="0a28d-114">Définir un point d'arrêt</span><span class="sxs-lookup"><span data-stu-id="0a28d-114">Set a breakpoint</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="0a28d-115">Définissez un *point d’arrêt* sur la ligne qui affiche le nom, la date et l’heure en cliquant dans la marge de gauche de la fenêtre de code sur cette ligne.</span><span class="sxs-lookup"><span data-stu-id="0a28d-115">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="0a28d-116">Vous pouvez également définir un point d’arrêt en plaçant le curseur dans la ligne de code, puis en appuyant sur **F9** ou en choisissant **Déboguer**  >  **basculer le point d’arrêt** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="0a28d-116">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="0a28d-117">Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* l’exécution de la ligne avec le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="0a28d-117">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="0a28d-118">Comme le montre l’illustration suivante, Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un point rouge dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="0a28d-118">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="0a28d-120">Exécutez le programme en mode débogage en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="0a28d-120">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span> <span data-ttu-id="0a28d-121">D’autres façons de démarrer le débogage sont en appuyant sur **F5** ou en choisissant **Déboguer**  >  **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-121">Other ways to start debugging are by pressing **F5** or by choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="0a28d-122">Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-122">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="0a28d-123">L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="0a28d-123">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="0a28d-124">La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0a28d-124">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Capture d’écran d’un point d’arrêt dans Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="0a28d-126">La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez.</span><span class="sxs-lookup"><span data-stu-id="0a28d-126">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="0a28d-127">Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.</span><span class="sxs-lookup"><span data-stu-id="0a28d-127">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="0a28d-128">Si la fenêtre **exécution** n’est pas visible, affichez-la en sélectionnant **Déboguer**les  >  **fenêtres**  >  **immédiates**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-128">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="0a28d-129">Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .</span><span class="sxs-lookup"><span data-stu-id="0a28d-129">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="0a28d-130">Entrez `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .</span><span class="sxs-lookup"><span data-stu-id="0a28d-130">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="0a28d-131">La fenêtre **exécution** affiche la valeur de la variable de chaîne et les propriétés de la <xref:System.DateTime> valeur.</span><span class="sxs-lookup"><span data-stu-id="0a28d-131">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="0a28d-132">En outre, les valeurs des variables sont mises à jour dans la fenêtre variables **locales** .</span><span class="sxs-lookup"><span data-stu-id="0a28d-132">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Variables locales et fenêtres immédiates dans Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="0a28d-134">Poursuivez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="0a28d-134">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="0a28d-135">Pour continuer, vous pouvez également choisir **Déboguer**  >  **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-135">Another way to continue is by choosing **Debug** > **Continue**.</span></span>

   <span data-ttu-id="0a28d-136">Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .</span><span class="sxs-lookup"><span data-stu-id="0a28d-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Fenêtre de console présentant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="0a28d-138">Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="0a28d-138">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="0a28d-139">Définir un point d’arrêt conditionnel</span><span class="sxs-lookup"><span data-stu-id="0a28d-139">Set a conditional breakpoint</span></span>

<span data-ttu-id="0a28d-140">Le programme affiche la chaîne que l’utilisateur entre.</span><span class="sxs-lookup"><span data-stu-id="0a28d-140">The program displays the string that the user enters.</span></span> <span data-ttu-id="0a28d-141">Que se passe-t-il si l’utilisateur n’entre rien ?</span><span class="sxs-lookup"><span data-stu-id="0a28d-141">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="0a28d-142">Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*, qui interrompt l’exécution du programme quand une ou plusieurs conditions sont remplies.</span><span class="sxs-lookup"><span data-stu-id="0a28d-142">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="0a28d-143">Pour définir un point d’arrêt conditionnel et voir ce qu’il se passe lorsque l’utilisateur n’entre pas de chaîne, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0a28d-143">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

1. <span data-ttu-id="0a28d-144">Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="0a28d-144">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="0a28d-145">Dans le menu contextuel, sélectionnez **conditions** pour ouvrir la boîte de dialogue **paramètres de point d’arrêt** .</span><span class="sxs-lookup"><span data-stu-id="0a28d-145">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="0a28d-146">Activez la case à cocher des **conditions** si elle n’est pas déjà sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0a28d-146">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="0a28d-148">Pour l' **expression conditionnelle**, entrez le code suivant dans le champ qui montre un exemple de code qui teste si a la touche `x` 5.</span><span class="sxs-lookup"><span data-stu-id="0a28d-148">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="0a28d-149">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="0a28d-149">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="0a28d-150">Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="0a28d-150">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="0a28d-151">Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une condition de *filtre*qui interrompt l’exécution du programme en fonction d’attributs tels que l’identificateur de thread, le nom de processus ou le nom de thread.</span><span class="sxs-lookup"><span data-stu-id="0a28d-151">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="0a28d-152">Sélectionnez **Fermer** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0a28d-152">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="0a28d-153">Démarrez le programme avec le débogage en appuyant sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-153">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="0a28d-154">Dans la fenêtre de la console, appuyez sur la touche **entrée** lorsque vous êtes invité à entrer votre nom.</span><span class="sxs-lookup"><span data-stu-id="0a28d-154">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="0a28d-155">Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la `Console.WriteLine` méthode s’exécute.</span><span class="sxs-lookup"><span data-stu-id="0a28d-155">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="0a28d-156">Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0a28d-156">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="0a28d-157">Dans ce cas, `Main` est la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0a28d-157">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="0a28d-158">Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a28d-158">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="0a28d-159">Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante dans la fenêtre **exécution** et en appuyant sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-159">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="0a28d-160">Le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="0a28d-160">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="0a28d-161">Le point d’interrogation dirige la fenêtre exécution pour [évaluer une expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="0a28d-161">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="0a28d-163">Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="0a28d-163">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="0a28d-164">Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="0a28d-164">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="0a28d-165">Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code.</span><span class="sxs-lookup"><span data-stu-id="0a28d-165">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="0a28d-166">Une autre façon de supprimer un point d’arrêt consiste à choisir **Déboguer > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="0a28d-166">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="0a28d-167">Parcourir un programme</span><span class="sxs-lookup"><span data-stu-id="0a28d-167">Step through a program</span></span>

<span data-ttu-id="0a28d-168">Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution.</span><span class="sxs-lookup"><span data-stu-id="0a28d-168">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="0a28d-169">En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme.</span><span class="sxs-lookup"><span data-stu-id="0a28d-169">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="0a28d-170">Étant donné que votre programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.</span><span class="sxs-lookup"><span data-stu-id="0a28d-170">Since your program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="0a28d-171">Choisissez **Déboguer**  >  **pas à pas**détaillé.</span><span class="sxs-lookup"><span data-stu-id="0a28d-171">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="0a28d-172">Vous pouvez également déboguer une instruction à la fois en appuyant sur **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-172">Another way to debug one statement at a time is by pressing **F11**.</span></span>

   <span data-ttu-id="0a28d-173">Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0a28d-173">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="0a28d-174">C#</span><span class="sxs-lookup"><span data-stu-id="0a28d-174">C#</span></span>

   ![Méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="0a28d-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a28d-176">Visual Basic</span></span>

   ![Méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="0a28d-178">À ce stade, la fenêtre **variables locales** indique que le `args` tableau est vide et `name` possède les `date` valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0a28d-178">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="0a28d-179">En outre, Visual Studio a ouvert une fenêtre de console vide.</span><span class="sxs-lookup"><span data-stu-id="0a28d-179">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="0a28d-180">Appuyez sur **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-180">Press **F11**.</span></span> <span data-ttu-id="0a28d-181">Visual Studio place maintenant en surbrillance la ligne suivante à exécuter.</span><span class="sxs-lookup"><span data-stu-id="0a28d-181">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="0a28d-182">La fenêtre **variables locales** est inchangée et la fenêtre de console reste vide.</span><span class="sxs-lookup"><span data-stu-id="0a28d-182">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="0a28d-183">C#</span><span class="sxs-lookup"><span data-stu-id="0a28d-183">C#</span></span>

   ![Source de la méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="0a28d-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a28d-185">Visual Basic</span></span>

   ![Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="0a28d-187">Appuyez sur **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-187">Press **F11**.</span></span> <span data-ttu-id="0a28d-188">Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`.</span><span class="sxs-lookup"><span data-stu-id="0a28d-188">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="0a28d-189">La fenêtre **variables locales** affiche la `name` `null` valeur et la fenêtre de console affiche la chaîne « quel est votre nom ? ».</span><span class="sxs-lookup"><span data-stu-id="0a28d-189">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="0a28d-190">Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-190">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="0a28d-191">La console ne répond pas et la chaîne que vous avez entrée n’est pas affichée dans la fenêtre de console, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode capture néanmoins votre entrée.</span><span class="sxs-lookup"><span data-stu-id="0a28d-191">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="0a28d-192">Appuyez sur **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-192">Press **F11**.</span></span> <span data-ttu-id="0a28d-193">Visual Studio met en surbrillance l’instruction qui comprend l' `date` affectation de la variable ( `currentDate` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0a28d-193">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="0a28d-194">La fenêtre **variables locales** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="0a28d-194">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0a28d-195">La fenêtre de console affiche également la chaîne que vous avez entrée à l’invite.</span><span class="sxs-lookup"><span data-stu-id="0a28d-195">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="0a28d-196">Appuyez sur **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-196">Press **F11**.</span></span> <span data-ttu-id="0a28d-197">La fenêtre **variables locales** affiche la valeur de la `date` variable après l’affectation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="0a28d-197">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0a28d-198">La fenêtre de console est inchangée.</span><span class="sxs-lookup"><span data-stu-id="0a28d-198">The console window is unchanged.</span></span>

1. <span data-ttu-id="0a28d-199">Appuyez sur **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-199">Press **F11**.</span></span> <span data-ttu-id="0a28d-200">Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a28d-200">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0a28d-201">La fenêtre de console affiche la chaîne mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0a28d-201">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="0a28d-202">Choisissez **Déboguer**  >  **pas à pas sortant**. Pour arrêter l’exécution pas à pas, vous pouvez également appuyer sur **MAJ** + **F11**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-202">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing **Shift**+**F11**.</span></span>

   <span data-ttu-id="0a28d-203">La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.</span><span class="sxs-lookup"><span data-stu-id="0a28d-203">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="0a28d-204">Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="0a28d-204">Press any key to close the console window and stop debugging.</span></span>

## <a name="build-a-release-version"></a><span data-ttu-id="0a28d-205">Créer une version Release</span><span class="sxs-lookup"><span data-stu-id="0a28d-205">Build a Release version</span></span>

<span data-ttu-id="0a28d-206">Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release.</span><span class="sxs-lookup"><span data-stu-id="0a28d-206">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="0a28d-207">La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application.</span><span class="sxs-lookup"><span data-stu-id="0a28d-207">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="0a28d-208">Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.</span><span class="sxs-lookup"><span data-stu-id="0a28d-208">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="0a28d-209">Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="0a28d-209">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="0a28d-211">Quand vous appuyez sur **F5** ou que vous choisissez **générer la solution** dans le menu **générer** , Visual Studio compile la version Release de l’application.</span><span class="sxs-lookup"><span data-stu-id="0a28d-211">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="0a28d-212">Vous pouvez le tester comme vous l’avez fait pour la version de débogage.</span><span class="sxs-lookup"><span data-stu-id="0a28d-212">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0a28d-213">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0a28d-213">Next steps</span></span>

<span data-ttu-id="0a28d-214">Dans ce didacticiel, vous avez utilisé les outils de débogage de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a28d-214">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="0a28d-215">Dans le didacticiel suivant, vous allez publier une version déployable de l’application.</span><span class="sxs-lookup"><span data-stu-id="0a28d-215">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0a28d-216">Publier une application console .NET Core avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0a28d-216">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
