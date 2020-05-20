---
title: Générer et consommer des flux asynchrones
description: Ce didacticiel avancé montre comment générer et utiliser des flux asynchrones. Les flux asynchrones offrent un moyen plus naturel de travailler avec des séquences de données qui peuvent être générées de façon asynchrone.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: fd9fed3469d18c919102640df7bb501b116f5e0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420368"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Didacticiel : générer et utiliser des flux asynchrones à l’aide de C# 8,0 et .NET Core 3,0

C# 8,0 introduit des **flux asynchrones**, qui modélisent une source de données de diffusion en continu. Les flux de données récupèrent et génèrent souvent des éléments de façon asynchrone. Les flux asynchrones s’appuient sur les nouvelles interfaces introduites dans .NET Standard 2,1. Ces interfaces sont prises en charge dans .NET Core 3,0 et versions ultérieures. Ils fournissent un modèle de programmation naturel pour les sources de données de streaming asynchrones.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - créer une source de données qui génère une séquence d’éléments de données de façon asynchrone ;
> - consommer cette source de données de façon asynchrone ;
> - Prendre en charge l’annulation et les contextes capturés pour les flux asynchrones.
> - reconnaître quand l’interface et la source de données nouvelles sont préférables aux séquences de données synchrones précédentes.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET Core, y compris le compilateur C# 8,0. Le compilateur C# 8 est disponible à partir de [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou du [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download).

Vous devrez créer un [jeton d’accès GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) afin de pouvoir accéder au point de terminaison GitHub GraphQL. Sélectionnez les autorisations suivantes pour votre jeton d’accès GitHub :

- repo:status
- public_repo

Enregistrez le jeton d’accès à un endroit sûr afin de pouvoir l’utiliser pour accéder au point de terminaison de l’API GitHub.

> [!WARNING]
> Sécurisez votre jeton d’accès personnel. Tous les logiciels disposant de votre jeton d’accès personnel peuvent effectuer des appels d’API GitHub à l’aide de vos droits d’accès.

Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.

## <a name="run-the-starter-application"></a>Exécutez l’application de démarrage

Vous pouvez obtenir le code pour l’application de démarrage utilisée dans ce didacticiel à partir du dépôt [dotnet/docs](https://github.com/dotnet/docs) dans le dossier [CSharp/tutoriels/AsyncStreams](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start) .

L’application de démarrage est une application console qui utilise l’interface [GitHub GraphQL](https://developer.github.com/v4/) pour récupérer des problèmes récents écrits dans le référentiel [dotnet/docs](https://github.com/dotnet/docs). Commencez par examiner le code suivant pour la méthode `Main` de l’application de démarrage :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

Vous pouvez soit définir une variable d’environnement `GitHubKey` sur votre jeton d’accès personnel, soit remplacer le dernier argument dans l’appel par `GenEnvVariable` avec votre jeton d’accès personnel. Ne placez pas votre code d’accès dans le code source si vous souhaitez partager la source avec d’autres utilisateurs. Ne téléchargez jamais de codes d’accès dans un référentiel source partagé.

Après la création du client de GitHub, le code dans `Main` crée un objet de rapport de progression et un jeton d’annulation. Une fois que ces objets sont créés, `Main` appelle `runPagedQueryAsync` pour récupérer les 250 problèmes créés les plus récents. Une fois cette tâche terminée, les résultats sont affichés.

Lorsque vous exécutez l’application de démarrage, vous pouvez faire quelques observations importantes concernant son fonctionnement.  Vous voyez la progression signalée pour chaque page retournée à partir de GitHub. Vous pouvez observer un temps de pause avant le retour de chaque nouvelle page de problèmes par GitHub. Enfin, les problèmes ne sont affichés que lorsque les 10 pages ont été récupérées à partir de GitHub.

## <a name="examine-the-implementation"></a>Examinez l’implémentation

L’implémentation révèle pourquoi vous avez observé le comportement décrit dans la section précédente. Examinez the code for `runPagedQueryAsync` :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

Concentrons-nous sur l’algorithme de pagination et sur la structure asynchrone du code précédent. (Vous pouvez consulter la [documentation de GitHub GraphQL](https://developer.github.com/v4/guides/) pour plus d’informations sur l’API GraphQL github.) La `runPagedQueryAsync` méthode énumère les problèmes du plus récent au plus ancien. Elle a besoin de 25 problèmes par page et examine la structure `pageInfo` de la réponse pour continuer avec la page précédente. Cela suit la prise en charge standard de la pagination de GraphQL pour les réponses multipages. La réponse inclut un objet `pageInfo` qui contient une valeur `hasPreviousPages` et une valeur `startCursor` utilisées pour demander la page précédente. Les problèmes se trouvent dans le tableau `nodes`. La méthode `runPagedQueryAsync` ajoute ces nœuds à un tableau qui contient tous les résultats de toutes les pages.

Après la récupération et la restauration d’une page de résultats, `runPagedQueryAsync` signale la progression et vérifie l’annulation. Si l’annulation a été demandée, `runPagedQueryAsync` lève une <xref:System.OperationCanceledException>.

Plusieurs éléments de ce code peuvent être améliorés. Plus important encore, `runPagedQueryAsync` doit allouer du stockage pour tous les problèmes retournés. Cet exemple s’arrête à 250 problèmes, car la récupération de tous les problèmes ouverts nécessiterait beaucoup plus de mémoire pour stocker tous les problèmes récupérées. Les protocoles de prise en charge des rapports de progression et de l’annulation rendent l’algorithme plus difficile à comprendre lors de sa première lecture. D’autres types et API sont impliqués. Vous devez suivre les communications via le <xref:System.Threading.CancellationTokenSource> et son associé <xref:System.Threading.CancellationToken> pour comprendre où l’annulation est demandée et où elle est accordée.

## <a name="async-streams-provide-a-better-way"></a>Les flux asynchrones sont mieux adaptés

Les flux asynchrones et la prise en charge associée du langage résolvent tous ces problèmes. Le code qui génère la séquence peut désormais utiliser `yield return` pour retourner des éléments dans une méthode qui a été déclarée avec le modificateur `async`. Vous pouvez consommer un flux asynchrone à l’aide une boucle `await foreach` tout comme vous consommez n’importe quelle séquence à l’aide d’une boucle `foreach`.

Ces nouvelles fonctionnalités de langage dépendent de trois nouvelles interfaces ajoutées à .NET Standard 2.1 et implémentées dans .NET Core 3.0 :

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

Ces trois interfaces sont très certainement familières à la plupart des développeurs C#. Elles se comportent de manière similaire à leurs équivalents synchrones :

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Il est possible que le type <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType> ne soit pas familier. Le struct `ValueTask` fournit une API similaire à la classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` est utilisé dans ces interfaces pour des raisons de performances.

## <a name="convert-to-async-streams"></a>Convertir en flux asynchrones

Ensuite, convertissez la méthode `runPagedQueryAsync` pour générer un flux asynchrone. Tout d’abord, modifiez la signature de `runPagedQueryAsync` pour retourner un `IAsyncEnumerable<JToken>` et supprimer les objets de jeton d’annulation et de progression de la liste de paramètres comme indiqué dans le code suivant :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

Le code de démarrage traite chaque page lorsqu’elle est récupérée, comme indiqué dans le code suivant :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

Remplacez ces trois lignes par le code suivant :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

Vous pouvez également supprimer la déclaration de `finalResults` plus tôt dans cette méthode et l’instruction `return` qui suit la boucle que vous avez modifiée.

Vous avez terminé les modifications permettant de générer un flux asynchrone. La méthode terminée doit ressembler au code suivant :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

Ensuite, vous modifiez le code qui utilise la collection pour consommer le flux de données asynchrone. Recherchez dans `Main` le code suivant, qui traite l’ensemble des problèmes :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

Remplacez-le par la boucle `await foreach` suivante :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

La nouvelle interface <xref:System.Collections.Generic.IAsyncEnumerator%601> dérive de <xref:System.IAsyncDisposable> . Cela signifie que la boucle précédente disposera de façon asynchrone le flux lorsque la boucle se terminera. Vous pouvez imaginer que la boucle ressemble au code suivant :

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

Par défaut, les éléments de flux sont traités dans le contexte capturé. Si vous souhaitez désactiver la capture du contexte, utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> méthode d’extension. Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, consultez l’article sur l' [utilisation du modèle asynchrone basé](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)sur des tâches.

Les flux asynchrones prennent en charge l’annulation en utilisant le même protocole que les autres `async` méthodes. Vous pouvez modifier la signature de la méthode d’itérateur Async comme suit pour prendre en charge l’annulation :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

L' <xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> attribut force le compilateur à générer du code pour le <xref:System.Collections.Generic.IAsyncEnumerator%601> qui rend le jeton passé `GetAsyncEnumerator` visible au corps de l’itérateur Async comme cet argument. Dans `runQueryAsync` , vous pouvez examiner l’état du jeton et annuler un travail supplémentaire si nécessaire.

Vous utilisez une autre méthode d’extension, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A> , pour transmettre le jeton d’annulation au flux asynchrone. Vous pouvez modifier la boucle en énumérant les problèmes comme suit :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

Vous pouvez obtenir le code du didacticiel terminé à partir du dépôt [dotnet/docs](https://github.com/dotnet/docs) dans le dossier [CSharp/tutoriels/AsyncStreams](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished) .

## <a name="run-the-finished-application"></a>Exécutez l'application terminée

Exécutez de nouveau l'application. Comparez son comportement avec le comportement de l’application de démarrage. La première page de résultats est énumérée dès qu’elle est disponible. Une pause peut être observée lorsque chaque nouvelle page est demandée et récupérée, puis les résultats de la page suivante sont rapidement énumérés. Le bloc `try` / `catch` n’est pas nécessaire pour gérer l’annulation : l’appelant peut arrêter l’énumération de la collection. Le rapport de progression est clair, car le flux asynchrone génère des résultats à mesure que chaque page est téléchargée. L’état de chaque problème renvoyé est inclus en toute transparence dans la `await foreach` boucle. Vous n’avez pas besoin d’un objet de rappel pour suivre la progression.

Vous pouvez voir des améliorations lors de l’utilisation de mémoire en examinant le code. Vous n’avez plus besoin d’allouer une collection pour stocker tous les résultats avant qu’ils ne soient énumérés. L’appelant peut déterminer comment utiliser les résultats et si une collection de stockage est nécessaire.

Exécutez les applications de démarrage et les applications terminées. Ceci vous permettra d’observer les différences entre les implémentations pour vous. À la fin de ce tutoriel, vous pouvez supprimer le jeton d’accès GitHub que vous avez créé au début. Si un attaquant arrive à accéder à ce jeton, il pourrait accéder aux API GitHub à l’aide de vos informations d’identification.
