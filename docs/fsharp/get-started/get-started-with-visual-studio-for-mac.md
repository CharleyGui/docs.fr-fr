---
title: Prise F# en main de dans Visual Studio pour Mac
description: Découvrez comment utiliser F# avec Visual Studio pour Mac.
ms.date: 07/03/2018
ms.openlocfilehash: 679ed1ea28f5d0e0d910dbd407b38d1d2f0314f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629751"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="003ef-103">Prise F# en main de dans Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="003ef-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="003ef-104">F#et les outils F# visuels sont pris en charge dans l’IDE Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="003ef-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="003ef-105">Vérifiez que vous avez [Visual Studio pour Mac installé](install-fsharp.md#install-f-with-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="003ef-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="003ef-106">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="003ef-106">Creating a console application</span></span>

<span data-ttu-id="003ef-107">L’un des projets les plus basiques de Visual Studio pour Mac est l’application console.</span><span class="sxs-lookup"><span data-stu-id="003ef-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="003ef-108">Voici comment faire.</span><span class="sxs-lookup"><span data-stu-id="003ef-108">Here's how to do it.</span></span>  <span data-ttu-id="003ef-109">Une fois Visual Studio pour Mac est ouvert:</span><span class="sxs-lookup"><span data-stu-id="003ef-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="003ef-110">Dans le menu **fichier** , pointez sur **nouvelle solution**.</span><span class="sxs-lookup"><span data-stu-id="003ef-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="003ef-111">Dans la boîte de dialogue Nouveau projet, il existe 2 modèles différents pour l’application console.</span><span class="sxs-lookup"><span data-stu-id="003ef-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="003ef-112">Il y en a un sous autre-> .NET qui cible le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="003ef-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="003ef-113">L’autre modèle est sous .NET Core-> application qui cible .NET Core.</span><span class="sxs-lookup"><span data-stu-id="003ef-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="003ef-114">L’un ou l’autre des modèles doit fonctionner dans le cadre de cet article.</span><span class="sxs-lookup"><span data-stu-id="003ef-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="003ef-115">Sous application console, remplacez C# par F# si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="003ef-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="003ef-116">Choisissez le bouton **suivant** pour avancer!</span><span class="sxs-lookup"><span data-stu-id="003ef-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="003ef-117">Donnez un nom à votre projet, puis choisissez les options souhaitées pour l’application.</span><span class="sxs-lookup"><span data-stu-id="003ef-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="003ef-118">Notez que le volet de visualisation sur le côté de l’écran affiche la structure de répertoires qui sera créée en fonction des options sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="003ef-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="003ef-119">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="003ef-119">Click **Create**.</span></span>  <span data-ttu-id="003ef-120">Vous devez maintenant voir un F# projet dans le Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="003ef-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="003ef-121">Écriture de votre code</span><span class="sxs-lookup"><span data-stu-id="003ef-121">Writing your code</span></span>

<span data-ttu-id="003ef-122">Commençons par écrire du code.</span><span class="sxs-lookup"><span data-stu-id="003ef-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="003ef-123">Assurez-vous `Program.fs` que le fichier est ouvert, puis remplacez son contenu par ce qui suit:</span><span class="sxs-lookup"><span data-stu-id="003ef-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="003ef-124">Dans l’exemple de code précédent, une `square` fonction a été définie et prend une entrée `x` nommée et la multiplie par elle-même.</span><span class="sxs-lookup"><span data-stu-id="003ef-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="003ef-125">Étant F# donné que utilise l’inférence de [type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.</span><span class="sxs-lookup"><span data-stu-id="003ef-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="003ef-126">Le F# compilateur comprend les types où la multiplication est valide, et assigne un type à `x` en fonction de `square` la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="003ef-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="003ef-127">Si vous pointez `square`sur, les éléments suivants doivent s’afficher:</span><span class="sxs-lookup"><span data-stu-id="003ef-127">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="003ef-128">C’est ce que l’on appelle la signature de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="003ef-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="003ef-129">Il peut être lu comme suit: «Square est une fonction qui accepte un entier nommé x et produit un entier «».</span><span class="sxs-lookup"><span data-stu-id="003ef-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="003ef-130">Notez que le compilateur a `square` donné `int` le type pour le moment, car la multiplication n’est pas générique pour *tous les* types, mais plutôt générique dans un ensemble fermé de types.</span><span class="sxs-lookup"><span data-stu-id="003ef-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="003ef-131">Le F# compilateur a `int` choisi à ce stade, mais il ajuste la signature de type si `square` vous appelez avec un autre type d’entrée, `float`tel qu’un.</span><span class="sxs-lookup"><span data-stu-id="003ef-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="003ef-132">Une autre fonction `main`,, est définie, qui est décorée `EntryPoint` avec l’attribut pour F# indiquer au compilateur que l’exécution du programme doit démarrer.</span><span class="sxs-lookup"><span data-stu-id="003ef-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="003ef-133">Il suit la même convention que les autres langages de [programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code `0`d’entier est retourné (en général).</span><span class="sxs-lookup"><span data-stu-id="003ef-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="003ef-134">C’est dans cette fonction que nous appelons la `square` fonction avec un argument de `12`.</span><span class="sxs-lookup"><span data-stu-id="003ef-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="003ef-135">Le F# compilateur assigne ensuite le type de `square` à la `int -> int` valeur (autrement dit, une fonction qui prend `int` un et produit `int`un).</span><span class="sxs-lookup"><span data-stu-id="003ef-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="003ef-136">L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, des paramètres qui correspondent à ceux spécifiés dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="003ef-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="003ef-137">Exécution de votre code</span><span class="sxs-lookup"><span data-stu-id="003ef-137">Running your code</span></span>

<span data-ttu-id="003ef-138">Vous pouvez exécuter le code et afficher les résultats en cliquant sur **exécuter** dans le menu de niveau supérieur, puis exécuter **sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="003ef-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="003ef-139">Cette opération exécute le programme sans débogage et vous permet de voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="003ef-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="003ef-140">Vous devez maintenant voir le code suivant affiché dans la fenêtre de console qui Visual Studio pour Mac affichée:</span><span class="sxs-lookup"><span data-stu-id="003ef-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="003ef-141">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="003ef-141">Congratulations!</span></span>  <span data-ttu-id="003ef-142">Vous avez créé votre premier F# projet dans Visual Studio pour Mac, écrit une F# fonction à l’impression des résultats de l’appel de cette fonction, puis j’exécute le projet pour afficher des résultats.</span><span class="sxs-lookup"><span data-stu-id="003ef-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="003ef-143">Utilisation F# du mode interactif</span><span class="sxs-lookup"><span data-stu-id="003ef-143">Using F# Interactive</span></span>

<span data-ttu-id="003ef-144">L’une des meilleures fonctionnalités des outils visuels F# dans Visual Studio pour Mac est la F# fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="003ef-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="003ef-145">Elle vous permet d’envoyer du code à un processus dans lequel vous pouvez appeler ce code et consulter le résultat de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="003ef-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="003ef-146">Pour commencer à l’utiliser, mettez `square` en surbrillance la fonction définie dans votre code.</span><span class="sxs-lookup"><span data-stu-id="003ef-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="003ef-147">Ensuite, cliquez sur **modifier** dans le menu de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="003ef-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="003ef-148">Sélectionnez ensuite **Envoyer la sélection F# à interactive**.</span><span class="sxs-lookup"><span data-stu-id="003ef-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="003ef-149">Cela exécute le code dans la F# fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="003ef-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="003ef-150">Vous pouvez également cliquer avec le bouton droit sur la sélection et choisir **Envoyer la F# sélection vers interactive**.</span><span class="sxs-lookup"><span data-stu-id="003ef-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="003ef-151">La F# fenêtre interactive doit s’afficher avec les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="003ef-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="003ef-152">Cela montre la même signature de fonction pour `square` la fonction, que vous avez vu précédemment quand vous avez pointé sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="003ef-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="003ef-153">Étant `square` donné que est maintenant défini F# dans le processus interactif, vous pouvez l’appeler avec des valeurs différentes:</span><span class="sxs-lookup"><span data-stu-id="003ef-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="003ef-154">Cela exécute la fonction, lie le résultat à un nouveau nom `it`et affiche le type et la valeur de. `it`</span><span class="sxs-lookup"><span data-stu-id="003ef-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="003ef-155">Notez que vous devez terminer chaque ligne par `;;`.</span><span class="sxs-lookup"><span data-stu-id="003ef-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="003ef-156">C’est ainsi F# que l’interactivité sait quand l’appel de fonction est terminé.</span><span class="sxs-lookup"><span data-stu-id="003ef-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="003ef-157">Vous pouvez également définir de nouvelles fonctions F# dans Interactive:</span><span class="sxs-lookup"><span data-stu-id="003ef-157">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="003ef-158">La section ci-dessus définit une `isOdd`nouvelle fonction,, `int` qui prend un et vérifie si elle est impaire.</span><span class="sxs-lookup"><span data-stu-id="003ef-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="003ef-159">Vous pouvez appeler cette fonction pour voir ce qu’elle retourne avec des entrées différentes.</span><span class="sxs-lookup"><span data-stu-id="003ef-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="003ef-160">Vous pouvez appeler des fonctions dans les appels de fonction:</span><span class="sxs-lookup"><span data-stu-id="003ef-160">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="003ef-161">Vous pouvez également utiliser l' [opérateur](../language-reference/symbol-and-operator-reference/index.md) de redirection pour canaliser la valeur dans les deux fonctions:</span><span class="sxs-lookup"><span data-stu-id="003ef-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="003ef-162">L’opérateur de redirection, et bien plus encore, sont traités dans les didacticiels ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="003ef-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="003ef-163">Il ne s’agit là que d’une idée de ce F# que vous pouvez faire avec interactive.</span><span class="sxs-lookup"><span data-stu-id="003ef-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="003ef-164">Pour plus d’informations, consultez [programmation interactive avec F# ](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="003ef-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="003ef-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="003ef-165">Next steps</span></span>

<span data-ttu-id="003ef-166">Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage.</span><span class="sxs-lookup"><span data-stu-id="003ef-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="003ef-167">Il vous donne une vue d’ensemble des fonctionnalités de F#et fournit de larges exemples de code que vous pouvez copier dans Visual Studio pour Mac et exécuter.</span><span class="sxs-lookup"><span data-stu-id="003ef-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="003ef-168">Vous pouvez également utiliser des ressources externes intéressantes, présentées dans le [ F# Guide](../index.md).</span><span class="sxs-lookup"><span data-stu-id="003ef-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="003ef-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="003ef-169">See also</span></span>

- [<span data-ttu-id="003ef-170">Visual F#</span><span class="sxs-lookup"><span data-stu-id="003ef-170">Visual F#</span></span>](../index.md)
- [<span data-ttu-id="003ef-171">Présentation de F#</span><span class="sxs-lookup"><span data-stu-id="003ef-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="003ef-172">F#Référence du langage</span><span class="sxs-lookup"><span data-stu-id="003ef-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="003ef-173">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="003ef-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="003ef-174">Informations de référence sur les symboles et les opérateurs</span><span class="sxs-lookup"><span data-stu-id="003ef-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
