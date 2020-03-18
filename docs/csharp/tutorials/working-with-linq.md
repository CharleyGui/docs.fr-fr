---
title: Utilisation de LINQ
description: Ce didacticiel vous apprend à générer des séquences avec LINQ, à écrire des méthodes pour les requêtes LINQ et à faire la distinction entre l’évaluation stricte et l’évaluation paresseuse.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240013"
---
# <a name="work-with-language-integrated-query-linq"></a><span data-ttu-id="d9e17-103">Travailler avec la requête intégrée en langue (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d9e17-103">Work with Language-Integrated Query (LINQ)</span></span>

## <a name="introduction"></a><span data-ttu-id="d9e17-104">Introduction</span><span class="sxs-lookup"><span data-stu-id="d9e17-104">Introduction</span></span>

<span data-ttu-id="d9e17-105">Ce tutoriel vous présente les fonctionnalités de .NET Core et du langage C#.</span><span class="sxs-lookup"><span data-stu-id="d9e17-105">This tutorial teaches you features in .NET Core and the C# language.</span></span> <span data-ttu-id="d9e17-106">Vous découvrirez comment effectuer les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d9e17-106">You’ll learn how to:</span></span>

- <span data-ttu-id="d9e17-107">Générer des séquences avec LINQ.</span><span class="sxs-lookup"><span data-stu-id="d9e17-107">Generate sequences with LINQ.</span></span>
- <span data-ttu-id="d9e17-108">Écrivez des méthodes qui peuvent être facilement utilisées dans les requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="d9e17-108">Write methods that can be easily used in LINQ queries.</span></span>
- <span data-ttu-id="d9e17-109">Distinguer entre l’évaluation avide et paresseuse.</span><span class="sxs-lookup"><span data-stu-id="d9e17-109">Distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="d9e17-110">Vous apprendrez ces techniques en créant une application qui illustre l’une des compétences de base de tout magicien : le [mélange faro](https://en.wikipedia.org/wiki/Faro_shuffle).</span><span class="sxs-lookup"><span data-stu-id="d9e17-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="d9e17-111">En quelques mots, le mélange faro est une technique qui consiste à diviser un paquet de cartes en deux moitiés exactes, puis à intercaler une carte sur deux de chacune des deux moitiés de façon à reconstruire le jeu d’origine.</span><span class="sxs-lookup"><span data-stu-id="d9e17-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="d9e17-112">Les magiciens utilisent cette technique parce que chaque carte se trouve à un emplacement connu après chaque mélange, suivant un motif répétitif.</span><span class="sxs-lookup"><span data-stu-id="d9e17-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span>

<span data-ttu-id="d9e17-113">Dans notre cas, c’est une façon plaisante d’envisager la manipulation de séquences de données.</span><span class="sxs-lookup"><span data-stu-id="d9e17-113">For your purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="d9e17-114">L’application que vous construirez construit un jeu de cartes, puis effectue une séquence de mélanges, en écrivant la séquence à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="d9e17-114">The application you'll build constructs a card deck and then performs a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="d9e17-115">Vous comparerez également le nouvel ordre à l’ordre d’origine.</span><span class="sxs-lookup"><span data-stu-id="d9e17-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="d9e17-116">Ce didacticiel comporte plusieurs étapes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="d9e17-117">Après chaque étape, vous pourrez exécuter l’application et voir la progression.</span><span class="sxs-lookup"><span data-stu-id="d9e17-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="d9e17-118">Vous pouvez également voir l’[exemple terminé](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dans le dépôt GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="d9e17-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="d9e17-119">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d9e17-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9e17-120">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="d9e17-120">Prerequisites</span></span>

<span data-ttu-id="d9e17-121">Vous devez configurer votre ordinateur pour exécuter .NET core.</span><span class="sxs-lookup"><span data-stu-id="d9e17-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="d9e17-122">Vous pouvez trouver les instructions d’installation sur la page [.NET Core Download.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="d9e17-122">You can find the installation instructions on the [.NET Core Download](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="d9e17-123">Vous pouvez exécuter cette application sur Windows, Ubuntu Linux, ou OS X, ou dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="d9e17-123">You can run this application on Windows, Ubuntu Linux, or OS X, or in a Docker container.</span></span> <span data-ttu-id="d9e17-124">Vous devez installer l’éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="d9e17-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="d9e17-125">Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/) qui est un éditeur open source, multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="d9e17-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross-platform editor.</span></span> <span data-ttu-id="d9e17-126">Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.</span><span class="sxs-lookup"><span data-stu-id="d9e17-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="d9e17-127">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="d9e17-127">Create the Application</span></span>

<span data-ttu-id="d9e17-128">La première étape consiste à créer une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="d9e17-128">The first step is to create a new application.</span></span> <span data-ttu-id="d9e17-129">Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="d9e17-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="d9e17-130">Réglez-le comme répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="d9e17-130">Make that the current directory.</span></span> <span data-ttu-id="d9e17-131">Saisissez la commande `dotnet new console` à l’invite.</span><span class="sxs-lookup"><span data-stu-id="d9e17-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="d9e17-132">Elle crée les fichiers de démarrage d’une application « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="d9e17-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="d9e17-133">Si vous n’avez jamais utilisé C#, [ce didacticiel](console-teleprompter.md) explique la structure d’un programme C#.</span><span class="sxs-lookup"><span data-stu-id="d9e17-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="d9e17-134">Vous pouvez le lire, puis revenir ici pour en savoir plus sur LINQ.</span><span class="sxs-lookup"><span data-stu-id="d9e17-134">You can read that and then return here to learn more about LINQ.</span></span>

## <a name="create-the-data-set"></a><span data-ttu-id="d9e17-135">Créer l’ensemble de données</span><span class="sxs-lookup"><span data-stu-id="d9e17-135">Create the Data Set</span></span>

<span data-ttu-id="d9e17-136">Avant de commencer, vérifiez que les lignes suivantes figurent en haut du fichier `Program.cs` généré par `dotnet new console` :</span><span class="sxs-lookup"><span data-stu-id="d9e17-136">Before you begin, make sure that the following lines are at the top of the `Program.cs` file generated by `dotnet new console`:</span></span>

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="d9e17-137">Si ces trois lignes (instructions `using`) ne figurent pas en haut du fichier, le programme ne se compilera pas.</span><span class="sxs-lookup"><span data-stu-id="d9e17-137">If these three lines (`using` statements) aren't at the top of the file, our program will not compile.</span></span>

<span data-ttu-id="d9e17-138">Maintenant que vous avez toutes les références dont vous avez besoin, réfléchissons à ce qui compose un jeu de cartes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-138">Now that you have all of the references that you'll need, consider what constitutes a deck of cards.</span></span> <span data-ttu-id="d9e17-139">En général, un jeu de cartes à jouer comporte quatre couleurs, et chaque couleur a treize valeurs.</span><span class="sxs-lookup"><span data-stu-id="d9e17-139">Commonly, a deck of playing cards has four suits, and each suit has thirteen values.</span></span> <span data-ttu-id="d9e17-140">On pourrait envisager de créer directement une classe `Card` et de remplir manuellement une collection d’objets `Card`.</span><span class="sxs-lookup"><span data-stu-id="d9e17-140">Normally, you might consider creating a `Card` class right off the bat and populating a collection of `Card` objects by hand.</span></span> <span data-ttu-id="d9e17-141">Avec LINQ, il est possible d’être plus concis que cela.</span><span class="sxs-lookup"><span data-stu-id="d9e17-141">With LINQ, you can be more concise than the usual way of dealing with creating a deck of cards.</span></span> <span data-ttu-id="d9e17-142">Au lieu de créer une classe `Card`, vous pouvez créer deux séquences pour représenter respectivement les couleurs et les rangs.</span><span class="sxs-lookup"><span data-stu-id="d9e17-142">Instead of creating a `Card` class, you can create two sequences to represent suits and ranks, respectively.</span></span> <span data-ttu-id="d9e17-143">Créez deux [*méthodes d’itération*](../iterators.md#enumeration-sources-with-iterator-methods) simples qui génèreront les rangs et les couleurs sous forme de <xref:System.Collections.Generic.IEnumerable%601> de chaînes :</span><span class="sxs-lookup"><span data-stu-id="d9e17-143">You'll create a really simple pair of [*iterator methods*](../iterators.md#enumeration-sources-with-iterator-methods) that will generate the ranks and suits as <xref:System.Collections.Generic.IEnumerable%601>s of strings:</span></span>

```csharp
// Program.cs
// The Main() method

static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="d9e17-144">Placez-les sous la méthode `Main` dans votre fichier `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="d9e17-144">Place these underneath the `Main` method in your `Program.cs` file.</span></span> <span data-ttu-id="d9e17-145">Les deux méthodes utilisent la syntaxe `yield return` pour produire une séquence lors de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="d9e17-145">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="d9e17-146">Le compilateur génère un objet qui implémente <xref:System.Collections.Generic.IEnumerable%601> et génère la séquence de chaînes au fur et à mesure.</span><span class="sxs-lookup"><span data-stu-id="d9e17-146">The compiler builds an object that implements <xref:System.Collections.Generic.IEnumerable%601> and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="d9e17-147">Maintenant, utilisez ces méthodes d’itération pour créer le jeu de cartes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-147">Now, use these iterator methods to create the deck of cards.</span></span> <span data-ttu-id="d9e17-148">Placez la requête LINQ dans la méthode `Main`</span><span class="sxs-lookup"><span data-stu-id="d9e17-148">You'll place the LINQ query in our `Main` method.</span></span> <span data-ttu-id="d9e17-149">:</span><span class="sxs-lookup"><span data-stu-id="d9e17-149">Here's a look at it:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    // Display each card that we've generated and placed in startingDeck in the console
    foreach (var card in startingDeck)
    {
        Console.WriteLine(card);
    }
}
```

<span data-ttu-id="d9e17-150">Les clauses `from` multiples produisent un <xref:System.Linq.Enumerable.SelectMany%2A>, qui crée une séquence unique en combinant chaque élément de la première séquence avec chaque élément de la deuxième séquence.</span><span class="sxs-lookup"><span data-stu-id="d9e17-150">The multiple `from` clauses produce a <xref:System.Linq.Enumerable.SelectMany%2A>, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="d9e17-151">L’ordre est important ici.</span><span class="sxs-lookup"><span data-stu-id="d9e17-151">The order is important for our purposes.</span></span> <span data-ttu-id="d9e17-152">Le premier élément de la première séquence source (couleurs) est associé à chacun des éléments de la deuxième séquence (rangs).</span><span class="sxs-lookup"><span data-stu-id="d9e17-152">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Ranks).</span></span> <span data-ttu-id="d9e17-153">Cette opération génère les treize cartes de la première couleur.</span><span class="sxs-lookup"><span data-stu-id="d9e17-153">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="d9e17-154">Ce processus est reproduit pour chaque élément de la première séquence (couleurs).</span><span class="sxs-lookup"><span data-stu-id="d9e17-154">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="d9e17-155">Le résultat final est un jeu de cartes classé par couleurs, puis par valeurs.</span><span class="sxs-lookup"><span data-stu-id="d9e17-155">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="d9e17-156">Il est important de garder à l’esprit la chose suivante : que vous choisissiez d’écrire votre code LINQ dans la syntaxe de requête utilisée plus haut ou d’utiliser plutôt la syntaxe de méthode, vous pourrez toujours passer d’une forme syntaxique à l’autre.</span><span class="sxs-lookup"><span data-stu-id="d9e17-156">It's important to keep in mind that whether you choose to write your LINQ in the query syntax used above or use method syntax instead, it's always possible to go from one form of syntax to the other.</span></span> <span data-ttu-id="d9e17-157">La requête ci-dessus, écrite dans la syntaxe de requête, s’écrit ainsi dans la syntaxe de méthode :</span><span class="sxs-lookup"><span data-stu-id="d9e17-157">The above query written in query syntax can be written in method syntax as:</span></span>

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

<span data-ttu-id="d9e17-158">Le compilateur traduit les instructions LINQ écrites avec la syntaxe de requête dans la syntaxe d’appel de méthode équivalente.</span><span class="sxs-lookup"><span data-stu-id="d9e17-158">The compiler translates LINQ statements written with query syntax into the equivalent method call syntax.</span></span> <span data-ttu-id="d9e17-159">Par conséquent, les deux versions de la requête produisent le même résultat quel que soit le choix de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="d9e17-159">Therefore, regardless of your syntax choice, the two versions of the query produce the same result.</span></span> <span data-ttu-id="d9e17-160">Choisissez la plus adaptée à votre situation : par exemple, si certains membres de votre équipe ont des difficultés à utiliser la syntaxe de méthode, privilégiez dans la mesure du possible la syntaxe de requête.</span><span class="sxs-lookup"><span data-stu-id="d9e17-160">Choose which syntax works best for your situation: for instance, if you're working in a team where some of the members have difficulty with method syntax, try to prefer using query syntax.</span></span>

<span data-ttu-id="d9e17-161">Ensuite, exécutez l’exemple que vous avez commencé à élaborer.</span><span class="sxs-lookup"><span data-stu-id="d9e17-161">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="d9e17-162">Il affiche les 52 cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="d9e17-162">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="d9e17-163">Il peut être très utile d’exécuter cet exemple avec un débogueur pour observer la façon dont les méthodes `Suits()` et `Ranks()` s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="d9e17-163">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Ranks()` methods execute.</span></span> <span data-ttu-id="d9e17-164">Vous pouvez clairement voir que chaque chaîne de chaque séquence est générée uniquement au moment requis.</span><span class="sxs-lookup"><span data-stu-id="d9e17-164">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![Fenêtre console montrant l’application produisant 52 cartes.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a><span data-ttu-id="d9e17-166">Manipuler l’ordre</span><span class="sxs-lookup"><span data-stu-id="d9e17-166">Manipulate the Order</span></span>

<span data-ttu-id="d9e17-167">Maintenant, réfléchissons à la façon dont nous allons battre les cartes du jeu.</span><span class="sxs-lookup"><span data-stu-id="d9e17-167">Next, focus on how you're going to shuffle the cards in the deck.</span></span> <span data-ttu-id="d9e17-168">Pour bien faire, la première étape consiste à couper le jeu en deux.</span><span class="sxs-lookup"><span data-stu-id="d9e17-168">The first step in any good shuffle is to split the deck in two.</span></span> <span data-ttu-id="d9e17-169">Les méthodes <xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A>, qui font partie des API LINQ, offrent cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d9e17-169">The <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods that are part of the LINQ APIs provide that feature for you.</span></span> <span data-ttu-id="d9e17-170">Placez-les sous la boucle `foreach` :</span><span class="sxs-lookup"><span data-stu-id="d9e17-170">Place them underneath the `foreach` loop:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    // 52 cards in a deck, so 52 / 2 = 26
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
}
```

<span data-ttu-id="d9e17-171">Cependant, il n’y a pas de méthode de battage dans la bibliothèque standard ; vous devez donc écrire la vôtre.</span><span class="sxs-lookup"><span data-stu-id="d9e17-171">However, there's no shuffle method to take advantage of in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="d9e17-172">Comme elle illustrera plusieurs techniques des programmes LINQ, nous allons expliquer les différentes parties du processus étape par étape.</span><span class="sxs-lookup"><span data-stu-id="d9e17-172">The shuffle method you'll be creating illustrates several techniques that you'll use with LINQ-based programs, so each part of this process will be explained in steps.</span></span>

<span data-ttu-id="d9e17-173">Pour ajouter des fonctionnalités aux interactions possibles avec les <xref:System.Collections.Generic.IEnumerable%601> obtenus à partir des requêtes LINQ, vous allez écrire des méthodes d’un genre particulier, nommées [méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d9e17-173">In order to add some functionality to how you interact with the <xref:System.Collections.Generic.IEnumerable%601> you'll get back from LINQ queries, you'll need to write some special kinds of methods called [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d9e17-174">En bref, une méthode d’extension est une *méthode statique* spéciale qui ajoute de nouvelles fonctionnalités à un type existant sans qu’il soit nécessaire de modifier le type d’origine.</span><span class="sxs-lookup"><span data-stu-id="d9e17-174">Briefly, an extension method is a special purpose *static method* that adds new functionality to an already-existing type without having to modify the original type you want to add functionality to.</span></span>

<span data-ttu-id="d9e17-175">Pour accueillir vos méthodes d’extension, ajoutez à votre programme un nouveau fichier de classe *statique*, nommé `Extensions.cs`, puis créez la première méthode d’extension :</span><span class="sxs-lookup"><span data-stu-id="d9e17-175">Give your extension methods a new home by adding a new *static* class file to your program called `Extensions.cs`, and then start building out the first extension method:</span></span>

```csharp
// Extensions.cs
using System;
using System.Collections.Generic;
using System.Linq;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>(this IEnumerable<T> first, IEnumerable<T> second)
        {
            // Your implementation will go here soon enough
        }
    }
}
```

<span data-ttu-id="d9e17-176">Examinez attentivement la signature de méthode, et en particulier les paramètres :</span><span class="sxs-lookup"><span data-stu-id="d9e17-176">Look at the method signature for a moment, specifically the parameters:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="d9e17-177">On peut voir l’ajout du modificateur `this` au premier argument de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d9e17-177">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="d9e17-178">Cela signifie que vous appelez la méthode comme s’il s’agissait d’une méthode membre du type du premier argument.</span><span class="sxs-lookup"><span data-stu-id="d9e17-178">That means you call the method as though it were a member method of the type of the first argument.</span></span> <span data-ttu-id="d9e17-179">Cette déclaration de méthode suit également un idiome standard selon lequel les types d’entrée et de sortie sont `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="d9e17-179">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="d9e17-180">Cette pratique permet d’enchaîner les méthodes LINQ afin d’exécuter des requêtes plus complexes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-180">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

<span data-ttu-id="d9e17-181">Bien entendu, le jeu ayant été coupé en deux, il faut réunir les deux moitiés.</span><span class="sxs-lookup"><span data-stu-id="d9e17-181">Naturally, since you split the deck into halves, you'll need to join those halves together.</span></span> <span data-ttu-id="d9e17-182">En code, cela signifie que vous énumérerez les deux <xref:System.Linq.Enumerable.Take%2A> séquences que vous avez acquises à travers et <xref:System.Linq.Enumerable.Skip%2A> à la fois, *`interleaving`* les éléments, et la création d’une séquence: votre jeu de cartes maintenant mélangé.</span><span class="sxs-lookup"><span data-stu-id="d9e17-182">In code, this means you'll be enumerating both of the sequences you acquired through <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> at once, *`interleaving`* the elements, and creating one sequence: your now-shuffled deck of cards.</span></span> <span data-ttu-id="d9e17-183">Pour écrire une méthode LINQ qui fonctionne avec deux séquences, vous devez comprendre comment <xref:System.Collections.Generic.IEnumerable%601> fonctionne.</span><span class="sxs-lookup"><span data-stu-id="d9e17-183">Writing a LINQ method that works with two sequences requires that you understand how <xref:System.Collections.Generic.IEnumerable%601> works.</span></span>

<span data-ttu-id="d9e17-184">L’interface <xref:System.Collections.Generic.IEnumerable%601> possède une seule méthode : <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9e17-184">The <xref:System.Collections.Generic.IEnumerable%601> interface has one method: <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>.</span></span> <span data-ttu-id="d9e17-185">L’objet retourné par <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a une méthode permettant d’atteindre l’élément suivant et une propriété qui récupère l’élément actif dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="d9e17-185">The object returned by <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="d9e17-186">Vous allez utiliser ces deux membres pour énumérer la collection et retourner les éléments.</span><span class="sxs-lookup"><span data-stu-id="d9e17-186">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="d9e17-187">Cette méthode Interleave sera une méthode d’itération ; par conséquent, au lieu de créer une collection et de la retourner, vous allez utiliser la syntaxe `yield return` présentée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d9e17-187">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span>

<span data-ttu-id="d9e17-188">Voici l’implémentation de cette méthode :</span><span class="sxs-lookup"><span data-stu-id="d9e17-188">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="d9e17-189">Maintenant que vous avez écrit cette méthode, revenez à la méthode `Main` et mélangez le jeu une fois :</span><span class="sxs-lookup"><span data-stu-id="d9e17-189">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="d9e17-190">Comparaisons</span><span class="sxs-lookup"><span data-stu-id="d9e17-190">Comparisons</span></span>

<span data-ttu-id="d9e17-191">Combien de battages faut-il compter pour remettre le jeu dans l’ordre d’origine ?</span><span class="sxs-lookup"><span data-stu-id="d9e17-191">How many shuffles it takes to set the deck back to its original order?</span></span> <span data-ttu-id="d9e17-192">Pour le savoir, il faut écrire une méthode qui détermine si deux séquences sont égales.</span><span class="sxs-lookup"><span data-stu-id="d9e17-192">To find out, you'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="d9e17-193">Ensuite, il vous faudra placer le code qui mélange le jeu dans une boucle et vérifier si le jeu est de nouveau dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="d9e17-193">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="d9e17-194">Vous ne devriez pas avoir de problèmes à écrire une méthode qui détermine si deux séquences sont égales.</span><span class="sxs-lookup"><span data-stu-id="d9e17-194">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="d9e17-195">La structure est similaire à celle de la méthode que vous avez écrite pour mélanger le jeu.</span><span class="sxs-lookup"><span data-stu-id="d9e17-195">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="d9e17-196">Seulement, cette fois, au lieu d’utiliser l’instruction `yield return` sur chaque élément, vous allez comparer les éléments correspondants de chaque séquence.</span><span class="sxs-lookup"><span data-stu-id="d9e17-196">Only this time, instead of `yield return`ing each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="d9e17-197">Une fois que la séquence aura été énumérée en entier, si tous les éléments correspondent, les séquences sont les mêmes :</span><span class="sxs-lookup"><span data-stu-id="d9e17-197">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="d9e17-198">Cet exemple montre un autre terme LINQ : les méthodes terminales.</span><span class="sxs-lookup"><span data-stu-id="d9e17-198">This shows a second LINQ idiom: terminal methods.</span></span> <span data-ttu-id="d9e17-199">Elles prennent une séquence en entrée (ou, dans ce cas, deux séquences) et retournent une valeur scalaire unique.</span><span class="sxs-lookup"><span data-stu-id="d9e17-199">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="d9e17-200">Les méthodes terminales sont toujours la dernière méthode de la chaîne de méthodes d’une requête LINQ ; d’où le nom « terminal ».</span><span class="sxs-lookup"><span data-stu-id="d9e17-200">When using terminal methods, they are always the final method in a chain of methods for a LINQ query, hence the name "terminal".</span></span>

<span data-ttu-id="d9e17-201">Vous pourrez les voir en action lorsque vous les utiliserez pour déterminer si le jeu est dans l’ordre d’origine.</span><span class="sxs-lookup"><span data-stu-id="d9e17-201">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="d9e17-202">Placez le code de mélange à l’intérieur d’une boucle, et arrêtez-la lorsque la séquence est à nouveau dans l’ordre d’origine en appliquant la méthode `SequenceEquals()`.</span><span class="sxs-lookup"><span data-stu-id="d9e17-202">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="d9e17-203">Vous pouvez voir qu’il s’agit toujours de la dernière méthode d’une requête, parce qu’elle retourne une valeur unique plutôt qu’une séquence :</span><span class="sxs-lookup"><span data-stu-id="d9e17-203">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
// Program.cs
static void Main(string[] args)
{
    // Query for building the deck

    // Shuffling using InterleaveSequenceWith<T>();

    var times = 0;
    // We can re-use the shuffle variable from earlier, or you can make a new one
    shuffle = startingDeck;
    do
    {
        shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

        foreach (var card in shuffle)
        {
            Console.WriteLine(card);
        }
        Console.WriteLine();
        times++;

    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="d9e17-204">Exécutez le code ainsi obtenu et étudiez la façon dont le jeu se réorganise à chaque battage.</span><span class="sxs-lookup"><span data-stu-id="d9e17-204">Run the code you've got so far and take note of how the deck rearranges on each shuffle.</span></span> <span data-ttu-id="d9e17-205">Après huit battages (itérations de la boucle do-while), le jeu revient à la configuration qu’il avait à sa création avec la requête LINQ initiale.</span><span class="sxs-lookup"><span data-stu-id="d9e17-205">After 8 shuffles (iterations of the do-while loop), the deck returns to the original configuration it was in when you first created it from the starting LINQ query.</span></span>

## <a name="optimizations"></a><span data-ttu-id="d9e17-206">Optimisations</span><span class="sxs-lookup"><span data-stu-id="d9e17-206">Optimizations</span></span>

<span data-ttu-id="d9e17-207">L’exemple que vous avez produit jusque-là exécute un *mélange extérieur*, où les cartes du haut et du bas restent les mêmes à chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="d9e17-207">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="d9e17-208">Faisons une modification en effectuant plutôt un *mélange intérieur*, où les 52 cartes changent toutes de position.</span><span class="sxs-lookup"><span data-stu-id="d9e17-208">Let's make one change: we'll use an *in shuffle* instead, where all 52 cards change position.</span></span> <span data-ttu-id="d9e17-209">Dans le cas d’un mélange intérieur, on intercale les deux moitiés du jeu de sorte que la première carte de la moitié du dessous devienne la première carte du jeu.</span><span class="sxs-lookup"><span data-stu-id="d9e17-209">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="d9e17-210">Cela signifie que la dernière carte de la moitié du dessus devient la carte du bas.</span><span class="sxs-lookup"><span data-stu-id="d9e17-210">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="d9e17-211">Cette modification simple ne concerne qu’une ligne de code.</span><span class="sxs-lookup"><span data-stu-id="d9e17-211">This is a simple change to a singular line of code.</span></span> <span data-ttu-id="d9e17-212">Mettez à jour la requête de battage actuelle en inversant les positions de <xref:System.Linq.Enumerable.Take%2A> et de <xref:System.Linq.Enumerable.Skip%2A>,</span><span class="sxs-lookup"><span data-stu-id="d9e17-212">Update the current shuffle query by switching the positions of <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span> <span data-ttu-id="d9e17-213">de façon à modifier l’ordre des moitiés du dessus et du dessous du jeu :</span><span class="sxs-lookup"><span data-stu-id="d9e17-213">This will change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="d9e17-214">Réexécutez le programme : vous verrez qu’il faut 52 itérations pour que le jeu se réorganise.</span><span class="sxs-lookup"><span data-stu-id="d9e17-214">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="d9e17-215">Vous commencerez également à remarquer de sérieuses dégradations des performances lors de l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="d9e17-215">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="d9e17-216">Il y a plusieurs raisons à cela.</span><span class="sxs-lookup"><span data-stu-id="d9e17-216">There are a number of reasons for this.</span></span> <span data-ttu-id="d9e17-217">L’une des causes principales de cette baisse de performances est une utilisation inefficace de [*l’évaluation paresseuse*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d9e17-217">You can tackle one of the major causes of this performance drop: inefficient use of [*lazy evaluation*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="d9e17-218">En bref, l’évaluation d’une instruction n’est effectuée que lorsque sa valeur devient nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d9e17-218">Briefly, lazy evaluation states that the evaluation of a statement is not performed until its value is needed.</span></span> <span data-ttu-id="d9e17-219">Les requêtes LINQ sont évaluées de cette manière.</span><span class="sxs-lookup"><span data-stu-id="d9e17-219">LINQ queries are statements that are evaluated lazily.</span></span> <span data-ttu-id="d9e17-220">Les séquences sont générées uniquement au moment où les éléments sont demandés.</span><span class="sxs-lookup"><span data-stu-id="d9e17-220">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="d9e17-221">En règle générale, c’est un avantage majeur de LINQ.</span><span class="sxs-lookup"><span data-stu-id="d9e17-221">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="d9e17-222">Toutefois, dans une utilisation du type de ce programme, cela entraîne une croissance exponentielle de la durée d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d9e17-222">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="d9e17-223">N’oubliez pas que nous avons généré le jeu d’origine à l’aide d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="d9e17-223">Remember that we generated the original deck using a LINQ query.</span></span> <span data-ttu-id="d9e17-224">Chaque mélange est généré en effectuant trois requêtes LINQ sur le jeu précédent.</span><span class="sxs-lookup"><span data-stu-id="d9e17-224">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="d9e17-225">Toutes ces opérations sont effectuées de façon retardée.</span><span class="sxs-lookup"><span data-stu-id="d9e17-225">All these are performed lazily.</span></span> <span data-ttu-id="d9e17-226">Cela signifie également qu’elles sont effectuées à chaque fois que la séquence est demandée.</span><span class="sxs-lookup"><span data-stu-id="d9e17-226">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="d9e17-227">À la 52e itération, vous aurez régénéré le jeu d’origine de nombreuses fois.</span><span class="sxs-lookup"><span data-stu-id="d9e17-227">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="d9e17-228">Nous allons écrire dans un journal pour illustrer ce comportement.</span><span class="sxs-lookup"><span data-stu-id="d9e17-228">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="d9e17-229">Ensuite, vous résoudrez le problème.</span><span class="sxs-lookup"><span data-stu-id="d9e17-229">Then, you'll fix it.</span></span>

<span data-ttu-id="d9e17-230">Dans votre fichier `Extensions.cs`, tapez ou copiez la méthode d’extension ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d9e17-230">In your `Extensions.cs` file, type in or copy the method below.</span></span> <span data-ttu-id="d9e17-231">Elle crée un fichier nommé `debug.log` au sein de votre répertoire de projet et enregistre la requête en cours d’exécution dans le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="d9e17-231">This extension method creates a new file called `debug.log` within your project directory and records what query is currently being executed to the log file.</span></span> <span data-ttu-id="d9e17-232">Elle peut être ajoutée à une requête pour marquer le fait qu’elle s’est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d9e17-232">This extension method can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="d9e17-233">Vous verrez une ligne ondulée rouge sous `File`, ce qui signifie qu’elle n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d9e17-233">You will see a red squiggle under `File`, meaning it doesn't exist.</span></span> <span data-ttu-id="d9e17-234">Elle ne sera pas compilée, puisque le compilateur ne sait pas ce qu’est `File`.</span><span class="sxs-lookup"><span data-stu-id="d9e17-234">It won't compile, since the compiler doesn't know what `File` is.</span></span> <span data-ttu-id="d9e17-235">Pour résoudre ce problème, veillez à ajouter la ligne de code suivante sous la première ligne dans `Extensions.cs` :</span><span class="sxs-lookup"><span data-stu-id="d9e17-235">To solve this problem, make sure to add the following line of code under the very first line in `Extensions.cs`:</span></span>

```csharp
using System.IO;
```

<span data-ttu-id="d9e17-236">Cela devrait résoudre le problème et faire disparaître l’erreur rouge.</span><span class="sxs-lookup"><span data-stu-id="d9e17-236">This should solve the issue and the red error disappears.</span></span>

<span data-ttu-id="d9e17-237">Instrumentez ensuite la définition de chaque requête avec un message de journalisation :</span><span class="sxs-lookup"><span data-stu-id="d9e17-237">Next, instrument the definition of each query with a log message:</span></span>

```csharp
// Program.cs
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        // Out shuffle
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        // In shuffle
        shuffle = shuffle.Skip(26).LogQuery("Bottom Half")
                .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
                .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="d9e17-238">Remarquez que vous n’écrivez pas dans le journal à chaque fois que vous accédez à une requête,</span><span class="sxs-lookup"><span data-stu-id="d9e17-238">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="d9e17-239">mais seulement lors de la création de la requête d’origine.</span><span class="sxs-lookup"><span data-stu-id="d9e17-239">You log only when you create the original query.</span></span> <span data-ttu-id="d9e17-240">Le programme met toujours longtemps à s’exécuter, mais vous pouvez maintenant voir pourquoi.</span><span class="sxs-lookup"><span data-stu-id="d9e17-240">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="d9e17-241">Si vous perdez patience au cours de l’exécution du mélange intérieur avec journalisation, revenez au mélange extérieur.</span><span class="sxs-lookup"><span data-stu-id="d9e17-241">If you run out of patience running the in shuffle with logging turned on, switch back to the out shuffle.</span></span> <span data-ttu-id="d9e17-242">Vous verrez quand même les effets de l’évaluation paresseuse.</span><span class="sxs-lookup"><span data-stu-id="d9e17-242">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="d9e17-243">Sur une itération, elle exécute 2 592 requêtes, génération de toutes les valeurs et couleurs comprise.</span><span class="sxs-lookup"><span data-stu-id="d9e17-243">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="d9e17-244">Vous pouvez améliorer les performances du code en réduisant le nombre d’exécutions effectuées.</span><span class="sxs-lookup"><span data-stu-id="d9e17-244">You can improve the performance of the code here to reduce the number of executions you make.</span></span> <span data-ttu-id="d9e17-245">L’un des correctifs les plus simples consiste à mettre en *cache* les résultats de la requête LINQ d’origine qui construit le jeu de cartes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-245">A simple fix you can make is to *cache* the results of the original LINQ query that constructs the deck of cards.</span></span> <span data-ttu-id="d9e17-246">Actuellement, les requêtes sont réexécutées chaque fois que la boucle do-while effectue une itération, construisant et battant de nouveau le jeu de cartes à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="d9e17-246">Currently, you're executing the queries again and again every time the do-while loop goes through an iteration, re-constructing the deck of cards and reshuffling it every time.</span></span> <span data-ttu-id="d9e17-247">Pour mettre en cache le jeu de cartes, vous pouvez utiliser les méthodes LINQ <xref:System.Linq.Enumerable.ToArray%2A> et <xref:System.Linq.Enumerable.ToList%2A> ; ajoutées aux requêtes, elles effectuent les actions voulues, mais en stockant respectivement les résultats dans un tableau ou dans une liste.</span><span class="sxs-lookup"><span data-stu-id="d9e17-247">To cache the deck of cards, you can leverage the LINQ methods <xref:System.Linq.Enumerable.ToArray%2A> and <xref:System.Linq.Enumerable.ToList%2A>; when you append them to the queries, they'll perform the same actions you've told them to, but now they'll store the results in an array or a list, depending on which method you choose to call.</span></span> <span data-ttu-id="d9e17-248">Ajoutez la méthode LINQ <xref:System.Linq.Enumerable.ToArray%2A> aux deux requêtes et réexécutez le programme :</span><span class="sxs-lookup"><span data-stu-id="d9e17-248">Append the LINQ method <xref:System.Linq.Enumerable.ToArray%2A> to both queries and run the program again:</span></span>

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="d9e17-249">Le mélange extérieur est descendu à 30 requêtes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-249">Now the out shuffle is down to 30 queries.</span></span> <span data-ttu-id="d9e17-250">Si vous repassez au mélange intérieur, vous constaterez des améliorations similaires : il ne comporte plus que 162 requêtes.</span><span class="sxs-lookup"><span data-stu-id="d9e17-250">Run again with the in shuffle and you'll see similar improvements: it now executes 162 queries.</span></span>

<span data-ttu-id="d9e17-251">Sachez que cet exemple est **conçu** pour mettre en évidence les cas d’usage où l’évaluation paresseuse cause des problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="d9e17-251">Please note that this example is **designed** to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="d9e17-252">S’il est important de voir son impact sur les performances du code, il faut également comprendre que toutes les requêtes ne doivent pas s’exécuter de manière stricte.</span><span class="sxs-lookup"><span data-stu-id="d9e17-252">While it's important to see where lazy evaluation can impact code performance, it's equally important to understand that not all queries should run eagerly.</span></span> <span data-ttu-id="d9e17-253">La baisse de performances que l’on constate sans <xref:System.Linq.Enumerable.ToArray%2A> est due au fait que chaque nouvelle disposition du jeu de cartes est construite à partir de la configuration précédente.</span><span class="sxs-lookup"><span data-stu-id="d9e17-253">The performance hit you incur without using <xref:System.Linq.Enumerable.ToArray%2A> is because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="d9e17-254">Avec l’évaluation paresseuse, chaque nouvelle configuration du jeu est générée à partir du jeu d’origine, y compris l’exécution du code qui a construit `startingDeck`,</span><span class="sxs-lookup"><span data-stu-id="d9e17-254">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="d9e17-255">ce qui entraîne une grande quantité de travail supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d9e17-255">That causes a large amount of extra work.</span></span>

<span data-ttu-id="d9e17-256">Dans la pratique, certains algorithmes fonctionnent bien avec l’évaluation stricte, d’autres avec l’évaluation paresseuse.</span><span class="sxs-lookup"><span data-stu-id="d9e17-256">In practice, some algorithms run well using eager evaluation, and others run well using lazy evaluation.</span></span> <span data-ttu-id="d9e17-257">Au quotidien, l’évaluation paresseuse est en général un meilleur choix lorsque la source de données est un processus distinct, comme un moteur de base de données.</span><span class="sxs-lookup"><span data-stu-id="d9e17-257">For daily usage, lazy evaluation is usually a better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="d9e17-258">L’évaluation paresseuse permet dans ce cas d’exécuter des requêtes plus complexes avec un seul aller-retour entre le processus de base de données et le reste du code.</span><span class="sxs-lookup"><span data-stu-id="d9e17-258">For databases, lazy evaluation allows more complex queries to execute only one round trip to the database process and back to the rest of your code.</span></span> <span data-ttu-id="d9e17-259">LINQ peut s’adapter tant à l’évaluation paresseuse qu’à l’évaluation stricte. Par conséquent, examinez vos processus et choisissez le type d’évaluation qui vous offre les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="d9e17-259">LINQ is flexible whether you choose to utilize lazy or eager evaluation, so measure your processes and pick whichever kind of evaluation gives you the best performance.</span></span>

## <a name="conclusion"></a><span data-ttu-id="d9e17-260">Conclusion</span><span class="sxs-lookup"><span data-stu-id="d9e17-260">Conclusion</span></span>

<span data-ttu-id="d9e17-261">Dans ce projet, nous avons vu comment :</span><span class="sxs-lookup"><span data-stu-id="d9e17-261">In this project, you covered:</span></span>

- <span data-ttu-id="d9e17-262">utiliser des requêtes LINQ pour agréger des données en une séquence explicite ;</span><span class="sxs-lookup"><span data-stu-id="d9e17-262">using LINQ queries to aggregate data into a meaningful sequence</span></span>
- <span data-ttu-id="d9e17-263">écrire des méthodes d’extension pour ajouter des fonctionnalités personnalisées aux requêtes LINQ ;</span><span class="sxs-lookup"><span data-stu-id="d9e17-263">writing Extension methods to add our own custom functionality to LINQ queries</span></span>
- <span data-ttu-id="d9e17-264">localiser les zones du code où les requêtes LINQ risquent de poser des problèmes de performances, comme une dégradation de la vitesse ;</span><span class="sxs-lookup"><span data-stu-id="d9e17-264">locating areas in our code where our LINQ queries might run into performance issues like degraded speed</span></span>
- <span data-ttu-id="d9e17-265">utiliser l’évaluation paresseuse et l’évaluation stricte dans des requêtes LINQ, avec les implications que cela comporte sur les performances de requête.</span><span class="sxs-lookup"><span data-stu-id="d9e17-265">lazy and eager evaluation in regards to LINQ queries and the implications they might have on query performance</span></span>

<span data-ttu-id="d9e17-266">En dehors de LINQ, vous avez appris une technique de tour de cartes utilisée par les magiciens.</span><span class="sxs-lookup"><span data-stu-id="d9e17-266">Aside from LINQ, you learned a bit about a technique magicians use for card tricks.</span></span> <span data-ttu-id="d9e17-267">Les magiciens utilisent le mélange faro pour pouvoir contrôler le déplacement de chaque carte dans le jeu.</span><span class="sxs-lookup"><span data-stu-id="d9e17-267">Magicians use the Faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="d9e17-268">Maintenant que vous le savez, gardez le secret !</span><span class="sxs-lookup"><span data-stu-id="d9e17-268">Now that you know, don't spoil it for everyone else!</span></span>

<span data-ttu-id="d9e17-269">Pour plus d’informations sur LINQ, voir :</span><span class="sxs-lookup"><span data-stu-id="d9e17-269">For more information on LINQ, see:</span></span>

- [<span data-ttu-id="d9e17-270">Requête intégrée linguistique (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d9e17-270">Language Integrated Query (LINQ)</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d9e17-271">Introduction à LINQ</span><span class="sxs-lookup"><span data-stu-id="d9e17-271">Introduction to LINQ</span></span>](../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d9e17-272">Opérations de requête LINQ de base (C#)</span><span class="sxs-lookup"><span data-stu-id="d9e17-272">Basic LINQ Query Operations (C#)</span></span>](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [<span data-ttu-id="d9e17-273">Transformations de données avec LINQ (C)</span><span class="sxs-lookup"><span data-stu-id="d9e17-273">Data Transformations With LINQ (C#)</span></span>](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [<span data-ttu-id="d9e17-274">Syntaxe de requête et syntaxe de méthode dans LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d9e17-274">Query Syntax and Method Syntax in LINQ (C#)</span></span>](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [<span data-ttu-id="d9e17-275">Caractéristiques de CMD qui prennent en charge LINQ</span><span class="sxs-lookup"><span data-stu-id="d9e17-275">C# Features That Support LINQ</span></span>](../programming-guide/concepts/linq/features-that-support-linq.md)
