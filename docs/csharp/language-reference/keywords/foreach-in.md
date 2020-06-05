---
title: foreach, instruction (C#)
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401886"
---
# <a name="foreach-in-c-reference"></a>foreach, instruction (C#)

L’instruction `foreach` exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. L' `foreach` instruction n’est pas limitée à ces types et peut être appliquée à une instance de n’importe quel type répondant aux conditions suivantes :

- comporte la méthode `GetEnumerator` sans paramètre publique dont le retour est de type classe, struct ou interface,
- le type de retour de la méthode `GetEnumerator` contient la propriété publique `Current` et la méthode sans paramètre publique `MoveNext`, dont le type de retour est <xref:System.Boolean>.

Dans la plupart des utilisations, `foreach` itère une `IEnumerable<T>` expression où chaque élément est de type `T` . Toutefois, les éléments peuvent être de n’importe quel type qui a une conversion implicite ou explicite à partir du type de la `Current` propriété. Si la `Current` propriété retourne `SomeType` , le type des éléments peut être :

- Toutes les classes de base de `SomeType` .
- L’une des interfaces implémentées par `SomeType` .

En outre, si `SomeType` est un `class` ou un `interface` et non `sealed` , le type d’éléments peut inclure :

- Tout type dérivé de `SomeType` .
- Toute interface arbitraire. Toute interface est autorisée, car toute interface peut être implémentée par une classe dérivée de ou implémentant `SomeType` .

Vous pouvez déclarer la variable d’itération à l’aide de n’importe quel type qui correspond aux règles précédentes. Si la conversion de `SomeType` en type de la variable d’itération requiert un cast explicite, cette opération peut lever une exception <xref:System.InvalidCastException> en cas d’échec de la conversion.

À compter de C# 7,3, si la propriété de l’énumérateur `Current` retourne une [valeur de retour de référence](ref.md#reference-return-values) ( `ref T` où `T` est le type de l’élément de collection), vous pouvez déclarer la variable d’itération avec le `ref` `ref readonly` modificateur ou.

À compter de C# 8,0, l' `await` opérateur peut être appliqué à l' `foreach` instruction lorsque le type de collection implémente l' <xref:System.Collections.Generic.IAsyncEnumerable%601> interface. Chaque itération de la boucle peut être interrompue pendant que l’élément suivant est récupéré de manière asynchrone. Par défaut, les éléments de flux sont traités dans le contexte capturé. Si vous souhaitez désactiver la capture du contexte, utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> méthode d’extension. Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, consultez l’article sur l' [utilisation du modèle asynchrone basé](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)sur des tâches.

À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md). Vous pouvez également quitter une `foreach` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .

Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée. Si la collection source de l' `foreach` instruction est vide, le corps de la `foreach` boucle n’est pas exécuté et ignoré.

## <a name="examples"></a>Exemples

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

L’exemple suivant montre l’utilisation de l’instruction `foreach` avec une instance de type <xref:System.Collections.Generic.List%601> qui implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

L’exemple suivant utilise l’instruction `foreach` avec une instance de type <xref:System.Span%601?displayProperty=nameWithType> qui n’implémente aucune interface :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

L’exemple suivant utilise une variable d’itération `ref` pour définir la valeur de chaque élément dans un tableau stackalloc. La version `ref readonly` effectue une itération de la collection pour imprimer toutes les valeurs. La déclaration `readonly` utilise une déclaration de variable locale implicite. Les déclarations de variable implicite peuvent être utilisées avec les déclarations `ref` ou `ref readonly`, tout comme les déclarations de variable explicitement typée.

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

L’exemple suivant utilise `await foreach` pour itérer une collection qui génère chaque élément de façon asynchrone :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Utilisation de foreach avec des tableaux](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for, instruction](for.md)
