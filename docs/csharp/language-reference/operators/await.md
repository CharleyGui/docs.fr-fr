---
title: Opérateur await – Informations de référence sur C#
ms.date: 07/13/2020
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 1941174d7e8d1676d11a13fa3ee6c7b84fe3952c
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063235"
---
# <a name="await-operator-c-reference"></a>Opérateur await (informations de référence sur C#)

L’opérateur `await` suspend l’évaluation de la méthode [async](../keywords/async.md) englobante jusqu’à ce que l’opération asynchrone représentée par son opérande se termine. Une fois l’opération asynchrone terminée, l’opérateur `await` retourne le résultat de l’opération, le cas échéant. Lorsque l' `await` opérateur est appliqué à l’opérande qui représente une opération déjà terminée, il retourne le résultat de l’opération immédiatement sans suspension de la méthode englobante. L’opérateur `await` ne bloque pas le thread qui évalue la méthode async. Lorsque l' `await` opérateur interrompt la méthode Async englobante, le contrôle retourne à l’appelant de la méthode.

Dans l’exemple suivant, la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retourne l’instance `Task<byte[]>`, qui représente une opération asynchrone qui produit un tableau d’octets au moment où elle se termine. Tant que l’opération n’est pas terminée, l’opérateur `await` suspend la méthode `DownloadDocsMainPageAsync`. Quand la méthode `DownloadDocsMainPageAsync` est suspendue, le contrôle est retourné à la méthode `Main`, qui est l’appelant de `DownloadDocsMainPageAsync`. La méthode `Main` s’exécute jusqu’à ce qu’elle ait besoin du résultat de l’opération asynchrone effectuée par la méthode `DownloadDocsMainPageAsync`. Une fois que tous les octets ont été obtenus par <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, le reste de la méthode `DownloadDocsMainPageAsync` est évalué. Après cela, le reste de la méthode `Main` est évalué.

[!code-csharp[await example](snippets/shared/AwaitOperator.cs)]

L’exemple précédent utilise la [ `Main` méthode Async](../../programming-guide/main-and-command-args/index.md), qui est possible à partir de C# 7,1. Pour plus d’informations, consultez la section [Opérateur await dans la méthode Main](#await-operator-in-the-main-method).

> [!NOTE]
> Pour obtenir une introduction à la programmation asynchrone, consultez [Programmation asynchrone avec async et await](../../programming-guide/concepts/async/index.md). La programmation asynchrone avec `async` et `await` suit le [modèle asynchrone basé sur les tâches](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Vous pouvez utiliser l’opérateur `await` uniquement dans une méthode, une [expression lambda](lambda-expressions.md) ou une [méthode anonyme](delegate-operator.md) modifiée par le mot clé [async](../keywords/async.md). Dans une méthode Async, vous ne pouvez pas utiliser l' `await` opérateur dans le corps d’une fonction synchrone, à l’intérieur du bloc d’une [instruction lock](../keywords/lock-statement.md)et dans un contexte [unsafe](../keywords/unsafe.md) .

L’opérande de l’opérateur `await` est généralement un des types .NET suivants : <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>. Cependant, n’importe quelle expression awaitable peut être l’opérande de l’opérateur `await`. Pour plus d’informations, consultez la section [Expressions awaitable](~/_csharplang/spec/expressions.md#awaitable-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Le type d’expression `await t` est `TResult` si le type d’expression `t` est <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.ValueTask%601>. Si le type de `t` est <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.ValueTask>, le type de `await t` est `void`. Dans les deux cas, si `t` lève une exception, `await t` lève à nouveau l’exception. Pour plus d’informations sur le gestion des exceptions, consultez la section [Exceptions dans les méthodes async](../keywords/try-catch.md#exceptions-in-async-methods) de l’article [Instruction try-catch](../keywords/try-catch.md).

Les `async` `await` Mots clés et sont disponibles dans C# 5 et versions ultérieures.

## <a name="asynchronous-streams-and-disposables"></a>Flux asynchrones et supprimables

À compter de C# 8,0, vous pouvez utiliser des flux asynchrones et des sources jetables.

Vous utilisez l' `await foreach` instruction pour consommer un flux de données asynchrone. Pour plus d’informations, consultez l’article sur les [ `foreach` instructions](../keywords/foreach-in.md) et la section relative aux [flux asynchrones](../../whats-new/csharp-8.md#asynchronous-streams) de l’article [Nouveautés de C# 8,0](../../whats-new/csharp-8.md) .

Vous utilisez l' `await using` instruction pour travailler avec un objet pouvant être supprimé de manière asynchrone, autrement dit, un objet d’un type qui implémente une <xref:System.IAsyncDisposable> interface. Pour plus d’informations, consultez la section [utilisation de Async jetable](../../../standard/garbage-collection/implementing-disposeasync.md#using-async-disposable) de l’article [implémentation d’une méthode DisposeAsync](../../../standard/garbage-collection/implementing-disposeasync.md) .

## <a name="await-operator-in-the-main-method"></a>Opérateur await dans la méthode Main

À compter de C# 7,1, la [ `Main` méthode](../../programming-guide/main-and-command-args/index.md), qui est le point d’entrée de l’application, peut retourner `Task` ou, ce qui lui permet `Task<int>` d’être asynchrone afin que vous puissiez utiliser l' `await` opérateur dans son corps. Dans les versions antérieures de C#, pour être certain que la méthode `Main` attend la fin d’une opération asynchrone, vous pouvez récupérer la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> de l’instance <xref:System.Threading.Tasks.Task%601> retournée par la méthode asyn correspondante. Pour les opérations asynchrones qui ne produisent pas de valeur, vous pouvez appeler la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Pour plus d’informations sur la façon de sélectionner la version linguistique, consultez contrôle de [version du langage C#](../configure-language-version.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions await](~/_csharplang/spec/expressions.md#await-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Suppr](../keywords/async.md)
- [Modèle de programmation asynchrone des tâches](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programmation asynchrone](../../async.md)
- [Async en détail](../../../standard/async-in-depth.md)
- [Procédure pas à pas : accès au Web avec Async et await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Didacticiel : générer et utiliser des flux asynchrones à l’aide de C# 8,0 et .NET Core 3,0](../../tutorials/generate-consume-asynchronous-stream.md)
