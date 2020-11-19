---
title: Débogage d’une application console .NET à l’aide de Visual Studio
description: Découvrez comment déboguer une application console .NET à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 8a914dc6cf069c011ea5b077ada514bf8cec331d
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916186"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio"></a><span data-ttu-id="bd930-103">Didacticiel : déboguer une application console .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd930-103">Tutorial: Debug a .NET console application using Visual Studio</span></span>

<span data-ttu-id="bd930-104">Ce didacticiel présente les outils de débogage disponibles dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd930-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd930-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="bd930-105">Prerequisites</span></span>

- <span data-ttu-id="bd930-106">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net à l’aide de Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="bd930-106">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="bd930-107">Utiliser la configuration de build Debug</span><span class="sxs-lookup"><span data-stu-id="bd930-107">Use Debug build configuration</span></span>

<span data-ttu-id="bd930-108">*Debug* et *Release* sont des configurations de build intégrées à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd930-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="bd930-109">Vous utilisez la configuration de build Debug pour le débogage et la configuration Release pour la distribution de la version finale.</span><span class="sxs-lookup"><span data-stu-id="bd930-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="bd930-110">Dans la configuration Debug, un programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation.</span><span class="sxs-lookup"><span data-stu-id="bd930-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="bd930-111">L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="bd930-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="bd930-112">La configuration Release d’un programme n’a pas d’informations de débogage symboliques et est entièrement optimisée.</span><span class="sxs-lookup"><span data-stu-id="bd930-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="bd930-113">Par défaut, Visual Studio utilise la configuration de build Debug. vous n’avez donc pas besoin de le modifier avant le débogage.</span><span class="sxs-lookup"><span data-stu-id="bd930-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="bd930-114">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd930-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="bd930-115">Ouvrez le projet que vous avez créé dans [créer une application console .net à l’aide de Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="bd930-115">Open the project that you created in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

   <span data-ttu-id="bd930-116">La configuration de build actuelle s’affiche sur la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="bd930-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="bd930-117">L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :</span><span class="sxs-lookup"><span data-stu-id="bd930-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png" alt-text="Barre d’outils Visual Studio avec débogage mis en surbrillance":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="bd930-119">Définir un point d'arrêt</span><span class="sxs-lookup"><span data-stu-id="bd930-119">Set a breakpoint</span></span>

<span data-ttu-id="bd930-120">Un *point d’arrêt* interrompt temporairement l’exécution de l’application avant l’exécution de la ligne avec le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bd930-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="bd930-121">Définissez un *point d’arrêt* sur la ligne qui affiche le nom, la date et l’heure en cliquant dans la marge de gauche de la fenêtre de code sur cette ligne.</span><span class="sxs-lookup"><span data-stu-id="bd930-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="bd930-122">La marge de gauche se trouve à gauche des numéros de ligne.</span><span class="sxs-lookup"><span data-stu-id="bd930-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="bd930-123">D’autres façons de définir un point d’arrêt consiste à placer le curseur dans la ligne de code, puis à appuyer sur <kbd>F9</kbd> ou à choisir **Déboguer** le  >  **point d’arrêt** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="bd930-123">Other ways to set a breakpoint are by placing the cursor in the line of code and then pressing <kbd>F9</kbd> or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="bd930-124">Comme le montre l’illustration suivante, Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un point rouge dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="bd930-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/set-breakpoint-in-editor.png" alt-text="Fenêtre Programme de Visual Studio avec un point d’arrêt défini":::

1. <span data-ttu-id="bd930-126">Appuyez sur <kbd>F5</kbd> pour exécuter le programme en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="bd930-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="bd930-127">Une autre façon de démarrer le débogage consiste à choisir **Déboguer**  >  **Démarrer le débogage** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="bd930-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="bd930-128">Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="bd930-129">L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="bd930-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="bd930-130">La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bd930-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/breakpoint-hit.png" alt-text="Capture d’écran d’un point d’arrêt dans Visual Studio":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="bd930-132">Utiliser la fenêtre exécution</span><span class="sxs-lookup"><span data-stu-id="bd930-132">Use the Immediate window</span></span>

<span data-ttu-id="bd930-133">La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez.</span><span class="sxs-lookup"><span data-stu-id="bd930-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="bd930-134">Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.</span><span class="sxs-lookup"><span data-stu-id="bd930-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="bd930-135">Si la fenêtre **exécution** n’est pas visible, affichez-la en sélectionnant **Déboguer** les  >  **fenêtres**  >  **immédiates**.</span><span class="sxs-lookup"><span data-stu-id="bd930-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="bd930-136">Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="bd930-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="bd930-137">Entrez `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` dans la fenêtre **exécution** et appuyez sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="bd930-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="bd930-138">La fenêtre **exécution** affiche la valeur de la variable de chaîne et les propriétés de la <xref:System.DateTime> valeur.</span><span class="sxs-lookup"><span data-stu-id="bd930-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="bd930-139">En outre, les valeurs des variables sont mises à jour dans la fenêtre variables **locales** .</span><span class="sxs-lookup"><span data-stu-id="bd930-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/locals-immediate-window.png" alt-text="Variables locales et fenêtres immédiates dans Visual Studio 2019":::

1. <span data-ttu-id="bd930-141">Appuyez sur <kbd>F5</kbd> pour continuer l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="bd930-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="bd930-142">Pour continuer, vous pouvez également choisir **Déboguer**  >  **Continuer** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="bd930-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="bd930-143">Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .</span><span class="sxs-lookup"><span data-stu-id="bd930-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/console-window.png" alt-text="Fenêtre de console présentant les valeurs entrées":::

1. <span data-ttu-id="bd930-145">Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="bd930-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="bd930-146">Définir un point d’arrêt conditionnel</span><span class="sxs-lookup"><span data-stu-id="bd930-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="bd930-147">Le programme affiche la chaîne que l’utilisateur entre.</span><span class="sxs-lookup"><span data-stu-id="bd930-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="bd930-148">Que se passe-t-il si l’utilisateur n’entre rien ?</span><span class="sxs-lookup"><span data-stu-id="bd930-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="bd930-149">Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*.</span><span class="sxs-lookup"><span data-stu-id="bd930-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="bd930-150">Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="bd930-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="bd930-151">Dans le menu contextuel, sélectionnez **conditions** pour ouvrir la boîte de dialogue **paramètres de point d’arrêt** .</span><span class="sxs-lookup"><span data-stu-id="bd930-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="bd930-152">Activez la case à cocher des **conditions** si elle n’est pas déjà sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bd930-152">Select the box for **Conditions** if it's not already selected.</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/breakpoint-settings.png" alt-text="Éditeur montrant le panneau des paramètres de point d’arrêt - C#":::

1. <span data-ttu-id="bd930-154">Pour l' **expression conditionnelle**, entrez le code suivant dans le champ qui montre un exemple de code qui teste si a la touche `x` 5.</span><span class="sxs-lookup"><span data-stu-id="bd930-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="bd930-155">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="bd930-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="bd930-156">Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="bd930-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="bd930-157">Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre de fois spécifié.</span><span class="sxs-lookup"><span data-stu-id="bd930-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="bd930-158">Une autre option consiste à spécifier une *condition de filtre*, qui interrompt l’exécution du programme en fonction d’attributs tels qu’un identificateur de thread, un nom de processus ou un nom de thread.</span><span class="sxs-lookup"><span data-stu-id="bd930-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="bd930-159">Sélectionnez **Fermer** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bd930-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="bd930-160">Démarrez le programme avec le débogage en appuyant sur <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="bd930-161">Dans la fenêtre de la console, appuyez sur la touche <kbd>entrée</kbd> lorsque vous êtes invité à entrer votre nom.</span><span class="sxs-lookup"><span data-stu-id="bd930-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="bd930-162">Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la `Console.WriteLine` méthode s’exécute.</span><span class="sxs-lookup"><span data-stu-id="bd930-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="bd930-163">Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bd930-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="bd930-164">Dans ce cas, `Main` est la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bd930-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="bd930-165">Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd930-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="bd930-166">Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante dans la fenêtre **exécution** et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="bd930-167">Le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="bd930-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="bd930-168">Le point d’interrogation dirige la fenêtre exécution pour [évaluer une expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="bd930-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/immediate-window-output.png" alt-text="Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#":::

1. <span data-ttu-id="bd930-170">Appuyez sur <kbd>F5</kbd> pour continuer l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="bd930-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="bd930-171">Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="bd930-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="bd930-172">Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code.</span><span class="sxs-lookup"><span data-stu-id="bd930-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="bd930-173">Pour supprimer un point d’arrêt, vous pouvez notamment appuyer sur <kbd>F9</kbd> ou choisir **déboguer > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bd930-173">Other ways to clear a breakpoint are by pressing <kbd>F9</kbd> or choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="bd930-174">Parcourir un programme</span><span class="sxs-lookup"><span data-stu-id="bd930-174">Step through a program</span></span>

<span data-ttu-id="bd930-175">Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution.</span><span class="sxs-lookup"><span data-stu-id="bd930-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="bd930-176">En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme.</span><span class="sxs-lookup"><span data-stu-id="bd930-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="bd930-177">Étant donné que ce programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.</span><span class="sxs-lookup"><span data-stu-id="bd930-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="bd930-178">Choisissez **Déboguer**  >  **pas à pas** détaillé.</span><span class="sxs-lookup"><span data-stu-id="bd930-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="bd930-179">Vous pouvez également déboguer une instruction à la fois en appuyant sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="bd930-180">Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bd930-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="bd930-181">C#</span><span class="sxs-lookup"><span data-stu-id="bd930-181">C#</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/step-into-method.png" alt-text="Méthode pas à pas détaillée dans Visual Studio - C#":::

   <span data-ttu-id="bd930-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd930-183">Visual Basic</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/vb-step-into-method.png" alt-text="Méthode pas à pas détaillée dans Visual Studio - Visual Basic":::

   <span data-ttu-id="bd930-185">À ce stade, la fenêtre **variables locales** indique que le `args` tableau est vide et `name` possède les `date` valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="bd930-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="bd930-186">En outre, Visual Studio a ouvert une fenêtre de console vide.</span><span class="sxs-lookup"><span data-stu-id="bd930-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="bd930-187">Appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="bd930-188">Visual Studio place maintenant en surbrillance la ligne suivante à exécuter.</span><span class="sxs-lookup"><span data-stu-id="bd930-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="bd930-189">La fenêtre **variables locales** est inchangée et la fenêtre de console reste vide.</span><span class="sxs-lookup"><span data-stu-id="bd930-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="bd930-190">C#</span><span class="sxs-lookup"><span data-stu-id="bd930-190">C#</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/step-into-source-method.png" alt-text="Source de la méthode pas à pas détaillée dans Visual Studio - C#":::

   <span data-ttu-id="bd930-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd930-192">Visual Basic</span></span>

   :::image type="content" source="./media/debugging-with-visual-studio/vb-step-into-source-method.png" alt-text="Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic":::

1. <span data-ttu-id="bd930-194">Appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="bd930-195">Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`.</span><span class="sxs-lookup"><span data-stu-id="bd930-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="bd930-196">La fenêtre **variables locales** affiche la `name` `null` valeur et la fenêtre de console affiche la chaîne « quel est votre nom ? ».</span><span class="sxs-lookup"><span data-stu-id="bd930-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="bd930-197">Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="bd930-198">La console ne répond pas et la chaîne que vous avez entrée n’est pas affichée dans la fenêtre de console, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode capture néanmoins votre entrée.</span><span class="sxs-lookup"><span data-stu-id="bd930-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="bd930-199">Appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="bd930-200">Visual Studio met en surbrillance l’instruction qui comprend l' `date` affectation de la variable ( `currentDate` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="bd930-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="bd930-201">La fenêtre **variables locales** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="bd930-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bd930-202">La fenêtre de console affiche également la chaîne que vous avez entrée à l’invite.</span><span class="sxs-lookup"><span data-stu-id="bd930-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="bd930-203">Appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="bd930-204">La fenêtre **variables locales** affiche la valeur de la `date` variable après l’affectation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="bd930-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bd930-205">La fenêtre de console est inchangée.</span><span class="sxs-lookup"><span data-stu-id="bd930-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="bd930-206">Appuyez sur <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="bd930-207">Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd930-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bd930-208">La fenêtre de console affiche la chaîne mise en forme.</span><span class="sxs-lookup"><span data-stu-id="bd930-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="bd930-209">Choisissez **Déboguer**  >  **pas à pas sortant**. Pour arrêter l’exécution pas à pas, vous pouvez également appuyer sur <kbd>MAJ</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="bd930-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="bd930-210">La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.</span><span class="sxs-lookup"><span data-stu-id="bd930-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="bd930-211">Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="bd930-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="bd930-212">Utiliser la configuration de build Release</span><span class="sxs-lookup"><span data-stu-id="bd930-212">Use Release build configuration</span></span>

<span data-ttu-id="bd930-213">Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release.</span><span class="sxs-lookup"><span data-stu-id="bd930-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="bd930-214">La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application.</span><span class="sxs-lookup"><span data-stu-id="bd930-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="bd930-215">Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.</span><span class="sxs-lookup"><span data-stu-id="bd930-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="bd930-216">Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.</span><span class="sxs-lookup"><span data-stu-id="bd930-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

:::image type="content" source="./media/debugging-with-visual-studio/visual-studio-toolbar-release.png" alt-text="barre d’outils Visual Studio par défaut avec mise en surbrillance":::

<span data-ttu-id="bd930-218">Quand vous appuyez sur <kbd>F5</kbd> ou que vous choisissez **générer la solution** dans le menu **générer** , Visual Studio compile la version Release de l’application.</span><span class="sxs-lookup"><span data-stu-id="bd930-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="bd930-219">Vous pouvez le tester comme vous l’avez fait pour la version de débogage.</span><span class="sxs-lookup"><span data-stu-id="bd930-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bd930-220">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bd930-220">Next steps</span></span>

<span data-ttu-id="bd930-221">Dans ce didacticiel, vous avez utilisé les outils de débogage de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd930-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="bd930-222">Dans le didacticiel suivant, vous allez publier une version déployable de l’application.</span><span class="sxs-lookup"><span data-stu-id="bd930-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd930-223">Publier une application console .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd930-223">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
