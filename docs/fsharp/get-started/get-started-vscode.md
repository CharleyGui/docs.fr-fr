---
title: Prise en main F# dans Visual Studio Code
description: Découvrez comment utiliser F# avec Visual Studio Code et la suite de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: d9d5ed4008f657f956ee7a5611a2f5fdd8e5b44a
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051876"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="e9736-103">Prise en main F# dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e9736-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="e9736-104">Vous pouvez écrire F# dans [Visual Studio Code](https://code.visualstudio.com) avec la [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour obtenir une bonne expérience d’un environnement de développement intégré (IDE), multiplateforme et léger, des IntelliSense et le code de base refactorisations.</span><span class="sxs-lookup"><span data-stu-id="e9736-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="e9736-105">Visitez [Ionide.io](http://ionide.io) pour en savoir plus sur le plug-in.</span><span class="sxs-lookup"><span data-stu-id="e9736-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="e9736-106">Pour commencer, assurez-vous d’avoir [ F# et le plug-in Ionide correctement installé](install-fsharp.md#install-f-with-visual-studio-code).</span><span class="sxs-lookup"><span data-stu-id="e9736-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="e9736-107">Ionide générera le .NET Framework F# projets, pas sur dotnet core, ce qui peut avoir des problèmes de compatibilité entre les plate-formes.</span><span class="sxs-lookup"><span data-stu-id="e9736-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="e9736-108">Si vous exécutez sur **Linux** ou **OSX**, prise en main d’un moyen plus simple consiste à utiliser le [des outils de ligne de commande](get-started-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="e9736-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="e9736-109">Créer votre premier projet avec Ionide</span><span class="sxs-lookup"><span data-stu-id="e9736-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="e9736-110">Pour créer un nouveau F# projet d’équipe, ouvrez Visual Studio Code dans un nouveau dossier (vous pouvez le nommer comme vous le souhaitez).</span><span class="sxs-lookup"><span data-stu-id="e9736-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="e9736-111">Ensuite, ouvrez la palette de commandes (**vue > Palette de commandes**) et tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e9736-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="e9736-112">Cela est alimenté par le [FORGE](https://github.com/fsharp-editing/Forge) projet.</span><span class="sxs-lookup"><span data-stu-id="e9736-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="e9736-113">Si vous ne voyez pas les options de modèle, essayez d’actualiser les modèles en exécutant la commande suivante dans la Palette de commandes : `>F#: Refresh Project Templates`.</span><span class="sxs-lookup"><span data-stu-id="e9736-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="e9736-114">Sélectionnez «F#: En appuyant sur un nouveau projet » **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e9736-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="e9736-115">Vous accédez à l’étape suivante, ce qui concerne la sélection d’un modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="e9736-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="e9736-116">Choisir le `classlib` modèle et le positionnement **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e9736-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="e9736-117">Ensuite, choisissez un répertoire pour créer le projet dans.</span><span class="sxs-lookup"><span data-stu-id="e9736-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="e9736-118">Si vous laissez vide, il utilise le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="e9736-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="e9736-119">Enfin, nommez votre projet dans l’étape finale.</span><span class="sxs-lookup"><span data-stu-id="e9736-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="e9736-120">F#utilise [casse Pascal](http://c2.com/cgi/wiki?PascalCase) pour les noms de projet.</span><span class="sxs-lookup"><span data-stu-id="e9736-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="e9736-121">Cet article utilise `ClassLibraryDemo` comme nom.</span><span class="sxs-lookup"><span data-stu-id="e9736-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="e9736-122">Une fois que vous avez entré le nom souhaité pour votre projet, appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e9736-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="e9736-123">Si vous avez suivi l’étape précédente, vous devez obtenir le Visual Studio Code espace de travail sur le côté gauche apparaissent avec les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e9736-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="e9736-124">Le F# projet lui-même, en dessous du `ClassLibraryDemo` dossier.</span><span class="sxs-lookup"><span data-stu-id="e9736-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="e9736-125">La structure de répertoire correct pour l’ajout de packages via [ `Paket` ](https://fsprojects.github.io/Paket/).</span><span class="sxs-lookup"><span data-stu-id="e9736-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="e9736-126">Un multiplates-générer le script avec [ `FAKE` ](https://fsharp.github.io/FAKE/).</span><span class="sxs-lookup"><span data-stu-id="e9736-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="e9736-127">Le `paket.exe` exécutable qui peut extraire les packages et résoudre les dépendances pour vous.</span><span class="sxs-lookup"><span data-stu-id="e9736-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="e9736-128">Un `.gitignore` fichier si vous souhaitez ajouter ce projet au contrôle de code source Git.</span><span class="sxs-lookup"><span data-stu-id="e9736-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="e9736-129">Écrire du code</span><span class="sxs-lookup"><span data-stu-id="e9736-129">Writing some code</span></span>

<span data-ttu-id="e9736-130">Ouvrez le *ClassLibraryDemo* dossier.</span><span class="sxs-lookup"><span data-stu-id="e9736-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="e9736-131">Vous devez voir les fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="e9736-131">You should see the following files:</span></span>

1. <span data-ttu-id="e9736-132">`ClassLibraryDemo.fs`, un F# fichier d’implémentation avec une classe définie.</span><span class="sxs-lookup"><span data-stu-id="e9736-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="e9736-133">`ClassLibraryDemo.fsproj`, un F# fichier projet utilisé pour générer ce projet.</span><span class="sxs-lookup"><span data-stu-id="e9736-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="e9736-134">`Script.fsx`, un F# fichier de script qui charge le fichier source.</span><span class="sxs-lookup"><span data-stu-id="e9736-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="e9736-135">`paket.references`, un fichier Paket qui spécifie les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="e9736-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="e9736-136">Ouvrez `Script.fsx`et ajoutez le code suivant à la fin de celle-ci :</span><span class="sxs-lookup"><span data-stu-id="e9736-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="e9736-137">Cette fonction convertit un mot à un formulaire de [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span><span class="sxs-lookup"><span data-stu-id="e9736-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="e9736-138">L’étape suivante consiste à évaluer à l’aide de F# Interactive (FSI).</span><span class="sxs-lookup"><span data-stu-id="e9736-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="e9736-139">Mettez en surbrillance de la fonction entière (il doit être 11 lignes longues).</span><span class="sxs-lookup"><span data-stu-id="e9736-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="e9736-140">Une fois qu’elle est mise en surbrillance, maintenez la **Alt** clé, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="e9736-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="e9736-141">Vous remarquerez une fenêtre contextuelle ci-dessous, et il doit s’afficher quelque chose comme ceci :</span><span class="sxs-lookup"><span data-stu-id="e9736-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![Exemple de F# Interactive avec Ionide de sortie](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="e9736-143">Cela fait trois choses :</span><span class="sxs-lookup"><span data-stu-id="e9736-143">This did three things:</span></span>

1. <span data-ttu-id="e9736-144">Il a démarré le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-144">It started the FSI process.</span></span>
2. <span data-ttu-id="e9736-145">Il envoyé le code que vous avez sélectionnée sur le processus FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="e9736-146">Le processus FSI évalué le code que vous avez envoyé via.</span><span class="sxs-lookup"><span data-stu-id="e9736-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="e9736-147">Étant donné que ce que vous avez envoyé via a été un [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI !</span><span class="sxs-lookup"><span data-stu-id="e9736-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="e9736-148">Dans la fenêtre interactive, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e9736-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="e9736-149">Vous devez voir le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="e9736-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="e9736-150">À présent, essayons avec une voyelle en tant que la première lettre.</span><span class="sxs-lookup"><span data-stu-id="e9736-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="e9736-151">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e9736-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="e9736-152">Vous devez voir le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="e9736-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="e9736-153">La fonction semble fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="e9736-153">The function appears to be working as expected.</span></span> <span data-ttu-id="e9736-154">Félicitations, vous venez d’écrire votre première F# fonctionner dans Visual Studio Code et il évaluée avec FSI !</span><span class="sxs-lookup"><span data-stu-id="e9736-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="e9736-155">Comme vous l’avez peut-être remarqué, les lignes dans FSI sont terminent par `;;`.</span><span class="sxs-lookup"><span data-stu-id="e9736-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="e9736-156">Il s’agit, car FSI vous permet d’entrer plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="e9736-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="e9736-157">Le `;;` à la fin informe FSI lorsque le code est terminé.</span><span class="sxs-lookup"><span data-stu-id="e9736-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="e9736-158">Explication du code</span><span class="sxs-lookup"><span data-stu-id="e9736-158">Explaining the code</span></span>

<span data-ttu-id="e9736-159">Si vous n’êtes pas sûr de ce que le code est en fait, Voici un pas à pas.</span><span class="sxs-lookup"><span data-stu-id="e9736-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="e9736-160">Comme vous pouvez le voir, `toPigLatin` est une fonction qui accepte un mot comme entrée et le convertit en une représentation sous forme de Pig Latin de ce mot.</span><span class="sxs-lookup"><span data-stu-id="e9736-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="e9736-161">Les règles pour ce sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e9736-161">The rules for this are as follows:</span></span>

<span data-ttu-id="e9736-162">Si le premier caractère dans un mot commence par une voyelle, ajoutez « hourra » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="e9736-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="e9736-163">Si elle ne commence pas par une voyelle, déplacer ce premier caractère à la fin du mot et « ay » lui ajouter.</span><span class="sxs-lookup"><span data-stu-id="e9736-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="e9736-164">Vous avez peut-être remarqué ce qui suit dans FSI :</span><span class="sxs-lookup"><span data-stu-id="e9736-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="e9736-165">Cela indique que `toPigLatin` est une fonction qui accepte un `string` en tant qu’entrée (appelé `word`), ainsi qu’un autre `string`.</span><span class="sxs-lookup"><span data-stu-id="e9736-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="e9736-166">Il s’agit du [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un élément fondamental de F# qui est essentielle pour comprendre F# code.</span><span class="sxs-lookup"><span data-stu-id="e9736-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="e9736-167">Vous pouvez également constater si vous pointez sur la fonction dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e9736-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="e9736-168">Dans le corps de la fonction, vous remarquerez deux parties distinctes :</span><span class="sxs-lookup"><span data-stu-id="e9736-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="e9736-169">Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à un des modèles fournis par le biais de [critères spéciaux](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="e9736-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="e9736-170">Un [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) expression qui vérifie si le premier caractère est une voyelle et les constructions de la valeur renvoyée hors les caractères d’entrée selon que le premier caractère a été une voyelle ou non :</span><span class="sxs-lookup"><span data-stu-id="e9736-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="e9736-171">Le flux de `toPigLatin` est donc :</span><span class="sxs-lookup"><span data-stu-id="e9736-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="e9736-172">Vérifiez si le premier caractère du mot d’entrée est une voyelle.</span><span class="sxs-lookup"><span data-stu-id="e9736-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="e9736-173">Dans le cas, attachez « hourra » à la fin du mot.</span><span class="sxs-lookup"><span data-stu-id="e9736-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="e9736-174">Sinon, déplacez ce premier caractère à la fin du mot et « ay » lui ajouter.</span><span class="sxs-lookup"><span data-stu-id="e9736-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="e9736-175">Il existe une dernière chose à noter à ce sujet : il n’existe aucune instruction explicite à retourner à partir de la fonction, contrairement à nombreux autres langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="e9736-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="e9736-176">Il s’agit, car F# est basé sur l’Expression, et la dernière expression dans le corps d’une fonction est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="e9736-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="e9736-177">Étant donné que `if..then..else` lui-même est une expression, le corps de la `then` bloc ou dans le corps de la `else` bloc s’affichera en fonction de la valeur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e9736-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="e9736-178">Déplacement de votre code de script dans le fichier d’implémentation</span><span class="sxs-lookup"><span data-stu-id="e9736-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="e9736-179">Les sections précédentes de cet article démontré une première étape dans l’écriture courantes F# code : écriture d’une fonction initiale et l’exécuter interactivement avec FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="e9736-180">On parle de développement piloté par les REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) est l’acronyme « Read-Evaluate-Print boucle ».</span><span class="sxs-lookup"><span data-stu-id="e9736-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="e9736-181">Il est un excellent moyen de faire des essais avec des fonctionnalités jusqu'à ce que vous avez quelque chose fonctionne.</span><span class="sxs-lookup"><span data-stu-id="e9736-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="e9736-182">L’étape suivante dans le développement piloté par REPL consiste à déplacer le code de travail dans un F# fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="e9736-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="e9736-183">Il peut ensuite être compilé par le F# compilateur dans un assembly qui peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="e9736-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="e9736-184">Pour commencer, ouvrez `ClassLibraryDemo.fs`.</span><span class="sxs-lookup"><span data-stu-id="e9736-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="e9736-185">Vous remarquerez que du code existe déjà dans.</span><span class="sxs-lookup"><span data-stu-id="e9736-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="e9736-186">Continuer et supprimer la définition de classe, mais veillez à laisser le [ `namespace` ](../language-reference/namespaces.md) déclaration en haut.</span><span class="sxs-lookup"><span data-stu-id="e9736-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="e9736-187">Ensuite, créez un nouveau [ `module` ](../language-reference/modules.md) appelé `PigLatin` et copiez le `toPigLatin` fonction dedans ainsi :</span><span class="sxs-lookup"><span data-stu-id="e9736-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="e9736-188">Ensuite, ouvrez le `Script.fsx` à nouveau de fichiers et de supprimer l’intégralité de `toPigLatin` de fonctionner, mais veillez à conserver les deux lignes suivantes dans le fichier :</span><span class="sxs-lookup"><span data-stu-id="e9736-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="e9736-189">Sélectionnez les deux lignes de texte et appuyez sur Alt + Entrée pour exécuter ces lignes dans FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="e9736-190">Ces chargera le contenu de la bibliothèque Pig Latin dans le processus FSI et `open` le `ClassLibraryDemo` espace de noms afin que vous avez accès à la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e9736-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="e9736-191">Ensuite, dans la fenêtre FSI, appelez la fonction avec le `PigLatin` module que vous avez défini précédemment :</span><span class="sxs-lookup"><span data-stu-id="e9736-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="e9736-192">Opération réussie</span><span class="sxs-lookup"><span data-stu-id="e9736-192">Success!</span></span> <span data-ttu-id="e9736-193">Vous obtenez les mêmes résultats que précédemment, mais maintenant chargé à partir d’un F# fichier d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="e9736-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="e9736-194">La principale différence ici est que F# fichiers source sont compilés dans des assemblys qui peuvent être exécutées n’importe où, pas seulement dans FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="e9736-195">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="e9736-195">Summary</span></span>

<span data-ttu-id="e9736-196">Dans cet article, vous avez appris :</span><span class="sxs-lookup"><span data-stu-id="e9736-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="e9736-197">Comment configurer Visual Studio Code avec Ionide.</span><span class="sxs-lookup"><span data-stu-id="e9736-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="e9736-198">Comment créer votre première F# projet avec Ionide.</span><span class="sxs-lookup"><span data-stu-id="e9736-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="e9736-199">Comment utiliser F# script pour écrire votre première F# Ionide de fonction, puis l’exécuter dans FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="e9736-200">Comment migrer votre code de script F# source, puis appelez ce code à partir de FSI.</span><span class="sxs-lookup"><span data-stu-id="e9736-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="e9736-201">Vous êtes désormais équipés pour écrire bien plus encore F# code à l’aide de Visual Studio Code et Ionide.</span><span class="sxs-lookup"><span data-stu-id="e9736-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e9736-202">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="e9736-202">Troubleshooting</span></span>

<span data-ttu-id="e9736-203">Voici quelques façons que vous pouvez résoudre certains problèmes que vous pouvez rencontrer :</span><span class="sxs-lookup"><span data-stu-id="e9736-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="e9736-204">Pour obtenir les fonctionnalités de Ionide, de modification du code votre F# fichiers doivent être enregistrés sur disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e9736-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="e9736-205">Si vous avez apporté des modifications à votre système ou installé des composants requis de Ionide avec Visual Studio Code open, redémarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e9736-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="e9736-206">Vérifiez que vous pouvez utiliser le F# compilateur et F# interactive à partir de la ligne de commande sans un chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="e9736-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="e9736-207">Vous pouvez le faire en tapant `fsc` dans une ligne de commande pour le F# compilateur, et `fsi` ou `fsharpi` pour l’élément visuel F# outils sur Windows et Mono sur Mac/Linux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e9736-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="e9736-208">Si vous avez des caractères non valides dans vos répertoires de projet, Ionide peut ne pas fonctionne.</span><span class="sxs-lookup"><span data-stu-id="e9736-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="e9736-209">Renommez vos répertoires de projet si c’est le cas.</span><span class="sxs-lookup"><span data-stu-id="e9736-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="e9736-210">Si aucun des commandes Ionide travaillez, vérifiez votre [les combinaisons de touches Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) pour voir si vous êtes les remplaçant par inadvertance.</span><span class="sxs-lookup"><span data-stu-id="e9736-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="e9736-211">Si Ionide est rompue sur votre ordinateur et aucun d'entre eux a résolu votre problème, essayez de supprimer le `ionide-fsharp` répertoire sur votre ordinateur et réinstaller la suite de plug-in.</span><span class="sxs-lookup"><span data-stu-id="e9736-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="e9736-212">Ionide est un projet open source construit et géré par les membres de la F# Communauté.</span><span class="sxs-lookup"><span data-stu-id="e9736-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="e9736-213">Veuillez signaler des problèmes et n’hésitez pas à contribuer à la [Ionide-VSCode : Référentiel GitHub de FSharp](https://github.com/ionide/ionide-vscode-fsharp).</span><span class="sxs-lookup"><span data-stu-id="e9736-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="e9736-214">Si vous rencontrez un problème au rapport, suivez [les instructions pour obtenir les journaux à utiliser lorsque vous signalez un problème](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span><span class="sxs-lookup"><span data-stu-id="e9736-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="e9736-215">Vous pouvez également poser pour obtenir de l’aide des développeurs Ionide et F# communautaire dans les [Ionide Gitter canal](https://gitter.im/ionide/ionide-project).</span><span class="sxs-lookup"><span data-stu-id="e9736-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e9736-216">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e9736-216">Next steps</span></span>

<span data-ttu-id="e9736-217">Pour en savoir plus sur F# et les fonctionnalités du langage, consultez [visite guidée de F# ](../tour.md).</span><span class="sxs-lookup"><span data-stu-id="e9736-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
