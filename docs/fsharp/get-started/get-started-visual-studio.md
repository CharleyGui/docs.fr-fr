---
title: Prise F# en main de dans Visual Studio
description: Découvrez comment utiliser F# avec Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552818"
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="edaed-103">Prise F# en main de dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="edaed-103">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="edaed-104">F#et les outils F# visuels sont pris en charge dans l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="edaed-104">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>

<span data-ttu-id="edaed-105">Pour commencer, assurez-vous que [Visual Studio est F#installé avec ](install-fsharp.md#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="edaed-105">To begin, ensure that you have [Visual Studio installed with F#](install-fsharp.md#install-f-with-visual-studio).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="edaed-106">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="edaed-106">Creating a console application</span></span>

<span data-ttu-id="edaed-107">L’un des projets les plus basiques dans Visual Studio est l’application console.</span><span class="sxs-lookup"><span data-stu-id="edaed-107">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="edaed-108">Voici comment faire.</span><span class="sxs-lookup"><span data-stu-id="edaed-108">Here's how to do it.</span></span>  <span data-ttu-id="edaed-109">Une fois Visual Studio ouvert :</span><span class="sxs-lookup"><span data-stu-id="edaed-109">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="edaed-110">Dans le menu **fichier** , pointez sur **nouveau**, puis choisissez **projet**.</span><span class="sxs-lookup"><span data-stu-id="edaed-110">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2. <span data-ttu-id="edaed-111">Dans la boîte de dialogue Nouveau projet, sous **modèles**, vous devez voir **visuel F#** .</span><span class="sxs-lookup"><span data-stu-id="edaed-111">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="edaed-112">Choisissez cette valeur pour afficher F# les modèles.</span><span class="sxs-lookup"><span data-stu-id="edaed-112">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="edaed-113">Sélectionnez **application console .net Core** ou **application console**.</span><span class="sxs-lookup"><span data-stu-id="edaed-113">Select either **.NET Core Console app** or **Console app**.</span></span>

4. <span data-ttu-id="edaed-114">Choisissez le bouton **OK** pour créer le F# projet.</span><span class="sxs-lookup"><span data-stu-id="edaed-114">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="edaed-115">Vous devez maintenant voir un F# projet dans le Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="edaed-115">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="edaed-116">Écriture de votre code</span><span class="sxs-lookup"><span data-stu-id="edaed-116">Writing your code</span></span>

<span data-ttu-id="edaed-117">Commençons par écrire du code.</span><span class="sxs-lookup"><span data-stu-id="edaed-117">Let's get started by writing some code first.</span></span>  <span data-ttu-id="edaed-118">Assurez-vous que le fichier `Program.fs` est ouvert, puis remplacez son contenu par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="edaed-118">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="edaed-119">Dans l’exemple de code précédent, une fonction `square` a été définie, qui prend une entrée nommée `x` et la multiplie par elle-même.</span><span class="sxs-lookup"><span data-stu-id="edaed-119">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="edaed-120">Étant F# donné que utilise l' [inférence de type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.</span><span class="sxs-lookup"><span data-stu-id="edaed-120">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="edaed-121">Le F# compilateur comprend les types où la multiplication est valide, et assigne un type à `x` en fonction de la façon dont `square` est appelé.</span><span class="sxs-lookup"><span data-stu-id="edaed-121">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="edaed-122">Si vous pointez sur `square`, vous devriez voir ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="edaed-122">If you hover over `square`, you should see the following:</span></span>

```fsharp
val square: x:int -> int
```

<span data-ttu-id="edaed-123">C’est ce que l’on appelle la signature de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="edaed-123">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="edaed-124">Il peut être lu comme suit : « Square est une fonction qui prend un entier nommé x et produit un entier ».</span><span class="sxs-lookup"><span data-stu-id="edaed-124">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="edaed-125">Notez que le compilateur a donné `square` le type de `int` pour le moment, car la multiplication n’est pas générique pour *tous les* types, mais plutôt générique dans un ensemble fermé de types.</span><span class="sxs-lookup"><span data-stu-id="edaed-125">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="edaed-126">Le F# compilateur a choisi `int` à ce stade, mais il ajustera la signature du type si vous appelez `square` avec un type d’entrée différent, tel qu’un `float`.</span><span class="sxs-lookup"><span data-stu-id="edaed-126">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="edaed-127">Une autre fonction, `main`, est définie, qui est décorée avec l’attribut `EntryPoint` pour F# indiquer au compilateur que l’exécution du programme doit démarrer.</span><span class="sxs-lookup"><span data-stu-id="edaed-127">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="edaed-128">Il suit la même convention que les autres [langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).</span><span class="sxs-lookup"><span data-stu-id="edaed-128">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="edaed-129">C’est dans cette fonction que nous appelons la fonction `square` avec un argument de `12`.</span><span class="sxs-lookup"><span data-stu-id="edaed-129">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="edaed-130">Le F# compilateur assigne ensuite le type de `square` à `int -> int` (autrement dit, une fonction qui prend un `int` et produit une `int`).</span><span class="sxs-lookup"><span data-stu-id="edaed-130">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="edaed-131">L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, des paramètres qui correspondent à ceux spécifiés dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="edaed-131">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="edaed-132">Exécution de votre code</span><span class="sxs-lookup"><span data-stu-id="edaed-132">Running your code</span></span>

<span data-ttu-id="edaed-133">Vous pouvez exécuter le code et afficher les résultats en appuyant sur **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="edaed-133">You can run the code and see results by pressing **Ctrl**+**F5**.</span></span>  <span data-ttu-id="edaed-134">Cela exécute le programme sans débogage et vous permet de voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="edaed-134">This runs the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="edaed-135">Vous pouvez également choisir l’élément de menu de niveau supérieur de **débogage** dans Visual Studio et choisir **exécuter sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="edaed-135">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="edaed-136">Vous devez maintenant voir les éléments suivants affichés dans la fenêtre de console affichée par Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="edaed-136">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="edaed-137">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="edaed-137">Congratulations!</span></span>  <span data-ttu-id="edaed-138">Vous avez créé votre premier F# projet dans Visual Studio, écrit une F# fonction a imprimé les résultats de l’appel de cette fonction, puis j’exécute le projet pour afficher des résultats.</span><span class="sxs-lookup"><span data-stu-id="edaed-138">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="edaed-139">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="edaed-139">Next steps</span></span>

<span data-ttu-id="edaed-140">Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage.</span><span class="sxs-lookup"><span data-stu-id="edaed-140">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="edaed-141">Il vous donne une vue d’ensemble des fonctionnalités de F#et fournit de larges exemples de code que vous pouvez copier dans Visual Studio et exécuter.</span><span class="sxs-lookup"><span data-stu-id="edaed-141">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="edaed-142">Vous pouvez également en savoir plus sur F# la documentation dans la [ F# page d’accueil docs](../index.yml).</span><span class="sxs-lookup"><span data-stu-id="edaed-142">You can also learn more about the F# documentation in the [F# docs homepage](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="edaed-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edaed-143">See also</span></span>

- [<span data-ttu-id="edaed-144">Présentation de F#</span><span class="sxs-lookup"><span data-stu-id="edaed-144">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="edaed-145">F#Référence du langage</span><span class="sxs-lookup"><span data-stu-id="edaed-145">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="edaed-146">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="edaed-146">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="edaed-147">Informations de référence sur les symboles et les opérateurs</span><span class="sxs-lookup"><span data-stu-id="edaed-147">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
