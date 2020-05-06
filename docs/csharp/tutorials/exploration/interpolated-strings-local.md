---
title: Interpolation de chaîne - Tutoriel C#
description: Ce tutoriel montre comment utiliser la fonctionnalité d’interpolation de chaîne en C# pour insérer les résultats d’expressions mises en forme dans une chaîne plus grande.
ms.date: 10/23/2018
ms.openlocfilehash: d1b78670361e8b333499d12b68c0364ad9e40a85
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796052"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a>Utiliser l’interpolation de chaîne pour construire des chaînes mises en forme

Ce tutoriel explique comment utiliser [l’interpolation de chaîne](../../language-reference/tokens/interpolated.md) en C# pour insérer des valeurs dans une chaîne de résultat unique. Vous allez écrire un code en C# et afficher les résultats de la compilation et de l’exécution du code. Le tutoriel contient une série de leçons qui expliquent comment insérer des valeurs dans une chaîne et mettre en forme ces valeurs de différentes façons.

Ce tutoriel suppose que vous disposez d’un ordinateur que vous pouvez utiliser pour le développement. Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS. Vous pouvez également compléter la [version interactive](interpolated-strings.yml) de ce didacticiel dans votre navigateur.

## <a name="create-an-interpolated-string"></a>Créer une chaîne interpolée

Créez un répertoire nommé *interpolated*. Faites-en le répertoire actif et exécutez la commande suivante à partir d’une fenêtre de console :

```dotnetcli
dotnet new console
```

Cette commande crée une nouvelle application console .NET Core dans le répertoire actuel.

Ouvrez *Program.cs* dans votre éditeur favori, puis remplacez la ligne `Console.WriteLine("Hello World!");` par le code qui suit, en remplaçant `<name>` par votre nom :

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

Essayez ce code en tapant `dotnet run` dans la fenêtre de console. Quand vous exécutez le programme, celui-ci affiche une chaîne unique qui inclut votre nom dans le message d’accueil. La chaîne qui se trouve dans l’appel de méthode <xref:System.Console.WriteLine%2A> est une *expression de chaîne interpolée*. C’est un genre de modèle qui vous permet de construire une chaîne unique (appelée *chaîne de résultat*) à partir d’une chaîne qui comprend du code incorporé. Les chaînes interpolées sont particulièrement utiles pour insérer des valeurs dans une chaîne ou pour concaténer (joindre) des chaînes.

Cet exemple simple contient les deux éléments que chaque chaîne interpolée doit avoir :

- Un littéral de chaîne qui commence par le caractère `$` avant ses guillemets ouvrants. Il ne peut pas y avoir d’espace entre le symbole `$` et les guillemets. (Si vous voulez voir ce qui se passe si vous en incluez un, insérez un espace après le caractère `$`, enregistrez le fichier et réexécutez le programme en tapant `dotnet run` dans la fenêtre de console. Le compilateur C# affiche un message d’erreur « Erreur CS1056 : caractère inattendu ’$’ ».)

- Une ou plusieurs *expressions d’interpolation*. Une expression d’interpolation est indiquée par des accolades ouvrantes et fermantes (`{` et `}`). Vous pouvez placer n’importe quelle expression C# qui retourne une valeur (notamment `null`) à l’intérieur des accolades.

Essayons quelques autres exemples d’interpolation de chaîne avec d’autres types de données.

## <a name="include-different-data-types"></a>Inclure différents types de données

Dans la section précédente, vous avez utilisé l’interpolation de chaîne pour insérer une chaîne à l’intérieur d’une autre. Le résultat d’une expression d’interpolation peut toutefois être de n’importe quel type de données. Nous allons insérer des valeurs de différents types de données dans une chaîne interpolée.

Dans l’exemple suivant, nous commençons par définir une [classe](../../programming-guide/classes-and-structs/classes.md) comme type de données `Vegetable` avec la `Name` [propriété](../../properties.md) et la `ToString` [méthode](../../methods.md), qui [remplace](../../language-reference/keywords/override.md) le comportement de la méthode <xref:System.Object.ToString?displayProperty=nameWithType>. Le [ `public` modificateur d’accès](../../language-reference/keywords/public.md) rend cette méthode disponible pour tout code client pour obtenir la représentation sous forme `Vegetable` de chaîne d’une instance. Dans l’exemple, `Vegetable.ToString` la méthode retourne la valeur de `Name` la propriété qui est initialisée dans `Vegetable` le [constructeur](../../programming-guide/classes-and-structs/constructors.md):

```csharp
public Vegetable(string name) => Name = name;
```

Ensuite, nous créons une instance de `Vegetable` la classe `item` nommée à l’aide de l' [ `new` opérateur](../../language-reference/operators/new-operator.md) et fournissons un `Vegetable`nom pour le constructeur :

```csharp
var item = new Vegetable("eggplant");
```

Enfin, nous incluons la variable `item` dans une chaîne interpolée qui contient également une valeur <xref:System.DateTime>, une valeur <xref:System.Decimal> et une valeur d’ [énumération](../../language-reference/builtin-types/enum.md)`Unit`. Remplacez tout le code C# dans votre éditeur par le code suivant, puis utilisez la commande `dotnet run` pour l’exécuter :

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;

   public string Name { get; }

   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

Notez que l’expression d’interpolation `item` dans la chaîne interpolée résout le texte « eggplant » (aubergine) dans la chaîne de résultat. En effet, lorsque le résultat de l’expression n’est pas de type chaîne, il est résolu en une chaîne de la façon suivante :

- Si l’expression d’interpolation donne une valeur `null`, une chaîne vide («» ou <xref:System.String.Empty?displayProperty=nameWithType>) est utilisée.

- Si l’expression d’interpolation ne donne pas une valeur `null`, en général, la méthode `ToString` du type de résultat est appelée. Vous pouvez tester cela en mettant à jour l’implémentation de la méthode `Vegetable.ToString`. Il n’est peut-être même pas nécessaire d’implémenter la méthode `ToString` étant donné que chaque type a déjà une implémentation de cette méthode. Pour tester cela, commentez la définition de la méthode `Vegetable.ToString` dans l’exemple (en la faisant précéder d’un symbole de commentaire `//`). Dans la sortie, la chaîne « eggplant » (aubergines) est remplacée par le nom de type complet (« Vegetable » dans cet exemple), ce qui est le comportement par défaut de la méthode <xref:System.Object.ToString?displayProperty=nameWithType>. Le comportement par défaut de la méthode `ToString` pour une valeur d’énumération est de retourner la représentation sous forme de chaîne de la valeur.

Dans la sortie de cet exemple, la date est trop précise (le prix des aubergines ne change pas chaque seconde) et la valeur du prix n’indique pas la devise locale. Dans la section suivante, vous découvrirez comment résoudre ces problèmes en contrôlant le format des représentations sous forme de chaînes des résultats des expressions.

## <a name="control-the-formatting-of-interpolation-expressions"></a>Contrôler la mise en forme des expressions d’interpolation

Dans la section précédente, deux chaînes à la mise en forme incorrecte ont été insérées dans la chaîne de résultat. L’une était une valeur de date et d’heure pour laquelle seule la date était appropriée. La deuxième était un prix qui n’indiquait pas la devise locale. Ces deux problèmes sont faciles à résoudre. En utilisant l’interpolation de chaîne, vous pouvez spécifier des *chaînes de format* qui contrôlent la mise en forme de types particuliers. Modifiez l’appel à `Console.WriteLine` de l’exemple précédent de façon à inclure les chaînes de format pour les expressions de date et de prix, comme indiqué dans la ligne de code suivante :

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

Vous spécifiez une chaîne de format en plaçant après l’expression d’interpolation un signe deux-points (« : ») et la chaîne de format. « d » est une [chaîne de format de date et d’heure standard](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) qui représente le format de date courte. « C2 » est une [chaîne de format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) qui représente un nombre sous la forme d’une valeur monétaire avec deux chiffres après la virgule décimale.

Plusieurs types dans les bibliothèques .NET prennent en charge un ensemble prédéfini de chaînes de format. Il s’agit notamment de tous les types numériques et des types de date et d’heure. Pour obtenir une liste complète des types qui prennent en charge les chaînes de format, consultez [Chaînes de format et types de bibliothèque de classes .NET](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) dans l’article [Mise en forme des types dans .NET](../../../standard/base-types/formatting-types.md).

Essayez de modifier les chaînes de format dans votre éditeur de texte et, à chaque modification, relancez le programme pour voir comment celles-ci affectent la mise en forme de la date et de l’heure et la valeur numérique. Remplacez le « d » dans `{date:d}` par « t » (pour afficher le format d’heure courte), « y » (pour afficher l’année et mois) et « yyyy » (pour afficher l’année sous forme de nombre à quatre chiffres). Remplacez le « C2 » dans `{price:C2}` par « e » (pour la notation exponentielle) et « F3 » (pour une valeur numérique avec trois chiffres après la virgule).

En plus de contrôler la mise en forme, vous pouvez contrôler la largeur de champ et l’alignement des chaînes mises en forme qui sont incluses dans la chaîne de résultat. Dans la section suivante, vous allez découvrir comment effectuer cette opération.

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a>Contrôler la largeur de champ et l’alignement des expressions d’interpolation

En règle générale, lorsque le résultat d’une expression d’interpolation est mise en forme en chaîne, cette chaîne est inclue dans une chaîne de résultats sans espace de début ou de fin. Contrôler la largeur d’un champ et l’alignement du texte vous permet de rendre une sortie plus lisible, en particulier quand vous utilisez un jeu de données. Pour voir cela, remplacez tout le code dans votre éditeur de texte par le code suivant, puis tapez `dotnet run` pour exécuter le programme :

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

Les noms des auteurs sont alignés à gauche, et leurs titres sont alignés à droite. Vous spécifiez l’alignement en ajoutant une virgule (« , ») après une expression d’interpolation et en spécifiant la largeur de champ *minimum*. Si la valeur spécifiée est un nombre positif, le champ est aligné à droite. Si c’est un nombre négatif, le champ est aligné à gauche.

Essayez de supprimer les signes négatifs du code `{"Author",-25}` et `{title.Key,-25}`, puis réexécutez l’exemple, comme avec le code suivant :

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

Cette fois, les informations sur l’auteur sont alignées à droite.

Vous pouvez combiner un spécificateur d’alignement et une chaîne de format pour une même expression d’interpolation. Pour cela, spécifiez d’abord l’alignement, puis un signe deux-points et la chaîne de format. Remplacez tout le code à l’intérieur de la méthode `Main` par le code suivant, qui affiche trois chaînes mises en forme avec des largeurs de champ définies. Ensuite, exécutez le programme en entrant la commande `dotnet run`.

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

La sortie ressemble à ceci :

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

Vous avez terminé le tutoriel sur l’interpolation de chaîne.

Pour plus d’informations, consultez la rubrique [Interpolation de chaîne](../../language-reference/tokens/interpolated.md) et le tutoriel [Interpolation de chaîne en C#](../string-interpolation.md).
