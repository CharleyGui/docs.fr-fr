---
title: Instructions de niveau supérieur-didacticiel C#
description: Ce didacticiel montre comment vous pouvez utiliser des instructions de niveau supérieur pour expérimenter et prouver des concepts tout en explorant vos idées
ms.date: 10/28/2020
ms.openlocfilehash: 210fbd83bf4677061cab303089d0b27f1a4a7d01
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189393"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a><span data-ttu-id="d0ca4-103">Didacticiel : Explorez des idées à l’aide d’instructions de niveau supérieur pour générer du code à mesure que vous en Apprenez</span><span class="sxs-lookup"><span data-stu-id="d0ca4-103">Tutorial: Explore ideas using top-level statements to build code as you learn</span></span>

<span data-ttu-id="d0ca4-104">Ce didacticiel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-104">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d0ca4-105">Découvrez les règles qui régissent l’utilisation des instructions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-105">Learn the rules governing your use of top-level statements.</span></span>
> - <span data-ttu-id="d0ca4-106">Utilisez les instructions de niveau supérieur pour explorer les algorithmes.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-106">Use top-level statements to explore algorithms.</span></span>
> - <span data-ttu-id="d0ca4-107">Refactorisez les explorations dans des composants réutilisables.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-107">Refactor explorations into reusable components.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d0ca4-108">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="d0ca4-108">Prerequisites</span></span>

<span data-ttu-id="d0ca4-109">Vous devez configurer votre ordinateur pour exécuter .NET 5, qui comprend le compilateur C# 9.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-109">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="d0ca4-110">Le compilateur C# 9 est disponible à partir de [Visual Studio 2019 version 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) ou [.net 5,0 SDK](https://dot.net/get-dotnet5).</span><span class="sxs-lookup"><span data-stu-id="d0ca4-110">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="d0ca4-111">Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-111">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="start-exploring"></a><span data-ttu-id="d0ca4-112">Commencez à explorer</span><span class="sxs-lookup"><span data-stu-id="d0ca4-112">Start exploring</span></span>

<span data-ttu-id="d0ca4-113">Les instructions de niveau supérieur vous permettent d’éviter la cérémonie supplémentaire requise en plaçant le point d’entrée de votre programme dans une méthode statique dans une classe.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-113">Top-level statements enable you to avoid the extra ceremony required by placing your program's entry point in a static method in a class.</span></span> <span data-ttu-id="d0ca4-114">Le point de départ classique d’une nouvelle application console ressemble au code suivant :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-114">The typical starting point for a new console application looks like the following code:</span></span>

```csharp
using System;

namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="d0ca4-115">Le code précédent est le résultat de l’exécution de la `dotnet new console` commande et de la création d’une nouvelle application console.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-115">The preceding code is the result of running the `dotnet new console` command and creating a new console application.</span></span> <span data-ttu-id="d0ca4-116">Ces 11 lignes contiennent une seule ligne de code exécutable.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-116">Those 11 lines contain only one line of executable code.</span></span> <span data-ttu-id="d0ca4-117">Vous pouvez simplifier ce programme avec la nouvelle fonctionnalité d’instructions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-117">You can simplify that program with the new top-level statements feature.</span></span> <span data-ttu-id="d0ca4-118">Cela vous permet de supprimer toutes les lignes, sauf deux, dans ce programme :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-118">That enables you to remove all but two of the lines in this program:</span></span>

```csharp
using System;

Console.WriteLine("Hello World!");
```

<span data-ttu-id="d0ca4-119">Cette action simplifie ce qui est nécessaire pour commencer à explorer de nouvelles idées.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-119">This action simplifies what's needed to begin exploring new ideas.</span></span> <span data-ttu-id="d0ca4-120">Vous pouvez utiliser des instructions de niveau supérieur pour les scénarios de script ou pour explorer.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-120">You can use top-level statements for scripting scenarios, or to explore.</span></span> <span data-ttu-id="d0ca4-121">Une fois les principes de base opérationnels, vous pouvez commencer à refactoriser le code et créer des méthodes, des classes ou d’autres assemblys pour des composants réutilisables que vous avez générés.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-121">Once you've got the basics working, you can start refactoring the code and create methods, classes, or other assemblies for reusable components you've built.</span></span> <span data-ttu-id="d0ca4-122">Les instructions de niveau supérieur permettent d’effectuer des expérimentations rapides et des didacticiels débutants.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-122">Top-level statements do enable quick experimentation and beginner tutorials.</span></span> <span data-ttu-id="d0ca4-123">Ils fournissent également un chemin lisse entre l’expérimentation et les programmes complets.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-123">They also provide a smooth path from experimentation to full programs.</span></span>

<span data-ttu-id="d0ca4-124">Les instructions de niveau supérieur sont exécutées dans l’ordre dans lequel elles apparaissent dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-124">Top-level statements are executed in the order they appear in the file.</span></span> <span data-ttu-id="d0ca4-125">Les instructions de niveau supérieur ne peuvent être utilisées que dans un seul fichier source dans votre application.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-125">Top-level statements can only be used in one source file in your application.</span></span> <span data-ttu-id="d0ca4-126">Le compilateur génère une erreur si vous les utilisez dans plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-126">The compiler generates an error if you use them in more than one file.</span></span>

## <a name="build-a-magic-net-answer-machine"></a><span data-ttu-id="d0ca4-127">Créer un ordinateur de réponse Magic .NET</span><span class="sxs-lookup"><span data-stu-id="d0ca4-127">Build a magic .NET answer machine</span></span>

<span data-ttu-id="d0ca4-128">Pour ce didacticiel, nous allons créer une application console qui répond à une question « oui » ou « non » avec une réponse aléatoire.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-128">For this tutorial, let's build a console application that answers a "yes" or "no" question with a random answer.</span></span> <span data-ttu-id="d0ca4-129">Vous allez créer les fonctionnalités pas à pas.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-129">You'll build out the functionality step by step.</span></span> <span data-ttu-id="d0ca4-130">Vous pouvez vous concentrer sur votre tâche plutôt que sur la cérémonie nécessaire à la structure d’un programme standard.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-130">You can focus on your task rather than ceremony needed for the structure of a typical program.</span></span> <span data-ttu-id="d0ca4-131">Ensuite, une fois que vous êtes satisfait de la fonctionnalité, vous pouvez refactoriser l’application comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-131">Then, once you're happy with the functionality, you can refactor the application as you see fit.</span></span>

<span data-ttu-id="d0ca4-132">Un bon point de départ consiste à réécrire la question sur la console.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-132">A good starting point is to write the question back to the console.</span></span> <span data-ttu-id="d0ca4-133">Vous pouvez commencer par écrire le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-133">You can start by writing the following code:</span></span>

```csharp
using System;

Console.WriteLine(args);
```

<span data-ttu-id="d0ca4-134">Vous ne déclarez pas de `args` variable.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-134">You don't declare an `args` variable.</span></span> <span data-ttu-id="d0ca4-135">Pour le fichier source unique qui contient vos instructions de niveau supérieur, le compilateur reconnaît `args` les arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-135">For the single source file that contains your top-level statements, the compiler recognizes `args` to mean the command-line arguments.</span></span> <span data-ttu-id="d0ca4-136">Le type des arguments est un `string[]` , comme dans tous les programmes C#.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-136">The type of args is a `string[]`, as in all C# programs.</span></span>

<span data-ttu-id="d0ca4-137">Vous pouvez tester votre code en exécutant la `dotnet run` commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-137">You can test your code by running the following `dotnet run` command:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

<span data-ttu-id="d0ca4-138">Les arguments qui suivent le `--` sur la ligne de commande sont passés au programme.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-138">The arguments after the `--` on the command line are passed to the program.</span></span> <span data-ttu-id="d0ca4-139">Vous pouvez voir le type de la `args` variable, car il s’agit de l’impression sur la console :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-139">You can see the type of the `args` variable, because that's what's printed to the console:</span></span>

```console
System.String[]
```

<span data-ttu-id="d0ca4-140">Pour écrire la question dans la console, vous devez énumérer les arguments et les séparer par un espace.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-140">To write the question to the console, you'll need to enumerate the arguments and separate them with a space.</span></span> <span data-ttu-id="d0ca4-141">Remplacez l' `WriteLine` appel par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-141">Replace the `WriteLine` call with the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="EchoInput":::

<span data-ttu-id="d0ca4-142">Désormais, lorsque vous exécutez le programme, la question est correctement affichée sous la forme d’une chaîne d’arguments.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-142">Now, when you run the program, it will correctly display the question as a string of arguments.</span></span>

## <a name="respond-with-a-random-answer"></a><span data-ttu-id="d0ca4-143">Répondre avec une réponse aléatoire</span><span class="sxs-lookup"><span data-stu-id="d0ca4-143">Respond with a random answer</span></span>

<span data-ttu-id="d0ca4-144">Après avoir renvoyé la question, vous pouvez ajouter le code pour générer la réponse aléatoire.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-144">After echoing the question, you can add the code to generate the random answer.</span></span> <span data-ttu-id="d0ca4-145">Commencez par ajouter un tableau de réponses possibles :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-145">Start by adding an array of possible answers:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="Answers":::

<span data-ttu-id="d0ca4-146">Ce tableau a 12 réponses positives, six qui ne sont pas valides et six négatives.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-146">This array has 12 answers that are affirmative, six that are non-committal, and six that are negative.</span></span> <span data-ttu-id="d0ca4-147">Ensuite, ajoutez le code suivant pour générer et afficher une réponse aléatoire à partir du tableau :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-147">Next, add the following code to generate and display a random answer from the array:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="GenerateAnswer":::

<span data-ttu-id="d0ca4-148">Vous pouvez réexécuter l’application pour voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-148">You can run the application again to see the results.</span></span> <span data-ttu-id="d0ca4-149">Vous devriez voir une sortie semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-149">You should see something like the following output:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

<span data-ttu-id="d0ca4-150">Ce code répond aux questions, mais nous allons ajouter une fonctionnalité supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-150">This code answers the questions, but let's add one more feature.</span></span> <span data-ttu-id="d0ca4-151">Vous aimeriez que votre application de question simule une réflexion sur la réponse.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-151">You'd like your question app to simulate thinking about the answer.</span></span> <span data-ttu-id="d0ca4-152">Vous pouvez le faire en ajoutant un peu d’animations ASCII et en interrompant le travail.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-152">You can do that by adding a bit of ASCII animation, and pausing while working.</span></span>  <span data-ttu-id="d0ca4-153">Ajoutez le code suivant après la ligne qui renvoie la question :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-153">Add the following code after the line that echoes the question:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

<span data-ttu-id="d0ca4-154">Vous devez également ajouter une `using` instruction en haut du fichier source :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-154">You'll also need to add a `using` statement to the top of the source file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="d0ca4-155">Les `using` instructions doivent être antérieures à toute autre instruction dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-155">The `using` statements must be before any other statements in the file.</span></span> <span data-ttu-id="d0ca4-156">Dans le cas contraire, il s’agit d’une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-156">Otherwise, it's a compiler error.</span></span> <span data-ttu-id="d0ca4-157">Vous pouvez réexécuter le programme et voir l’animation.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-157">You can run the program again and see the animation.</span></span> <span data-ttu-id="d0ca4-158">Cela offre une meilleure expérience.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-158">That makes a better experience.</span></span> <span data-ttu-id="d0ca4-159">Expérimentez la longueur du délai pour vous adapter à votre goût.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-159">Experiment with the length of the delay to match your taste.</span></span>

<span data-ttu-id="d0ca4-160">Le code précédent crée un ensemble de lignes en rotation séparées par un espace.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-160">The preceding code creates a set of spinning lines separated by a space.</span></span> <span data-ttu-id="d0ca4-161">L’ajout du `await` mot clé indique au compilateur de générer le point d’entrée du programme en tant que méthode avec le `async` modificateur et retourne un <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d0ca4-161">Adding the `await` keyword instructs the compiler to generate the program entry point as a method that has the `async` modifier, and returns a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d0ca4-162">Ce programme ne retourne pas de valeur, donc le point d’entrée du programme retourne un `Task` .</span><span class="sxs-lookup"><span data-stu-id="d0ca4-162">This program does not return a value, so the program entry point returns a `Task`.</span></span> <span data-ttu-id="d0ca4-163">Si votre programme retourne une valeur entière, vous devez ajouter une instruction return à la fin de vos instructions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-163">If your program returns an integer value, you would add a return statement to the end of your top-level statements.</span></span> <span data-ttu-id="d0ca4-164">Cette instruction return spécifie la valeur entière à retourner.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-164">That return statement would specify the integer value to return.</span></span> <span data-ttu-id="d0ca4-165">Si vos instructions de niveau supérieur incluent une `await` expression, le type de retour devient <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d0ca4-165">If your top-level statements include an `await` expression, the return type becomes <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span></span>

## <a name="refactoring-for-the-future"></a><span data-ttu-id="d0ca4-166">Refactorisation à l’avenir</span><span class="sxs-lookup"><span data-stu-id="d0ca4-166">Refactoring for the future</span></span>

<span data-ttu-id="d0ca4-167">Votre programme doit ressembler au code suivant :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-167">Your program should look like the following code:</span></span>

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

<span data-ttu-id="d0ca4-168">Le code précédent est raisonnable.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-168">The preceding code is reasonable.</span></span> <span data-ttu-id="d0ca4-169">Il fonctionne.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-169">It works.</span></span> <span data-ttu-id="d0ca4-170">Mais il n’est pas réutilisable.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-170">But it isn't reusable.</span></span> <span data-ttu-id="d0ca4-171">Maintenant que l’application fonctionne, il est temps de tirer parti des parties réutilisables.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-171">Now that you have the application working, it's time to pull out reusable parts.</span></span>

<span data-ttu-id="d0ca4-172">Un candidat est le code qui affiche l’animation en attente.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-172">One candidate is the code that displays the waiting animation.</span></span> <span data-ttu-id="d0ca4-173">Cet extrait de code peut devenir une méthode :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-173">That snippet can become a method:</span></span>

<span data-ttu-id="d0ca4-174">Vous pouvez commencer par créer une fonction locale dans votre fichier.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-174">You can start by creating a local function in your file.</span></span> <span data-ttu-id="d0ca4-175">Remplacez l’animation actuelle par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-175">Replace the current animation with the following code:</span></span>

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

<span data-ttu-id="d0ca4-176">Le code précédent crée une fonction locale à l’intérieur de votre méthode main.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-176">The preceding code creates a local function inside your main method.</span></span> <span data-ttu-id="d0ca4-177">Cela n’est toujours pas réutilisable.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-177">That's still not reusable.</span></span> <span data-ttu-id="d0ca4-178">Ainsi, extrayez ce code dans une classe.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-178">So, extract that code into a class.</span></span> <span data-ttu-id="d0ca4-179">Créez un nouveau fichier nommé *Utilities.cs* et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-179">Create a new file named *utilities.cs* and add the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

<span data-ttu-id="d0ca4-180">Les instructions de niveau supérieur ne peuvent figurer que dans un seul fichier, et ce fichier ne peut pas contenir d’espaces de noms ou de types.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-180">Top-level statements can only be in one file, and that file cannot contain namespaces or types.</span></span>

<span data-ttu-id="d0ca4-181">Enfin, vous pouvez nettoyer le code de l’animation pour supprimer des doublons :</span><span class="sxs-lookup"><span data-stu-id="d0ca4-181">Finally, you can clean the animation code to remove some duplication:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Utiliities.cs" ID="Animation":::

<span data-ttu-id="d0ca4-182">Vous disposez maintenant d’une application complète et vous avez refactorisé les parties réutilisables pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-182">Now you have a complete application, and you've refactored the reusable parts for later use.</span></span>

## <a name="summary"></a><span data-ttu-id="d0ca4-183">Résumé</span><span class="sxs-lookup"><span data-stu-id="d0ca4-183">Summary</span></span>

<span data-ttu-id="d0ca4-184">Les instructions de niveau supérieur facilitent la création de programmes simples à utiliser pour explorer les nouveaux algorithmes.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-184">Top-level statements make it easier to create simple programs for use to explore new algorithms.</span></span> <span data-ttu-id="d0ca4-185">Vous pouvez expérimenter des algorithmes en essayant différents extraits de code.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-185">You can experiment with algorithms by trying different snippets of code.</span></span> <span data-ttu-id="d0ca4-186">Une fois que vous avez appris ce qui fonctionne, vous pouvez Refactoriser le code pour qu’il soit plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-186">Once you've learned what works, you can refactor the code to be more maintainable.</span></span>

<span data-ttu-id="d0ca4-187">Les instructions de niveau supérieur simplifient les programmes basés sur les applications console.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-187">Top-level statements simplify programs that are based on console applications.</span></span> <span data-ttu-id="d0ca4-188">Il s’agit notamment des fonctions Azure, des actions GitHub et d’autres petits utilitaires.</span><span class="sxs-lookup"><span data-stu-id="d0ca4-188">These include Azure functions, GitHub actions, and other small utilities.</span></span>
