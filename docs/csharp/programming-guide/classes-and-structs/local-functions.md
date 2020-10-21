---
title: Fonctions locales - Guide de programmation C#
description: Les fonctions locales en C# sont des méthodes privées qui sont imbriquées dans un autre membre et peuvent être appelées à partir de leur membre conteneur.
ms.date: 10/16/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 75accda2e40443073274ece4d8964c13a0945dad
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332898"
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
<modifiers> <return-type> <method-name> <parameter-list>
```

Vous pouvez utiliser les modificateurs suivants avec une fonction locale :

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- [`static`](../../language-reference/keywords/static.md) (en C# 8,0 et versions ultérieures). Une fonction locale statique ne peut pas capturer les variables locales ou l’état de l’instance.
- [`extern`](../../language-reference/keywords/extern.md) (en C# 9,0 et versions ultérieures). Une fonction locale externe doit être `static` .

Toutes les variables locales définies dans le membre conteneur, y compris ses paramètres de méthode, sont accessibles dans une fonction locale non statique.

Contrairement à une définition de méthode, une définition de fonction locale ne peut pas inclure le modificateur d’accès au membre. Comme toutes les fonctions locales sont privées, l’inclusion d’un modificateur d’accès, tel que le mot clé `private`, génère l’erreur de compilateur CS0106 : « Le modificateur « private » n’est pas valide pour cet élément ».

L’exemple suivant définit une fonction locale nommée `AppendPathSeparator` qui est privée pour une méthode nommée `GetText` :

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

À compter de C# 9,0, vous pouvez appliquer des attributs à une fonction locale, à ses paramètres et à ses paramètres de type, comme le montre l’exemple suivant :

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

L’exemple précédent utilise un [attribut spécial](../../language-reference/attributes/nullable-analysis.md) pour aider le compilateur dans une analyse statique dans un contexte Nullable.

## <a name="local-functions-and-exceptions"></a>Fonctions locales et exceptions

L’une des caractéristiques intéressantes des fonctions locales est qu’elles permettent l’affichage immédiat des exceptions. Pour les itérateurs de méthode, les exceptions apparaissent uniquement au moment où la séquence retournée est énumérée, et non à la récupération de l’itérateur. Pour les méthodes async, les exceptions levées dans une méthode async sont observées quand la tâche retournée est attendue.

L’exemple suivant définit une `OddSequence` méthode qui énumère les nombres impairs dans une plage spécifiée. Sachant qu’elle passe à la méthode d’énumérateur `OddSequence` un nombre supérieur à 100, la méthode lève une exception <xref:System.ArgumentOutOfRangeException>. Comme le montre la sortie de l’exemple, l’exception apparaît uniquement au moment d’itérer les nombres, et non à la récupération de l’énumérateur.

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

Si vous placez la logique d’itérateur dans une fonction locale, les exceptions de validation d’argument sont levées lorsque vous récupérez l’énumérateur, comme le montre l’exemple suivant :

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

Vous pouvez utiliser des fonctions locales de la même façon avec les opérations asynchrones. Exceptions levées dans une surface de méthode Async lorsque la tâche correspondante est attendue. Les fonctions locales permettent à votre code d’échouer rapidement et à votre exception d’être à la fois levée et observée de manière synchrone.

L’exemple suivant utilise une méthode asynchrone nommée `GetMultipleAsync` visant à marquer une pause pendant un nombre défini de secondes et retourner une valeur qui est un multiple aléatoire de ce nombre de secondes. Le délai maximal est de 5 secondes ; une exception <xref:System.ArgumentOutOfRangeException> est obtenue si la valeur est supérieure à 5. Comme le montre l’exemple suivant, l’exception levée lorsqu’une valeur de 6 est passée à la `GetMultipleAsync` méthode est observée uniquement lorsque la tâche est attendue.

:::code language="csharp" source="snippets/local-functions/AsyncWithoutLocal.cs" :::

Comme avec l’itérateur de méthode, vous pouvez refactoriser l’exemple précédent et placer le code de l’opération asynchrone dans une fonction locale. Comme le montre la sortie de l’exemple suivant, le <xref:System.ArgumentOutOfRangeException> est levé dès que la `GetMultiple` méthode est appelée.

:::code language="csharp" source="snippets/local-functions/AsyncWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a>Fonctions locales et expressions lambda

À première vue, les fonctions locales et les [expressions lambda](../../language-reference/operators/lambda-expressions.md) sont très similaires. Souvent, le choix d’utiliser des expressions lambda ou des fonctions locales est une question de style et de préférences personnelles. Toutefois, il existe de réelles différences qui vous feront utiliser les unes ou les autres et que vous devez connaître.

Examinons les différences entre l’implémentation de l’algorithme factoriel avec une fonction locale et une expression lambda. Voici la version à l’aide d’une fonction locale :

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

Cette version utilise des expressions lambda :

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

### <a name="naming"></a>Dénomination

Les fonctions locales sont nommées explicitement comme les méthodes. Les expressions lambda sont des méthodes anonymes qui doivent être assignées à des variables d’un `delegate` type, généralement des `Action` `Func` types ou. Lorsque vous déclarez une fonction locale, le processus est semblable à l’écriture d’une méthode normale ; vous déclarez un type de retour et une signature de fonction.

### <a name="function-signatures-and-lambda-expression-types"></a>Signatures de fonctions et types d’expression lambda

Les expressions lambda s’appuient sur le type de la `Action` / `Func` variable qu’elles sont assignées pour déterminer les types d’arguments et de retour. Dans les fonctions locales, étant donné que la syntaxe est très similaire à l’écriture d’une méthode normale, les types d’argument et le type de retour font déjà partie de la déclaration de fonction.

### <a name="definite-assignment"></a>Assignation définie

Les expressions lambda sont des objets qui sont déclarés et assignés au moment de l’exécution. Pour qu’une expression lambda soit utilisée, elle doit être assignée de manière définitive : la `Action` / `Func` variable à laquelle elle sera assignée doit être déclarée et l’expression lambda assignée à celle-ci. Notez que `LambdaFactorial` doit déclarer et initialiser l’expression lambda `nthFactorial` avant de la définir. Si ce n’est pas le cas, cela entraîne une erreur de compilation due au fait que vous référencez `nthFactorial` avant de lui affecter une valeur.

Les fonctions locales sont définies au moment de la compilation. Comme elles ne sont pas affectées à des variables, elles peuvent être référencées à partir de n’importe quel emplacement de code **où elles se trouvent dans la portée**; dans notre premier exemple `LocalFunctionFactorial` , nous pourrions déclarer notre fonction locale soit au-dessus soit au-dessous de l' `return` instruction et ne déclenchent aucune erreur du compilateur.

Ces différences font que les algorithmes récursifs sont plus faciles à créer en utilisant des fonctions locales. Vous pouvez déclarer et définir une fonction locale qui s’appelle elle-même. Les expressions lambda doivent être déclarées et une valeur par défaut doit leur être affectée avant qu’elles puissent être réaffectées à un corps référençant la même expression lambda.

### <a name="implementation-as-a-delegate"></a>Implémentation en tant que délégué

Les expressions lambda sont converties en délégués lorsqu’elles sont déclarées. Les fonctions locales sont plus flexibles dans la mesure où elles peuvent être écrites comme une méthode traditionnelle *ou* en tant que délégué. Les fonctions locales sont converties en délégués uniquement lorsqu’elles sont ***utilisées*** en tant que délégué.

Si vous déclarez une fonction locale et la référencez uniquement en l’appelant comme une méthode, elle ne sera pas convertie en délégué.

### <a name="variable-capture"></a>Capture de variables

Les règles d' [assignation définie](../../../../_csharplang/spec/variables.md#definite-assignment) affectent également toutes les variables capturées par la fonction locale ou l’expression lambda. Le compilateur peut effectuer une analyse statique qui permet aux fonctions locales d’affecter de manière définitive des variables capturées dans la portée englobante. Prenons l’exemple suivant :

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

Notez que lorsqu’une fonction locale capture des variables dans la portée englobante, la fonction locale est implémentée en tant que type délégué.

### <a name="heap-allocations"></a>Allocations de tas

En fonction de leur utilisation, les fonctions locales peuvent éviter les allocations de tas qui sont toujours nécessaires pour les expressions lambda. Si une fonction locale n’est jamais convertie en délégué, et si aucune des variables capturées par la fonction locale n’est capturée par d’autres expressions lambda ou fonctions locales converties en délégués, le compilateur peut éviter les allocations de tas.

Penchons-nous sur cet exemple asynchrone :

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

La fermeture de cette expression lambda contient les variables `address`, `index` et `name`. Dans le cas des fonctions locales, l’objet qui implémente la fermeture peut être un type `struct`. Ce type de struct serait transmis par référence à la fonction locale. Cette différence d’implémentation évite une allocation.

L’instanciation nécessaire pour les expressions lambda signifie des allocations de mémoire supplémentaires, qui peuvent être un facteur influençant les performances dans les chemins de code critiques au niveau du temps. Les fonctions locales n’entraînent pas cette charge supplémentaire. Dans l’exemple ci-dessus, la version des fonctions locales a deux allocations moins nombreuses que la version de l’expression lambda.

Si vous savez que votre fonction locale ne sera pas convertie en un délégué et qu’aucune des variables capturées par celle-ci n’est capturée par d’autres expressions lambda ou fonctions locales converties en délégués, vous pouvez vous assurer que votre fonction locale évite d’être allouée sur le tas en la déclarant comme une `static` fonction locale. Notez que cette fonctionnalité est disponible dans C# 8,0 et versions ultérieures.

> [!NOTE]
> L’équivalent de cette méthode avec une fonction locale fait aussi appel à une classe pour la fermeture. Le fait que la fermeture d’une fonction locale soit implémentée en tant que `class` ou `struct` est un détail d’implémentation. Une fonction locale peut utiliser un type `struct` contrairement à une expression lambda qui utilise toujours un type `class`.

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

### <a name="usage-of-the-yield-keyword"></a>Utilisation du `yield` mot clé

Ultime avantage non décrit dans cet exemple : les fonctions locales peuvent être implémentées en tant qu’itérateurs, en utilisant la syntaxe `yield return` pour produire une séquence de valeurs.

:::code language="csharp" source="snippets/local-functions/Program.cs" id="YieldReturn" :::

L' `yield return` instruction n’est pas autorisée dans les expressions lambda, consultez [Erreur du compilateur CS1621](../../misc/cs1621.md).

Alors que les fonctions locales peuvent sembler redondantes par rapport aux expressions lambda, elles ont en réalité des objectifs différents et des utilisations différentes. Les fonctions locales sont plus efficaces dans le cas où vous voulez écrire une fonction qui est appelée seulement dans le contexte d’une autre méthode.

## <a name="see-also"></a>Voir aussi

- [Méthodes](methods.md)
