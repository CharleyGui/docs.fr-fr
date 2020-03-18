---
title: Opérateur await – Informations de référence sur C#
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 9f541ae9c26eb12acdcf9a8c59bab98c4772c3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173443"
---
# <a name="await-operator-c-reference"></a>Opérateur await (informations de référence sur C#)

L’opérateur `await` suspend l’évaluation de la méthode [async](../keywords/async.md) englobante jusqu’à ce que l’opération asynchrone représentée par son opérande se termine. Une fois l’opération asynchrone terminée, l’opérateur `await` retourne le résultat de l’opération, le cas échéant. Quand l’opérateur `await` est appliqué à l’opérande qui représente l’opération déjà terminée, il retourne immédiatement le résultat de l’opération sans suspendre la méthode englobante. L’opérateur `await` ne bloque pas le thread qui évalue la méthode async. Lorsque `await` l’opérateur suspend la méthode d’async cisurant, le contrôle retourne à l’appelant de la méthode.

Dans l’exemple suivant, la méthode <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retourne l’instance `Task<byte[]>`, qui représente une opération asynchrone qui produit un tableau d’octets au moment où elle se termine. Tant que l’opération n’est pas terminée, l’opérateur `await` suspend la méthode `DownloadDocsMainPageAsync`. Quand la méthode `DownloadDocsMainPageAsync` est suspendue, le contrôle est retourné à la méthode `Main`, qui est l’appelant de `DownloadDocsMainPageAsync`. La méthode `Main` s’exécute jusqu’à ce qu’elle ait besoin du résultat de l’opération asynchrone effectuée par la méthode `DownloadDocsMainPageAsync`. Une fois que tous les octets ont été obtenus par <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, le reste de la méthode `DownloadDocsMainPageAsync` est évalué. Après cela, le reste de la méthode `Main` est évalué.

[!code-csharp[await example](snippets/AwaitOperator.cs)]

L’exemple précédent utilise la [méthode async `Main` ](../../programming-guide/main-and-command-args/index.md), qui est possible en commençant par C 7.1. Pour plus d’informations, consultez la section [Opérateur await dans la méthode Main](#await-operator-in-the-main-method).

> [!NOTE]
> Pour obtenir une introduction à la programmation asynchrone, consultez [Programmation asynchrone avec async et await](../../programming-guide/concepts/async/index.md). La programmation asynchrone avec `async` et `await` suit le [modèle asynchrone basé sur les tâches](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Vous pouvez utiliser l’opérateur `await` uniquement dans une méthode, une [expression lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ou une [méthode anonyme](delegate-operator.md) modifiée par le mot clé [async](../keywords/async.md). Dans le cadre d’une méthode async, vous ne pouvez pas utiliser l’opérateur `await` dans le corps d’une fonction synchrone, à l’intérieur du bloc d’une déclaration de [verrouillage,](../keywords/lock-statement.md)et dans un contexte [dangereux.](../keywords/unsafe.md)

L’opérande de l’opérateur `await` est généralement un des types .NET suivants : <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>. Cependant, n’importe quelle expression awaitable peut être l’opérande de l’opérateur `await`. Pour plus d’informations, consultez la section [Expressions awaitable](~/_csharplang/spec/expressions.md#awaitable-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

En commençant par C 8.0, `await foreach` vous pouvez utiliser l’instruction pour consommer un flux asynchrone de données. Pour plus d’informations, consultez l’article [ `foreach` de déclaration](../keywords/foreach-in.md) et la section [Asynchrone streams](../../whats-new/csharp-8.md#asynchronous-streams) de [l’article What’s new in C 8.0.](../../whats-new/csharp-8.md)

Le type d’expression `await t` est `TResult` si le type d’expression `t` est <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.ValueTask%601>. Si le type de `t` est <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.ValueTask>, le type de `await t` est `void`. Dans les deux cas, si `t` lève une exception, `await t` lève à nouveau l’exception. Pour plus d’informations sur le gestion des exceptions, consultez la section [Exceptions dans les méthodes async](../keywords/try-catch.md#exceptions-in-async-methods) de l’article [Instruction try-catch](../keywords/try-catch.md).

Les `async` `await` mots-clés et les mots clés sont disponibles dans C 5 et plus tard.

## <a name="await-operator-in-the-main-method"></a>Opérateur await dans la méthode Main

Commençant par C 7.1, `Task<int>`la `await` [ `Main` méthode](../../programming-guide/main-and-command-args/index.md), qui est `Task` le point d’entrée d’application, peut revenir ou, permettant d’être async afin que vous puissiez utiliser l’opérateur dans son corps. Dans les versions antérieures de C#, pour être certain que la méthode `Main` attend la fin d’une opération asynchrone, vous pouvez récupérer la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> de l’instance <xref:System.Threading.Tasks.Task%601> retournée par la méthode asyn correspondante. Pour les opérations asynchrones qui ne produisent pas de valeur, vous pouvez appeler la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Pour plus d’informations sur la façon de sélectionner la version linguistique, voir [la version linguistique C .](../configure-language-version.md)

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Expressions await](~/_csharplang/spec/expressions.md#await-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Async](../keywords/async.md)
- [Modèle de programmation asynchrone des tâches](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programmation asynchrone](../../async.md)
- [Async en détail](../../../standard/async-in-depth.md)
- [Procédure pas à pas : accès au web avec async et await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Tutorial: Générer et consommer des flux async à l’aide de C 8.0 et .NET Core 3.0](../../tutorials/generate-consume-asynchronous-stream.md)
