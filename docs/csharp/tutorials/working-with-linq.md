---
title: Utilisation de LINQ
description: Ce didacticiel vous apprend à générer des séquences avec LINQ, à écrire des méthodes pour les requêtes LINQ et à faire la distinction entre l’évaluation stricte et l’évaluation paresseuse.
ms.date: 10/29/2018
ms.technology: csharp-linq
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: ece001e82c0aa44a91999bea78d2fd695ff9362b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240013"
---
# <a name="work-with-language-integrated-query-linq"></a>Utiliser LINQ (Language-Integrated Query)

## <a name="introduction"></a>Introduction

Ce tutoriel vous présente les fonctionnalités de .NET Core et du langage C#. Vous découvrirez comment effectuer les actions suivantes :

- Générer des séquences avec LINQ.
- Méthodes d’écriture qui peuvent être facilement utilisées dans les requêtes LINQ.
- Distinguer les évaluations hâtif et tardive.

Vous apprendrez ces techniques en créant une application qui illustre l’une des compétences de base de tout magicien : le [mélange faro](https://en.wikipedia.org/wiki/Faro_shuffle). En quelques mots, le mélange faro est une technique qui consiste à diviser un paquet de cartes en deux moitiés exactes, puis à intercaler une carte sur deux de chacune des deux moitiés de façon à reconstruire le jeu d’origine.

Les magiciens utilisent cette technique parce que chaque carte se trouve à un emplacement connu après chaque mélange, suivant un motif répétitif.

Dans notre cas, c’est une façon plaisante d’envisager la manipulation de séquences de données. L’application que vous allez générer construit un jeu de cartes, puis effectue une séquence de mélange, en écrivant chaque séquence à chaque fois. Vous comparerez également le nouvel ordre à l’ordre d’origine.

Ce didacticiel comporte plusieurs étapes. Après chaque étape, vous pourrez exécuter l’application et voir la progression. Vous pouvez également voir l’[exemple terminé](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) dans le dépôt GitHub dotnet/samples. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Composants requis

Vous devez configurer votre ordinateur pour exécuter .NET core. Vous trouverez les instructions d’installation sur la page de [téléchargement de .net Core](https://dotnet.microsoft.com/download) . Vous pouvez exécuter cette application sur Windows, Ubuntu Linux ou OS X, ou dans un conteneur d’ancrage. Vous devez installer l’éditeur de code de votre choix. Les descriptions ci-dessous utilisent [Visual Studio code](https://code.visualstudio.com/) qui est un éditeur multiplateforme Open source. Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.

## <a name="create-the-application"></a>Création de l’application

La première étape consiste à créer une nouvelle application. Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application. Réglez-le comme répertoire actuel. Saisissez la commande `dotnet new console` à l’invite. Elle crée les fichiers de démarrage d’une application « Hello World » de base.

Si vous n’avez jamais utilisé C#, [ce didacticiel](console-teleprompter.md) explique la structure d’un programme C#. Vous pouvez le lire, puis revenir ici pour en savoir plus sur LINQ.

## <a name="create-the-data-set"></a>Créer le jeu de données

Avant de commencer, vérifiez que les lignes suivantes figurent en haut du fichier `Program.cs` généré par `dotnet new console` :

```csharp
// Program.cs
using System;
using System.Collections.Generic;
using System.Linq;
```

Si ces trois lignes (instructions `using`) ne figurent pas en haut du fichier, le programme ne se compilera pas.

Maintenant que vous avez toutes les références dont vous avez besoin, réfléchissons à ce qui compose un jeu de cartes. En général, un jeu de cartes à jouer comporte quatre couleurs, et chaque couleur a treize valeurs. On pourrait envisager de créer directement une classe `Card` et de remplir manuellement une collection d’objets `Card`. Avec LINQ, il est possible d’être plus concis que cela. Au lieu de créer une classe `Card`, vous pouvez créer deux séquences pour représenter respectivement les couleurs et les rangs. Créez deux [*méthodes d’itération*](../iterators.md#enumeration-sources-with-iterator-methods) simples qui génèreront les rangs et les couleurs sous forme de <xref:System.Collections.Generic.IEnumerable%601> de chaînes :

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

Placez-les sous la méthode `Main` dans votre fichier `Program.cs`. Les deux méthodes utilisent la syntaxe `yield return` pour produire une séquence lors de leur exécution. Le compilateur génère un objet qui implémente <xref:System.Collections.Generic.IEnumerable%601> et génère la séquence de chaînes au fur et à mesure.

Maintenant, utilisez ces méthodes d’itération pour créer le jeu de cartes. Placez la requête LINQ dans la méthode `Main` :

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

Les clauses `from` multiples produisent un <xref:System.Linq.Enumerable.SelectMany%2A>, qui crée une séquence unique en combinant chaque élément de la première séquence avec chaque élément de la deuxième séquence. L’ordre est important ici. Le premier élément de la première séquence source (couleurs) est associé à chacun des éléments de la deuxième séquence (rangs). Cette opération génère les treize cartes de la première couleur. Ce processus est reproduit pour chaque élément de la première séquence (couleurs). Le résultat final est un jeu de cartes classé par couleurs, puis par valeurs.

Il est important de garder à l’esprit la chose suivante : que vous choisissiez d’écrire votre code LINQ dans la syntaxe de requête utilisée plus haut ou d’utiliser plutôt la syntaxe de méthode, vous pourrez toujours passer d’une forme syntaxique à l’autre. La requête ci-dessus, écrite dans la syntaxe de requête, s’écrit ainsi dans la syntaxe de méthode :

```csharp
var startingDeck = Suits().SelectMany(suit => Ranks().Select(rank => new { Suit = suit, Rank = rank }));
```

Le compilateur traduit les instructions LINQ écrites avec la syntaxe de requête dans la syntaxe d’appel de méthode équivalente. Par conséquent, les deux versions de la requête produisent le même résultat quel que soit le choix de syntaxe. Choisissez la plus adaptée à votre situation : par exemple, si certains membres de votre équipe ont des difficultés à utiliser la syntaxe de méthode, privilégiez dans la mesure du possible la syntaxe de requête.

Ensuite, exécutez l’exemple que vous avez commencé à élaborer. Il affiche les 52 cartes du jeu. Il peut être très utile d’exécuter cet exemple avec un débogueur pour observer la façon dont les méthodes `Suits()` et `Ranks()` s’exécutent. Vous pouvez clairement voir que chaque chaîne de chaque séquence est générée uniquement au moment requis.

![Fenêtre console montrant l’application produisant 52 cartes.](./media/working-with-linq/console-52-card-application.png)

## <a name="manipulate-the-order"></a>Manipuler la commande

Maintenant, réfléchissons à la façon dont nous allons battre les cartes du jeu. Pour bien faire, la première étape consiste à couper le jeu en deux. Les méthodes <xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A>, qui font partie des API LINQ, offrent cette fonctionnalité. Placez-les sous la boucle `foreach` :

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

Cependant, il n’y a pas de méthode de battage dans la bibliothèque standard ; vous devez donc écrire la vôtre. Comme elle illustrera plusieurs techniques des programmes LINQ, nous allons expliquer les différentes parties du processus étape par étape.

Pour ajouter des fonctionnalités aux interactions possibles avec les <xref:System.Collections.Generic.IEnumerable%601> obtenus à partir des requêtes LINQ, vous allez écrire des méthodes d’un genre particulier, nommées [méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md). En bref, une méthode d’extension est une *méthode statique* spéciale qui ajoute de nouvelles fonctionnalités à un type existant sans qu’il soit nécessaire de modifier le type d’origine.

Pour accueillir vos méthodes d’extension, ajoutez à votre programme un nouveau fichier de classe *statique*, nommé `Extensions.cs`, puis créez la première méthode d’extension :

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

Examinez attentivement la signature de méthode, et en particulier les paramètres :

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T> (this IEnumerable<T> first, IEnumerable<T> second)
```

On peut voir l’ajout du modificateur `this` au premier argument de la méthode. Cela signifie que vous appelez la méthode comme s’il s’agissait d’une méthode membre du type du premier argument. Cette déclaration de méthode suit également un idiome standard selon lequel les types d’entrée et de sortie sont `IEnumerable<T>`. Cette pratique permet d’enchaîner les méthodes LINQ afin d’exécuter des requêtes plus complexes.

Bien entendu, le jeu ayant été coupé en deux, il faut réunir les deux moitiés. Dans le code, cela signifie énumérer d’un seul coup les deux séquences acquises avec <xref:System.Linq.Enumerable.Take%2A> et <xref:System.Linq.Enumerable.Skip%2A>, en intercalant (*`interleaving`*) les éléments pour créer une seule séquence : le jeu de cartes battu. Pour écrire une méthode LINQ qui fonctionne avec deux séquences, vous devez comprendre comment <xref:System.Collections.Generic.IEnumerable%601> fonctionne.

L’interface <xref:System.Collections.Generic.IEnumerable%601> possède une seule méthode : <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>. L’objet retourné par <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a une méthode permettant d’atteindre l’élément suivant et une propriété qui récupère l’élément actif dans la séquence. Vous allez utiliser ces deux membres pour énumérer la collection et retourner les éléments. Cette méthode Interleave sera une méthode d’itération ; par conséquent, au lieu de créer une collection et de la retourner, vous allez utiliser la syntaxe `yield return` présentée ci-dessus.

Voici l’implémentation de cette méthode :

[!CODE-csharp[InterleaveSequenceWith](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

Maintenant que vous avez écrit cette méthode, revenez à la méthode `Main` et mélangez le jeu une fois :

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

## <a name="comparisons"></a>Comparaisons

Combien de battages faut-il compter pour remettre le jeu dans l’ordre d’origine ? Pour le savoir, il faut écrire une méthode qui détermine si deux séquences sont égales. Ensuite, il vous faudra placer le code qui mélange le jeu dans une boucle et vérifier si le jeu est de nouveau dans l’ordre.

Vous ne devriez pas avoir de problèmes à écrire une méthode qui détermine si deux séquences sont égales. La structure est similaire à celle de la méthode que vous avez écrite pour mélanger le jeu. Seulement, cette fois, au lieu d’utiliser l’instruction `yield return` sur chaque élément, vous allez comparer les éléments correspondants de chaque séquence. Une fois que la séquence aura été énumérée en entier, si tous les éléments correspondent, les séquences sont les mêmes :

[!CODE-csharp[SequenceEquals](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

Cet exemple montre un autre terme LINQ : les méthodes terminales. Elles prennent une séquence en entrée (ou, dans ce cas, deux séquences) et retournent une valeur scalaire unique. Les méthodes terminales sont toujours la dernière méthode de la chaîne de méthodes d’une requête LINQ ; d’où le nom « terminal ».

Vous pourrez les voir en action lorsque vous les utiliserez pour déterminer si le jeu est dans l’ordre d’origine. Placez le code de mélange à l’intérieur d’une boucle, et arrêtez-la lorsque la séquence est à nouveau dans l’ordre d’origine en appliquant la méthode `SequenceEquals()`. Vous pouvez voir qu’il s’agit toujours de la dernière méthode d’une requête, parce qu’elle retourne une valeur unique plutôt qu’une séquence :

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

Exécutez le code ainsi obtenu et étudiez la façon dont le jeu se réorganise à chaque battage. Après huit battages (itérations de la boucle do-while), le jeu revient à la configuration qu’il avait à sa création avec la requête LINQ initiale.

## <a name="optimizations"></a>Optimisations

L’exemple que vous avez produit jusque-là exécute un *mélange extérieur*, où les cartes du haut et du bas restent les mêmes à chaque exécution. Faisons une modification en effectuant plutôt un *mélange intérieur*, où les 52 cartes changent toutes de position. Dans le cas d’un mélange intérieur, on intercale les deux moitiés du jeu de sorte que la première carte de la moitié du dessous devienne la première carte du jeu. Cela signifie que la dernière carte de la moitié du dessus devient la carte du bas. Cette modification simple ne concerne qu’une ligne de code. Mettez à jour la requête de battage actuelle en inversant les positions de <xref:System.Linq.Enumerable.Take%2A> et de <xref:System.Linq.Enumerable.Skip%2A>, de façon à modifier l’ordre des moitiés du dessus et du dessous du jeu :

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

Réexécutez le programme : vous verrez qu’il faut 52 itérations pour que le jeu se réorganise. Vous commencerez également à remarquer de sérieuses dégradations des performances lors de l’exécution du programme.

Il y a plusieurs raisons à cela. L’une des causes principales de cette baisse de performances est une utilisation inefficace de [*l’évaluation paresseuse*](../programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

En bref, l’évaluation d’une instruction n’est effectuée que lorsque sa valeur devient nécessaire. Les requêtes LINQ sont évaluées de cette manière. Les séquences sont générées uniquement au moment où les éléments sont demandés. En règle générale, c’est un avantage majeur de LINQ. Toutefois, dans une utilisation du type de ce programme, cela entraîne une croissance exponentielle de la durée d’exécution.

N’oubliez pas que nous avons généré le jeu d’origine à l’aide d’une requête LINQ. Chaque mélange est généré en effectuant trois requêtes LINQ sur le jeu précédent. Toutes ces opérations sont effectuées de façon retardée. Cela signifie également qu’elles sont effectuées à chaque fois que la séquence est demandée. À la 52e itération, vous aurez régénéré le jeu d’origine de nombreuses fois. Nous allons écrire dans un journal pour illustrer ce comportement. Ensuite, vous résoudrez le problème.

Dans votre fichier `Extensions.cs`, tapez ou copiez la méthode d’extension ci-dessous. Elle crée un fichier nommé `debug.log` au sein de votre répertoire de projet et enregistre la requête en cours d’exécution dans le fichier journal. Elle peut être ajoutée à une requête pour marquer le fait qu’elle s’est exécutée.

[!CODE-csharp[LogQuery](../../../samples/snippets/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

Vous verrez une ligne ondulée rouge sous `File`, ce qui signifie qu’elle n’existe pas. Elle ne sera pas compilée, puisque le compilateur ne sait pas ce qu’est `File`. Pour résoudre ce problème, veillez à ajouter la ligne de code suivante sous la première ligne dans `Extensions.cs` :

```csharp
using System.IO;
```

Cela devrait résoudre le problème et faire disparaître l’erreur rouge.

Instrumentez ensuite la définition de chaque requête avec un message de journalisation :

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

Remarquez que vous n’écrivez pas dans le journal à chaque fois que vous accédez à une requête, mais seulement lors de la création de la requête d’origine. Le programme met toujours longtemps à s’exécuter, mais vous pouvez maintenant voir pourquoi. Si vous perdez patience au cours de l’exécution du mélange intérieur avec journalisation, revenez au mélange extérieur. Vous verrez quand même les effets de l’évaluation paresseuse. Sur une itération, elle exécute 2 592 requêtes, génération de toutes les valeurs et couleurs comprise.

Vous pouvez améliorer les performances du code en réduisant le nombre d’exécutions effectuées. L’un des correctifs les plus simples consiste à mettre en *cache* les résultats de la requête LINQ d’origine qui construit le jeu de cartes. Actuellement, les requêtes sont réexécutées chaque fois que la boucle do-while effectue une itération, construisant et battant de nouveau le jeu de cartes à chaque fois. Pour mettre en cache le jeu de cartes, vous pouvez utiliser les méthodes LINQ <xref:System.Linq.Enumerable.ToArray%2A> et <xref:System.Linq.Enumerable.ToList%2A> ; ajoutées aux requêtes, elles effectuent les actions voulues, mais en stockant respectivement les résultats dans un tableau ou dans une liste. Ajoutez la méthode LINQ <xref:System.Linq.Enumerable.ToArray%2A> aux deux requêtes et réexécutez le programme :

[!CODE-csharp[Main](../../../samples/snippets/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

Le mélange extérieur est descendu à 30 requêtes. Si vous repassez au mélange intérieur, vous constaterez des améliorations similaires : il ne comporte plus que 162 requêtes.

Sachez que cet exemple est **conçu** pour mettre en évidence les cas d’usage où l’évaluation paresseuse cause des problèmes de performances. S’il est important de voir son impact sur les performances du code, il faut également comprendre que toutes les requêtes ne doivent pas s’exécuter de manière stricte. La baisse de performances que l’on constate sans <xref:System.Linq.Enumerable.ToArray%2A> est due au fait que chaque nouvelle disposition du jeu de cartes est construite à partir de la configuration précédente. Avec l’évaluation paresseuse, chaque nouvelle configuration du jeu est générée à partir du jeu d’origine, y compris l’exécution du code qui a construit `startingDeck`, ce qui entraîne une grande quantité de travail supplémentaire.

Dans la pratique, certains algorithmes fonctionnent bien avec l’évaluation stricte, d’autres avec l’évaluation paresseuse. Au quotidien, l’évaluation paresseuse est en général un meilleur choix lorsque la source de données est un processus distinct, comme un moteur de base de données. L’évaluation paresseuse permet dans ce cas d’exécuter des requêtes plus complexes avec un seul aller-retour entre le processus de base de données et le reste du code. LINQ peut s’adapter tant à l’évaluation paresseuse qu’à l’évaluation stricte. Par conséquent, examinez vos processus et choisissez le type d’évaluation qui vous offre les meilleures performances.

## <a name="conclusion"></a>Conclusion

Dans ce projet, nous avons vu comment :

- utiliser des requêtes LINQ pour agréger des données en une séquence explicite ;
- écrire des méthodes d’extension pour ajouter des fonctionnalités personnalisées aux requêtes LINQ ;
- localiser les zones du code où les requêtes LINQ risquent de poser des problèmes de performances, comme une dégradation de la vitesse ;
- utiliser l’évaluation paresseuse et l’évaluation stricte dans des requêtes LINQ, avec les implications que cela comporte sur les performances de requête.

En dehors de LINQ, vous avez appris une technique de tour de cartes utilisée par les magiciens. Les magiciens utilisent le mélange faro pour pouvoir contrôler le déplacement de chaque carte dans le jeu. Maintenant que vous le savez, gardez le secret !

Pour plus d’informations sur LINQ, voir :

- [LINQ (Language Integrated Query)](../programming-guide/concepts/linq/index.md)
- [Introduction à LINQ](../programming-guide/concepts/linq/index.md)
- [Opérations de requête LINQ de base (C#)](../programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Transformations de données avec LINQ (C#)](../programming-guide/concepts/linq/data-transformations-with-linq.md)
- [Syntaxe de requête et syntaxe de méthode dans LINQ (C#)](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)
- [Fonctionnalités C# qui prennent en charge LINQ](../programming-guide/concepts/linq/features-that-support-linq.md)
