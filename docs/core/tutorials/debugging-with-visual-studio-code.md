---
title: Déboguer une application console .NET à l’aide d’Visual Studio Code
description: Découvrez comment déboguer une application console .NET à l’aide de Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: 7215ed4a93b31ebac313c04708734667148c4e02
ms.sourcegitcommit: 30fef5b0ed76e334377d28fa8e80159b29353e10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96556107"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="542d8-103">Didacticiel : déboguer une application console .NET à l’aide d’Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="542d8-103">Tutorial: Debug a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="542d8-104">Ce didacticiel présente les outils de débogage disponibles dans Visual Studio Code pour l’utilisation des applications .NET.</span><span class="sxs-lookup"><span data-stu-id="542d8-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="542d8-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="542d8-105">Prerequisites</span></span>

- <span data-ttu-id="542d8-106">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net à l’aide de Visual Studio code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="542d8-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="542d8-107">Utiliser la configuration de build Debug</span><span class="sxs-lookup"><span data-stu-id="542d8-107">Use Debug build configuration</span></span>

<span data-ttu-id="542d8-108">*Debug* et *Release* sont des configurations de build intégrées de .net core.</span><span class="sxs-lookup"><span data-stu-id="542d8-108">*Debug* and *Release* are .NET Core's built-in build configurations.</span></span> <span data-ttu-id="542d8-109">Vous utilisez la configuration de build Debug pour le débogage et la configuration Release pour la distribution de la version finale.</span><span class="sxs-lookup"><span data-stu-id="542d8-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="542d8-110">Dans la configuration Debug, un programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation.</span><span class="sxs-lookup"><span data-stu-id="542d8-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="542d8-111">L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="542d8-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="542d8-112">La configuration Release d’un programme n’a pas d’informations de débogage symboliques et est entièrement optimisée.</span><span class="sxs-lookup"><span data-stu-id="542d8-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="542d8-113">Par défaut, Visual Studio Code paramètres de lancement utilisent la configuration de build Debug. vous n’avez donc pas besoin de le modifier avant de procéder au débogage.</span><span class="sxs-lookup"><span data-stu-id="542d8-113">By default, Visual Studio Code launch settings use the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="542d8-114">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="542d8-114">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="542d8-115">Ouvrez le dossier du projet que vous avez créé dans [créer une application console .net à l’aide de Visual Studio code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="542d8-115">Open the folder of the project that you created in [Create a .NET console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="542d8-116">Définir un point d'arrêt</span><span class="sxs-lookup"><span data-stu-id="542d8-116">Set a breakpoint</span></span>

<span data-ttu-id="542d8-117">Un *point d’arrêt* interrompt temporairement l’exécution de l’application avant l’exécution de la ligne avec le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="542d8-117">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="542d8-118">Ouvrez le fichier *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="542d8-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="542d8-119">Définissez un *point d’arrêt* sur la ligne qui affiche le nom, la date et l’heure en cliquant dans la marge de gauche de la fenêtre de code.</span><span class="sxs-lookup"><span data-stu-id="542d8-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="542d8-120">La marge de gauche se trouve à gauche des numéros de ligne.</span><span class="sxs-lookup"><span data-stu-id="542d8-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="542d8-121">Les autres méthodes de définition d’un point d’arrêt sont les suivantes : Appuyez sur <kbd>F9</kbd> ou choisissez **exécuter**  >  **basculer le point d’arrêt** dans le menu pendant que la ligne de code est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="542d8-121">Other ways to set a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run** > **Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

   <span data-ttu-id="542d8-122">Visual Studio Code indique la ligne sur laquelle le point d’arrêt est défini en affichant un point rouge dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="542d8-122">Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Point d’arrêt défini":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="542d8-124">Configuration des entrées de terminal</span><span class="sxs-lookup"><span data-stu-id="542d8-124">Set up for terminal input</span></span>

<span data-ttu-id="542d8-125">Le point d’arrêt se trouve après un `Console.ReadLine` appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="542d8-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="542d8-126">Le **console de débogage** n’accepte pas les entrées de terminal pour un programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="542d8-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="542d8-127">Pour gérer l’entrée de terminal pendant le débogage, vous pouvez utiliser le terminal intégré (l’une des fenêtres Visual Studio Code) ou un terminal externe.</span><span class="sxs-lookup"><span data-stu-id="542d8-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="542d8-128">Pour ce tutoriel, vous utilisez le terminal intégré.</span><span class="sxs-lookup"><span data-stu-id="542d8-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="542d8-129">Ouvrez *.vscode/launch.json*.</span><span class="sxs-lookup"><span data-stu-id="542d8-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="542d8-130">Remplacez le `console` paramètre par `internalConsole` `integratedTerminal` :</span><span class="sxs-lookup"><span data-stu-id="542d8-130">Change the `console` setting from `internalConsole` to `integratedTerminal`:</span></span>

   ```json
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="542d8-131">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="542d8-131">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="542d8-132">Démarrer le débogage</span><span class="sxs-lookup"><span data-stu-id="542d8-132">Start debugging</span></span>

1. <span data-ttu-id="542d8-133">Ouvrez la vue déboguer en sélectionnant l’icône de débogage dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="542d8-133">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Ouvrir l’onglet Débogage dans Visual Studio Code":::

1. <span data-ttu-id="542d8-135">Sélectionnez la flèche verte en haut du volet, en regard de **lancement de .net Core (console)**.</span><span class="sxs-lookup"><span data-stu-id="542d8-135">Select the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span> <span data-ttu-id="542d8-136">D’autres façons de démarrer le programme en mode débogage sont en appuyant sur <kbd>F5</kbd> ou en choisissant **exécuter**  >  **Démarrer le débogage** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="542d8-136">Other ways to start the program in debugging mode are by pressing <kbd>F5</kbd> or choosing **Run** > **Start Debugging** from the menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Démarrer le débogage":::

1. <span data-ttu-id="542d8-138">Sélectionnez l’onglet **Terminal** pour afficher le « quel est votre nom ? »</span><span class="sxs-lookup"><span data-stu-id="542d8-138">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="542d8-139">Invitez le programme à s’afficher avant d’attendre une réponse.</span><span class="sxs-lookup"><span data-stu-id="542d8-139">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Sélectionner l’onglet terminal":::

1. <span data-ttu-id="542d8-141">Entrez une chaîne dans la fenêtre de **Terminal** en réponse à l’invite de nom, puis appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-141">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="542d8-142">L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="542d8-142">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="542d8-143">La section variables **locales** de la fenêtre **variables** affiche les valeurs des variables définies dans la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="542d8-143">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Point d’arrêt atteint, avec des variables locales":::

## <a name="use-the-debug-console"></a><span data-ttu-id="542d8-145">Utilisez la Console de débogage</span><span class="sxs-lookup"><span data-stu-id="542d8-145">Use the Debug Console</span></span>

<span data-ttu-id="542d8-146">La fenêtre **console de débogage** vous permet d’interagir avec l’application que vous déboguez.</span><span class="sxs-lookup"><span data-stu-id="542d8-146">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="542d8-147">Vous pouvez modifier la valeur des variables pour voir comment elles affectent votre programme.</span><span class="sxs-lookup"><span data-stu-id="542d8-147">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="542d8-148">Sélectionnez l’onglet **console de débogage** .</span><span class="sxs-lookup"><span data-stu-id="542d8-148">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="542d8-149">Entrez `name = "Gracie"` à l’invite au bas de la fenêtre de **console de débogage** et appuyez sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="542d8-149">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Modifier les valeurs des variables":::

1. <span data-ttu-id="542d8-151">Entrez `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` au bas de la fenêtre de **console de débogage** et appuyez sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="542d8-151">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="542d8-152">La fenêtre **variables** affiche les nouvelles valeurs des `name` variables et `date` .</span><span class="sxs-lookup"><span data-stu-id="542d8-152">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="542d8-153">Poursuivez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="542d8-153">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="542d8-154">Pour continuer, vous pouvez également appuyer sur <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-154">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Continuer le débogage":::

1. <span data-ttu-id="542d8-156">Sélectionnez à nouveau l’onglet **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="542d8-156">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="542d8-157">Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées au **console de débogage**.</span><span class="sxs-lookup"><span data-stu-id="542d8-157">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminal présentant les valeurs entrées":::

1. <span data-ttu-id="542d8-159">Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="542d8-159">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="542d8-160">Définir un point d’arrêt conditionnel</span><span class="sxs-lookup"><span data-stu-id="542d8-160">Set a conditional breakpoint</span></span>

<span data-ttu-id="542d8-161">Le programme affiche la chaîne que l’utilisateur entre.</span><span class="sxs-lookup"><span data-stu-id="542d8-161">The program displays the string that the user enters.</span></span> <span data-ttu-id="542d8-162">Que se passe-t-il si l’utilisateur n’entre rien ?</span><span class="sxs-lookup"><span data-stu-id="542d8-162">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="542d8-163">Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*.</span><span class="sxs-lookup"><span data-stu-id="542d8-163">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="542d8-164">Cliquez avec le bouton droit (<kbd>CTRL</kbd>+ clic sur MacOS) sur le point rouge représentant le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="542d8-164">Right-click (<kbd>Ctrl</kbd>-click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="542d8-165">Dans le menu contextuel, sélectionnez **modifier le point d’arrêt** pour ouvrir une boîte de dialogue qui vous permet d’entrer une expression conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="542d8-165">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Menu contextuel Point d'arrêt":::

1. <span data-ttu-id="542d8-167">Sélectionnez `Expression` dans la liste déroulante, entrez l’expression conditionnelle suivante, puis appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-167">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Entrer une expression conditionnelle":::

   <span data-ttu-id="542d8-169">Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="542d8-169">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="542d8-170">Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre de fois spécifié.</span><span class="sxs-lookup"><span data-stu-id="542d8-170">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="542d8-171">Une autre option consiste à spécifier une *condition de filtre*, qui interrompt l’exécution du programme en fonction d’attributs tels qu’un identificateur de thread, un nom de processus ou un nom de thread.</span><span class="sxs-lookup"><span data-stu-id="542d8-171">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="542d8-172">Démarrez le programme avec le débogage en appuyant sur <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-172">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="542d8-173">Dans l’onglet **Terminal** , appuyez sur la touche <kbd>entrée</kbd> lorsque vous êtes invité à entrer votre nom.</span><span class="sxs-lookup"><span data-stu-id="542d8-173">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="542d8-174">Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la `Console.WriteLine` méthode s’exécute.</span><span class="sxs-lookup"><span data-stu-id="542d8-174">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="542d8-175">La fenêtre **variables** indique que la valeur de la `name` variable est `""` , ou <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="542d8-175">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="542d8-176">Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante à l’invite **console de débogage** et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-176">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="542d8-177">Le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="542d8-177">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Console de débogage retournant la valeur true après l’exécution de l’instruction":::

1. <span data-ttu-id="542d8-179">Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="542d8-179">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="542d8-180">Sélectionnez l’onglet **Terminal** , puis appuyez sur n’importe quelle touche pour quitter le programme et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="542d8-180">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="542d8-181">Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code.</span><span class="sxs-lookup"><span data-stu-id="542d8-181">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="542d8-182">Pour supprimer un point d’arrêt, vous pouvez d’autres façons d’appuyer sur <kbd>F9</kbd> ou de choisir **exécuter > basculer le point d’arrêt** dans le menu pendant que la ligne de code est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="542d8-182">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Run > Toggle Breakpoint** from the menu while the line of code is selected.</span></span>

1. <span data-ttu-id="542d8-183">Si vous recevez un avertissement indiquant que la condition de point d’arrêt sera perdue, sélectionnez **supprimer le point d’arrêt**.</span><span class="sxs-lookup"><span data-stu-id="542d8-183">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="542d8-184">Parcourir un programme</span><span class="sxs-lookup"><span data-stu-id="542d8-184">Step through a program</span></span>

<span data-ttu-id="542d8-185">Visual Studio Code vous permet également d’effectuer un pas à pas détaillé ligne par ligne à l’aide d’un programme et de surveiller son exécution.</span><span class="sxs-lookup"><span data-stu-id="542d8-185">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="542d8-186">En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme.</span><span class="sxs-lookup"><span data-stu-id="542d8-186">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="542d8-187">Étant donné que ce programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.</span><span class="sxs-lookup"><span data-stu-id="542d8-187">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="542d8-188">Définissez un point d’arrêt sur l’accolade ouvrante de la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="542d8-188">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="542d8-189">Appuyez sur <kbd>F5</kbd> pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="542d8-189">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="542d8-190">Visual Studio Code met en surbrillance la ligne de point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="542d8-190">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="542d8-191">À ce stade, la fenêtre **variables** indique que le `args` tableau est vide, et `name` possède les `date` valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="542d8-191">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="542d8-192">Sélectionnez **exécuter** un  >  **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-192">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Bouton pas à pas détaillé":::

   <span data-ttu-id="542d8-194">Visual Studio Code met en surbrillance la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="542d8-194">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="542d8-195">Sélectionnez **exécuter** un  >  **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-195">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="542d8-196">Visual Studio Code exécute le `Console.WriteLine` pour l’invite de nom et met en surbrillance la ligne suivante d’exécution.</span><span class="sxs-lookup"><span data-stu-id="542d8-196">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="542d8-197">La ligne suivante est le `Console.ReadLine` pour le `name` .</span><span class="sxs-lookup"><span data-stu-id="542d8-197">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="542d8-198">La fenêtre **variables** est inchangée et l’onglet **Terminal** affiche « quel est votre nom ? ».</span><span class="sxs-lookup"><span data-stu-id="542d8-198">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="542d8-199">prompt.</span><span class="sxs-lookup"><span data-stu-id="542d8-199">prompt.</span></span>

1. <span data-ttu-id="542d8-200">Sélectionnez **exécuter** un  >  **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-200">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="542d8-201">Visual Studio met en surbrillance l' `name` attribution de variable.</span><span class="sxs-lookup"><span data-stu-id="542d8-201">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="542d8-202">La fenêtre **variables** affiche `name` toujours `null` .</span><span class="sxs-lookup"><span data-stu-id="542d8-202">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="542d8-203">Répondez à l’invite en entrant une chaîne dans l’onglet terminal et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-203">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="542d8-204">L’onglet **Terminal** peut ne pas afficher la chaîne que vous entrez lors de son entrée, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode capture votre entrée.</span><span class="sxs-lookup"><span data-stu-id="542d8-204">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="542d8-205">Sélectionnez **exécuter** un  >  **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-205">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="542d8-206">Visual Studio Code met en surbrillance l' `date` attribution de variable.</span><span class="sxs-lookup"><span data-stu-id="542d8-206">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="542d8-207">La fenêtre **variables** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="542d8-207">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="542d8-208">L’onglet **Terminal** affiche la chaîne que vous avez entrée à l’invite.</span><span class="sxs-lookup"><span data-stu-id="542d8-208">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="542d8-209">Sélectionnez **exécuter** un  >  **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-209">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="542d8-210">La fenêtre **variables** affiche la valeur de la `date` variable après l’assignation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="542d8-210">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="542d8-211">Sélectionnez **exécuter** un  >  **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-211">Select **Run** > **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="542d8-212">Visual Studio Code appelle la <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="542d8-212">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="542d8-213">La fenêtre de console affiche la chaîne mise en forme.</span><span class="sxs-lookup"><span data-stu-id="542d8-213">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="542d8-214">Sélectionnez **exécuter** le  >  **pas à pas sortant** ou appuyez sur <kbd>MAJ</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="542d8-214">Select **Run** > **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Bouton de pas à pas sortant":::

1. <span data-ttu-id="542d8-216">Sélectionnez l’onglet **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="542d8-216">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="542d8-217">Le terminal affiche « appuyez sur une touche pour quitter... »</span><span class="sxs-lookup"><span data-stu-id="542d8-217">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="542d8-218">Appuyez sur n’importe quelle touche pour quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="542d8-218">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="542d8-219">Utiliser la configuration de build Release</span><span class="sxs-lookup"><span data-stu-id="542d8-219">Use Release build configuration</span></span>

<span data-ttu-id="542d8-220">Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release.</span><span class="sxs-lookup"><span data-stu-id="542d8-220">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="542d8-221">La version Release intègre des optimisations du compilateur qui peuvent affecter le comportement d’une application.</span><span class="sxs-lookup"><span data-stu-id="542d8-221">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="542d8-222">Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.</span><span class="sxs-lookup"><span data-stu-id="542d8-222">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="542d8-223">Pour générer et tester la version Release de votre application console, ouvrez le **Terminal** et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="542d8-223">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="542d8-224">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="542d8-224">Additional resources</span></span>

* [<span data-ttu-id="542d8-225">Débogage dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="542d8-225">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="542d8-226">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="542d8-226">Next steps</span></span>

<span data-ttu-id="542d8-227">Dans ce didacticiel, vous avez utilisé Visual Studio Code outils de débogage.</span><span class="sxs-lookup"><span data-stu-id="542d8-227">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="542d8-228">Dans le didacticiel suivant, vous allez publier une version déployable de l’application.</span><span class="sxs-lookup"><span data-stu-id="542d8-228">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="542d8-229">Publier une application console .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="542d8-229">Publish a .NET console application using Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
