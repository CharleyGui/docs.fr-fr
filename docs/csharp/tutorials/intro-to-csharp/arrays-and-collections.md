---
title: Utilisation des collections - Présentation du tutoriel C#
description: Découvrez C# en explorant la collection de listes de ce guide de démarrage rapide.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: c99f5582702120db238de1206de42d964837cdbd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396894"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="68c1f-103">Apprenez à gérer les collections de données en utilisant le type de liste générique</span><span class="sxs-lookup"><span data-stu-id="68c1f-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="68c1f-104">Ce didacticiel propose une introduction au langage C# et présente les concepts de base de la classe <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="68c1f-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="68c1f-105">Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement.</span><span class="sxs-lookup"><span data-stu-id="68c1f-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="68c1f-106">Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="68c1f-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="68c1f-107">Vous trouverez une brève vue d’ensemble des commandes utilisées disponible dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.</span><span class="sxs-lookup"><span data-stu-id="68c1f-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="68c1f-108">Exemple de liste de base</span><span class="sxs-lookup"><span data-stu-id="68c1f-108">A basic list example</span></span>

<span data-ttu-id="68c1f-109">Créez un répertoire nommé *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="68c1f-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="68c1f-110">Faites-en le répertoire actuel et exécutez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="68c1f-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="68c1f-111">Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez le code existant par le suivant :</span><span class="sxs-lookup"><span data-stu-id="68c1f-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="68c1f-112">Remplacez `<name>` par votre nom.</span><span class="sxs-lookup"><span data-stu-id="68c1f-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="68c1f-113">Enregistrez *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="68c1f-113">Save *Program.cs*.</span></span> <span data-ttu-id="68c1f-114">Tapez `dotnet run` dans votre fenêtre de console pour effectuer un essai.</span><span class="sxs-lookup"><span data-stu-id="68c1f-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="68c1f-115">Vous avez créé une liste de chaînes, ajouté trois noms à cette liste et affiché les noms en majuscules.</span><span class="sxs-lookup"><span data-stu-id="68c1f-115">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="68c1f-116">Vous utilisez des concepts que vous avez appris dans les tutoriels précédents pour lire la liste en boucle.</span><span class="sxs-lookup"><span data-stu-id="68c1f-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="68c1f-117">Le code permettant d’afficher les noms utilise la fonctionnalité [d’interpolation de chaîne](../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="68c1f-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="68c1f-118">Quand vous faites précéder une `string` du caractère `$`, vous pouvez incorporer le code C# dans la déclaration de chaîne.</span><span class="sxs-lookup"><span data-stu-id="68c1f-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="68c1f-119">La chaîne réelle remplace ce code C# par la valeur qu’elle génère.</span><span class="sxs-lookup"><span data-stu-id="68c1f-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="68c1f-120">Dans cet exemple, elle remplace `{name.ToUpper()}` par chaque nom, converti en majuscules, car vous avez appelé la méthode <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="68c1f-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="68c1f-121">Continuons notre exploration.</span><span class="sxs-lookup"><span data-stu-id="68c1f-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="68c1f-122">Modifier le contenu de la liste</span><span class="sxs-lookup"><span data-stu-id="68c1f-122">Modify list contents</span></span>

<span data-ttu-id="68c1f-123">La collection que vous avez créée utilise le type <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="68c1f-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="68c1f-124">Ce type stocke les séquences d’éléments.</span><span class="sxs-lookup"><span data-stu-id="68c1f-124">This type stores sequences of elements.</span></span> <span data-ttu-id="68c1f-125">Vous spécifiez le type des éléments entre crochets angulaires.</span><span class="sxs-lookup"><span data-stu-id="68c1f-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="68c1f-126">Un aspect important du type <xref:System.Collections.Generic.List%601> est qu’il peut augmenter ou diminuer, ce qui vous permet d’ajouter ou de supprimer des éléments.</span><span class="sxs-lookup"><span data-stu-id="68c1f-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="68c1f-127">Ajoutez ce code avant de fermer le `}` dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="68c1f-127">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="68c1f-128">Vous avez ajouté deux noms supplémentaires à la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="68c1f-129">Vous en avez également supprimé un.</span><span class="sxs-lookup"><span data-stu-id="68c1f-129">You've also removed one as well.</span></span> <span data-ttu-id="68c1f-130">Enregistrez le fichier et tapez `dotnet run` pour effectuer un essai.</span><span class="sxs-lookup"><span data-stu-id="68c1f-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="68c1f-131">La <xref:System.Collections.Generic.List%601> vous permet en outre de faire référence à des éléments individuels par **index**.</span><span class="sxs-lookup"><span data-stu-id="68c1f-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="68c1f-132">Vous placez l’index entre les jetons `[` et `]` après le nom de la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="68c1f-133">C# utilise la valeur 0 pour le premier index.</span><span class="sxs-lookup"><span data-stu-id="68c1f-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="68c1f-134">Ajoutez le code directement sous le code que vous venez d’ajouter et effectuez un essai :</span><span class="sxs-lookup"><span data-stu-id="68c1f-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="68c1f-135">Vous ne pouvez pas accéder à un index au-delà de la fin de la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-135">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="68c1f-136">Rappelez-vous que les index commencent à partir de 0, de sorte que le plus grand index valide correspond au nombre d’éléments de la liste moins un.</span><span class="sxs-lookup"><span data-stu-id="68c1f-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="68c1f-137">Vous pouvez vérifier la longueur de la liste à l’aide de la propriété <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="68c1f-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="68c1f-138">Ajoutez le code suivant à la fin de la méthode Main :</span><span class="sxs-lookup"><span data-stu-id="68c1f-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="68c1f-139">Enregistrez le fichier et tapez de nouveau `dotnet run` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="68c1f-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="68c1f-140">Trier les listes et y effectuer des recherches</span><span class="sxs-lookup"><span data-stu-id="68c1f-140">Search and sort lists</span></span>

<span data-ttu-id="68c1f-141">Nos exemples utilisent des listes relativement petites, mais vos applications peuvent souvent générer des listes contenant beaucoup plus d’éléments, qui se comptent parfois même en milliers.</span><span class="sxs-lookup"><span data-stu-id="68c1f-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="68c1f-142">Pour rechercher des éléments dans ces collections plus volumineuses, vous devez rechercher différents éléments dans la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="68c1f-143">La méthode <xref:System.Collections.Generic.List%601.IndexOf%2A> recherche un élément et retourne l’index de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="68c1f-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="68c1f-144">Si l’élément n’est pas dans la liste, `IndexOf` retourne `-1` .</span><span class="sxs-lookup"><span data-stu-id="68c1f-144">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="68c1f-145">Ajoutez ce code en bas de votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="68c1f-145">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="68c1f-146">Il est également possible de trier les éléments de la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="68c1f-147">La <xref:System.Collections.Generic.List%601.Sort%2A> méthode trie tous les éléments de la liste dans l’ordre normal (par ordre alphabétique pour les chaînes).</span><span class="sxs-lookup"><span data-stu-id="68c1f-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="68c1f-148">Ajoutez ce code en bas de notre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="68c1f-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="68c1f-149">Enregistrez le fichier et tapez `dotnet run` pour tester cette dernière version.</span><span class="sxs-lookup"><span data-stu-id="68c1f-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="68c1f-150">Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="68c1f-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="68c1f-151">Cela nous permettra de travailler plus facilement avec un nouvel exemple.</span><span class="sxs-lookup"><span data-stu-id="68c1f-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="68c1f-152">Renommez votre méthode `Main``WorkingWithStrings` et écrivez une nouvelle méthode `Main` qui appelle `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="68c1f-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="68c1f-153">Lorsque vous avez terminé, votre code doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="68c1f-153">When you've finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="68c1f-154">Listes d’autres types</span><span class="sxs-lookup"><span data-stu-id="68c1f-154">Lists of other types</span></span>

<span data-ttu-id="68c1f-155">Vous avez jusqu'à présent utilisé le type `string` dans les listes.</span><span class="sxs-lookup"><span data-stu-id="68c1f-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="68c1f-156">Nous allons maintenant créer une <xref:System.Collections.Generic.List%601> en utilisant un autre type.</span><span class="sxs-lookup"><span data-stu-id="68c1f-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="68c1f-157">Commençons par créer un ensemble de nombres.</span><span class="sxs-lookup"><span data-stu-id="68c1f-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="68c1f-158">Ajoutez le code suivant en bas de votre nouvelle méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="68c1f-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="68c1f-159">Cela crée une liste d’entiers et définit les deux premiers entiers sur la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="68c1f-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="68c1f-160">Il s’agit des deux premières valeurs d’une *séquence Fibonacci* (séquence de nombres).</span><span class="sxs-lookup"><span data-stu-id="68c1f-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="68c1f-161">Chaque nombre Fibonacci suivant correspond à la somme des deux nombres précédents.</span><span class="sxs-lookup"><span data-stu-id="68c1f-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="68c1f-162">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68c1f-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="68c1f-163">Enregistrez le fichier et tapez `dotnet run` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="68c1f-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="68c1f-164">Pour vous concentrer uniquement sur cette section, vous pouvez commenter le code qui appelle `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="68c1f-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="68c1f-165">Insérez simplement deux caractères `/` devant l’appel comme suit :  `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="68c1f-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="68c1f-166">Test</span><span class="sxs-lookup"><span data-stu-id="68c1f-166">Challenge</span></span>

<span data-ttu-id="68c1f-167">Vérifiez si vous pouvez mettre en pratique certains des concepts appris ici et dans d’autres leçons antérieures.</span><span class="sxs-lookup"><span data-stu-id="68c1f-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="68c1f-168">Approfondissez à partir de ce que vous avez créé jusqu'à présent avec les nombres de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="68c1f-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="68c1f-169">Essayez d’écrire le code pour générer les 20 premiers nombres de la séquence.</span><span class="sxs-lookup"><span data-stu-id="68c1f-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="68c1f-170">(Astuce, le 20ème nombre Fibonacci est 6765.)</span><span class="sxs-lookup"><span data-stu-id="68c1f-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="68c1f-171">Terminer le test</span><span class="sxs-lookup"><span data-stu-id="68c1f-171">Complete challenge</span></span>

<span data-ttu-id="68c1f-172">Vous pouvez voir un exemple de solution en [consultant l’exemple de code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="68c1f-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="68c1f-173">À chaque itération de la boucle, vous sélectionnez les deux derniers entiers de la liste, les additionner et ajoutez la valeur obtenue à la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="68c1f-174">La boucle se répète jusqu'à ce que vous ayez ajouté 20 éléments à la liste.</span><span class="sxs-lookup"><span data-stu-id="68c1f-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="68c1f-175">Félicitations, vous avez terminé ce didacticiel sur les listes.</span><span class="sxs-lookup"><span data-stu-id="68c1f-175">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="68c1f-176">Vous pouvez passer au tutoriel [Introduction aux classes](introduction-to-classes.md) dans votre propre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="68c1f-176">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="68c1f-177">Vous pouvez en savoir plus sur l’utilisation du `List` type dans l’article du [Guide .net](../../../standard/index.yml) sur les [Collections](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="68c1f-177">You can learn more about working with the `List` type in the [.NET guide](../../../standard/index.yml) article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="68c1f-178">Vous allez également en découvrir plus sur de nombreux autres types de collection.</span><span class="sxs-lookup"><span data-stu-id="68c1f-178">You'll also learn about many other collection types.</span></span>
