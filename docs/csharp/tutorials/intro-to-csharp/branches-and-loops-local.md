---
title: Branches et boucles – Tutoriel d’introduction à C#
description: Dans ce tutoriel sur les branches et les boucles, vous allez écrire du code en C# pour explorer la syntaxe du langage qui gère les branches et les boucles conditionnelles permettant d’exécuter des instructions de manière répétée.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396878"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="df631-103">Découvrir la logique conditionnelle avec des instructions de branches et de boucles</span><span class="sxs-lookup"><span data-stu-id="df631-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="df631-104">Ce tutoriel explique comment écrire du code qui examine des variables et modifie le chemin d’exécution en fonction de ces variables.</span><span class="sxs-lookup"><span data-stu-id="df631-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="df631-105">Vous allez écrire un code en C# et afficher les résultats de la compilation et de l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="df631-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="df631-106">Ce tutoriel comporte une série de leçons visant à explorer les constructions de type branches et boucles en C#.</span><span class="sxs-lookup"><span data-stu-id="df631-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="df631-107">Ces leçons présentent les concepts de base du langage C#.</span><span class="sxs-lookup"><span data-stu-id="df631-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="df631-108">Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement.</span><span class="sxs-lookup"><span data-stu-id="df631-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="df631-109">Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="df631-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="df631-110">Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.</span><span class="sxs-lookup"><span data-stu-id="df631-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="df631-111">Prendre des décisions à l’aide de l’instruction `if`</span><span class="sxs-lookup"><span data-stu-id="df631-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="df631-112">Créez un répertoire nommé *branches-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="df631-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="df631-113">Créez le répertoire actif et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="df631-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="df631-114">Cette commande crée une nouvelle application console .NET Core dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="df631-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="df631-115">Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez la ligne `Console.WriteLine("Hello World!");` par le code qui suit :</span><span class="sxs-lookup"><span data-stu-id="df631-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="df631-116">Essayez ce code en tapant `dotnet run` dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="df631-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="df631-117">Le message « La réponse est supérieure à 10 » doit s’afficher</span><span class="sxs-lookup"><span data-stu-id="df631-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="df631-118">dans votre console.</span><span class="sxs-lookup"><span data-stu-id="df631-118">printed to your console.</span></span>

<span data-ttu-id="df631-119">Modifiez la déclaration de `b` pour que la somme soit inférieure à 10 :</span><span class="sxs-lookup"><span data-stu-id="df631-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="df631-120">Tapez `dotnet run` à nouveau.</span><span class="sxs-lookup"><span data-stu-id="df631-120">Type `dotnet run` again.</span></span> <span data-ttu-id="df631-121">La réponse étant inférieure à 10, rien ne s’affiche.</span><span class="sxs-lookup"><span data-stu-id="df631-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="df631-122">La **condition** que vous testez a une valeur false.</span><span class="sxs-lookup"><span data-stu-id="df631-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="df631-123">Vous n’avez pas de code à exécuter, car vous avez uniquement écrit l’une des branches possibles pour une instruction `if` : la branche true.</span><span class="sxs-lookup"><span data-stu-id="df631-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="df631-124">Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code.</span><span class="sxs-lookup"><span data-stu-id="df631-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="df631-125">Le compilateur détectera et signalera les erreurs.</span><span class="sxs-lookup"><span data-stu-id="df631-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="df631-126">Observez attentivement la sortie d’erreur et le code ayant généré l’erreur.</span><span class="sxs-lookup"><span data-stu-id="df631-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="df631-127">L’erreur du compilateur peut en général vous aider à trouver le problème.</span><span class="sxs-lookup"><span data-stu-id="df631-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="df631-128">Le premier exemple montre la puissance de l’instruction `if` et des types booléens.</span><span class="sxs-lookup"><span data-stu-id="df631-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="df631-129">Un *booléen* est une variable qui peut avoir l’une des deux valeurs suivantes : `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="df631-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="df631-130">C# définit un type spécial, `bool`, pour les variables booléennes.</span><span class="sxs-lookup"><span data-stu-id="df631-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="df631-131">L’instruction `if` vérifie la valeur d’un `bool`.</span><span class="sxs-lookup"><span data-stu-id="df631-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="df631-132">Quand la valeur est `true`, l’instruction qui suit `if` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="df631-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="df631-133">Dans le cas contraire, elle est ignorée.</span><span class="sxs-lookup"><span data-stu-id="df631-133">Otherwise, it's skipped.</span></span>

<span data-ttu-id="df631-134">Ce processus de vérification des conditions et d’exécution d’instructions en fonction de ces conditions est puissant.</span><span class="sxs-lookup"><span data-stu-id="df631-134">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="df631-135">Utiliser if et else ensemble</span><span class="sxs-lookup"><span data-stu-id="df631-135">Make if and else work together</span></span>

<span data-ttu-id="df631-136">Pour exécuter un code différent dans les branches true et false, vous créez une branche `else` qui s’exécute quand la condition a une valeur false.</span><span class="sxs-lookup"><span data-stu-id="df631-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="df631-137">Essayez ceci.</span><span class="sxs-lookup"><span data-stu-id="df631-137">Try this.</span></span> <span data-ttu-id="df631-138">Ajoutez les deux dernières lignes dans le code ci-dessous à votre méthode `Main` (vous devriez déjà avoir les quatre premières lignes) :</span><span class="sxs-lookup"><span data-stu-id="df631-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="df631-139">L’instruction qui suit le mot clé `else` s’exécute uniquement quand la condition testée a une valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="df631-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="df631-140">La combinaison de `if` et `else` avec des conditions booléennes offre les hautes performances dont vous avez besoin pour traiter une condition `true` et une condition `false`.</span><span class="sxs-lookup"><span data-stu-id="df631-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df631-141">La mise en retrait sous les instructions `if` et `else` a simplement pour but de faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="df631-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="df631-142">Le langage C# ne considère pas la mise en retrait ou les espaces blancs comme des éléments significatifs.</span><span class="sxs-lookup"><span data-stu-id="df631-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="df631-143">L’instruction qui suit le mot clé `if` ou `else` sera exécutée en fonction de la condition.</span><span class="sxs-lookup"><span data-stu-id="df631-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="df631-144">Tous les exemples de ce tutoriel suivent une pratique courante qui consiste à mettre en retrait les lignes en fonction du flux de contrôle des instructions.</span><span class="sxs-lookup"><span data-stu-id="df631-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="df631-145">Étant donné que la mise en retrait n’est pas significative, vous devez utiliser `{` et `}` pour indiquer quand vous souhaitez que plusieurs instructions fassent partie du bloc qui s’exécute de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="df631-145">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="df631-146">Les programmeurs C# utilisent généralement les accolades pour toutes les clauses `if` et `else`.</span><span class="sxs-lookup"><span data-stu-id="df631-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="df631-147">L’exemple suivant est identique à celui que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="df631-147">The following example is the same as the one you created.</span></span> <span data-ttu-id="df631-148">Modifiez votre code ci-dessus pour qu’il corresponde au code suivant :</span><span class="sxs-lookup"><span data-stu-id="df631-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="df631-149">Dans le reste de ce didacticiel, tous les exemples de code incluent les accolades, conformément aux pratiques acceptées.</span><span class="sxs-lookup"><span data-stu-id="df631-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="df631-150">Vous pouvez tester des conditions plus complexes.</span><span class="sxs-lookup"><span data-stu-id="df631-150">You can test more complicated conditions.</span></span> <span data-ttu-id="df631-151">Ajoutez le code suivant à votre méthode `Main` après le code que vous avez écrit jusque-là :</span><span class="sxs-lookup"><span data-stu-id="df631-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="df631-152">Le symbole `==` teste *l’égalité*.</span><span class="sxs-lookup"><span data-stu-id="df631-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="df631-153">`==` se distingue du test d’égalité d’attribution, que nous avons vu avec `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="df631-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="df631-154">`&&` représente « et ».</span><span class="sxs-lookup"><span data-stu-id="df631-154">The `&&` represents "and".</span></span> <span data-ttu-id="df631-155">Cela signifie que les deux conditions doivent être true pour que l’instruction s’exécute dans la branche true.</span><span class="sxs-lookup"><span data-stu-id="df631-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="df631-156">Ces exemples montrent également que vous pouvez avoir plusieurs instructions dans chaque branche conditionnelle, à condition de les mettre entre `{` et `}`.</span><span class="sxs-lookup"><span data-stu-id="df631-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="df631-157">Vous pouvez également utiliser `||` pour représenter « ou ».</span><span class="sxs-lookup"><span data-stu-id="df631-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="df631-158">Ajoutez le code suivant après ce que vous avez écrit jusque-là :</span><span class="sxs-lookup"><span data-stu-id="df631-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="df631-159">Modifiez les valeurs de `a`, `b` et `c` et passez de `&&` à `||` et inversement.</span><span class="sxs-lookup"><span data-stu-id="df631-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="df631-160">Vous comprendrez mieux comment fonctionnent les opérateurs `&&` et `||`.</span><span class="sxs-lookup"><span data-stu-id="df631-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="df631-161">Vous avez terminé la première étape.</span><span class="sxs-lookup"><span data-stu-id="df631-161">You've finished the first step.</span></span> <span data-ttu-id="df631-162">Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="df631-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="df631-163">Cela nous permettra de travailler plus facilement avec un nouvel exemple.</span><span class="sxs-lookup"><span data-stu-id="df631-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="df631-164">Renommez votre méthode `Main``ExploreIf` et écrivez une nouvelle méthode `Main` qui appelle `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="df631-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="df631-165">Lorsque vous avez terminé, votre code doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="df631-165">When you've finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="df631-166">Commentez l’appel à `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="df631-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="df631-167">La sortie est ainsi moins encombrée lorsque vous travaillez dans cette section :</span><span class="sxs-lookup"><span data-stu-id="df631-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="df631-168">`//` démarre un **commentaire** dans C#.</span><span class="sxs-lookup"><span data-stu-id="df631-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="df631-169">Les commentaires correspondent à du texte que vous voulez conserver dans votre code source sans l’exécuter en tant que code.</span><span class="sxs-lookup"><span data-stu-id="df631-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="df631-170">Le compilateur ne génère pas de code exécutable à partir de commentaires.</span><span class="sxs-lookup"><span data-stu-id="df631-170">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="df631-171">Utiliser des boucles pour répéter des opérations</span><span class="sxs-lookup"><span data-stu-id="df631-171">Use loops to repeat operations</span></span>

<span data-ttu-id="df631-172">Dans cette section, vous utilisez des **boucles** pour répéter des instructions.</span><span class="sxs-lookup"><span data-stu-id="df631-172">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="df631-173">Essayez ce code dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="df631-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="df631-174">L’instruction `while` vérifie une condition et exécute l’instruction ou le bloc d’instructions qui suit `while`.</span><span class="sxs-lookup"><span data-stu-id="df631-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="df631-175">Elle répète la vérification de la condition et l’exécution de ces instructions jusqu'à ce que la condition soit false.</span><span class="sxs-lookup"><span data-stu-id="df631-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="df631-176">Cet exemple contient un nouvel opérateur.</span><span class="sxs-lookup"><span data-stu-id="df631-176">There's one other new operator in this example.</span></span> <span data-ttu-id="df631-177">`++` après la variable `counter` est l’opérateur d’**incrémentation**.</span><span class="sxs-lookup"><span data-stu-id="df631-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="df631-178">Il ajoute 1 à la valeur de `counter` et stocke cette valeur dans la variable de `counter`.</span><span class="sxs-lookup"><span data-stu-id="df631-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df631-179">Assurez-vous que la condition de boucle `while` devient false quand vous exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="df631-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="df631-180">Dans le cas contraire, vous allez créer une **boucle infinie** dans laquelle votre programme ne se terminera jamais.</span><span class="sxs-lookup"><span data-stu-id="df631-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="df631-181">Ceci n’est pas démontré dans cet exemple, car vous devez forcer la fermeture de votre programme avec **CTRL-C** ou à l’aide d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="df631-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="df631-182">La boucle `while` teste la condition avant d’exécuter le code qui suit `while`.</span><span class="sxs-lookup"><span data-stu-id="df631-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="df631-183">La boucle `do` ... `while` exécute d’abord le code, puis vérifie la condition.</span><span class="sxs-lookup"><span data-stu-id="df631-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="df631-184">La boucle *do while* est illustrée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="df631-184">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="df631-185">Cette boucle `do` et la boucle antérieure `while` produisent la même sortie.</span><span class="sxs-lookup"><span data-stu-id="df631-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="df631-186">Utiliser la boucle for</span><span class="sxs-lookup"><span data-stu-id="df631-186">Work with the for loop</span></span>

<span data-ttu-id="df631-187">La boucle **for** est couramment utilisée dans C#.</span><span class="sxs-lookup"><span data-stu-id="df631-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="df631-188">Essayez ce code dans votre méthode Main() :</span><span class="sxs-lookup"><span data-stu-id="df631-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="df631-189">Le code précédent effectue le même travail que la `while` boucle et la `do` boucle que vous avez déjà utilisée.</span><span class="sxs-lookup"><span data-stu-id="df631-189">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="df631-190">L’instruction `for` comprend trois parties qui contrôlent son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="df631-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="df631-191">La première partie est l' **initialiseur**: `int index = 0;` déclare qui `index` est la variable de boucle et définit sa valeur initiale sur `0` .</span><span class="sxs-lookup"><span data-stu-id="df631-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="df631-192">La partie centrale est la **condition for**: `index < 10` déclare que cette `for` boucle continue à s’exécuter tant que la valeur du compteur est inférieure à 10.</span><span class="sxs-lookup"><span data-stu-id="df631-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="df631-193">La dernière partie est l' **itérateur for**: `index++` spécifie comment modifier la variable de boucle après l’exécution du bloc après l' `for` instruction.</span><span class="sxs-lookup"><span data-stu-id="df631-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="df631-194">Il spécifie ici que `index` doit être incrémenté de 1 chaque fois que le bloc s’exécute.</span><span class="sxs-lookup"><span data-stu-id="df631-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="df631-195">Expérimentez vous-même.</span><span class="sxs-lookup"><span data-stu-id="df631-195">Experiment yourself.</span></span> <span data-ttu-id="df631-196">Essayez chacune des variantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="df631-196">Try each of the following variations:</span></span>

- <span data-ttu-id="df631-197">Modifiez l’initialiseur pour définir le démarrage à une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="df631-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="df631-198">Modifiez la condition pour définir l’arrêt à une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="df631-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="df631-199">Une fois terminé, vous allez vous-même écrire des codes pour mettre en pratique ce que vous avez appris.</span><span class="sxs-lookup"><span data-stu-id="df631-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="df631-200">Il existe une autre instruction de boucle qui n’est pas traitée dans ce didacticiel : l' `foreach` instruction.</span><span class="sxs-lookup"><span data-stu-id="df631-200">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="df631-201">L' `foreach` instruction répète son instruction pour chaque élément d’une séquence d’éléments.</span><span class="sxs-lookup"><span data-stu-id="df631-201">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="df631-202">La plupart du temps, elle est utilisée avec les *regroupements*. elle est donc traitée dans le didacticiel suivant.</span><span class="sxs-lookup"><span data-stu-id="df631-202">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="df631-203">Boucles imbriquées créées</span><span class="sxs-lookup"><span data-stu-id="df631-203">Created nested loops</span></span>

<span data-ttu-id="df631-204">Une `while` `do` boucle, ou `for` peut être imbriquée dans une autre boucle pour créer une matrice à l’aide de la combinaison de chaque élément de la boucle externe avec chaque élément de la boucle interne.</span><span class="sxs-lookup"><span data-stu-id="df631-204">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="df631-205">Nous allons donc créer un ensemble de paires alphanumériques pour représenter les lignes et les colonnes.</span><span class="sxs-lookup"><span data-stu-id="df631-205">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="df631-206">Une seule `for` boucle peut générer les lignes :</span><span class="sxs-lookup"><span data-stu-id="df631-206">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="df631-207">Une autre boucle peut générer les colonnes :</span><span class="sxs-lookup"><span data-stu-id="df631-207">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="df631-208">Vous pouvez imbriquer une boucle à l’intérieur de l’autre pour former des paires :</span><span class="sxs-lookup"><span data-stu-id="df631-208">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="df631-209">Vous pouvez voir que la boucle externe incrémente une fois pour chaque exécution complète de la boucle interne.</span><span class="sxs-lookup"><span data-stu-id="df631-209">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="df631-210">Inversez l’imbrication de lignes et de colonnes et observez les modifications pour vous-même.</span><span class="sxs-lookup"><span data-stu-id="df631-210">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="df631-211">Combiner des branches et des boucles</span><span class="sxs-lookup"><span data-stu-id="df631-211">Combine branches and loops</span></span>

<span data-ttu-id="df631-212">Maintenant que vous avez vu l’instruction `if` et la création de boucles en langage C#, vérifiez si vous pouvez écrire un code C# pour obtenir la somme de tous les entiers de 1 à 20 divisibles par 3.</span><span class="sxs-lookup"><span data-stu-id="df631-212">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="df631-213">Voici quelques conseils :</span><span class="sxs-lookup"><span data-stu-id="df631-213">Here are a few hints:</span></span>

- <span data-ttu-id="df631-214">L’opérateur `%` vous donne le reste d’une opération de division.</span><span class="sxs-lookup"><span data-stu-id="df631-214">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="df631-215">L’instruction `if` vous donne la condition pour vérifier si un nombre doit être inclus dans la somme.</span><span class="sxs-lookup"><span data-stu-id="df631-215">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="df631-216">La boucle `for` peut vous aider à répéter une série d’étapes pour tous les nombres de 1 à 20.</span><span class="sxs-lookup"><span data-stu-id="df631-216">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="df631-217">Essayez par vous-même</span><span class="sxs-lookup"><span data-stu-id="df631-217">Try it yourself.</span></span> <span data-ttu-id="df631-218">et vérifiez le résultat.</span><span class="sxs-lookup"><span data-stu-id="df631-218">Then check how you did.</span></span> <span data-ttu-id="df631-219">Vous devriez obtenir 63 comme réponse.</span><span class="sxs-lookup"><span data-stu-id="df631-219">You should get 63 for an answer.</span></span> <span data-ttu-id="df631-220">Vous pouvez voir une réponse possible en [consultant le code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="df631-220">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="df631-221">Vous avez terminé le didacticiel « Branches et boucles ».</span><span class="sxs-lookup"><span data-stu-id="df631-221">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="df631-222">Vous pouvez passer au tutoriel [Tableaux et collections](arrays-and-collections.md) dans votre propre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="df631-222">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="df631-223">Pour plus d’informations sur ces concepts, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="df631-223">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="df631-224">Instruction if et else</span><span class="sxs-lookup"><span data-stu-id="df631-224">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="df631-225">While (instruction)</span><span class="sxs-lookup"><span data-stu-id="df631-225">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="df631-226">Instruction do</span><span class="sxs-lookup"><span data-stu-id="df631-226">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="df631-227">Instruction for</span><span class="sxs-lookup"><span data-stu-id="df631-227">For statement</span></span>](../../language-reference/keywords/for.md)
