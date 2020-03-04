---
title: Générer et consommer des flux asynchrones
description: Ce tutoriel avancé illustre des scénarios où la génération et la consommation de flux asynchrones permet de travailler plus naturellement avec des séquences de données pouvant être générées de façon asynchrone.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 2fab2917a26a1774ad73866fa0448dbf47c94583
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240091"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Didacticiel : générer et utiliser des flux asynchrones à l’aide C# de 8,0 et .net Core 3,0

C# 8.0 introduit des **flux asynchrones**, ce qui permet de modéliser une source de données en diffusion en continu lorsque les éléments du flux de données peuvent être récupérés ou générés de façon asynchrone. Les flux asynchrones sont basés sur de nouvelles interfaces introduites dans .NET Standard 2.1 et implémentées dans .NET Core 3.0 afin de fournir un modèle de programmation naturel pour les sources de données asynchrones en diffusion en continu.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - créer une source de données qui génère une séquence d’éléments de données de façon asynchrone ;
> - consommer cette source de données de façon asynchrone ;
> - reconnaître quand l’interface et la source de données nouvelles sont préférables aux séquences de données synchrones précédentes.

## <a name="prerequisites"></a>Composants requis

Vous devez configurer votre ordinateur pour exécuter .NET Core, y compris le C# compilateur 8,0. Le C# compilateur 8 est disponible à partir de [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou du [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download).

Vous devrez créer un [jeton d’accès GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) afin de pouvoir accéder au point de terminaison GitHub GraphQL. Sélectionnez les autorisations suivantes pour votre jeton d’accès GitHub :

- repo:status
- public_repo

Enregistrez le jeton d’accès à un endroit sûr afin de pouvoir l’utiliser pour accéder au point de terminaison de l’API GitHub.

> [!WARNING]
> Sécurisez votre jeton d’accès personnel. Tous les logiciels disposant de votre jeton d’accès personnel peuvent effectuer des appels d’API GitHub à l’aide de vos droits d’accès.

Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.

## <a name="run-the-starter-application"></a>Exécutez l’application de démarrage

Vous pouvez obtenir le code pour l’application de démarrage utilisée dans ce tutoriel dans notre référentiel [dotnet/samples](https://github.com/dotnet/samples), dossier [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start).

L’application de démarrage est une application console qui utilise l’interface [GitHub GraphQL](https://developer.github.com/v4/) pour récupérer des problèmes récents écrits dans le référentiel [dotnet/docs](https://github.com/dotnet/docs). Commencez par examiner le code suivant pour la méthode `Main` de l’application de démarrage :

[!code-csharp[StarterAppMain](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Vous pouvez soit définir une variable d’environnement `GitHubKey` sur votre jeton d’accès personnel, soit remplacer le dernier argument dans l’appel par `GenEnvVariable` avec votre jeton d’accès personnel. Ne placez pas votre code d’accès dans le code source si vous envisagez d’enregistrer la source avec d’autres utilisateurs, ou de la placer dans un référentiel de code source partagé.

Après la création du client de GitHub, le code dans `Main` crée un objet de rapport de progression et un jeton d’annulation. Une fois que ces objets sont créés, `Main` appelle `runPagedQueryAsync` pour récupérer les 250 problèmes créés les plus récents. Une fois cette tâche terminée, les résultats sont affichés.

Lorsque vous exécutez l’application de démarrage, vous pouvez faire quelques observations importantes concernant son fonctionnement.  Vous voyez la progression signalée pour chaque page retournée à partir de GitHub. Vous pouvez observer un temps de pause avant le retour de chaque nouvelle page de problèmes par GitHub. Enfin, les problèmes ne sont affichés que lorsque les 10 pages ont été récupérées à partir de GitHub.

## <a name="examine-the-implementation"></a>Examinez l’implémentation

L’implémentation révèle pourquoi vous avez observé le comportement décrit dans la section précédente. Examinez the code for `runPagedQueryAsync` :

[!code-csharp[RunPagedQueryStarter](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Concentrons-nous sur l’algorithme de pagination et sur la structure asynchrone du code précédent. (Vous pouvez consulter la [documentation de GitHub GraphQL](https://developer.github.com/v4/guides/) pour plus d’informations sur l’API GraphQL github.) La méthode `runPagedQueryAsync` énumère les problèmes de la plus récente à la plus ancienne. Elle a besoin de 25 problèmes par page et examine la structure `pageInfo` de la réponse pour continuer avec la page précédente. Cela suit la prise en charge standard de la pagination de GraphQL pour les réponses multipages. La réponse inclut un objet `pageInfo` qui contient une valeur `hasPreviousPages` et une valeur `startCursor` utilisées pour demander la page précédente. Les problèmes se trouvent dans le tableau `nodes`. La méthode `runPagedQueryAsync` ajoute ces nœuds à un tableau qui contient tous les résultats de toutes les pages.

Après la récupération et la restauration d’une page de résultats, `runPagedQueryAsync` signale la progression et vérifie l’annulation. Si l’annulation a été demandée, `runPagedQueryAsync` lève une <xref:System.OperationCanceledException>.

Plusieurs éléments de ce code peuvent être améliorés. Plus important encore, `runPagedQueryAsync` doit allouer du stockage pour tous les problèmes retournés. Cet exemple s’arrête à 250 problèmes, car la récupération de tous les problèmes ouverts nécessiterait beaucoup plus de mémoire pour stocker tous les problèmes récupérées. De plus, les protocoles pour la prise en charge de la progression et de l’annulation rendent l’algorithme plus difficile à comprendre lors de sa première lecture. Vous devez rechercher la classe de progression pour trouver le rapport de progression. Vous devez également suivre les communications via le <xref:System.Threading.CancellationTokenSource> et son <xref:System.Threading.CancellationToken> associé pour comprendre où l’annulation est demandée et où elle est accordée.

## <a name="async-streams-provide-a-better-way"></a>Les flux asynchrones sont mieux adaptés

Les flux asynchrones et la prise en charge associée du langage résolvent tous ces problèmes. Le code qui génère la séquence peut désormais utiliser `yield return` pour retourner des éléments dans une méthode qui a été déclarée avec le modificateur `async`. Vous pouvez consommer un flux asynchrone à l’aide une boucle `await foreach` tout comme vous consommez n’importe quelle séquence à l’aide d’une boucle `foreach`.

Ces nouvelles fonctionnalités de langage dépendent de trois nouvelles interfaces ajoutées à .NET Standard 2.1 et implémentées dans .NET Core 3.0 :

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

Ces trois interfaces sont très certainement familières à la plupart des développeurs C#. Elles se comportent de manière similaire à leurs équivalents synchrones :

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Il est possible que le type <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType> ne soit pas familier. Le struct `ValueTask` fournit une API similaire à la classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` est utilisé dans ces interfaces pour des raisons de performances.

## <a name="convert-to-async-streams"></a>Convertir en flux asynchrones

Ensuite, convertissez la méthode `runPagedQueryAsync` pour générer un flux asynchrone. Tout d’abord, modifiez la signature de `runPagedQueryAsync` pour retourner un `IAsyncEnumerable<JToken>` et supprimer les objets de jeton d’annulation et de progression de la liste de paramètres comme indiqué dans le code suivant :

[!code-csharp[FinishedSignature](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Le code de démarrage traite chaque page lorsqu’elle est récupérée, comme indiqué dans le code suivant :

[!code-csharp[StarterPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Remplacez ces trois lignes par le code suivant :

[!code-csharp[FinishedPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Vous pouvez également supprimer la déclaration de `finalResults` plus tôt dans cette méthode et l’instruction `return` qui suit la boucle que vous avez modifiée.

Vous avez terminé les modifications permettant de générer un flux asynchrone. La méthode terminée doit ressembler au code ci-dessous :

[!code-csharp[FinishedGenerate](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Ensuite, vous modifiez le code qui utilise la collection pour consommer le flux de données asynchrone. Recherchez dans `Main` le code suivant, qui traite l’ensemble des problèmes :

[!code-csharp[EnumerateOldStyle](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Remplacez-le par la boucle `await foreach` suivante :

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Vous pouvez obtenir le code du tutoriel terminé dans le référentiel [dotnet/samples](https://github.com/dotnet/samples), dossier [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished).

## <a name="run-the-finished-application"></a>Exécutez l'application terminée

Exécutez de nouveau l'application. Comparez son comportement avec le comportement de l’application de démarrage. La première page de résultats est énumérée dès qu’elle est disponible. Une pause peut être observée lorsque chaque nouvelle page est demandée et récupérée, puis les résultats de la page suivante sont rapidement énumérés. Le bloc `try` / `catch` n’est pas nécessaire pour gérer l’annulation : l’appelant peut arrêter l’énumération de la collection. Le rapport de progression est clair, car le flux asynchrone génère des résultats à mesure que chaque page est téléchargée. L’état de chaque problème renvoyé est inclus en toute transparence dans la boucle `await foreach`. Vous n’avez pas besoin d’un objet de rappel pour suivre la progression.

Vous pouvez voir des améliorations lors de l’utilisation de mémoire en examinant le code. Vous n’avez plus besoin d’allouer une collection pour stocker tous les résultats avant qu’ils ne soient énumérés. L’appelant peut déterminer comment utiliser les résultats et si une collection de stockage est nécessaire.

Exécutez les applications de démarrage et les applications terminées. Ceci vous permettra d’observer les différences entre les implémentations pour vous. À la fin de ce tutoriel, vous pouvez supprimer le jeton d’accès GitHub que vous avez créé au début. Si un attaquant arrive à accéder à ce jeton, il pourrait accéder aux API GitHub à l’aide de vos informations d’identification.
