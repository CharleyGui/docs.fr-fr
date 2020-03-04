---
title: Opérateur await – Informations de référence sur C#
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 156c07561406caed6ebb4a354a5cc2b484c832db
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239506"
---
# <a name="await-operator-c-reference"></a>Opérateur await (informations de référence sur C#)

L’opérateur `await` suspend l’évaluation de la méthode [async](../keywords/async.md) englobante jusqu’à ce que l’opération asynchrone représentée par son opérande se termine. Une fois l’opération asynchrone terminée, l’opérateur `await` retourne le résultat de l’opération, le cas échéant. Quand l’opérateur `await` est appliqué à l’opérande qui représente l’opération déjà terminée, il retourne immédiatement le résultat de l’opération sans suspendre la méthode englobante. L’opérateur `await` ne bloque pas le thread qui évalue la méthode async. Lorsque l’opérateur `await` interrompt la méthode Async englobante, le contrôle retourne à l’appelant de la méthode.

Dans l’exemple suivant, la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retourne l’instance `Task<byte[]>`, qui représente une opération asynchrone qui produit un tableau d’octets au moment où elle se termine. Tant que l’opération n’est pas terminée, l’opérateur `await` suspend la méthode `DownloadDocsMainPageAsync`. Quand la méthode `DownloadDocsMainPageAsync` est suspendue, le contrôle est retourné à la méthode `Main`, qui est l’appelant de `DownloadDocsMainPageAsync`. La méthode `Main` s’exécute jusqu’à ce qu’elle ait besoin du résultat de l’opération asynchrone effectuée par la méthode `DownloadDocsMainPageAsync`. Une fois que tous les octets ont été obtenus par <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, le reste de la méthode `DownloadDocsMainPageAsync` est évalué. Après cela, le reste de la méthode `Main` est évalué.

[!code-csharp[await example](~/samples/snippets/csharp/language-reference/operators/AwaitOperator.cs)]

L’exemple précédent utilise la [méthode async `Main`](../../programming-guide/main-and-command-args/index.md), qui est possible à partir C# de 7,1. Pour plus d’informations, consultez la section [Opérateur await dans la méthode Main](#await-operator-in-the-main-method).

> [!NOTE]
> Pour obtenir une introduction à la programmation asynchrone, consultez [Programmation asynchrone avec async et await](../../programming-guide/concepts/async/index.md). La programmation asynchrone avec `async` et `await` suit le [modèle asynchrone basé sur les tâches](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Vous pouvez utiliser l’opérateur `await` uniquement dans une méthode, une [expression lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [méthode anonyme](delegate-operator.md) modifiée par le mot clé [async](../keywords/async.md). Dans une méthode async, vous ne pouvez pas utiliser l’opérateur `await` dans le corps d’une fonction synchrone, à l’intérieur du bloc d’une [instruction lock](../keywords/lock-statement.md) et dans un contexte [unsafe](../keywords/unsafe.md).

L’opérande de l’opérateur `await` est généralement un des types .NET suivants : <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>. Cependant, n’importe quelle expression awaitable peut être l’opérande de l’opérateur `await`. Pour plus d’informations, consultez la section [Expressions awaitable](~/_csharplang/spec/expressions.md#awaitable-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

À partir C# de 8,0, vous pouvez utiliser l’instruction `await foreach` pour consommer un flux de données asynchrone. Pour plus d’informations, consultez la section [Streams asynchrones](../../whats-new/csharp-8.md#asynchronous-streams) de l’article [Nouveautés de C# 8,0](../../whats-new/csharp-8.md) .

Le type d’expression `await t` est `TResult` si le type d’expression `t` est <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.ValueTask%601>. Si le type de `t` est <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.ValueTask>, le type de `await t` est `void`. Dans les deux cas, si `t` lève une exception, `await t` lève à nouveau l’exception. Pour plus d’informations sur le gestion des exceptions, consultez la section [Exceptions dans les méthodes async](../keywords/try-catch.md#exceptions-in-async-methods) de l’article [Instruction try-catch](../keywords/try-catch.md).

Les mots clés `async` et `await` sont disponibles C# dans 5 et versions ultérieures.

## <a name="await-operator-in-the-main-method"></a>Opérateur await dans la méthode Main

À partir C# de 7,1, la [méthode`Main`](../../programming-guide/main-and-command-args/index.md), qui est le point d’entrée de l’application, peut retourner `Task` ou `Task<int>`, ce qui lui permet d’être asynchrone afin que vous puissiez utiliser l’opérateur `await` dans son corps. Dans les versions antérieures de C#, pour être certain que la méthode `Main` attend la fin d’une opération asynchrone, vous pouvez récupérer la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> de l’instance <xref:System.Threading.Tasks.Task%601> retournée par la méthode asyn correspondante. Pour les opérations asynchrones qui ne produisent pas de valeur, vous pouvez appeler la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Pour plus d’informations sur la façon de sélectionner la version linguistique, consultez [ C# Language Versioning](../configure-language-version.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions await](~/_csharplang/spec/expressions.md#await-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [async](../keywords/async.md)
- [Modèle de programmation asynchrone des tâches](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programmation asynchrone](../../async.md)
- [Async en détail](../../../standard/async-in-depth.md)
- [Procédure pas à pas : accès au web avec async et await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Didacticiel : générer et utiliser des flux asynchrones à l’aide C# de 8,0 et .net Core 3,0](../../tutorials/generate-consume-asynchronous-stream.md)
