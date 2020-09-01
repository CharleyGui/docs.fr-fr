---
description: foreach, instruction (C#)
title: foreach, instruction (C#)
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 2ed89fa52b2d3d369d668bf79ab32eaf7be18a8a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142074"
---
# <a name="foreach-in-c-reference"></a>foreach, instruction (C#)

L' `foreach` instruction exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l' <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface ou, comme le montre l’exemple suivant :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

L' `foreach` instruction n’est pas limitée à ces types. Vous pouvez l’utiliser avec une instance de n’importe quel type répondant aux conditions suivantes :

- un type a la méthode sans paramètre public `GetEnumerator` dont le type de retour est de type classe, struct ou interface.
- le type de retour de la méthode `GetEnumerator` contient la propriété publique `Current` et la méthode sans paramètre publique `MoveNext`, dont le type de retour est <xref:System.Boolean>.

L’exemple suivant utilise l' `foreach` instruction avec une instance du <xref:System.Span%601?displayProperty=nameWithType> type, qui n’implémente aucune interface :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

À compter de C# 7,3, si la propriété de l’énumérateur `Current` retourne une [valeur de retour de référence](ref.md#reference-return-values) ( `ref T` où `T` est le type d’un élément de collection), vous pouvez déclarer une variable d’itération avec le `ref` `ref readonly` modificateur ou, comme le montre l’exemple suivant :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

À compter de C# 8,0, vous pouvez utiliser l' `await foreach` instruction pour consommer un flux de données asynchrone, autrement dit, le type de collection qui implémente l' <xref:System.Collections.Generic.IAsyncEnumerable%601> interface. Chaque itération de la boucle peut être interrompue pendant que l’élément suivant est récupéré de manière asynchrone. L’exemple suivant montre comment utiliser l' `await foreach` instruction :

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

Par défaut, les éléments de flux sont traités dans le contexte capturé. Si vous souhaitez désactiver la capture du contexte, utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> méthode d’extension. Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, consultez [utilisation du modèle asynchrone basé sur des tâches](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md). Pour plus d’informations sur les flux asynchrones, consultez la section [Streams asynchrones](../../whats-new/csharp-8.md#asynchronous-streams) de l’article [nouveautés de C# 8,0](../../whats-new/csharp-8.md) .

À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md). Vous pouvez également quitter une `foreach` boucle à l’aide des instructions [goto](goto.md), [Return](return.md)ou [throw](throw.md) .

Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée. Si la collection source de l' `foreach` instruction est vide, le corps de la `foreach` boucle n’est pas exécuté et ignoré.

## <a name="type-of-an-iteration-variable"></a>Type d’une variable d’itération

Vous pouvez utiliser le `var` mot clé pour permettre au compilateur de déduire le type d’une variable d’itération dans l' `foreach` instruction, comme le montre le code suivant :

```csharp
foreach (var item in collection) { }
```

Vous pouvez également spécifier explicitement le type d’une variable d’itération, comme le montre le code suivant :

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

Dans le formulaire précédent, le type `T` d’un élément de collection doit être implicitement ou explicitement convertible en type `V` d’une variable d’itération. Si une conversion explicite de `T` en `V` échoue au moment de l’exécution, l' `foreach` instruction lève une exception <xref:System.InvalidCastException> . Par exemple, si `T` est un type de classe non scellé, `V` peut être n’importe quel type d’interface, même celui qui `T` n’est pas implémenté. Au moment de l’exécution, le type d’un élément de collection peut être celui qui dérive de `T` et implémente réellement `V` . Si ce n’est pas le cas, une <xref:System.InvalidCastException> exception est levée.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Mots clés C#](index.md)
- [Utilisation de foreach avec des tableaux](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for, instruction](for.md)
