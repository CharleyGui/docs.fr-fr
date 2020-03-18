---
title: Comment lancer en toute sécurité en utilisant l’appariement des motifs et l’est et en tant qu’opérateurs
description: Découvrez les techniques relatives aux critères spéciaux pour caster de manière sécurisée des variables vers un autre type. Vous pouvez utiliser les critères spéciaux, ainsi que les opérateurs is et as pour convertir des types de manière sécurisée.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 762f8135063f7256ce7a167c65013703d9249039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973091"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Comment lancer en toute sécurité en utilisant l’appariement des motifs et l’est et en tant qu’opérateurs

Dans la mesure où les objets sont polymorphes, une variable d’un type de classe de base peut contenir un [type](../programming-guide/types/index.md) dérivé. Pour accéder aux membres d’instance du type dérivé, il est nécessaire de réeffectuer un [cast](../programming-guide/types/casting-and-type-conversions.md) de la valeur vers le type dérivé. Toutefois, un cast risque de lever <xref:System.InvalidCastException>. C# fournit des instructions relatives aux [critères spéciaux](../pattern-matching.md), qui effectuent un cast de manière conditionnelle, uniquement en cas de réussite. C# fournit également les opérateurs [is](../language-reference/operators/type-testing-and-cast.md#is-operator) et [as](../language-reference/operators/type-testing-and-cast.md#as-operator) pour tester l’appartenance d’une valeur à un certain type.

Le code suivant illustre l’instruction `is` relative aux critères spéciaux. Il contient des méthodes qui testent un argument de méthode pour déterminer s’il s’agit d’un ensemble possible de types dérivés :

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

L’exemple précédent illustre quelques fonctionnalités de la syntaxe relative aux critères spéciaux. Les instructions `if (a is Mammal m)` et `if (o is Mammal m)` combinent le test à une assignation d’initialisation. L’assignation n’a lieu qu’en cas de réussite du test. La variable `m` se trouve uniquement dans l’étendue de l’instruction `if` incorporée, à laquelle elle a été assignée. Vous ne pouvez pas accéder à `m` plus tard dans la même méthode. Faites un essai dans la fenêtre interactive.

Vous pouvez également utiliser la même syntaxe pour tester si un [type de valeur nul a](../language-reference/builtin-types/nullable-value-types.md) une valeur, comme indiqué dans le code de l’échantillon suivant :

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

L’exemple précédent illustre d’autres fonctionnalités relatives aux critères spéciaux pour les conversions. Vous pouvez tester le modèle null d’une variable en vérifiant spécifiquement la valeur `null`. Quand la valeur runtime de la variable est `null`, une instruction `is` de vérification de type retourne toujours `false`. L’instruction `is` relative aux critères spéciaux n’autorise aucun type valeur Nullable, par exemple `int?` ou `Nullable<int>`. Toutefois, vous pouvez tester un autre type valeur. Les `is` modèles de l’exemple précédent ne se limitent pas aux types de valeur nuls. Vous pouvez également utiliser ces modèles pour tester si une variable `null`d’un type de référence a une valeur ou c’est .

L’exemple précédent montre également comment utiliser l’expression `is` relative aux critères spéciaux dans une instruction `switch`, où la variable peut avoir plusieurs types différents.

Pour déterminer si une variable a un type donné, mais sans l’assigner pour autant à une nouvelle variable, vous pouvez utiliser les opérateurs `is` et `as` pour les types référence et les types Nullable. Le code suivant montre comment utiliser les instructions `is` et `as`, qui faisaient partie du langage C# avant l’introduction des critères spéciaux permettant de déterminer l’existence ou non d’un type donné pour une variable :

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Comme vous pouvez le constater en comparant ce code avec le code utilisant les critères spéciaux, la syntaxe des critères spéciaux fournit des fonctionnalités plus robustes, car elle combine le test et l’assignation dans une seule instruction. Utilisez la syntaxe des critères spéciaux autant que possible.

Vous pouvez essayer ces échantillons en regardant le code dans notre [référentiel GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Vous pouvez aussi télécharger les exemples [sous forme de fichier zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
