---
title: Fonctions locales - Guide de programmation C#
description: Les fonctions locales en C# sont des méthodes privées qui sont imbriquées dans un autre membre et peuvent être appelées à partir de leur membre conteneur.
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 854ec7ab4a4cc637c0a5ad03e0344d2f1f7679d2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063300"
---
# <a name="local-functions-c-programming-guide"></a>Fonctions locales (Guide de programmation C#)

À compter de C# 7.0, C# prend en charge les *fonctions locales*. Les fonctions locales sont des méthodes privées d’un type qui sont imbriqués dans un autre membre. Elles ne peuvent être appelées qu’à partir de leur membre conteneur. Les fonctions locales peuvent être déclarées et appelées dans et à partir des éléments suivants :

- Méthodes, tout particulièrement les méthodes iterator et async
- Constructeurs
- Accesseurs de propriété
- Accesseurs d’événement
- Méthodes anonymes
- Expressions lambda
- Finaliseurs
- Autres fonctions locales

En revanche, les fonctions locales ne peuvent pas être déclarées à l’intérieur d’un membre expression-bodied.

> [!NOTE]
> Dans certains cas, vous pouvez utiliser une expression lambda pour implémenter la fonctionnalité également prise en charge par une fonction locale. Pour une comparaison, consultez [fonctions locales et expressions lambda](#local-functions-vs-lambda-expressions).

Les fonctions locales permettent de clarifier l’objectif de votre code. Toute personne lisant votre code peut voir que la méthode ne peut pas être appelée, sauf par la méthode conteneur. Pour les projets d’équipe, elles empêchent aussi à un autre développeur d’appeler par inadvertance la méthode directement à partir d’un autre emplacement dans la classe ou le struct.

## <a name="local-function-syntax"></a>Syntaxe des fonctions locales

Une fonction locale est définie en tant que méthode imbriquée à l’intérieur d’un membre conteneur. Sa définition présente la syntaxe suivante :

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Les fonctions locales peuvent utiliser les modificateurs [async](../../language-reference/keywords/async.md) et [unsafe](../../language-reference/keywords/unsafe.md).

Notez que toutes les variables locales définies dans le membre conteneur, y compris ses paramètres de méthode, sont accessibles dans la fonction locale.

Contrairement à une définition de méthode, une définition de fonction locale ne peut pas inclure le modificateur d’accès au membre. Comme toutes les fonctions locales sont privées, l’inclusion d’un modificateur d’accès, tel que le mot clé `private`, génère l’erreur de compilateur CS0106 : « Le modificateur « private » n’est pas valide pour cet élément ».

> [!NOTE]
> Avant C# 8,0, les fonctions locales ne peuvent pas inclure le `static` modificateur. L’inclusion du mot clé `static` génère l’erreur de compilateur CS0106 : « Le modificateur « static » n’est pas valide pour cet élément ».

Par ailleurs, les attributs ne peuvent pas être appliqués à la fonction locale ou à ses paramètres et paramètres de type.

L’exemple suivant définit une fonction locale nommée `AppendPathSeparator` qui est privée pour une méthode nommée `GetText` :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Fonctions locales et exceptions

L’une des caractéristiques intéressantes des fonctions locales est qu’elles permettent l’affichage immédiat des exceptions. Pour les itérateurs de méthode, les exceptions apparaissent uniquement au moment où la séquence retournée est énumérée, et non à la récupération de l’itérateur. Pour les méthodes async, les exceptions levées dans une méthode async sont observées quand la tâche retournée est attendue.

L’exemple suivant définit une méthode `OddSequence` qui énumère les nombres impairs dans une plage spécifiée. Sachant qu’elle passe à la méthode d’énumérateur `OddSequence` un nombre supérieur à 100, la méthode lève une exception <xref:System.ArgumentOutOfRangeException>. Comme le montre la sortie de l’exemple, l’exception apparaît uniquement au moment d’itérer les nombres, et non à la récupération de l’énumérateur.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Au lieu de cela, vous pouvez lever une exception au moment d’effectuer la validation et avant la récupération de l’itérateur en retournant l’itérateur à partir d’une fonction locale, comme dans l’exemple suivant.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Les fonctions locales peuvent être utilisées de manière similaire pour gérer les exceptions en dehors de l’opération asynchrone. D’ordinaire, les exceptions levées dans la méthode async nécessitent que vous examiniez les exceptions internes d’un <xref:System.AggregateException>. Les fonctions locales permettent à votre code d’échouer rapidement et à votre exception d’être à la fois levée et observée de manière synchrone.

L’exemple suivant utilise une méthode asynchrone nommée `GetMultipleAsync` visant à marquer une pause pendant un nombre défini de secondes et retourner une valeur qui est un multiple aléatoire de ce nombre de secondes. Le délai maximal est de 5 secondes ; une exception <xref:System.ArgumentOutOfRangeException> est obtenue si la valeur est supérieure à 5. Comme le montre l’exemple suivant, l’exception qui est levée quand une valeur de 6 est passée à la méthode `GetMultipleAsync` est encapsulée dans une exception <xref:System.AggregateException> après que la méthode `GetMultipleAsync` a démarré son exécution.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Comme nous l’avons fait avec l’itérateur de méthode, nous pouvons refactoriser le code de cet exemple pour assurer la validation avant l’appel de la méthode asynchrone. Comme le montre la sortie de l’exemple suivant, l’exception <xref:System.ArgumentOutOfRangeException> n’est pas encapsulée dans une exception <xref:System.AggregateException>.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Fonctions locales et expressions lambda

À première vue, les fonctions locales et les [expressions lambda](../../language-reference/operators/lambda-expressions.md) sont très similaires. Souvent, le choix d’utiliser des expressions lambda ou des fonctions locales est une question de style et de préférences personnelles. Toutefois, il existe de réelles différences qui vous feront utiliser les unes ou les autres et que vous devez connaître.

Examinons les différences entre l’implémentation de l’algorithme factoriel avec une fonction locale et une expression lambda. Voici tout d’abord la version utilisant une fonction locale :

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Comparez cette implémentation avec une version qui utilise des expressions lambda :

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Les fonctions locales ont des noms. Les expressions lambda sont des méthodes anonymes qui sont affectées aux variables de type `Func` ou `Action`. Lorsque vous déclarez une fonction locale, les types d’arguments et le type de retour font partie de la déclaration de fonction. Au lieu de faire partie du corps de l’expression lambda, les types d’arguments et le type de retour font partie de la déclaration de type de variable de l’expression lambda. Ces deux différences peuvent rendre le code plus clair.

Les fonctions locales ont des règles différentes pour l’affectation définie par rapport aux expressions lambda. Une déclaration de fonction locale peut être référencée à partir de n’importe quel emplacement de code où elle est dans la portée. Une expression lambda doit être assignée à une variable déléguée avant d’être accessible (ou appelée via le délégué référençant l’expression lambda). Notez que la version qui utilise l’expression lambda doit déclarer et initialiser l’expression lambda avant de la `nthFactorial` définir. Si ce n’est pas le cas, cela entraîne une erreur de compilation due au fait que vous référencez `nthFactorial` avant de lui affecter une valeur. Ces différences font que les algorithmes récursifs sont plus faciles à créer en utilisant des fonctions locales. Vous pouvez déclarer et définir une fonction locale qui s’appelle elle-même. Les expressions lambda doivent être déclarées et une valeur par défaut doit leur être affectée avant qu’elles puissent être réaffectées à un corps référençant la même expression lambda.

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

L’analyse qui active l’exemple d’analyse constitue la quatrième différence. En fonction de leur utilisation, les fonctions locales peuvent éviter les allocations de tas qui sont toujours nécessaires pour les expressions lambda. Si une fonction locale n’est jamais convertie en délégué, et qu’aucune des variables capturées par la fonction locale n’est capturée par d’autres expressions lambda ou fonctions locales qui sont converties en délégués, le compilateur peut éviter les allocations de tas.

Penchons-nous sur cet exemple asynchrone :

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

La fermeture de cette expression lambda contient les variables `address`, `index` et `name`. Dans le cas des fonctions locales, l’objet qui implémente la fermeture peut être un type `struct`. Ce type de struct serait transmis par référence à la fonction locale. Cette différence d’implémentation évite une allocation.

L’instanciation nécessaire pour les expressions lambda signifie des allocations de mémoire supplémentaires, qui peuvent être un facteur influençant les performances dans les chemins de code critiques au niveau du temps. Les fonctions locales n’entraînent pas cette charge supplémentaire. Dans l’exemple ci-dessus, la version à fonction locale a 2 allocations de moins que la version à expression lambda.

> [!NOTE]
> L’équivalent de cette méthode avec une fonction locale fait aussi appel à une classe pour la fermeture. Le fait que la fermeture d’une fonction locale soit implémentée en tant que `class` ou `struct` est un détail d’implémentation. Une fonction locale peut utiliser un type `struct` contrairement à une expression lambda qui utilise toujours un type `class`.

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Ultime avantage non décrit dans cet exemple : les fonctions locales peuvent être implémentées en tant qu’itérateurs, en utilisant la syntaxe `yield return` pour produire une séquence de valeurs. L’instruction `yield return` n’est pas autorisée dans les expressions lambda.

Alors que les fonctions locales peuvent sembler redondantes par rapport aux expressions lambda, elles ont en réalité des objectifs différents et des utilisations différentes. Les fonctions locales sont plus efficaces dans le cas où vous voulez écrire une fonction qui est appelée seulement dans le contexte d’une autre méthode.

## <a name="see-also"></a>Voir aussi

- [Méthodes](methods.md)
