---
title: Prise F# en main de dans Visual Studio
description: Découvrez comment utiliser F# avec Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337347"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="ec9a0-103">Prise F# en main de dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec9a0-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="ec9a0-104">F#et les outils F# visuels sont pris en charge dans l’environnement de développement intégré (IDE) de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-104">F# and the Visual F# tooling are supported in the Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="ec9a0-105">Pour commencer, assurez-vous que [Visual Studio est F# installé avec la prise en charge](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ec9a0-105">To begin, ensure that you have [Visual Studio installed with F# support](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="ec9a0-106">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="ec9a0-106">Create a console application</span></span>

<span data-ttu-id="ec9a0-107">L’un des projets les plus basiques dans Visual Studio est l’application console.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-107">One of the most basic projects in Visual Studio is the console app.</span></span> <span data-ttu-id="ec9a0-108">Voici comment en créer un :</span><span class="sxs-lookup"><span data-stu-id="ec9a0-108">Here's how to create one:</span></span>

1. <span data-ttu-id="ec9a0-109">Ouvrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-109">Open Visual Studio 2019.</span></span>

2. <span data-ttu-id="ec9a0-110">Dans la fenêtre de démarrage, choisissez **Créer un projet**.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-110">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="ec9a0-111">Dans la page **créer un nouveau projet** , choisissez **F#** dans la liste langue.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-111">On the **Create a new project** page, choose **F#** from the Language list.</span></span>

4. <span data-ttu-id="ec9a0-112">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-112">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

5. <span data-ttu-id="ec9a0-113">Dans la page **configurer votre nouveau projet** , entrez un nom dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="ec9a0-113">On the **Configure your new project** page, enter a name in the **Project name** box.</span></span> <span data-ttu-id="ec9a0-114">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-114">Then, choose **Create**.</span></span>

   <span data-ttu-id="ec9a0-115">Visual Studio crée le nouveau F# projet.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-115">Visual Studio creates the new F# project.</span></span> <span data-ttu-id="ec9a0-116">Vous pouvez le voir dans la fenêtre de Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-116">You can see it in the Solution Explorer window.</span></span>

## <a name="write-the-code"></a><span data-ttu-id="ec9a0-117">Écrire le code</span><span class="sxs-lookup"><span data-stu-id="ec9a0-117">Write the code</span></span>

<span data-ttu-id="ec9a0-118">Commençons par écrire du code.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-118">Let's get started by writing some code.</span></span> <span data-ttu-id="ec9a0-119">Assurez-vous que le fichier `Program.fs` est ouvert, puis remplacez son contenu par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ec9a0-119">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="ec9a0-120">L’exemple de code précédent définit une fonction appelée `square` qui prend une entrée nommée `x` et la multiplie par elle-même.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-120">The previous code sample defines a function called `square` that takes an input named `x` and multiplies it by itself.</span></span> <span data-ttu-id="ec9a0-121">Étant F# donné que utilise l' [inférence de type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-121">Because F# uses [Type inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span> <span data-ttu-id="ec9a0-122">Le F# compilateur comprend les types où la multiplication est valide et assigne un type à `x` en fonction de la façon dont `square` est appelé.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-122">The F# compiler understands the types where multiplication is valid and assigns a type to `x` based on how `square` is called.</span></span> <span data-ttu-id="ec9a0-123">Si vous pointez sur `square`, vous devriez voir ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ec9a0-123">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="ec9a0-124">C’est ce que l’on appelle la signature de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-124">This is what is known as the function's type signature.</span></span> <span data-ttu-id="ec9a0-125">Il peut être lu comme suit : « Square est une fonction qui accepte un entier nommé x et produit un entier ».</span><span class="sxs-lookup"><span data-stu-id="ec9a0-125">It can be read like this: "Square is a function that takes an integer named x and produces an integer".</span></span> <span data-ttu-id="ec9a0-126">Le compilateur a donné `square` le type de `int` pour l’instant ; Cela est dû au fait que la multiplication n’est pas générique pour *tous les* types, mais plutôt un ensemble fermé de types.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-126">The compiler gave `square` the `int` type for now; this is because multiplication is not generic across *all* types but rather a closed set of types.</span></span> <span data-ttu-id="ec9a0-127">Le F# compilateur ajuste la signature de type si vous appelez `square` avec un autre type d’entrée, tel qu’un `float`.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-127">The F# compiler will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="ec9a0-128">Une autre fonction, `main`, est définie, qui est décorée avec l’attribut `EntryPoint`.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-128">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute.</span></span> <span data-ttu-id="ec9a0-129">Cet attribut indique au F# compilateur que l’exécution du programme doit démarrer.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-129">This attribute tells the F# compiler that program execution should start there.</span></span> <span data-ttu-id="ec9a0-130">Il suit la même convention que les autres [langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).</span><span class="sxs-lookup"><span data-stu-id="ec9a0-130">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="ec9a0-131">Il se trouve dans la fonction de point d’entrée, `main`, que vous appelez la fonction `square` avec un argument de `12`.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-131">It is in the entry point function, `main`, that you call the `square` function with an argument of `12`.</span></span> <span data-ttu-id="ec9a0-132">Le F# compilateur assigne ensuite le type de `square` à `int -> int` (autrement dit, une fonction qui prend un `int` et produit une `int`).</span><span class="sxs-lookup"><span data-stu-id="ec9a0-132">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function that takes an `int` and produces an `int`).</span></span> <span data-ttu-id="ec9a0-133">L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format et imprime le résultat (et une nouvelle ligne).</span><span class="sxs-lookup"><span data-stu-id="ec9a0-133">The call to `printfn` is a formatted printing function that uses a format string and prints the result (and a new line).</span></span> <span data-ttu-id="ec9a0-134">La chaîne de format, similaire aux langages de programmation de style C, contient des paramètres (`%d`) qui correspondent aux arguments qui lui sont transmis, dans ce cas, `12` et `(square 12)`.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-134">The format string, similar to C-style programming languages, has parameters (`%d`) that correspond to the arguments that are passed to it, in this case, `12` and `(square 12)`.</span></span>

## <a name="run-the-code"></a><span data-ttu-id="ec9a0-135">Exécuter le code</span><span class="sxs-lookup"><span data-stu-id="ec9a0-135">Run the code</span></span>

<span data-ttu-id="ec9a0-136">Vous pouvez exécuter le code et afficher les résultats en appuyant sur **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-136">You can run the code and see the results by pressing **Ctrl**+**F5**.</span></span> <span data-ttu-id="ec9a0-137">Vous pouvez également choisir le > de **débogage** **exécuter sans débogage** à partir de la barre de menus de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-137">Alternatively, you can choose the **Debug** > **Start Without Debugging** from the top-level menu bar.</span></span> <span data-ttu-id="ec9a0-138">Cela exécute le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-138">This runs the program without debugging.</span></span>

<span data-ttu-id="ec9a0-139">La sortie suivante s’affiche dans la fenêtre de console ouverte par Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="ec9a0-139">The following output prints to the console window that Visual Studio opened:</span></span>

```console
12 squared is: 144!
```

<span data-ttu-id="ec9a0-140">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="ec9a0-140">Congratulations!</span></span> <span data-ttu-id="ec9a0-141">Vous avez créé votre premier F# projet dans Visual Studio, écrit une F# fonction qui calcule et imprime une valeur, puis exécute le projet pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-141">You've created your first F# project in Visual Studio, written an F# function that calculates and prints a value, and run the project to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec9a0-142">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec9a0-142">Next steps</span></span>

<span data-ttu-id="ec9a0-143">Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-143">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span> <span data-ttu-id="ec9a0-144">Il fournit une vue d’ensemble des fonctionnalités de et F# des exemples de code suffisamment larges que vous pouvez copier dans Visual Studio et exécuter.</span><span class="sxs-lookup"><span data-stu-id="ec9a0-144">It provides an overview of some of the capabilities of F# and ample code samples that you can copy into Visual Studio and run.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec9a0-145">Présentation de F#</span><span class="sxs-lookup"><span data-stu-id="ec9a0-145">Tour of F#</span></span>](../tour.md)

## <a name="see-also"></a><span data-ttu-id="ec9a0-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec9a0-146">See also</span></span>

- [<span data-ttu-id="ec9a0-147">F#Référence du langage</span><span class="sxs-lookup"><span data-stu-id="ec9a0-147">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="ec9a0-148">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="ec9a0-148">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="ec9a0-149">Informations de référence sur les symboles et les opérateurs</span><span class="sxs-lookup"><span data-stu-id="ec9a0-149">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
