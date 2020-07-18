---
title: Déboguer une application console .NET Core à l’aide de Visual Studio pour Mac
description: Découvrez comment déboguer une application console .NET Core à l’aide de Visual Studio Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 7e2a25266fab40b5ef1d0a38b8bbf06a6843746b
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416013"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="9d975-103">Didacticiel : déboguer une application console .NET Core à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="9d975-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="9d975-104">Ce didacticiel présente les outils de débogage disponibles dans Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="9d975-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9d975-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="9d975-105">Prerequisites</span></span>

- <span data-ttu-id="9d975-106">Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio pour Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="9d975-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="9d975-107">Utiliser la configuration de build Debug</span><span class="sxs-lookup"><span data-stu-id="9d975-107">Use Debug build configuration</span></span>

<span data-ttu-id="9d975-108">*Debug* et *Release* sont des configurations de build intégrées à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d975-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="9d975-109">Vous utilisez la configuration de build Debug pour le débogage et la configuration Release pour la distribution de la version finale.</span><span class="sxs-lookup"><span data-stu-id="9d975-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="9d975-110">Dans la configuration Debug, un programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation.</span><span class="sxs-lookup"><span data-stu-id="9d975-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="9d975-111">L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="9d975-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="9d975-112">La configuration Release d’un programme n’a pas d’informations de débogage symboliques et est entièrement optimisée.</span><span class="sxs-lookup"><span data-stu-id="9d975-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="9d975-113">Par défaut, Visual Studio utilise la configuration de build Debug. vous n’avez donc pas besoin de le modifier avant le débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="9d975-114">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="9d975-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="9d975-115">Ouvrez le projet que vous avez créé dans [créer une application console .net core dans Visual Studio pour Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="9d975-115">Open the project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="9d975-116">La configuration de build actuelle s’affiche sur la barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="9d975-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="9d975-117">L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :</span><span class="sxs-lookup"><span data-stu-id="9d975-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Barre d’outils Visual Studio avec débogage mis en surbrillance":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="9d975-119">Définir un point d'arrêt</span><span class="sxs-lookup"><span data-stu-id="9d975-119">Set a breakpoint</span></span>

<span data-ttu-id="9d975-120">Un *point d’arrêt* interrompt temporairement l’exécution de l’application avant l’exécution de la ligne avec le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9d975-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="9d975-121">Définissez un point d’arrêt sur la ligne qui affiche le nom, la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="9d975-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="9d975-122">Pour ce faire, placez le curseur dans la ligne de code et appuyez sur <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>commande</kbd> + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="9d975-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="9d975-123">Une autre façon de définir un point d’arrêt consiste à sélectionner **exécuter**  >  **basculer le point d’arrêt** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="9d975-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="9d975-124">Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un point rouge dans la marge de gauche.</span><span class="sxs-lookup"><span data-stu-id="9d975-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Fenêtre Programme de Visual Studio avec un point d’arrêt défini":::

1. <span data-ttu-id="9d975-126">Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour démarrer le programme en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="9d975-127">Une autre façon de démarrer le débogage consiste à choisir **exécuter**  >  **Démarrer le débogage** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="9d975-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="9d975-128">Entrez une chaîne dans la fenêtre de terminal lorsque le programme vous invite à entrer un nom, puis appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9d975-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="9d975-129">L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt, avant l’exécution de la `Console.WriteLine` méthode.</span><span class="sxs-lookup"><span data-stu-id="9d975-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Capture d’écran d’un point d’arrêt dans Visual Studio":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="9d975-131">Utiliser la fenêtre exécution</span><span class="sxs-lookup"><span data-stu-id="9d975-131">Use the Immediate window</span></span>

<span data-ttu-id="9d975-132">La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez.</span><span class="sxs-lookup"><span data-stu-id="9d975-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="9d975-133">Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.</span><span class="sxs-lookup"><span data-stu-id="9d975-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="9d975-134">Si la fenêtre **exécution** n’est pas visible, affichez-la en sélectionnant **Afficher**les  >  **blocs de débogage**  >  **immédiats**.</span><span class="sxs-lookup"><span data-stu-id="9d975-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="9d975-135">Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9d975-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="9d975-136">Entrez `date = date.AddDays(1)` dans la fenêtre **exécution** et appuyez sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9d975-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="9d975-137">La fenêtre **exécution** affiche la nouvelle valeur de la variable de chaîne et les propriétés de la <xref:System.DateTime> valeur.</span><span class="sxs-lookup"><span data-stu-id="9d975-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Fenêtre exécution dans Visual Studio":::

   <span data-ttu-id="9d975-139">La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d975-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="9d975-140">Les valeurs des variables que vous venez de modifier sont mises à jour dans la fenêtre **variables locales** .</span><span class="sxs-lookup"><span data-stu-id="9d975-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Fenêtre variables locales dans Visual Studio":::

1. <span data-ttu-id="9d975-142">Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour continuer le débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="9d975-143">Les valeurs affichées dans le terminal correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .</span><span class="sxs-lookup"><span data-stu-id="9d975-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="9d975-144">Si vous ne voyez pas le terminal, sélectionnez **Terminal-HelloWorld** dans la barre de navigation inférieure.</span><span class="sxs-lookup"><span data-stu-id="9d975-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Terminal Hello World dans la barre de navigation inférieure":::

1. <span data-ttu-id="9d975-146">Appuyez sur n’importe quelle touche pour quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="9d975-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="9d975-147">Fermez la fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="9d975-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="9d975-148">Définir un point d’arrêt conditionnel</span><span class="sxs-lookup"><span data-stu-id="9d975-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="9d975-149">Le programme affiche une chaîne que l’utilisateur entre.</span><span class="sxs-lookup"><span data-stu-id="9d975-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="9d975-150">Que se passe-t-il si l’utilisateur n’entre rien ?</span><span class="sxs-lookup"><span data-stu-id="9d975-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="9d975-151">Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*.</span><span class="sxs-lookup"><span data-stu-id="9d975-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="9d975-152"><kbd>CTRL</kbd>+ clic sur le point rouge représentant le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9d975-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="9d975-153">Dans le menu contextuel, sélectionnez **modifier le point d’arrêt**.</span><span class="sxs-lookup"><span data-stu-id="9d975-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="9d975-154">Dans la boîte de dialogue **modifier le point d’arrêt** , entrez le code suivant dans le champ qui suit **et la condition suivante est true**, puis sélectionnez **appliquer**.</span><span class="sxs-lookup"><span data-stu-id="9d975-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Éditeur qui présente le panneau des paramètres de point d’arrêt":::

   <span data-ttu-id="9d975-156">Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="9d975-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="9d975-157">Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre de fois spécifié.</span><span class="sxs-lookup"><span data-stu-id="9d975-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="9d975-158">Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="9d975-159">Dans la fenêtre de terminal, appuyez sur <kbd>entrée</kbd> lorsque vous êtes invité à entrer votre nom.</span><span class="sxs-lookup"><span data-stu-id="9d975-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="9d975-160">Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9d975-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="9d975-161">Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d975-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="9d975-162">Dans ce cas, `Main` est la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d975-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="9d975-163">Notez que la valeur de la `name` variable est `""` , autrement dit, <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9d975-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="9d975-164">Vous pouvez également voir que la valeur est une chaîne vide en entrant le `name` nom de la variable dans la fenêtre **exécution** et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9d975-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="La fenêtre exécution qui indique le nom est une chaîne vide":::

1. <span data-ttu-id="9d975-166">Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour continuer le débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="9d975-167">Dans la fenêtre de terminal, appuyez sur n’importe quelle touche pour quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="9d975-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="9d975-168">Fermez la fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="9d975-168">Close the terminal window.</span></span>

1. <span data-ttu-id="9d975-169">Effacez le point d’arrêt en cliquant sur le point rouge dans la marge de gauche de la fenêtre de code.</span><span class="sxs-lookup"><span data-stu-id="9d975-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="9d975-170">Pour supprimer un point d’arrêt, vous pouvez également choisir **exécuter > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="9d975-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="9d975-171">Parcourir un programme</span><span class="sxs-lookup"><span data-stu-id="9d975-171">Step through a program</span></span>

<span data-ttu-id="9d975-172">Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution.</span><span class="sxs-lookup"><span data-stu-id="9d975-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="9d975-173">En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme.</span><span class="sxs-lookup"><span data-stu-id="9d975-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="9d975-174">Étant donné que ce programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.</span><span class="sxs-lookup"><span data-stu-id="9d975-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="9d975-175">Définissez un point d’arrêt sur l’accolade qui marque le début de la `Main` méthode (appuyez sur <kbd>commande</kbd> + <kbd>\\</kbd> ).</span><span class="sxs-lookup"><span data-stu-id="9d975-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="9d975-176">Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="9d975-177">Visual Studio s’arrête sur la ligne avec le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="9d975-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="9d975-178">Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>) ou sélectionnez **exécuter**  >  un**pas à pas détaillé** pour avancer d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="9d975-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="9d975-179">Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d975-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Méthode pas à pas détaillé de Visual Studio":::

   <span data-ttu-id="9d975-181">À ce stade, la fenêtre **variables locales** indique que le `args` tableau est vide et `name` possède les `date` valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="9d975-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="9d975-182">En outre, Visual Studio a ouvert un terminal vide.</span><span class="sxs-lookup"><span data-stu-id="9d975-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="9d975-183">Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9d975-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9d975-184">Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`.</span><span class="sxs-lookup"><span data-stu-id="9d975-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="9d975-185">La fenêtre **variables locales** affiche la `name` `null` valeur, et le terminal affiche la chaîne « quel est votre nom ? ».</span><span class="sxs-lookup"><span data-stu-id="9d975-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="9d975-186">Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9d975-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="9d975-187">Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9d975-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9d975-188">Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date`.</span><span class="sxs-lookup"><span data-stu-id="9d975-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="9d975-189">La fenêtre **variables locales** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="9d975-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9d975-190">Le terminal affiche la chaîne que vous avez entrée à l’invite.</span><span class="sxs-lookup"><span data-stu-id="9d975-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="9d975-191">Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9d975-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9d975-192">La fenêtre **variables locales** affiche la valeur de la `date` variable après l’affectation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="9d975-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9d975-193">Le terminal est inchangé.</span><span class="sxs-lookup"><span data-stu-id="9d975-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="9d975-194">Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).</span><span class="sxs-lookup"><span data-stu-id="9d975-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="9d975-195">Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d975-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9d975-196">Le terminal affiche la chaîne mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9d975-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="9d975-197">Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>u</kbd> (<kbd>MAJ</kbd> + <kbd>commande</kbd> + <kbd>u</kbd>) ou sélectionnez **exécuter l’exécution**  >  **pas à pas**.</span><span class="sxs-lookup"><span data-stu-id="9d975-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="9d975-198">Le terminal affiche un message et attend que vous appuyiez sur une touche.</span><span class="sxs-lookup"><span data-stu-id="9d975-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="9d975-199">Appuyez sur n’importe quelle touche pour quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="9d975-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="9d975-200">Utiliser la configuration de build Release</span><span class="sxs-lookup"><span data-stu-id="9d975-200">Use Release build configuration</span></span>

<span data-ttu-id="9d975-201">Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release.</span><span class="sxs-lookup"><span data-stu-id="9d975-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="9d975-202">La version Release intègre des optimisations du compilateur qui peuvent affecter négativement le comportement d’une application.</span><span class="sxs-lookup"><span data-stu-id="9d975-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="9d975-203">Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.</span><span class="sxs-lookup"><span data-stu-id="9d975-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="9d975-204">Pour générer et tester la version Release de l’application console, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d975-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="9d975-205">Modifiez la configuration de build dans la barre d’outils de **Debug** à **Release**.</span><span class="sxs-lookup"><span data-stu-id="9d975-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance":::

1. <span data-ttu-id="9d975-207">Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter sans débogage.</span><span class="sxs-lookup"><span data-stu-id="9d975-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9d975-208">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9d975-208">Next steps</span></span>

<span data-ttu-id="9d975-209">Dans ce didacticiel, vous avez utilisé les outils de débogage de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d975-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="9d975-210">Dans le didacticiel suivant, vous allez publier une version déployable de l’application.</span><span class="sxs-lookup"><span data-stu-id="9d975-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d975-211">Publier une application console .NET Core avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="9d975-211">Publish a .NET Core console application with Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
