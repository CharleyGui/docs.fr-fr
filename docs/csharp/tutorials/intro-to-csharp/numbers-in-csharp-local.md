---
title: Nombres en C# – Tutoriel d’introduction à C#
description: Découvrez C# en explorant les types numériques, leurs propriétés et méthodes.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 65b31c29fa9662619f92efb7977577f12d23fb30
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423417"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="8cf27-103">Manipuler les nombres intégraux et à virgule flottante en C\#</span><span class="sxs-lookup"><span data-stu-id="8cf27-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="8cf27-104">Ce tutoriel permet de découvrir de manière interactive les types numériques en C#.</span><span class="sxs-lookup"><span data-stu-id="8cf27-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="8cf27-105">Vous allez écrire de petites quantités de code, puis vous compilerez et exécuterez ce code.</span><span class="sxs-lookup"><span data-stu-id="8cf27-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="8cf27-106">Ce tutoriel comporte une série de leçons visant à explorer les nombres et les opérations mathématiques en C#.</span><span class="sxs-lookup"><span data-stu-id="8cf27-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="8cf27-107">Ces leçons présentent les concepts de base du langage C#.</span><span class="sxs-lookup"><span data-stu-id="8cf27-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="8cf27-108">Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement.</span><span class="sxs-lookup"><span data-stu-id="8cf27-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="8cf27-109">La rubrique .NET [Bien démarrer en 10 minutes](https://www.microsoft.com/net/core) contient des instructions pour configurer votre environnement de développement local sur Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="8cf27-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="8cf27-110">Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.</span><span class="sxs-lookup"><span data-stu-id="8cf27-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="8cf27-111">Explorer les mathématiques avec des entiers</span><span class="sxs-lookup"><span data-stu-id="8cf27-111">Explore integer math</span></span>

<span data-ttu-id="8cf27-112">Créez un répertoire nommé **numbers-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="8cf27-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="8cf27-113">Faites-en le répertoire actuel et exécutez `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="8cf27-114">Ouvrez **Program.cs** dans votre éditeur favori, puis remplacez la ligne `Console.WriteLine("Hello World!");` par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="8cf27-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="8cf27-115">Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="8cf27-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="8cf27-116">Vous venez d’observer l’une des opérations mathématiques de base avec des entiers.</span><span class="sxs-lookup"><span data-stu-id="8cf27-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="8cf27-117">Le type `int` représente un **entier**, qui peut être positif ou négatif.</span><span class="sxs-lookup"><span data-stu-id="8cf27-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="8cf27-118">Vous utilisez le symbole `+` pour effectuer une addition.</span><span class="sxs-lookup"><span data-stu-id="8cf27-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="8cf27-119">Les autres opérations mathématiques courantes avec des entiers sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8cf27-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="8cf27-120">`-` pour la soustraction</span><span class="sxs-lookup"><span data-stu-id="8cf27-120">`-` for subtraction</span></span>
- <span data-ttu-id="8cf27-121">`*` pour la multiplication</span><span class="sxs-lookup"><span data-stu-id="8cf27-121">`*` for multiplication</span></span>
- <span data-ttu-id="8cf27-122">`/` pour la division</span><span class="sxs-lookup"><span data-stu-id="8cf27-122">`/` for division</span></span>

<span data-ttu-id="8cf27-123">Commencez par explorer ces différentes opérations.</span><span class="sxs-lookup"><span data-stu-id="8cf27-123">Start by exploring those different operations.</span></span> <span data-ttu-id="8cf27-124">Ajoutez ces lignes après la ligne qui écrit la valeur de `c` :</span><span class="sxs-lookup"><span data-stu-id="8cf27-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="8cf27-125">Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="8cf27-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="8cf27-126">Vous pouvez également, si vous le souhaitez, effectuer des essais en réalisant plusieurs opérations mathématiques dans la même ligne.</span><span class="sxs-lookup"><span data-stu-id="8cf27-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="8cf27-127">Essayez `c = a + b - 12 * 17;` par exemple.</span><span class="sxs-lookup"><span data-stu-id="8cf27-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="8cf27-128">La combinaison de variables et de nombres constants est autorisée.</span><span class="sxs-lookup"><span data-stu-id="8cf27-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="8cf27-129">Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code.</span><span class="sxs-lookup"><span data-stu-id="8cf27-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="8cf27-130">Le **compilateur** détectera ces erreurs et vous les signalera.</span><span class="sxs-lookup"><span data-stu-id="8cf27-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="8cf27-131">Si la sortie contient des messages d’erreur, vérifiez attentivement l’exemple de code ainsi que le code dans votre fenêtre pour identifier les corrections à apporter.</span><span class="sxs-lookup"><span data-stu-id="8cf27-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="8cf27-132">Cet exercice vous aidera à mieux comprendre la structure du code C#.</span><span class="sxs-lookup"><span data-stu-id="8cf27-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="8cf27-133">Vous avez terminé la première étape.</span><span class="sxs-lookup"><span data-stu-id="8cf27-133">You've finished the first step.</span></span> <span data-ttu-id="8cf27-134">Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="8cf27-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="8cf27-135">Cela nous permettra de travailler plus facilement avec un nouvel exemple.</span><span class="sxs-lookup"><span data-stu-id="8cf27-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="8cf27-136">Renommez votre méthode `Main` `WorkingWithIntegers` et écrivez une nouvelle méthode `Main` qui appelle `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="8cf27-137">Une fois terminé, votre code doit ressembler au code suivant :</span><span class="sxs-lookup"><span data-stu-id="8cf27-137">When you have finished, your code should look like this:</span></span>

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

## <a name="explore-order-of-operations"></a><span data-ttu-id="8cf27-138">Explorer l’ordre des opérations</span><span class="sxs-lookup"><span data-stu-id="8cf27-138">Explore order of operations</span></span>

<span data-ttu-id="8cf27-139">Commentez l’appel à `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="8cf27-140">La sortie est ainsi moins encombrée lorsque vous travaillez dans cette section :</span><span class="sxs-lookup"><span data-stu-id="8cf27-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="8cf27-141">`//` démarre un **commentaire** dans C#.</span><span class="sxs-lookup"><span data-stu-id="8cf27-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="8cf27-142">Les commentaires correspondent à du texte que vous voulez conserver dans votre code source sans l’exécuter en tant que code.</span><span class="sxs-lookup"><span data-stu-id="8cf27-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="8cf27-143">Le compilateur ne génère aucun fichier exécutable à partir des commentaires.</span><span class="sxs-lookup"><span data-stu-id="8cf27-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="8cf27-144">Le langage C# définit la priorité des différentes opérations mathématiques avec à l’aide de règles cohérentes avec les règles mathématiques que vous avez apprises.</span><span class="sxs-lookup"><span data-stu-id="8cf27-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="8cf27-145">La multiplication et la division ont priorité sur l’addition et la soustraction.</span><span class="sxs-lookup"><span data-stu-id="8cf27-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="8cf27-146">Explorez ce concept en ajoutant le code suivant à votre méthode `Main` et en exécutant `dotnet run` :</span><span class="sxs-lookup"><span data-stu-id="8cf27-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="8cf27-147">La sortie montre que la multiplication est effectuée avant l’addition.</span><span class="sxs-lookup"><span data-stu-id="8cf27-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="8cf27-148">Vous pouvez appliquer un ordre de calcul différent en mettant entre parenthèses la ou les opérations à exécuter en premier.</span><span class="sxs-lookup"><span data-stu-id="8cf27-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="8cf27-149">Ajoutez les lignes suivantes et exécutez à nouveau :</span><span class="sxs-lookup"><span data-stu-id="8cf27-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="8cf27-150">Pratiquez en combinant plusieurs opérations différentes.</span><span class="sxs-lookup"><span data-stu-id="8cf27-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="8cf27-151">Ajoutez quelque chose ressemblant aux lignes suivantes au bas de votre méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="8cf27-152">Essayez `dotnet run` à nouveau.</span><span class="sxs-lookup"><span data-stu-id="8cf27-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="8cf27-153">Vous avez peut-être observé un comportement intéressant des entiers.</span><span class="sxs-lookup"><span data-stu-id="8cf27-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="8cf27-154">La division d’entiers produit toujours un résultat entier, même quand vous pensez que le résultat devrait inclure une partie décimale ou fractionnaire.</span><span class="sxs-lookup"><span data-stu-id="8cf27-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="8cf27-155">Si vous n’avez pas observé ce comportement, essayez le code qui suit à la fin de votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="8cf27-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="8cf27-156">Tapez `dotnet run` à nouveau pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="8cf27-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="8cf27-157">Avant de continuer, prenez tout le code que vous avez écrit dans cette section et placez-le dans une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="8cf27-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="8cf27-158">Nommez cette nouvelle méthode `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="8cf27-159">Vous devriez obtenir un résultat similaire à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="8cf27-159">You should end up with something like this:</span></span>

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

            d = (a  + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="8cf27-160">Explorer la précision et les limites des entiers</span><span class="sxs-lookup"><span data-stu-id="8cf27-160">Explore integer precision and limits</span></span>

<span data-ttu-id="8cf27-161">Ce dernier exemple a montré que la division d’entiers tronque le résultat.</span><span class="sxs-lookup"><span data-stu-id="8cf27-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="8cf27-162">Vous pouvez obtenir le **reste** à l’aide de l’opérateur **modulo**, à savoir le caractère `%`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="8cf27-163">Essayez le code suivant dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="8cf27-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="8cf27-164">Le type d’entier C# diffère des entiers mathématiques d’une autre manière : le type `int` a des limites minimale et maximale.</span><span class="sxs-lookup"><span data-stu-id="8cf27-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="8cf27-165">Ajoutez ce code à votre méthode `Main` pour voir ces limites :</span><span class="sxs-lookup"><span data-stu-id="8cf27-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="8cf27-166">Si un calcul produit une valeur qui dépasse ces limites, vous obtenez une condition de **dépassement négatif** ou **dépassement positif**.</span><span class="sxs-lookup"><span data-stu-id="8cf27-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="8cf27-167">La réponse affichée indique la plage (d’une limite à l’autre).</span><span class="sxs-lookup"><span data-stu-id="8cf27-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="8cf27-168">Ajoutez ces deux lignes à votre méthode `Main` pour voir un exemple :</span><span class="sxs-lookup"><span data-stu-id="8cf27-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="8cf27-169">Notez que la réponse est très proche de l’entier minimal (négatif).</span><span class="sxs-lookup"><span data-stu-id="8cf27-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="8cf27-170">Il en est de même pour `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="8cf27-171">L’addition a produit un **dépassement négatif** des valeurs autorisées pour les entiers.</span><span class="sxs-lookup"><span data-stu-id="8cf27-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="8cf27-172">La réponse est un très grand nombre négatif, car un dépassement négatif « inclut » de la plus grande valeur d’entier possible à la plus petite.</span><span class="sxs-lookup"><span data-stu-id="8cf27-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="8cf27-173">Il existe d’autres types numériques avec une précision et des limites différentes que vous pouvez utiliser quand le type `int` ne répond pas à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="8cf27-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="8cf27-174">Nous les explorerons à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="8cf27-174">Let's explore those next.</span></span>

<span data-ttu-id="8cf27-175">Encore une fois, déplaçons le code que vous avez écrit dans cette section vers une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="8cf27-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="8cf27-176">Nommez-le `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="8cf27-177">Utiliser le type double</span><span class="sxs-lookup"><span data-stu-id="8cf27-177">Work with the double type</span></span>

<span data-ttu-id="8cf27-178">Le type numérique `double` représente un nombre à virgule flottante double précision.</span><span class="sxs-lookup"><span data-stu-id="8cf27-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="8cf27-179">Ces termes vous sont peut-être inconnus.</span><span class="sxs-lookup"><span data-stu-id="8cf27-179">Those terms may be new to you.</span></span> <span data-ttu-id="8cf27-180">Un nombre **à virgule flottante** est utile pour représenter de très grands ou petits nombres non intégraux.</span><span class="sxs-lookup"><span data-stu-id="8cf27-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="8cf27-181">La **double précision** signifie que ces nombres sont stockés avec une précision supérieure à la **simple précision**.</span><span class="sxs-lookup"><span data-stu-id="8cf27-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="8cf27-182">Sur les ordinateurs modernes, les nombres double précision sont généralement plus utilisés que les nombres simple précision.</span><span class="sxs-lookup"><span data-stu-id="8cf27-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="8cf27-183">Explorons ce type double.</span><span class="sxs-lookup"><span data-stu-id="8cf27-183">Let's explore.</span></span> <span data-ttu-id="8cf27-184">Ajoutez le code suivant et affichez le résultat :</span><span class="sxs-lookup"><span data-stu-id="8cf27-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="8cf27-185">Notez que la réponse inclut la partie décimale du quotient.</span><span class="sxs-lookup"><span data-stu-id="8cf27-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="8cf27-186">Essayez avec une expression légèrement plus complexe utilisant des doubles :</span><span class="sxs-lookup"><span data-stu-id="8cf27-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="8cf27-187">La plage d’une valeur double est nettement supérieure à celle de valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="8cf27-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="8cf27-188">Essayez le code suivant sous ce que vous avez écrit jusque-là :</span><span class="sxs-lookup"><span data-stu-id="8cf27-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="8cf27-189">Ces valeurs s’affichent sous forme de notation scientifique.</span><span class="sxs-lookup"><span data-stu-id="8cf27-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="8cf27-190">Le nombre à gauche du `E` est le nombre significatif.</span><span class="sxs-lookup"><span data-stu-id="8cf27-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="8cf27-191">Le nombre à droite est l’exposant, en puissance de 10.</span><span class="sxs-lookup"><span data-stu-id="8cf27-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="8cf27-192">Tout comme les nombres décimaux en mathématiques, les doubles en C# peuvent présenter des erreurs d’arrondi.</span><span class="sxs-lookup"><span data-stu-id="8cf27-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="8cf27-193">Exécutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8cf27-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="8cf27-194">Vous savez que la valeur extensible `0.3` ne correspond pas exactement à `1/3`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="8cf27-195">***Test***</span><span class="sxs-lookup"><span data-stu-id="8cf27-195">***Challenge***</span></span>

<span data-ttu-id="8cf27-196">Effectuez d’autres calculs avec des grands nombres, des petits nombres, des multiplications et des divisions à l’aide du type `double`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="8cf27-197">Effectuez des calculs plus complexes.</span><span class="sxs-lookup"><span data-stu-id="8cf27-197">Try more complicated calculations.</span></span>

<span data-ttu-id="8cf27-198">Après avoir consacré plus de temps au test, placez le code que vous avez écrit dans une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="8cf27-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="8cf27-199">Nommez cette nouvelle méthode `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="8cf27-200">Utiliser des types de virgule fixe</span><span class="sxs-lookup"><span data-stu-id="8cf27-200">Work with fixed point types</span></span>

<span data-ttu-id="8cf27-201">Vous avez vu les types numériques de base en C#, à savoir les entiers et les doubles.</span><span class="sxs-lookup"><span data-stu-id="8cf27-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="8cf27-202">Il existe un autre type à découvrir : le type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="8cf27-203">Le type `decimal` a une plage plus petite, mais une précision supérieure à celle du type `double`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="8cf27-204">Le terme **virgule fixe** signifie que la virgule décimale (ou virgule binaire) ne se déplace pas.</span><span class="sxs-lookup"><span data-stu-id="8cf27-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="8cf27-205">Étudions cela d’un peu plus près :</span><span class="sxs-lookup"><span data-stu-id="8cf27-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="8cf27-206">Notez que la plage est plus petite que celle du type `double`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="8cf27-207">Vous pouvez observer la plus haute précision du type décimal en exécutant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8cf27-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="8cf27-208">Le suffixe `M` des nombres permet d’indiquer comment une constante doit utiliser le type `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8cf27-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="8cf27-209">Notez que le calcul utilisant le type décimal a plus de chiffres à droite de la virgule décimale.</span><span class="sxs-lookup"><span data-stu-id="8cf27-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="8cf27-210">***Test***</span><span class="sxs-lookup"><span data-stu-id="8cf27-210">***Challenge***</span></span>

<span data-ttu-id="8cf27-211">Maintenant que vous avez vu les différents types numériques, écrivez du code qui calcule la surface d’un cercle avec un rayon de 2,5 centimètres.</span><span class="sxs-lookup"><span data-stu-id="8cf27-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="8cf27-212">Rappelez-vous que la surface d’un cercle est le rayon au carré multiplié par PI.</span><span class="sxs-lookup"><span data-stu-id="8cf27-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="8cf27-213">Conseil : .NET contient une constante pour PI, à savoir <xref:System.Math.PI?displayProperty=nameWithType>, que vous pouvez utiliser pour cette valeur.</span><span class="sxs-lookup"><span data-stu-id="8cf27-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="8cf27-214">Vous devriez obtenir une réponse comprise entre 19 et 20.</span><span class="sxs-lookup"><span data-stu-id="8cf27-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="8cf27-215">Vous pouvez vérifier votre réponse en [consultant l’exemple de code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="8cf27-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="8cf27-216">Si vous le voulez, essayez d’autres formules.</span><span class="sxs-lookup"><span data-stu-id="8cf27-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="8cf27-217">Vous avez terminé le guide de démarrage rapide « Nombres en C# ».</span><span class="sxs-lookup"><span data-stu-id="8cf27-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="8cf27-218">Vous pouvez passer au guide de démarrage rapide [Branches et boucles](branches-and-loops-local.md) dans votre propre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="8cf27-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="8cf27-219">Pour en savoir plus sur les nombres en C#, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8cf27-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="8cf27-220">Types intégraux</span><span class="sxs-lookup"><span data-stu-id="8cf27-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="8cf27-221">Tableau des types virgule flottante</span><span class="sxs-lookup"><span data-stu-id="8cf27-221">Floating-Point Types Table</span></span>](../../language-reference/keywords/floating-point-types-table.md)
- [<span data-ttu-id="8cf27-222">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="8cf27-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="8cf27-223">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="8cf27-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="8cf27-224">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="8cf27-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
