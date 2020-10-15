---
title: Bien démarrer avec F# dans Visual Studio Code
description: 'Découvrez comment utiliser F # avec Visual Studio Code et la suite de plug-in Ionide.'
ms.date: 12/23/2018
ms.openlocfilehash: 3317d0037d3c14a6b55079385d7b27e499c0c392
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050544"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="b8ca8-103">Bien démarrer avec F# dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b8ca8-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="b8ca8-104">Vous pouvez écrire du code F # dans [Visual Studio code](https://code.visualstudio.com) avec le [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour obtenir une expérience de l’environnement de développement intégré (IDE) multiplateforme et légère avec IntelliSense et les refactorisations de code.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="b8ca8-105">Visitez [Ionide.IO](https://ionide.io) pour en savoir plus sur le plug-in.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-105">Visit [Ionide.io](https://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="b8ca8-106">Pour commencer, assurez-vous que [F # et le plug-in Ionide sont correctement installés](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="b8ca8-107">Créer votre premier projet avec Ionide</span><span class="sxs-lookup"><span data-stu-id="b8ca8-107">Create your first project with Ionide</span></span>

<span data-ttu-id="b8ca8-108">Pour créer un projet F #, ouvrez une ligne de commande et créez un projet avec l’CLI .NET Core :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="b8ca8-109">Une fois l’opération terminée, accédez au répertoire du projet et ouvrez Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="b8ca8-110">Une fois le projet chargé sur Visual Studio Code, vous devez voir le volet de Explorateur de solutions F # sur le côté gauche de votre fenêtre ouvert.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="b8ca8-111">Cela signifie que Ionide a chargé avec succès le projet que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="b8ca8-112">Vous pouvez écrire du code dans l’éditeur avant ce point dans le temps, mais une fois que cela se produit, tout le chargement est terminé.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="b8ca8-113">Configurer F # Interactive</span><span class="sxs-lookup"><span data-stu-id="b8ca8-113">Configure F# interactive</span></span>

<span data-ttu-id="b8ca8-114">Tout d’abord, assurez-vous que le script .NET Core est votre environnement de script par défaut :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="b8ca8-115">Ouvrez les paramètres du Visual Studio code (paramètres des préférences de**code**  >  **Preferences**  >  **Settings**).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="b8ca8-116">Recherchez le terme **script F #**.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="b8ca8-117">Cochez la case **FSharp : Use SDK scripts**.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="b8ca8-118">Cela est actuellement nécessaire en raison de comportements hérités dans les scripts basés sur .NET Framework qui ne fonctionnent pas avec les scripts .NET Core, et Ionide s’efforce actuellement de la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="b8ca8-119">À l’avenir, les scripts .NET Core deviendront la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="b8ca8-120">Écrire votre premier script R</span><span class="sxs-lookup"><span data-stu-id="b8ca8-120">Write your first script</span></span>

<span data-ttu-id="b8ca8-121">Une fois que vous avez configuré Visual Studio Code pour utiliser les scripts .NET Core, accédez à l’affichage de l’Explorateur dans Visual Studio Code et créez un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="b8ca8-122">Nommez-le *MyFirstScript. FSX*.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="b8ca8-123">Ajoutez maintenant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="b8ca8-124">Cette fonction convertit un mot en une forme de [porc latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="b8ca8-125">L’étape suivante consiste à l’évaluer à l’aide de F# Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="b8ca8-126">Mettez en surbrillance la fonction entière (il doit s’agir de 11 lignes).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="b8ca8-127">Une fois qu’elle est mise en surbrillance, maintenez la touche **ALT** enfoncée et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="b8ca8-128">Vous remarquerez qu’une fenêtre de terminal s’affiche en bas de l’écran et devrait ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![Exemple de sortie de F# Interactive avec Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="b8ca8-130">Cela faisait trois choses :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-130">This did three things:</span></span>

1. <span data-ttu-id="b8ca8-131">Il a démarré le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-131">It started the FSI process.</span></span>
2. <span data-ttu-id="b8ca8-132">Il a envoyé le code que vous avez mis en surbrillance au cours du processus FSI.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="b8ca8-133">Le processus FSI a évalué le code que vous avez envoyé.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="b8ca8-134">Comme ce que vous avez envoyé via était une [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI !</span><span class="sxs-lookup"><span data-stu-id="b8ca8-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="b8ca8-135">Dans la fenêtre interactive, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="b8ca8-136">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="b8ca8-137">À présent, essayons avec une voyelle comme première lettre.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="b8ca8-138">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="b8ca8-139">Le résultat suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="b8ca8-140">La fonction semble fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-140">The function appears to be working as expected.</span></span> <span data-ttu-id="b8ca8-141">Félicitations, vous venez d’écrire votre première fonction F # dans Visual Studio Code et de l’évaluer avec FSI !</span><span class="sxs-lookup"><span data-stu-id="b8ca8-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="b8ca8-142">Comme vous l’avez peut-être remarqué, les lignes du FSI se terminent par `;;` .</span><span class="sxs-lookup"><span data-stu-id="b8ca8-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="b8ca8-143">Cela est dû au fait que FSI vous permet d’entrer plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="b8ca8-144">Le `;;` à la fin permet à la FSI de savoir à quel moment le code est terminé.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="b8ca8-145">Explication du code</span><span class="sxs-lookup"><span data-stu-id="b8ca8-145">Explaining the code</span></span>

<span data-ttu-id="b8ca8-146">Si vous n’êtes pas sûr de ce que fait le code, voici une procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="b8ca8-147">Comme vous pouvez le voir, `toPigLatin` est une fonction qui prend un mot comme entrée et la convertit en une représentation Pig-Latin de ce mot.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="b8ca8-148">Les règles applicables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-148">The rules for this are as follows:</span></span>

<span data-ttu-id="b8ca8-149">Si le premier caractère d’un mot commence par une voyelle, ajoutez « Ouais » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="b8ca8-150">S’il ne commence pas par une voyelle, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="b8ca8-151">Vous avez peut-être remarqué ce qui suit dans FSI :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="b8ca8-152">Il `toPigLatin` s’agit d’une fonction qui prend une `string` entrée comme entrée (appelée `word` ) et retourne une autre `string` .</span><span class="sxs-lookup"><span data-stu-id="b8ca8-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="b8ca8-153">C’est ce que l’on appelle la [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un élément fondamental de f # qui est essentiel pour comprendre le code f #.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="b8ca8-154">Vous remarquerez également cela si vous pointez sur la fonction dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="b8ca8-155">Dans le corps de la fonction, vous remarquerez deux parties distinctes :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="b8ca8-156">Une fonction interne, appelée `isVowel` , qui détermine si un caractère donné ( `c` ) est une voyelle en vérifiant si elle correspond à l’un des modèles fournis via des [critères spéciaux](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="b8ca8-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="b8ca8-157">[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)Expression qui vérifie si le premier caractère est une voyelle et construit une valeur de retour à partir des caractères d’entrée en fonction de si le premier caractère est une voyelle ou non :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="b8ca8-158">Le déroulement de `toPigLatin` est donc :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="b8ca8-159">Vérifie si le premier caractère du mot d’entrée est une voyelle.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="b8ca8-160">Si c’est le cas, attachez « Ouais » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="b8ca8-161">Dans le cas contraire, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="b8ca8-162">Il y a une dernière chose à noter : en F #, il n’y a pas d’instruction explicite à retourner à partir de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-162">There's one final thing to notice about this: in F#, there's no explicit instruction to return from the function.</span></span> <span data-ttu-id="b8ca8-163">En effet, F # est basé sur une expression et la dernière expression évaluée dans le corps d’une fonction détermine la valeur de retour de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-163">This is because F# is expression-based, and the last expression evaluated in the body of a function determines the return value of that function.</span></span> <span data-ttu-id="b8ca8-164">Étant donné que `if..then..else` est lui-même une expression, l’évaluation du corps du `then` bloc ou le corps du `else` bloc détermine la valeur retournée par la `toPigLatin` fonction.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-164">Because `if..then..else` is itself an expression, evaluation of the body of the `then` block or the body of the `else` block determines the value returned by the `toPigLatin` function.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="b8ca8-165">Transformez l’application console en un générateur latin de porc</span><span class="sxs-lookup"><span data-stu-id="b8ca8-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="b8ca8-166">Les sections précédentes de cet article ont montré une première étape courante dans l’écriture de code F # : écriture d’une fonction initiale et exécution interactive de cette dernière avec FSI.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="b8ca8-167">C’est ce que l’on appelle le développement basé sur REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) signifie « lecture-évaluation-impression Loop ».</span><span class="sxs-lookup"><span data-stu-id="b8ca8-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="b8ca8-168">C’est un excellent moyen d’expérimenter les fonctionnalités jusqu’à ce que vous ayez un peu de travail.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="b8ca8-169">L’étape suivante du développement piloté par REPL consiste à déplacer le code de travail dans un fichier d’implémentation F #.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="b8ca8-170">Il peut ensuite être compilé par le compilateur F # dans un assembly qui peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="b8ca8-171">Pour commencer, ouvrez le fichier *Program. FS* que vous avez créé précédemment avec le CLI .net core.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="b8ca8-172">Vous remarquerez que du code existe déjà.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="b8ca8-173">Ensuite, créez un nouveau [`module`](../language-reference/modules.md) nommé `PigLatin` et copiez la `toPigLatin` fonction que vous avez créée précédemment dans celui-ci en tant que tel :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="b8ca8-174">Ce module doit être au-dessus de la `main` fonction et se trouver sous la `open System` déclaration.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="b8ca8-175">L’ordre des déclarations est important en F #. vous devez donc définir la fonction avant de l’appeler dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="b8ca8-176">Maintenant, dans la `main` fonction, appelez la fonction de générateur latin du porc sur les arguments :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="b8ca8-177">Vous pouvez maintenant exécuter votre application console à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="b8ca8-178">Vous verrez qu’elle génère le même résultat que votre fichier de script, mais cette fois en tant que programme en cours d’exécution !</span><span class="sxs-lookup"><span data-stu-id="b8ca8-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="b8ca8-179">Résolution des problèmes Ionide</span><span class="sxs-lookup"><span data-stu-id="b8ca8-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="b8ca8-180">Voici quelques façons de résoudre certains problèmes que vous pouvez rencontrer :</span><span class="sxs-lookup"><span data-stu-id="b8ca8-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="b8ca8-181">Pour obtenir les fonctionnalités d’édition de code de Ionide, vos fichiers F # doivent être enregistrés sur le disque et se trouver à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="b8ca8-182">Si vous avez apporté des modifications à votre système ou si vous avez installé les composants requis de Ionide avec Visual Studio Code ouvrez, redémarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="b8ca8-183">Si vos répertoires de projet comportent des caractères non valides, Ionide peut ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="b8ca8-184">Si c’est le cas, renommez les répertoires de votre projet.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="b8ca8-185">Si aucune des commandes Ionide ne fonctionne, vérifiez vos [combinaisons de touches de Visual Studio code](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) pour voir si vous les remplacez par accident.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="b8ca8-186">Si Ionide est endommagé sur votre ordinateur et qu’aucun des éléments ci-dessus n’a résolu votre problème, essayez de supprimer le `ionide-fsharp` répertoire sur votre ordinateur et de réinstaller la suite de plug-in.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="b8ca8-187">En cas d’échec du chargement d’un projet (F # Explorateur de solutions l’affiche), cliquez avec le bouton droit sur ce projet et cliquez sur **afficher les détails** pour obtenir plus d’informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="b8ca8-188">Ionide est un projet open source créé et géré par les membres de la communauté F #.</span><span class="sxs-lookup"><span data-stu-id="b8ca8-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="b8ca8-189">Signalez les problèmes et n’hésitez pas à contribuer au [référentiel ionide-vscode-FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="b8ca8-190">Vous pouvez également demander de l’aide auprès des développeurs Ionide et de la communauté F # dans le [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8ca8-191">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b8ca8-191">Next steps</span></span>

<span data-ttu-id="b8ca8-192">Pour en savoir plus sur F # et les fonctionnalités du langage, consultez [visite guidée de f #](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="b8ca8-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
