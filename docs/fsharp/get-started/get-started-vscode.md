---
title: Bien démarrer avec F# dans Visual Studio Code
description: Découvrez comment utiliser F# avec Visual Studio code et la suite de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 91265303c2954387df0f500940c9af68b3c97dac
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559662"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="5c86a-103">Bien démarrer avec F# dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5c86a-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="5c86a-104">Vous pouvez écrire F# en [Visual Studio code](https://code.visualstudio.com) avec le [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour bénéficier d’une expérience de l’environnement de développement intégré (IDE) multiplateforme et légère avec IntelliSense et les refactorisations de code.</span><span class="sxs-lookup"><span data-stu-id="5c86a-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="5c86a-105">Visitez [Ionide.IO](http://ionide.io) pour en savoir plus sur le plug-in.</span><span class="sxs-lookup"><span data-stu-id="5c86a-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="5c86a-106">Pour commencer, assurez-vous que [ F# et le plug-in Ionide sont correctement installés](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="5c86a-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="5c86a-107">Créer votre premier projet avec Ionide</span><span class="sxs-lookup"><span data-stu-id="5c86a-107">Create your first project with Ionide</span></span>

<span data-ttu-id="5c86a-108">Pour créer un F# projet, ouvrez une ligne de commande et créez un projet avec l’CLI .net Core :</span><span class="sxs-lookup"><span data-stu-id="5c86a-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="5c86a-109">Une fois l’opération terminée, accédez au répertoire du projet et ouvrez Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="5c86a-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="5c86a-110">Une fois que le projet est chargé sur Visual Studio Code, le F# volet de Explorateur de solutions à gauche de votre fenêtre doit s’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="5c86a-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="5c86a-111">Cela signifie que Ionide a chargé avec succès le projet que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="5c86a-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="5c86a-112">Vous pouvez écrire du code dans l’éditeur avant ce point dans le temps, mais une fois que cela se produit, tout le chargement est terminé.</span><span class="sxs-lookup"><span data-stu-id="5c86a-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="5c86a-113">Configurer F# interactive</span><span class="sxs-lookup"><span data-stu-id="5c86a-113">Configure F# interactive</span></span>

<span data-ttu-id="5c86a-114">Tout d’abord, assurez-vous que le script .NET Core est votre environnement de script par défaut :</span><span class="sxs-lookup"><span data-stu-id="5c86a-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="5c86a-115">Ouvrez les paramètres du Visual Studio Code (paramètres **du > de** **code** > **paramètres**).</span><span class="sxs-lookup"><span data-stu-id="5c86a-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="5c86a-116">Recherchez le terme  **F# script**.</span><span class="sxs-lookup"><span data-stu-id="5c86a-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="5c86a-117">Cochez la case **FSharp : Use SDK scripts**.</span><span class="sxs-lookup"><span data-stu-id="5c86a-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="5c86a-118">Cela est actuellement nécessaire en raison de comportements hérités dans les scripts basés sur .NET Framework qui ne fonctionnent pas avec les scripts .NET Core, et Ionide s’efforce actuellement de la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="5c86a-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="5c86a-119">À l’avenir, les scripts .NET Core deviendront la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5c86a-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="5c86a-120">Écrire votre premier script R</span><span class="sxs-lookup"><span data-stu-id="5c86a-120">Write your first script</span></span>

<span data-ttu-id="5c86a-121">Une fois que vous avez configuré Visual Studio Code pour utiliser les scripts .NET Core, accédez à l’affichage de l’Explorateur dans Visual Studio Code et créez un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="5c86a-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="5c86a-122">Nommez-le *MyFirstScript. FSX*.</span><span class="sxs-lookup"><span data-stu-id="5c86a-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="5c86a-123">Ajoutez maintenant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5c86a-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="5c86a-124">Cette fonction convertit un mot en une forme de [porc latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="5c86a-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="5c86a-125">L’étape suivante consiste à l’évaluer à F# l’aide de l’interactivité (FSI).</span><span class="sxs-lookup"><span data-stu-id="5c86a-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="5c86a-126">Mettez en surbrillance la fonction entière (il doit s’agir de 11 lignes).</span><span class="sxs-lookup"><span data-stu-id="5c86a-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="5c86a-127">Une fois qu’elle est mise en surbrillance, maintenez la touche **ALT** enfoncée et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="5c86a-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="5c86a-128">Vous remarquerez qu’une fenêtre de terminal s’affiche en bas de l’écran et devrait ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="5c86a-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Exemple de F# sortie interactive avec Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="5c86a-130">Cela faisait trois choses :</span><span class="sxs-lookup"><span data-stu-id="5c86a-130">This did three things:</span></span>

1. <span data-ttu-id="5c86a-131">Il a démarré le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="5c86a-131">It started the FSI process.</span></span>
2. <span data-ttu-id="5c86a-132">Il a envoyé le code que vous avez mis en surbrillance au cours du processus FSI.</span><span class="sxs-lookup"><span data-stu-id="5c86a-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="5c86a-133">Le processus FSI a évalué le code que vous avez envoyé.</span><span class="sxs-lookup"><span data-stu-id="5c86a-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="5c86a-134">Comme ce que vous avez envoyé via était une [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI !</span><span class="sxs-lookup"><span data-stu-id="5c86a-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="5c86a-135">Dans la fenêtre interactive, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="5c86a-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="5c86a-136">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="5c86a-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="5c86a-137">À présent, essayons avec une voyelle comme première lettre.</span><span class="sxs-lookup"><span data-stu-id="5c86a-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="5c86a-138">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c86a-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="5c86a-139">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="5c86a-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="5c86a-140">La fonction semble fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="5c86a-140">The function appears to be working as expected.</span></span> <span data-ttu-id="5c86a-141">Félicitations, vous venez d’écrire votre F# première fonction dans Visual Studio code et de l’évaluer avec FSI !</span><span class="sxs-lookup"><span data-stu-id="5c86a-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="5c86a-142">Comme vous l’avez peut-être remarqué, les lignes du FSI se terminent par `;;`.</span><span class="sxs-lookup"><span data-stu-id="5c86a-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="5c86a-143">Cela est dû au fait que FSI vous permet d’entrer plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="5c86a-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="5c86a-144">La `;;` à la fin permet à la FSI de savoir quand le code est terminé.</span><span class="sxs-lookup"><span data-stu-id="5c86a-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="5c86a-145">Explication du code</span><span class="sxs-lookup"><span data-stu-id="5c86a-145">Explaining the code</span></span>

<span data-ttu-id="5c86a-146">Si vous n’êtes pas sûr de ce que fait le code, voici une procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="5c86a-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="5c86a-147">Comme vous pouvez le voir, `toPigLatin` est une fonction qui prend un mot comme entrée et la convertit en une représentation porc-latin de ce mot.</span><span class="sxs-lookup"><span data-stu-id="5c86a-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="5c86a-148">Les règles applicables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c86a-148">The rules for this are as follows:</span></span>

<span data-ttu-id="5c86a-149">Si le premier caractère d’un mot commence par une voyelle, ajoutez « Ouais » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="5c86a-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="5c86a-150">S’il ne commence pas par une voyelle, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5c86a-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="5c86a-151">Vous avez peut-être remarqué ce qui suit dans FSI :</span><span class="sxs-lookup"><span data-stu-id="5c86a-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="5c86a-152">Cela indique que `toPigLatin` est une fonction qui prend un `string` comme entrée (appelé `word`) et retourne un autre `string`.</span><span class="sxs-lookup"><span data-stu-id="5c86a-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="5c86a-153">C’est ce que l’on appelle la [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un F# élément fondamental de la clé F# de la compréhension du code.</span><span class="sxs-lookup"><span data-stu-id="5c86a-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="5c86a-154">Vous remarquerez également cela si vous pointez sur la fonction dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="5c86a-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="5c86a-155">Dans le corps de la fonction, vous remarquerez deux parties distinctes :</span><span class="sxs-lookup"><span data-stu-id="5c86a-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="5c86a-156">Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à l’un des modèles fournis via des [critères spéciaux](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="5c86a-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="5c86a-157">Expression [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) qui vérifie si le premier caractère est une voyelle et construit une valeur de retour en dehors des caractères d’entrée en fonction de si le premier caractère est une voyelle ou non :</span><span class="sxs-lookup"><span data-stu-id="5c86a-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="5c86a-158">Le déroulement de `toPigLatin` est donc :</span><span class="sxs-lookup"><span data-stu-id="5c86a-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="5c86a-159">Vérifie si le premier caractère du mot d’entrée est une voyelle.</span><span class="sxs-lookup"><span data-stu-id="5c86a-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="5c86a-160">Si c’est le cas, attachez « Ouais » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="5c86a-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="5c86a-161">Dans le cas contraire, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5c86a-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="5c86a-162">Il y a une dernière chose à noter : il n’existe pas d’instruction explicite à retourner à partir de la fonction, contrairement à de nombreux autres langages.</span><span class="sxs-lookup"><span data-stu-id="5c86a-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="5c86a-163">Cela est dû F# au fait que est basé sur une expression et que la dernière expression dans le corps d’une fonction est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="5c86a-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="5c86a-164">Étant donné que `if..then..else` est lui-même une expression, le corps du bloc `then` ou le corps du bloc `else` sera retourné en fonction de la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5c86a-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="5c86a-165">Transformez l’application console en un générateur latin de porc</span><span class="sxs-lookup"><span data-stu-id="5c86a-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="5c86a-166">Les sections précédentes de cet article ont montré une première étape courante dans F# l’écriture de code : écriture d’une fonction initiale et exécution interactive de cette dernière avec le FSI.</span><span class="sxs-lookup"><span data-stu-id="5c86a-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="5c86a-167">C’est ce que l’on appelle le développement basé sur REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) signifie « lecture-évaluation-impression Loop ».</span><span class="sxs-lookup"><span data-stu-id="5c86a-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="5c86a-168">C’est un excellent moyen d’expérimenter les fonctionnalités jusqu’à ce que vous ayez un peu de travail.</span><span class="sxs-lookup"><span data-stu-id="5c86a-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="5c86a-169">L’étape suivante du développement piloté par REPL consiste à déplacer le code de travail F# dans un fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="5c86a-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="5c86a-170">Il peut ensuite être compilé par le F# compilateur dans un assembly qui peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="5c86a-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="5c86a-171">Pour commencer, ouvrez le fichier *Program. FS* que vous avez créé précédemment avec le CLI .net core.</span><span class="sxs-lookup"><span data-stu-id="5c86a-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="5c86a-172">Vous remarquerez que du code existe déjà.</span><span class="sxs-lookup"><span data-stu-id="5c86a-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="5c86a-173">Créez ensuite une [`module`](../language-reference/modules.md) appelée `PigLatin` et copiez la fonction `toPigLatin` que vous avez créée précédemment dans celle-ci :</span><span class="sxs-lookup"><span data-stu-id="5c86a-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="5c86a-174">Ce module doit être au-dessus de la fonction `main` et se trouve en dessous de la déclaration `open System`.</span><span class="sxs-lookup"><span data-stu-id="5c86a-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="5c86a-175">Dans l’ordre des déclarations F#dans, vous devez définir la fonction avant de l’appeler dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="5c86a-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="5c86a-176">Maintenant, dans la fonction `main`, appelez votre fonction de générateur latin de porc sur les arguments :</span><span class="sxs-lookup"><span data-stu-id="5c86a-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="5c86a-177">Vous pouvez maintenant exécuter votre application console à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="5c86a-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="5c86a-178">Vous verrez qu’elle génère le même résultat que votre fichier de script, mais cette fois en tant que programme en cours d’exécution !</span><span class="sxs-lookup"><span data-stu-id="5c86a-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="5c86a-179">Résolution des problèmes Ionide</span><span class="sxs-lookup"><span data-stu-id="5c86a-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="5c86a-180">Voici quelques façons de résoudre certains problèmes que vous pouvez rencontrer :</span><span class="sxs-lookup"><span data-stu-id="5c86a-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="5c86a-181">Pour obtenir les fonctionnalités d’édition de code de Ionide F# , vous devez enregistrer vos fichiers sur le disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="5c86a-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="5c86a-182">Si vous avez apporté des modifications à votre système ou si vous avez installé les composants requis de Ionide avec Visual Studio Code ouvrez, redémarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="5c86a-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="5c86a-183">Si vos répertoires de projet comportent des caractères non valides, Ionide peut ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="5c86a-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="5c86a-184">Si c’est le cas, renommez les répertoires de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5c86a-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="5c86a-185">Si aucune des commandes Ionide ne fonctionne, vérifiez vos [combinaisons de touches de Visual Studio code](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) pour voir si vous les remplacez par accident.</span><span class="sxs-lookup"><span data-stu-id="5c86a-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="5c86a-186">Si Ionide est endommagé sur votre ordinateur et qu’aucun des éléments ci-dessus n’a résolu votre problème, essayez de supprimer le répertoire `ionide-fsharp` sur votre ordinateur et de réinstaller la suite de plug-in.</span><span class="sxs-lookup"><span data-stu-id="5c86a-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="5c86a-187">En cas d’échec du chargement d’un F# projet (la Explorateur de solutions l’affiche), cliquez avec le bouton droit sur le projet et cliquez sur **afficher les détails** pour obtenir plus d’informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="5c86a-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="5c86a-188">Ionide est un projet open source créé et géré par les membres de F# la communauté.</span><span class="sxs-lookup"><span data-stu-id="5c86a-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="5c86a-189">Signalez les problèmes et n’hésitez pas à contribuer au [référentiel ionide-vscode-FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="5c86a-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="5c86a-190">Vous pouvez également demander de l’aide auprès des développeurs et F# de la communauté Ionide dans le [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="5c86a-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5c86a-191">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c86a-191">Next steps</span></span>

<span data-ttu-id="5c86a-192">Pour en savoir plus F# sur et les fonctionnalités du langage, consultez la [visite guidée F#de ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="5c86a-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
