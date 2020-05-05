---
title: Nombres en C# – Tutoriel d’introduction à C#
description: Découvrez C# en explorant les types numériques, leurs utilisations, leurs propriétés et leurs méthodes.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 3dc2a5afc6321da45351525a632f586cb84bf7fe
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794609"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="e84bf-103">Manipuler les nombres intégraux et à virgule flottante en C\#</span><span class="sxs-lookup"><span data-stu-id="e84bf-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="e84bf-104">Ce tutoriel permet de découvrir de manière interactive les types numériques en C#.</span><span class="sxs-lookup"><span data-stu-id="e84bf-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="e84bf-105">Vous allez écrire de petites quantités de code, puis vous compilerez et exécuterez ce code.</span><span class="sxs-lookup"><span data-stu-id="e84bf-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="e84bf-106">Ce tutoriel comporte une série de leçons visant à explorer les nombres et les opérations mathématiques en C#.</span><span class="sxs-lookup"><span data-stu-id="e84bf-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="e84bf-107">Ces leçons présentent les concepts de base du langage C#.</span><span class="sxs-lookup"><span data-stu-id="e84bf-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="e84bf-108">Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement.</span><span class="sxs-lookup"><span data-stu-id="e84bf-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="e84bf-109">Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="e84bf-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="e84bf-110">Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.</span><span class="sxs-lookup"><span data-stu-id="e84bf-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="e84bf-111">Explorer les mathématiques avec des entiers</span><span class="sxs-lookup"><span data-stu-id="e84bf-111">Explore integer math</span></span>

<span data-ttu-id="e84bf-112">Créez un répertoire nommé *numbers-quickstart*.</span><span class="sxs-lookup"><span data-stu-id="e84bf-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="e84bf-113">Créez le répertoire actif et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e84bf-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="e84bf-114">Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez la ligne `Console.WriteLine("Hello World!");` par le code qui suit :</span><span class="sxs-lookup"><span data-stu-id="e84bf-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="e84bf-115">Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="e84bf-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="e84bf-116">Vous avez vu une des opérations mathématiques fondamentales avec des entiers.</span><span class="sxs-lookup"><span data-stu-id="e84bf-116">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="e84bf-117">Le `int` type représente un **entier**, un zéro, un nombre entier positif ou négatif.</span><span class="sxs-lookup"><span data-stu-id="e84bf-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="e84bf-118">Vous utilisez le symbole `+` pour effectuer une addition.</span><span class="sxs-lookup"><span data-stu-id="e84bf-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="e84bf-119">Les autres opérations mathématiques courantes avec des entiers sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e84bf-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="e84bf-120">`-` pour la soustraction</span><span class="sxs-lookup"><span data-stu-id="e84bf-120">`-` for subtraction</span></span>
- <span data-ttu-id="e84bf-121">`*` pour la multiplication</span><span class="sxs-lookup"><span data-stu-id="e84bf-121">`*` for multiplication</span></span>
- <span data-ttu-id="e84bf-122">`/` pour la division</span><span class="sxs-lookup"><span data-stu-id="e84bf-122">`/` for division</span></span>

<span data-ttu-id="e84bf-123">Commencez par explorer ces différentes opérations.</span><span class="sxs-lookup"><span data-stu-id="e84bf-123">Start by exploring those different operations.</span></span> <span data-ttu-id="e84bf-124">Ajoutez ces lignes après la ligne qui écrit la valeur de `c` :</span><span class="sxs-lookup"><span data-stu-id="e84bf-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="e84bf-125">Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="e84bf-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="e84bf-126">Vous pouvez également expérimenter en écrivant plusieurs opérations mathématiques dans la même ligne, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="e84bf-126">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="e84bf-127">Essayez `c = a + b - 12 * 17;` par exemple.</span><span class="sxs-lookup"><span data-stu-id="e84bf-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="e84bf-128">La combinaison de variables et de nombres constants est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e84bf-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="e84bf-129">Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code.</span><span class="sxs-lookup"><span data-stu-id="e84bf-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="e84bf-130">Le **compilateur** détectera ces erreurs et vous les signalera.</span><span class="sxs-lookup"><span data-stu-id="e84bf-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="e84bf-131">Si la sortie contient des messages d’erreur, vérifiez attentivement l’exemple de code ainsi que le code dans votre fenêtre pour identifier les corrections à apporter.</span><span class="sxs-lookup"><span data-stu-id="e84bf-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="e84bf-132">Cet exercice vous aidera à mieux comprendre la structure du code C#.</span><span class="sxs-lookup"><span data-stu-id="e84bf-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="e84bf-133">Vous avez terminé la première étape.</span><span class="sxs-lookup"><span data-stu-id="e84bf-133">You've finished the first step.</span></span> <span data-ttu-id="e84bf-134">Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="e84bf-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="e84bf-135">Cela nous permettra de travailler plus facilement avec un nouvel exemple.</span><span class="sxs-lookup"><span data-stu-id="e84bf-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="e84bf-136">Renommez votre méthode `Main``WorkingWithIntegers` et écrivez une nouvelle méthode `Main` qui appelle `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="e84bf-137">Lorsque vous avez terminé, votre code doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="e84bf-137">When you finish, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="e84bf-138">Explorer l’ordre des opérations</span><span class="sxs-lookup"><span data-stu-id="e84bf-138">Explore order of operations</span></span>

<span data-ttu-id="e84bf-139">Commentez l’appel à `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="e84bf-140">La sortie est ainsi moins encombrée lorsque vous travaillez dans cette section :</span><span class="sxs-lookup"><span data-stu-id="e84bf-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="e84bf-141">`//` démarre un **commentaire** dans C#.</span><span class="sxs-lookup"><span data-stu-id="e84bf-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="e84bf-142">Les commentaires correspondent à du texte que vous voulez conserver dans votre code source sans l’exécuter en tant que code.</span><span class="sxs-lookup"><span data-stu-id="e84bf-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="e84bf-143">Le compilateur ne génère pas de code exécutable à partir de commentaires.</span><span class="sxs-lookup"><span data-stu-id="e84bf-143">The compiler doesn't generate any executable code from comments.</span></span>

<span data-ttu-id="e84bf-144">Le langage C# définit la priorité des différentes opérations mathématiques avec à l’aide de règles cohérentes avec les règles mathématiques que vous avez apprises.</span><span class="sxs-lookup"><span data-stu-id="e84bf-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="e84bf-145">La multiplication et la division ont priorité sur l’addition et la soustraction.</span><span class="sxs-lookup"><span data-stu-id="e84bf-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="e84bf-146">Explorez ce concept en ajoutant le code suivant à votre méthode `Main` et en exécutant `dotnet run` :</span><span class="sxs-lookup"><span data-stu-id="e84bf-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="e84bf-147">La sortie montre que la multiplication est effectuée avant l’addition.</span><span class="sxs-lookup"><span data-stu-id="e84bf-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="e84bf-148">Vous pouvez appliquer un ordre de calcul différent en mettant entre parenthèses la ou les opérations à exécuter en premier.</span><span class="sxs-lookup"><span data-stu-id="e84bf-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="e84bf-149">Ajoutez les lignes suivantes et exécutez à nouveau :</span><span class="sxs-lookup"><span data-stu-id="e84bf-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="e84bf-150">Pratiquez en combinant plusieurs opérations différentes.</span><span class="sxs-lookup"><span data-stu-id="e84bf-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="e84bf-151">Ajoutez quelque chose ressemblant aux lignes suivantes au bas de votre méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="e84bf-152">Essayez `dotnet run` à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e84bf-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="e84bf-153">Vous avez peut-être observé un comportement intéressant des entiers.</span><span class="sxs-lookup"><span data-stu-id="e84bf-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="e84bf-154">La division d’entiers produit toujours un résultat entier, même quand vous pensez que le résultat devrait inclure une partie décimale ou fractionnaire.</span><span class="sxs-lookup"><span data-stu-id="e84bf-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="e84bf-155">Si vous n’avez pas observé ce comportement, essayez le code qui suit à la fin de votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="e84bf-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="e84bf-156">Tapez `dotnet run` à nouveau pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="e84bf-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="e84bf-157">Avant de continuer, prenez tout le code que vous avez écrit dans cette section et placez-le dans une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="e84bf-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="e84bf-158">Nommez cette nouvelle méthode `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="e84bf-159">Vous devez écrire un texte similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e84bf-159">You should write something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="e84bf-160">Explorer la précision et les limites des entiers</span><span class="sxs-lookup"><span data-stu-id="e84bf-160">Explore integer precision and limits</span></span>

<span data-ttu-id="e84bf-161">Ce dernier exemple a montré que la division d’entiers tronque le résultat.</span><span class="sxs-lookup"><span data-stu-id="e84bf-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="e84bf-162">Vous pouvez obtenir le **reste** à l’aide de l’opérateur **modulo**, à savoir le caractère `%`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="e84bf-163">Essayez le code suivant dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="e84bf-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="e84bf-164">Le type d’entier C# diffère des entiers mathématiques d’une autre manière : le type `int` a des limites minimale et maximale.</span><span class="sxs-lookup"><span data-stu-id="e84bf-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="e84bf-165">Ajoutez ce code à votre méthode `Main` pour voir ces limites :</span><span class="sxs-lookup"><span data-stu-id="e84bf-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="e84bf-166">Si un calcul produit une valeur qui dépasse ces limites, vous obtenez une condition de **dépassement négatif** ou **dépassement positif**.</span><span class="sxs-lookup"><span data-stu-id="e84bf-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="e84bf-167">La réponse affichée indique la plage (d’une limite à l’autre).</span><span class="sxs-lookup"><span data-stu-id="e84bf-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="e84bf-168">Ajoutez ces deux lignes à votre méthode `Main` pour voir un exemple :</span><span class="sxs-lookup"><span data-stu-id="e84bf-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="e84bf-169">Notez que la réponse est très proche de l’entier minimal (négatif).</span><span class="sxs-lookup"><span data-stu-id="e84bf-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="e84bf-170">Il en est de même pour `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="e84bf-171">L’addition a produit un **dépassement négatif** des valeurs autorisées pour les entiers.</span><span class="sxs-lookup"><span data-stu-id="e84bf-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="e84bf-172">La réponse est un très grand nombre négatif, car un dépassement négatif « inclut » de la plus grande valeur d’entier possible à la plus petite.</span><span class="sxs-lookup"><span data-stu-id="e84bf-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="e84bf-173">Il existe d’autres types numériques avec une précision et des limites différentes que vous pouvez utiliser quand le type `int` ne répond pas à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="e84bf-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="e84bf-174">Étudions les autres types suivants.</span><span class="sxs-lookup"><span data-stu-id="e84bf-174">Let's explore those other types next.</span></span>

<span data-ttu-id="e84bf-175">Encore une fois, déplaçons le code que vous avez écrit dans cette section vers une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="e84bf-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="e84bf-176">Nommez-le `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="e84bf-177">Utiliser le type double</span><span class="sxs-lookup"><span data-stu-id="e84bf-177">Work with the double type</span></span>

<span data-ttu-id="e84bf-178">Le type numérique `double` représente un nombre à virgule flottante double précision.</span><span class="sxs-lookup"><span data-stu-id="e84bf-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="e84bf-179">Ces termes vous sont peut-être inconnus.</span><span class="sxs-lookup"><span data-stu-id="e84bf-179">Those terms may be new to you.</span></span> <span data-ttu-id="e84bf-180">Un nombre à **virgule flottante** est utile pour représenter des nombres non intégraux qui peuvent être très grands ou très petits en amplitude.</span><span class="sxs-lookup"><span data-stu-id="e84bf-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="e84bf-181">La **double précision** est un terme relatif qui décrit le nombre de chiffres binaires utilisés pour stocker la valeur.</span><span class="sxs-lookup"><span data-stu-id="e84bf-181">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="e84bf-182">Les nombres à **double précision** ont deux fois le nombre de chiffres binaires comme **simple précision**.</span><span class="sxs-lookup"><span data-stu-id="e84bf-182">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="e84bf-183">Sur les ordinateurs modernes, il est plus courant d’utiliser une double précision que des nombres à simple précision.</span><span class="sxs-lookup"><span data-stu-id="e84bf-183">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="e84bf-184">Les nombres à **précision unique** sont déclarés à l’aide du `float` mot clé.</span><span class="sxs-lookup"><span data-stu-id="e84bf-184">**Single precision** numbers are declared using the `float` keyword.</span></span>
<span data-ttu-id="e84bf-185">Explorons ce type double.</span><span class="sxs-lookup"><span data-stu-id="e84bf-185">Let's explore.</span></span> <span data-ttu-id="e84bf-186">Ajoutez le code suivant et affichez le résultat :</span><span class="sxs-lookup"><span data-stu-id="e84bf-186">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="e84bf-187">Notez que la réponse inclut la partie décimale du quotient.</span><span class="sxs-lookup"><span data-stu-id="e84bf-187">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="e84bf-188">Essayez avec une expression légèrement plus complexe utilisant des doubles :</span><span class="sxs-lookup"><span data-stu-id="e84bf-188">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="e84bf-189">La plage d’une valeur double est nettement supérieure à celle de valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="e84bf-189">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="e84bf-190">Essayez le code suivant sous ce que vous avez écrit jusque-là :</span><span class="sxs-lookup"><span data-stu-id="e84bf-190">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="e84bf-191">Ces valeurs s’affichent sous forme de notation scientifique.</span><span class="sxs-lookup"><span data-stu-id="e84bf-191">These values are printed out in scientific notation.</span></span> <span data-ttu-id="e84bf-192">Le nombre à gauche du `E` est le nombre significatif.</span><span class="sxs-lookup"><span data-stu-id="e84bf-192">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="e84bf-193">Le nombre à droite est l’exposant, en puissance de 10.</span><span class="sxs-lookup"><span data-stu-id="e84bf-193">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="e84bf-194">Tout comme les nombres décimaux en mathématiques, les doubles en C# peuvent présenter des erreurs d’arrondi.</span><span class="sxs-lookup"><span data-stu-id="e84bf-194">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="e84bf-195">Exécutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e84bf-195">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="e84bf-196">Vous savez que `0.3` la répétition n’est pas exactement identique `1/3`à celle de.</span><span class="sxs-lookup"><span data-stu-id="e84bf-196">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="e84bf-197">***Test***</span><span class="sxs-lookup"><span data-stu-id="e84bf-197">***Challenge***</span></span>

<span data-ttu-id="e84bf-198">Essayez d’autres calculs avec de grands nombres, des petits nombres, des multiplications `double` et des divisions à l’aide du type.</span><span class="sxs-lookup"><span data-stu-id="e84bf-198">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="e84bf-199">Effectuez des calculs plus complexes.</span><span class="sxs-lookup"><span data-stu-id="e84bf-199">Try more complicated calculations.</span></span>

<span data-ttu-id="e84bf-200">Après avoir consacré plus de temps au test, placez le code que vous avez écrit dans une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="e84bf-200">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="e84bf-201">Nommez cette nouvelle méthode `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-201">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="e84bf-202">Utiliser des types décimaux</span><span class="sxs-lookup"><span data-stu-id="e84bf-202">Work with decimal types</span></span>

<span data-ttu-id="e84bf-203">Vous avez vu les types numériques de base en C#, à savoir les entiers et les doubles.</span><span class="sxs-lookup"><span data-stu-id="e84bf-203">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="e84bf-204">Il y a un autre type à apprendre : `decimal` le type.</span><span class="sxs-lookup"><span data-stu-id="e84bf-204">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="e84bf-205">Le type `decimal` a une plage plus petite, mais une précision supérieure à celle du type `double`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-205">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="e84bf-206">Étudions cela d’un peu plus près :</span><span class="sxs-lookup"><span data-stu-id="e84bf-206">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="e84bf-207">Notez que la plage est plus petite que celle du type `double`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-207">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="e84bf-208">Vous pouvez observer la plus haute précision du type décimal en exécutant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e84bf-208">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="e84bf-209">Le suffixe `M` des nombres permet d’indiquer comment une constante doit utiliser le type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e84bf-209">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="e84bf-210">Sinon, le compilateur suppose le `double` type.</span><span class="sxs-lookup"><span data-stu-id="e84bf-210">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="e84bf-211">La lettre `M` a été choisie comme lettre la plus distincte entre les `double` Mots clés `decimal` et.</span><span class="sxs-lookup"><span data-stu-id="e84bf-211">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="e84bf-212">Notez que le calcul utilisant le type décimal a plus de chiffres à droite de la virgule décimale.</span><span class="sxs-lookup"><span data-stu-id="e84bf-212">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="e84bf-213">***Test***</span><span class="sxs-lookup"><span data-stu-id="e84bf-213">***Challenge***</span></span>

<span data-ttu-id="e84bf-214">Maintenant que vous avez vu les différents types numériques, écrivez du code qui calcule la surface d’un cercle avec un rayon de 2,5 centimètres.</span><span class="sxs-lookup"><span data-stu-id="e84bf-214">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="e84bf-215">Rappelez-vous que la surface d’un cercle est le rayon au carré multiplié par PI.</span><span class="sxs-lookup"><span data-stu-id="e84bf-215">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="e84bf-216">Conseil : .NET contient une constante pour PI, à savoir <xref:System.Math.PI?displayProperty=nameWithType>, que vous pouvez utiliser pour cette valeur.</span><span class="sxs-lookup"><span data-stu-id="e84bf-216">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="e84bf-217"><xref:System.Math.PI?displayProperty=nameWithType>, comme toutes les constantes déclarées `System.Math` dans l’espace de `double` noms, est une valeur.</span><span class="sxs-lookup"><span data-stu-id="e84bf-217"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="e84bf-218">Pour cette raison, vous devez utiliser `double` au lieu `decimal` de valeurs pour ce défi.</span><span class="sxs-lookup"><span data-stu-id="e84bf-218">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="e84bf-219">Vous devriez obtenir une réponse comprise entre 19 et 20.</span><span class="sxs-lookup"><span data-stu-id="e84bf-219">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="e84bf-220">Vous pouvez vérifier votre réponse en [examinant l’exemple de code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span><span class="sxs-lookup"><span data-stu-id="e84bf-220">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="e84bf-221">Si vous le voulez, essayez d’autres formules.</span><span class="sxs-lookup"><span data-stu-id="e84bf-221">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="e84bf-222">Vous avez terminé le guide de démarrage rapide « Nombres en C# ».</span><span class="sxs-lookup"><span data-stu-id="e84bf-222">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="e84bf-223">Vous pouvez passer au guide de démarrage rapide [Branches et boucles](branches-and-loops-local.md) dans votre propre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="e84bf-223">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="e84bf-224">Vous pouvez en savoir plus sur les nombres en C# dans les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="e84bf-224">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="e84bf-225">Types numériques intégraux</span><span class="sxs-lookup"><span data-stu-id="e84bf-225">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="e84bf-226">Types numériques à virgule flottante</span><span class="sxs-lookup"><span data-stu-id="e84bf-226">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="e84bf-227">Conversions numériques intégrées</span><span class="sxs-lookup"><span data-stu-id="e84bf-227">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
