---
title: Prise F# en main de dans Visual Studio code
description: Découvrez comment utiliser F# avec Visual Studio code et la suite de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082985"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="2f1cb-103">Prise F# en main de dans Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="2f1cb-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="2f1cb-104">Vous pouvez écrire F# en [Visual Studio code](https://code.visualstudio.com) avec le [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour bénéficier d’une excellente expérience de l’environnement de développement intégré (IDE) multiplateforme et légère avec IntelliSense et des refactorisations de code de base.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="2f1cb-105">Visitez [Ionide.IO](http://ionide.io) pour en savoir plus sur le plug-in.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="2f1cb-106">Pour commencer, assurez-vous que [ F# et le plug-in Ionide sont correctement installés](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="2f1cb-107">Ionide génère des projets F# .NET Framework, pas dotnet Core, qui peuvent avoir des problèmes de compatibilité entre plateformes.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="2f1cb-108">Si vous exécutez sur **Linux** ou **OSX**, il est plus simple de commencer à utiliser les outils en [ligne de commande](get-started-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="2f1cb-109">Création de votre premier projet avec Ionide</span><span class="sxs-lookup"><span data-stu-id="2f1cb-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="2f1cb-110">Pour créer un nouveau F# projet, ouvrez Visual Studio code dans un nouveau dossier (vous pouvez le nommer comme vous le souhaitez).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="2f1cb-111">Ensuite, ouvrez la palette de commandes (**afficher > palette de commandes**) et tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```console
> F# new project
```

<span data-ttu-id="2f1cb-112">Ce projet est alimenté par le projet [Forge](https://github.com/fsharp-editing/Forge) .</span><span class="sxs-lookup"><span data-stu-id="2f1cb-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="2f1cb-113">Si vous ne voyez pas les options de modèle, essayez d’actualiser les modèles en exécutant la commande `>F#: Refresh Project Templates`suivante dans la palette de commandes :.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="2f1cb-114">Sélectionnez «F#: Nouveau projet» en appuyant sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="2f1cb-115">Vous accédez à l’étape suivante, qui permet de sélectionner un modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="2f1cb-116">Sélectionnez le `classlib` modèle et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="2f1cb-117">Sélectionnez ensuite un répertoire dans lequel créer le projet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="2f1cb-118">Si vous la laissez vide, le répertoire actif est utilisé.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="2f1cb-119">Enfin, nommez votre projet à l’étape finale.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="2f1cb-120">F#utilise la [casse Pascal](http://c2.com/cgi/wiki?PascalCase) pour les noms de projet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="2f1cb-121">Cet article utilise `ClassLibraryDemo` comme nom.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="2f1cb-122">Une fois que vous avez entré le nom souhaité pour votre projet, appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="2f1cb-123">Si vous avez suivi l’étape précédente, vous devez obtenir l’espace de travail Visual Studio Code sur le côté gauche pour qu’il apparaisse comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="2f1cb-124">Le F# projet lui-même, `ClassLibraryDemo` sous le dossier.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="2f1cb-125">Structure de répertoire correcte pour l’ajout de [`Paket`](https://fsprojects.github.io/Paket/)packages via.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="2f1cb-126">Script de génération multiplateforme avec [`FAKE`](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="2f1cb-127">`paket.exe` Fichier exécutable qui peut extraire des packages et résoudre les dépendances pour vous.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="2f1cb-128">Un `.gitignore` fichier si vous souhaitez ajouter ce projet au contrôle de code source git.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="2f1cb-129">Écrire du code</span><span class="sxs-lookup"><span data-stu-id="2f1cb-129">Writing some code</span></span>

<span data-ttu-id="2f1cb-130">Ouvrez le dossier *ClassLibraryDemo* .</span><span class="sxs-lookup"><span data-stu-id="2f1cb-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="2f1cb-131">Les fichiers suivants doivent s’afficher :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-131">You should see the following files:</span></span>

1. <span data-ttu-id="2f1cb-132">`ClassLibraryDemo.fs`, un F# fichier d’implémentation avec une classe définie.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="2f1cb-133">`ClassLibraryDemo.fsproj`, fichier F# projet utilisé pour générer ce projet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="2f1cb-134">`Script.fsx`, un F# fichier de script qui charge le fichier source.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="2f1cb-135">`paket.references`, un fichier Paket qui spécifie les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="2f1cb-136">Ouvrez `Script.fsx`et ajoutez le code suivant à la fin de l’opération :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="2f1cb-137">Cette fonction convertit un mot en une forme de [porc latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="2f1cb-138">L’étape suivante consiste à l’évaluer à F# l’aide de l’interactivité (FSI).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="2f1cb-139">Mettez en surbrillance la fonction entière (il doit s’agir de 11 lignes).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="2f1cb-140">Une fois qu’elle est mise en surbrillance, maintenez la touche **ALT** enfoncée et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="2f1cb-141">Vous remarquerez une fenêtre contextuelle ci-dessous, qui devrait afficher ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Exemple de F# sortie interactive avec Ionide](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="2f1cb-143">Cela faisait trois choses :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-143">This did three things:</span></span>

1. <span data-ttu-id="2f1cb-144">Il a démarré le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-144">It started the FSI process.</span></span>
2. <span data-ttu-id="2f1cb-145">Il a envoyé le code que vous avez mis en surbrillance au cours du processus FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="2f1cb-146">Le processus FSI a évalué le code que vous avez envoyé.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="2f1cb-147">Comme ce que vous avez envoyé via était une [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI !</span><span class="sxs-lookup"><span data-stu-id="2f1cb-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="2f1cb-148">Dans la fenêtre interactive, tapez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="2f1cb-149">Le résultat suivant doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="2f1cb-150">À présent, essayons avec une voyelle comme première lettre.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="2f1cb-151">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="2f1cb-152">Le résultat suivant doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="2f1cb-153">La fonction semble fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-153">The function appears to be working as expected.</span></span> <span data-ttu-id="2f1cb-154">Félicitations, vous venez d’écrire votre F# première fonction dans Visual Studio code et de l’évaluer avec FSI !</span><span class="sxs-lookup"><span data-stu-id="2f1cb-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="2f1cb-155">Comme vous l’avez peut-être remarqué, les lignes du FSI se `;;`terminent par.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="2f1cb-156">Cela est dû au fait que FSI vous permet d’entrer plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="2f1cb-157">Le `;;` à la fin permet à la FSI de savoir à quel moment le code est terminé.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="2f1cb-158">Explication du code</span><span class="sxs-lookup"><span data-stu-id="2f1cb-158">Explaining the code</span></span>

<span data-ttu-id="2f1cb-159">Si vous n’êtes pas sûr de ce que fait le code, voici une procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="2f1cb-160">Comme vous pouvez le voir `toPigLatin` , est une fonction qui prend un mot comme entrée et la convertit en une représentation porc-latin de ce mot.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="2f1cb-161">Les règles applicables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-161">The rules for this are as follows:</span></span>

<span data-ttu-id="2f1cb-162">Si le premier caractère d’un mot commence par une voyelle, ajoutez « Ouais » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="2f1cb-163">S’il ne commence pas par une voyelle, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="2f1cb-164">Vous avez peut-être remarqué ce qui suit dans FSI :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="2f1cb-165">Il s’agit d’une fonction qui prend une `string` entrée comme entrée (appelée `word`) et retourne une autre `string`. `toPigLatin`</span><span class="sxs-lookup"><span data-stu-id="2f1cb-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="2f1cb-166">C’est ce que l’on appelle la [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un F# élément fondamental de la clé F# de la compréhension du code.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="2f1cb-167">Vous remarquerez également cela si vous pointez sur la fonction dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="2f1cb-168">Dans le corps de la fonction, vous remarquerez deux parties distinctes :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="2f1cb-169">Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à l’un des modèles fournis via des [critères spéciaux](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="2f1cb-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="2f1cb-170">[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) Expression qui vérifie si le premier caractère est une voyelle et construit une valeur de retour à partir des caractères d’entrée en fonction de si le premier caractère est une voyelle ou non :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="2f1cb-171">Le déroulement de `toPigLatin` est donc :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="2f1cb-172">Vérifie si le premier caractère du mot d’entrée est une voyelle.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="2f1cb-173">Si c’est le cas, attachez « Ouais » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="2f1cb-174">Dans le cas contraire, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="2f1cb-175">Il y a une dernière chose à noter : il n’existe pas d’instruction explicite à retourner à partir de la fonction, contrairement à de nombreux autres langages.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="2f1cb-176">Cela est dû F# au fait que est basé sur une expression et que la dernière expression dans le corps d’une fonction est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="2f1cb-177">Étant `if..then..else` donné que est lui-même une expression, `then` le corps du bloc `else` ou le corps du bloc sont retournés en fonction de la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="2f1cb-178">Déplacement de votre code de script dans le fichier d’implémentation</span><span class="sxs-lookup"><span data-stu-id="2f1cb-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="2f1cb-179">Les sections précédentes de cet article ont montré une première étape courante dans F# l’écriture de code : écriture d’une fonction initiale et exécution interactive de cette dernière avec le FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="2f1cb-180">C’est ce que l’on appelle le développement basé sur REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) signifie « lecture-évaluation-impression Loop ».</span><span class="sxs-lookup"><span data-stu-id="2f1cb-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="2f1cb-181">C’est un excellent moyen d’expérimenter les fonctionnalités jusqu’à ce que vous ayez un peu de travail.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="2f1cb-182">L’étape suivante du développement piloté par REPL consiste à déplacer le code de travail F# dans un fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="2f1cb-183">Il peut ensuite être compilé par le F# compilateur dans un assembly qui peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="2f1cb-184">Pour commencer, ouvrez `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="2f1cb-185">Vous remarquerez que du code existe déjà.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="2f1cb-186">Poursuivez et supprimez la définition de classe, mais veillez à [`namespace`](../language-reference/namespaces.md) conserver la déclaration en haut.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="2f1cb-187">Ensuite, créez un nouveau [`module`](../language-reference/modules.md) nommé `PigLatin` et copiez `toPigLatin` -y la fonction comme suit :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="2f1cb-188">Ensuite, rouvrez le `Script.fsx` fichier et supprimez la fonction entière `toPigLatin` , mais veillez à conserver les deux lignes suivantes dans le fichier :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="2f1cb-189">Sélectionnez les deux lignes de texte et appuyez sur Alt + Entrée pour exécuter ces lignes dans FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="2f1cb-190">Celles-ci chargent le contenu de la bibliothèque latin de porc dans le `open` processus `ClassLibraryDemo` FSI et l’espace de noms afin que vous ayez accès aux fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="2f1cb-191">Ensuite, dans la fenêtre FSI, appelez la fonction avec le `PigLatin` module que vous avez défini précédemment :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="2f1cb-192">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="2f1cb-192">Success!</span></span> <span data-ttu-id="2f1cb-193">Vous recevez les mêmes résultats qu’avant, mais maintenant chargé à partir F# d’un fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="2f1cb-194">La principale différence réside dans le F# fait que les fichiers sources sont compilés dans des assemblys qui peuvent être exécutés n’importe où, pas seulement dans le FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="2f1cb-195">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="2f1cb-195">Summary</span></span>

<span data-ttu-id="2f1cb-196">Dans cet article, vous avez appris ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="2f1cb-197">Comment configurer Visual Studio Code avec Ionide.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="2f1cb-198">Comment créer votre premier F# projet avec Ionide.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="2f1cb-199">Comment utiliser F# les scripts pour écrire votre première F# fonction dans Ionide, puis l’exécuter dans le FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="2f1cb-200">Comment migrer votre code de script F# vers la source, puis appeler ce code à partir de FSI.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="2f1cb-201">Vous êtes maintenant prêt à écrire un plus F# grand nombre de code à l’aide de Visual Studio code et Ionide.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2f1cb-202">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="2f1cb-202">Troubleshooting</span></span>

<span data-ttu-id="2f1cb-203">Voici quelques façons de résoudre certains problèmes que vous pouvez rencontrer :</span><span class="sxs-lookup"><span data-stu-id="2f1cb-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="2f1cb-204">Pour obtenir les fonctionnalités d’édition de code de Ionide F# , vous devez enregistrer vos fichiers sur le disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="2f1cb-205">Si vous avez apporté des modifications à votre système ou si vous avez installé les composants requis de Ionide avec Visual Studio Code ouvrez, redémarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="2f1cb-206">Vérifiez que vous pouvez utiliser le F# compilateur et F# interactif à partir de la ligne de commande sans un chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="2f1cb-207">Pour ce faire, vous pouvez `fsc` taper dans une ligne de commande F# pour le compilateur `fsi` , `fsharpi` et ou pour F# les outils visuels sur Windows et mono sur Mac/Linux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="2f1cb-208">Si vos répertoires de projet comportent des caractères non valides, Ionide peut ne pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="2f1cb-209">Si c’est le cas, renommez les répertoires de votre projet.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="2f1cb-210">Si aucune des commandes Ionide ne fonctionne, vérifiez les [combinaisons de touches](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) de votre Visual Studio code pour voir si vous les remplacez par accident.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="2f1cb-211">Si Ionide est endommagé sur votre ordinateur et qu’aucun des éléments ci-dessus n’a résolu votre problème `ionide-fsharp` , essayez de supprimer le répertoire sur votre ordinateur et de réinstaller la suite de plug-in.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="2f1cb-212">Ionide est un projet open source créé et géré par les membres de F# la communauté.</span><span class="sxs-lookup"><span data-stu-id="2f1cb-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="2f1cb-213">Signalez les [problèmes et n’hésitez pas à contribuer au Ionide-VSCode : Référentiel GitHub FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="2f1cb-214">Si vous avez un problème à signaler, suivez [les instructions pour obtenir les journaux à utiliser lors du signalement d’un problème](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="2f1cb-215">Vous pouvez également demander de l’aide auprès des développeurs et F# de la communauté Ionide dans le [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f1cb-216">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2f1cb-216">Next steps</span></span>

<span data-ttu-id="2f1cb-217">Pour en savoir plus F# sur et les fonctionnalités du langage, consultez la [visite guidée F#de ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="2f1cb-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
