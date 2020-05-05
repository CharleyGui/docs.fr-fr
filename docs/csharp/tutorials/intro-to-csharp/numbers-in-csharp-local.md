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
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipuler les nombres intégraux et à virgule flottante en C\#

Ce tutoriel permet de découvrir de manière interactive les types numériques en C#. Vous allez écrire de petites quantités de code, puis vous compilerez et exécuterez ce code. Ce tutoriel comporte une série de leçons visant à explorer les nombres et les opérations mathématiques en C#. Ces leçons présentent les concepts de base du langage C#.

Ce tutoriel suppose de disposer d’un ordinateur utilisable pour le développement. Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS. Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.

## <a name="explore-integer-math"></a>Explorer les mathématiques avec des entiers

Créez un répertoire nommé *numbers-quickstart*. Créez le répertoire actif et exécutez la commande suivante :

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez la ligne `Console.WriteLine("Hello World!");` par le code qui suit :

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande.

Vous avez vu une des opérations mathématiques fondamentales avec des entiers. Le `int` type représente un **entier**, un zéro, un nombre entier positif ou négatif. Vous utilisez le symbole `+` pour effectuer une addition. Les autres opérations mathématiques courantes avec des entiers sont les suivantes :

- `-` pour la soustraction
- `*` pour la multiplication
- `/` pour la division

Commencez par explorer ces différentes opérations. Ajoutez ces lignes après la ligne qui écrit la valeur de `c` :

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

Exécutez ce code en tapant `dotnet run` dans votre fenêtre de commande.

Vous pouvez également expérimenter en écrivant plusieurs opérations mathématiques dans la même ligne, si vous le souhaitez. Essayez `c = a + b - 12 * 17;` par exemple. La combinaison de variables et de nombres constants est autorisée.

> [!TIP]
> Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code. Le **compilateur** détectera ces erreurs et vous les signalera. Si la sortie contient des messages d’erreur, vérifiez attentivement l’exemple de code ainsi que le code dans votre fenêtre pour identifier les corrections à apporter.
> Cet exercice vous aidera à mieux comprendre la structure du code C#.

Vous avez terminé la première étape. Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte. Cela nous permettra de travailler plus facilement avec un nouvel exemple. Renommez votre méthode `Main``WorkingWithIntegers` et écrivez une nouvelle méthode `Main` qui appelle `WorkingWithIntegers`. Lorsque vous avez terminé, votre code doit ressembler à ceci :

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

## <a name="explore-order-of-operations"></a>Explorer l’ordre des opérations

Commentez l’appel à `WorkingWithIntegers()`. La sortie est ainsi moins encombrée lorsque vous travaillez dans cette section :

```csharp
//WorkingWithIntegers();
```

`//` démarre un **commentaire** dans C#. Les commentaires correspondent à du texte que vous voulez conserver dans votre code source sans l’exécuter en tant que code. Le compilateur ne génère pas de code exécutable à partir de commentaires.

Le langage C# définit la priorité des différentes opérations mathématiques avec à l’aide de règles cohérentes avec les règles mathématiques que vous avez apprises.
La multiplication et la division ont priorité sur l’addition et la soustraction.
Explorez ce concept en ajoutant le code suivant à votre méthode `Main` et en exécutant `dotnet run` :

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

La sortie montre que la multiplication est effectuée avant l’addition.

Vous pouvez appliquer un ordre de calcul différent en mettant entre parenthèses la ou les opérations à exécuter en premier. Ajoutez les lignes suivantes et exécutez à nouveau :

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Pratiquez en combinant plusieurs opérations différentes. Ajoutez quelque chose ressemblant aux lignes suivantes au bas de votre méthode `Main`. Essayez `dotnet run` à nouveau.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Vous avez peut-être observé un comportement intéressant des entiers. La division d’entiers produit toujours un résultat entier, même quand vous pensez que le résultat devrait inclure une partie décimale ou fractionnaire.

Si vous n’avez pas observé ce comportement, essayez le code qui suit à la fin de votre méthode `Main` :

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Tapez `dotnet run` à nouveau pour afficher les résultats.

Avant de continuer, prenez tout le code que vous avez écrit dans cette section et placez-le dans une nouvelle méthode. Nommez cette nouvelle méthode `OrderPrecedence`.
Vous devez écrire un texte similaire à ce qui suit :

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

## <a name="explore-integer-precision-and-limits"></a>Explorer la précision et les limites des entiers

Ce dernier exemple a montré que la division d’entiers tronque le résultat.
Vous pouvez obtenir le **reste** à l’aide de l’opérateur **modulo**, à savoir le caractère `%`. Essayez le code suivant dans votre méthode `Main` :

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

Le type d’entier C# diffère des entiers mathématiques d’une autre manière : le type `int` a des limites minimale et maximale. Ajoutez ce code à votre méthode `Main` pour voir ces limites :

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Si un calcul produit une valeur qui dépasse ces limites, vous obtenez une condition de **dépassement négatif** ou **dépassement positif**. La réponse affichée indique la plage (d’une limite à l’autre). Ajoutez ces deux lignes à votre méthode `Main` pour voir un exemple :

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Notez que la réponse est très proche de l’entier minimal (négatif). Il en est de même pour `min + 2`.
L’addition a produit un **dépassement négatif** des valeurs autorisées pour les entiers.
La réponse est un très grand nombre négatif, car un dépassement négatif « inclut » de la plus grande valeur d’entier possible à la plus petite.

Il existe d’autres types numériques avec une précision et des limites différentes que vous pouvez utiliser quand le type `int` ne répond pas à vos besoins. Étudions les autres types suivants.

Encore une fois, déplaçons le code que vous avez écrit dans cette section vers une autre méthode. Nommez-le `TestLimits`.

## <a name="work-with-the-double-type"></a>Utiliser le type double

Le type numérique `double` représente un nombre à virgule flottante double précision. Ces termes vous sont peut-être inconnus. Un nombre à **virgule flottante** est utile pour représenter des nombres non intégraux qui peuvent être très grands ou très petits en amplitude. La **double précision** est un terme relatif qui décrit le nombre de chiffres binaires utilisés pour stocker la valeur. Les nombres à **double précision** ont deux fois le nombre de chiffres binaires comme **simple précision**. Sur les ordinateurs modernes, il est plus courant d’utiliser une double précision que des nombres à simple précision. Les nombres à **précision unique** sont déclarés à l’aide du `float` mot clé.
Explorons ce type double. Ajoutez le code suivant et affichez le résultat :

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Notez que la réponse inclut la partie décimale du quotient. Essayez avec une expression légèrement plus complexe utilisant des doubles :

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

La plage d’une valeur double est nettement supérieure à celle de valeurs entières. Essayez le code suivant sous ce que vous avez écrit jusque-là :

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Ces valeurs s’affichent sous forme de notation scientifique. Le nombre à gauche du `E` est le nombre significatif. Le nombre à droite est l’exposant, en puissance de 10.

Tout comme les nombres décimaux en mathématiques, les doubles en C# peuvent présenter des erreurs d’arrondi. Exécutez le code suivant :

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Vous savez que `0.3` la répétition n’est pas exactement identique `1/3`à celle de.

***Test***

Essayez d’autres calculs avec de grands nombres, des petits nombres, des multiplications `double` et des divisions à l’aide du type. Effectuez des calculs plus complexes.

Après avoir consacré plus de temps au test, placez le code que vous avez écrit dans une nouvelle méthode. Nommez cette nouvelle méthode `WorkWithDoubles`.

## <a name="work-with-decimal-types"></a>Utiliser des types décimaux

Vous avez vu les types numériques de base en C#, à savoir les entiers et les doubles.  Il y a un autre type à apprendre : `decimal` le type. Le type `decimal` a une plage plus petite, mais une précision supérieure à celle du type `double`. Étudions cela d’un peu plus près :

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Notez que la plage est plus petite que celle du type `double`. Vous pouvez observer la plus haute précision du type décimal en exécutant le code suivant :

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Le suffixe `M` des nombres permet d’indiquer comment une constante doit utiliser le type `decimal`. Sinon, le compilateur suppose le `double` type.

> [!NOTE]
> La lettre `M` a été choisie comme lettre la plus distincte entre les `double` Mots clés `decimal` et.

Notez que le calcul utilisant le type décimal a plus de chiffres à droite de la virgule décimale.

***Test***

Maintenant que vous avez vu les différents types numériques, écrivez du code qui calcule la surface d’un cercle avec un rayon de 2,5 centimètres. Rappelez-vous que la surface d’un cercle est le rayon au carré multiplié par PI. Conseil : .NET contient une constante pour PI, à savoir <xref:System.Math.PI?displayProperty=nameWithType>, que vous pouvez utiliser pour cette valeur. <xref:System.Math.PI?displayProperty=nameWithType>, comme toutes les constantes déclarées `System.Math` dans l’espace de `double` noms, est une valeur. Pour cette raison, vous devez utiliser `double` au lieu `decimal` de valeurs pour ce défi.

Vous devriez obtenir une réponse comprise entre 19 et 20.
Vous pouvez vérifier votre réponse en [examinant l’exemple de code terminé sur GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).

Si vous le voulez, essayez d’autres formules.

Vous avez terminé le guide de démarrage rapide « Nombres en C# ». Vous pouvez passer au guide de démarrage rapide [Branches et boucles](branches-and-loops-local.md) dans votre propre environnement de développement.

Vous pouvez en savoir plus sur les nombres en C# dans les articles suivants :

- [Types numériques intégraux](../../language-reference/builtin-types/integral-numeric-types.md)
- [Types numériques à virgule flottante](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Conversions numériques intégrées](../../language-reference/builtin-types/numeric-conversions.md)
