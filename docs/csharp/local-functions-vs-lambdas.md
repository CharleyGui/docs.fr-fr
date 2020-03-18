---
title: Fonctions locales et expressions lambda
description: Découvrez pourquoi des fonctions locales peuvent être un meilleur choix que les expressions lambda.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 13cc3fe47bbcd6a465347a6c991b2006586c78fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173339"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Fonctions locales comparées aux expressions lambda

À première vue, les [fonctions locales](programming-guide/classes-and-structs/local-functions.md) et les [expressions lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) sont très similaires. Souvent, le choix d’utiliser des expressions lambda ou des fonctions locales est une question de style et de préférences personnelles. Toutefois, il existe de réelles différences qui vous feront utiliser les unes ou les autres et que vous devez connaître.

Examinons les différences entre l’implémentation de l’algorithme factoriel avec une fonction locale et une expression lambda. Voici tout d’abord la version utilisant une fonction locale :

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Comparez cette implémentation avec une version qui utilise des expressions lambda :

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Les fonctions locales ont des noms. Les expressions lambda sont des méthodes anonymes qui sont affectées aux variables de type `Func` ou `Action`. Lorsque vous déclarez une fonction locale, les types d’arguments et le type de retour font partie de la déclaration de fonction. Au lieu de faire partie du corps de l’expression lambda, les types d’arguments et le type de retour font partie de la déclaration de type de variable de l’expression lambda. Ces deux différences peuvent rendre le code plus clair.

Les fonctions locales ont des règles différentes pour l’affectation définie par rapport aux expressions lambda. Une déclaration de fonction locale peut être référencée à partir de n’importe quel emplacement de code où elle est dans la portée. Une expression lambda doit être attribuée à une variable de délégué avant qu’elle puisse être consultée (ou appelée par le délégué faisant référence à l’expression lambda.) Notez que la version utilisant l’expression lambda doit `nthFactorial` déclarer et initialiser l’expression lambda, avant de la définir. Si ce n’est pas le cas, cela entraîne une erreur de compilation due au fait que vous référencez `nthFactorial` avant de lui affecter une valeur.
Ces différences font que les algorithmes récursifs sont plus faciles à créer en utilisant des fonctions locales. Vous pouvez déclarer et définir une fonction locale qui s’appelle elle-même. Les expressions lambda doivent être déclarées et une valeur par défaut doit leur être affectée avant qu’elles puissent être réaffectées à un corps référençant la même expression lambda.

Les règles d’affectation définies s’appliquent également à toutes les variables qui sont capturées par la fonction locale ou l’expression lambda. Les règles des fonctions locales comme celles des expression lambda exigent que toutes les variables capturées soient définitivement affectées au point marquant le moment où la fonction locale ou l’expression lambda est convertie en délégué. La différence est que les expressions lambda sont converties en délégués au moment où elles sont déclarées. Les fonctions locales sont converties en délégués uniquement lorsqu’elles sont utilisées en tant que délégué. Si vous déclarez une fonction locale et la référencez uniquement en l’appelant comme une méthode, elle ne sera pas convertie en délégué. Cette règle vous permet de déclarer une fonction locale à n’importe quel emplacement qui vous convient dans sa portée englobante. Il est courant de déclarer des fonctions locales à la fin de la méthode parente, après des instructions return.

Troisième différence, le compilateur peut effectuer une analyse statique qui active des fonctions locales de manière à affecter définitivement les variables capturées dans la portée englobante. Examinez cet exemple :

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Le compilateur peut déterminer que `LocalFunction` affecte `y` de manière définitive lorsqu’elle est appelée. Dans la mesure où `LocalFunction` est appelée avant l’instruction `return`, `y` est affecté de manière définitive à l’instruction `return`.

L’analyse qui active l’exemple d’analyse constitue la quatrième différence.
En fonction de leur utilisation, les fonctions locales peuvent éviter les allocations de tas qui sont toujours nécessaires pour les expressions lambda. Si une fonction locale n’est jamais convertie en délégué, et qu’aucune des variables capturées par la fonction locale n’est capturée par d’autres expressions lambda ou fonctions locales qui sont converties en délégués, le compilateur peut éviter les allocations de tas.

Penchons-nous sur cet exemple asynchrone :

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

La fermeture de cette expression lambda contient les variables `address`, `index` et `name`. Dans le cas des fonctions locales, l’objet qui implémente la fermeture peut être un type `struct`. Ce type de struct serait transmis par référence à la fonction locale. Cette différence d’implémentation évite une allocation.

L’instanciation nécessaire pour les expressions lambda signifie des allocations de mémoire supplémentaires, qui peuvent être un facteur influençant les performances dans les chemins de code critiques au niveau du temps.
Les fonctions locales n’entraînent pas cette charge supplémentaire. Dans l’exemple ci-dessus, la version à fonction locale a 2 allocations de moins que la version à expression lambda.

> [!NOTE]
> L’équivalent de cette méthode avec une fonction locale fait aussi appel à une classe pour la fermeture. Le fait que la fermeture d’une fonction locale soit implémentée en tant que `class` ou `struct` est un détail d’implémentation. Une fonction locale peut utiliser un type `struct` contrairement à une expression lambda qui utilise toujours un type `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Ultime avantage non décrit dans cet exemple : les fonctions locales peuvent être implémentées en tant qu’itérateurs, en utilisant la syntaxe `yield return` pour produire une séquence de valeurs. L’instruction `yield return` n’est pas autorisée dans les expressions lambda.

Alors que les fonctions locales peuvent sembler redondantes par rapport aux expressions lambda, elles ont en réalité des objectifs différents et des utilisations différentes.
Les fonctions locales sont plus efficaces dans le cas où vous voulez écrire une fonction qui est appelée seulement dans le contexte d’une autre méthode.
