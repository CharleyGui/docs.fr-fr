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
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Apprenez à gérer les collections de données en utilisant le type de liste générique

Ce didacticiel propose une introduction au langage C# et présente les concepts de base de la classe <xref:System.Collections.Generic.List%601>.

Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement. Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS. Vous trouverez une brève vue d’ensemble des commandes utilisées disponible dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.

## <a name="a-basic-list-example"></a>Exemple de liste de base

Créez un répertoire nommé *list-tutorial*. Faites-en le répertoire actuel et exécutez `dotnet new console`.

Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez le code existant par le suivant :

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

Remplacez `<name>` par votre nom. Enregistrez *Program.cs*. Tapez `dotnet run` dans votre fenêtre de console pour effectuer un essai.

Vous avez créé une liste de chaînes, ajouté trois noms à cette liste et affiché les noms en majuscules. Vous utilisez des concepts que vous avez appris dans les tutoriels précédents pour lire la liste en boucle.

Le code permettant d’afficher les noms utilise la fonctionnalité [d’interpolation de chaîne](../../language-reference/tokens/interpolated.md).  Quand vous faites précéder une `string` du caractère `$`, vous pouvez incorporer le code C# dans la déclaration de chaîne. La chaîne réelle remplace ce code C# par la valeur qu’elle génère. Dans cet exemple, elle remplace `{name.ToUpper()}` par chaque nom, converti en majuscules, car vous avez appelé la méthode <xref:System.String.ToUpper%2A>.

Continuons notre exploration.

## <a name="modify-list-contents"></a>Modifier le contenu de la liste

La collection que vous avez créée utilise le type <xref:System.Collections.Generic.List%601>. Ce type stocke les séquences d’éléments. Vous spécifiez le type des éléments entre crochets angulaires.

Un aspect important du type <xref:System.Collections.Generic.List%601> est qu’il peut augmenter ou diminuer, ce qui vous permet d’ajouter ou de supprimer des éléments. Ajoutez ce code avant de fermer le `}` dans la méthode `Main` :

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

Vous avez ajouté deux noms supplémentaires à la fin de la liste. Vous en avez également supprimé un. Enregistrez le fichier et tapez `dotnet run` pour effectuer un essai.

La <xref:System.Collections.Generic.List%601> vous permet en outre de faire référence à des éléments individuels par **index**. Vous placez l’index entre les jetons `[` et `]` après le nom de la liste. C# utilise la valeur 0 pour le premier index. Ajoutez le code directement sous le code que vous venez d’ajouter et effectuez un essai :

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Vous ne pouvez pas accéder à un index au-delà de la fin de la liste. Rappelez-vous que les index commencent à partir de 0, de sorte que le plus grand index valide correspond au nombre d’éléments de la liste moins un. Vous pouvez vérifier la longueur de la liste à l’aide de la propriété <xref:System.Collections.Generic.List%601.Count%2A>. Ajoutez le code suivant à la fin de la méthode Main :

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Enregistrez le fichier et tapez de nouveau `dotnet run` pour afficher les résultats.

## <a name="search-and-sort-lists"></a>Trier les listes et y effectuer des recherches

Nos exemples utilisent des listes relativement petites, mais vos applications peuvent souvent générer des listes contenant beaucoup plus d’éléments, qui se comptent parfois même en milliers. Pour rechercher des éléments dans ces collections plus volumineuses, vous devez rechercher différents éléments dans la liste. La méthode <xref:System.Collections.Generic.List%601.IndexOf%2A> recherche un élément et retourne l’index de ce dernier. Si l’élément n’est pas dans la liste, `IndexOf` retourne `-1` . Ajoutez ce code en bas de votre méthode `Main` :

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

Il est également possible de trier les éléments de la liste. La <xref:System.Collections.Generic.List%601.Sort%2A> méthode trie tous les éléments de la liste dans l’ordre normal (par ordre alphabétique pour les chaînes). Ajoutez ce code en bas de notre méthode `Main` :

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Enregistrez le fichier et tapez `dotnet run` pour tester cette dernière version.

Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte. Cela nous permettra de travailler plus facilement avec un nouvel exemple. Renommez votre méthode `Main``WorkingWithStrings` et écrivez une nouvelle méthode `Main` qui appelle `WorkingWithStrings`. Lorsque vous avez terminé, votre code doit ressembler à ceci :

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

## <a name="lists-of-other-types"></a>Listes d’autres types

Vous avez jusqu'à présent utilisé le type `string` dans les listes. Nous allons maintenant créer une <xref:System.Collections.Generic.List%601> en utilisant un autre type. Commençons par créer un ensemble de nombres.

Ajoutez le code suivant en bas de votre nouvelle méthode `Main` :

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Cela crée une liste d’entiers et définit les deux premiers entiers sur la valeur 1. Il s’agit des deux premières valeurs d’une *séquence Fibonacci* (séquence de nombres). Chaque nombre Fibonacci suivant correspond à la somme des deux nombres précédents. Ajoutez le code suivant :

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Enregistrez le fichier et tapez `dotnet run` pour afficher les résultats.

> [!TIP]
> Pour vous concentrer uniquement sur cette section, vous pouvez commenter le code qui appelle `WorkingWithStrings();`. Insérez simplement deux caractères `/` devant l’appel comme suit :  `// WorkingWithStrings();`.

## <a name="challenge"></a>Test

Vérifiez si vous pouvez mettre en pratique certains des concepts appris ici et dans d’autres leçons antérieures. Approfondissez à partir de ce que vous avez créé jusqu'à présent avec les nombres de Fibonacci. Essayez d’écrire le code pour générer les 20 premiers nombres de la séquence. (Astuce, le 20ème nombre Fibonacci est 6765.)

## <a name="complete-challenge"></a>Terminer le test

Vous pouvez voir un exemple de solution en [consultant l’exemple de code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).

À chaque itération de la boucle, vous sélectionnez les deux derniers entiers de la liste, les additionner et ajoutez la valeur obtenue à la liste. La boucle se répète jusqu'à ce que vous ayez ajouté 20 éléments à la liste.

Félicitations, vous avez terminé ce didacticiel sur les listes. Vous pouvez passer au tutoriel [Introduction aux classes](introduction-to-classes.md) dans votre propre environnement de développement.

Vous pouvez en savoir plus sur l’utilisation du `List` type dans l’article du [Guide .net](../../../standard/index.yml) sur les [Collections](../../../standard/collections/index.md). Vous allez également en découvrir plus sur de nombreux autres types de collection.
