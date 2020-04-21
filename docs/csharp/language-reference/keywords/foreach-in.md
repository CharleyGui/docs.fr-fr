---
title: foreach, instruction (C#)
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738813"
---
# <a name="foreach-in-c-reference"></a>foreach, instruction (C#)

L’instruction `foreach` exécute une instruction ou un bloc d’instructions pour chaque élément d’une instance du type qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. L’instruction `foreach` n’est pas limitée à ces types et peut être appliquée à une instance de n’importe quel type répondant aux conditions suivantes :

- comporte la méthode `GetEnumerator` sans paramètre publique dont le retour est de type classe, struct ou interface,
- le type de retour de la méthode `GetEnumerator` contient la propriété publique `Current` et la méthode sans paramètre publique `MoveNext`, dont le type de retour est <xref:System.Boolean>.

En commençant par le C 7.3, si `Current` la propriété de l’énumérateur retourne une valeur de [rendement de référence](ref.md#reference-return-values) (où`ref T` `T` est le type de l’élément de collecte), vous pouvez déclarer la variable d’itération avec le ou `ref` `ref readonly` le modificateur.

À partir de C 8.0, l’opérateur `await` peut être appliqué à l’instruction `foreach` lorsque le type de collection implémente l’interface. <xref:System.Collections.Generic.IAsyncEnumerable%601> Chaque itération de la boucle peut être suspendue pendant que l’élément suivant est récupéré asynchronement. Par défaut, les éléments de flux sont traités dans le contexte capturé. Si vous souhaitez désactiver la capture du <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> contexte, utilisez la méthode d’extension. Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, voir [l’article sur la consommation du modèle asynchrone basé sur les tâches](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

À tout moment dans le bloc d’instructions `foreach`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md). Vous pouvez également `foreach` sortir d’une boucle par le [goto](goto.md), [retour](return.md), ou [lancer des](throw.md) déclarations.

Si l’instruction `foreach` est appliquée à `null`, une <xref:System.NullReferenceException> est levée. Si la collecte `foreach` source de la déclaration `foreach` est vide, le corps de la boucle n’est pas exécuté et ignoré.

## <a name="examples"></a>Exemples

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

L’exemple suivant montre l’utilisation de l’instruction `foreach` avec une instance de type <xref:System.Collections.Generic.List%601> qui implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> :

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

L’exemple suivant utilise l’instruction `foreach` avec une instance de type <xref:System.Span%601?displayProperty=nameWithType> qui n’implémente aucune interface :

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

L’exemple suivant utilise une variable d’itération `ref` pour définir la valeur de chaque élément dans un tableau stackalloc. La version `ref readonly` effectue une itération de la collection pour imprimer toutes les valeurs. La déclaration `readonly` utilise une déclaration de variable locale implicite. Les déclarations de variable implicite peuvent être utilisées avec les déclarations `ref` ou `ref readonly`, tout comme les déclarations de variable explicitement typée.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

L’exemple `await foreach` suivant utilise pour itérer une collection qui génère chaque élément asynchronement:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction foreach](~/_csharplang/spec/statements.md#the-foreach-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Mots-clés C](index.md)
- [Utilisation de l’avant-car avec des tableaux](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [pour déclaration](for.md)
